
# Get Status Dokter API Documentation

This document explains how to make a get status doctor request to the specified API endpoint using JavaScript's `fetch` API. This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetStatusDokter`

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
    "data":{
        "kodeprovider" : "214",
        "tanggal_hari_ini" : "25-11-2024",
        "kode_dokter": "-721",
        "kode_poli": "347"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "tanggal_hari_ini" : "25-11-2024",
        "kode_dokter": "-721",
        "kode_poli": "347"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetStatusDokter", requestOptions)
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
            "tanggal_praktek": "25-11-2024",
            "status_praktek": "Praktek",
            "dsid": "5863",
            "waktu_awal": "08:00",
            "waktu_akhir": "12:30"
        },
        {
            "tanggal_praktek": "25-11-2024",
            "status_praktek": "Praktek",
            "dsid": "5864",
            "waktu_awal": "16:00",
            "waktu_akhir": "17:00"
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
- Replace the `kode_provider` with the appropriate values for your use case.
- Replace the `tanggal_praktek` with the date you want to get the data.
- Fill the `status_praktek` with the doctor status value, example: `Praktek`, `Tidak Praktek`, `Cuti`
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
