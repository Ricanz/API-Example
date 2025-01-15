
# Get Antrian Active API Documentation

This document explains how to make a get antrian active request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetAntrian_List`

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
        "nik" :"3173021008900007",
        "jenis_antrian" : "2"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "nik" :"3173021008900007",
        "jenis_antrian" : "2"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetAntrian_List", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.error(error));
```

---

## Response

The API will return the response in JSON format. Make sure to handle the result and errors accordingly.

### Example Response - Poli (Success)
```json
{
    "code": 200,
    "status": "Ok",
    "response": [
        {
            "jumlah_antrian": "0",
            "jumlah_antrian_dilayani": null
        }
    ]
}
```

### Example Response - Farmasi (Success)
```json
{
    "code": 200,
    "status": "Ok",
    "response": [
        {
            "jumlah_antrian": "0",
            "jumlah_antrian_dilayani": null,
            "no_antrian": "0",
            "no_antrian_aktif_racikan": null,
            "no_antrian_aktif_nonracikan": null
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
- Replace the `jenis_antrian` with 1 for `antrian poli`, 2 for `antrian farmasi` and 3 for `antrian penunjang medis`
- Replace the `kode_provider` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.