
# Get Info Bed API Documentation

This document explains how to make a get info bed request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetInfoBed`

**Method**:  
`POST`

---

## Headers

Include the `Authorization` header with Basic authentication credentials.

```javascript
const myHeaders = new Headers();
myHeaders.append("Authorization", "Basic XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX");
```

---

## Body

Send the following form data in the request body:

```json
{
    "data" : {
        "kodeprovider" : "214",
        "tanggal_input" : "2024-09-30"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data" : {
        "kodeprovider" : "214",
        "tanggal_input" : "2024-09-30"
    }
});
```

---

## Request Options

Set up the request with the appropriate method, headers, and body:

```javascript
const requestOptions = {
  method: "POST",
  headers: myHeaders,
  body: raw,
  redirect: "follow"
};
```

---

## Fetch Example

Use the `fetch` API to send the request:

```javascript
fetch("https://simrs-api.example.com/api/v1/pass/GetInfoBed", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.error(error));
```

---

## Response

The API will return the response in JSON format. Make sure to handle the result and errors accordingly.

### Example Response (Success)
```json
{
    "code": 200,
    "status": "Ok",
    "response": [
        {
            "jenis_kamar": "BANGSAL ISOLASI KAMAJAYA",
            "nama_ruangan": "-",
            "total_bed": "5",
            "total_bed_kosong": "0",
            "last_update": "2018-04-27 11:37:26.050794+07"
        },
        {
            "jenis_kamar": "BANGSAL ISOLASI NAKULA",
            "nama_ruangan": "-",
            "total_bed": "3",
            "total_bed_kosong": "0",
            "last_update": "2018-04-26 14:34:32.642289+07"
        },
        {
            "jenis_kamar": "HCU",
            "nama_ruangan": "-",
            "total_bed": "8",
            "total_bed_kosong": "0",
            "last_update": "2018-04-24 14:58:38.185269+07"
        }
    ]
}
```

### Example Response (Error)
```json
{
    "code": 404,
    "status": "Not Found",
    "message": "Data tidak ditemukan"
}
```

---

## Notes
- Ensure you have the correct `Authorization` credentials.
- Replace the `nik` or `rm` with the appropriate values for your use case.
- Replace the `jenis_identitas` with 1 for get data by nik or 2 for get data by rm
- Replace the `kode_provider` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
