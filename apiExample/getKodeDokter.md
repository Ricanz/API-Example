
# Get Kode Dokter API Documentation

This document explains how to make a get kode dokter request to the specified API endpoint using JavaScript's `fetch` API. This API currently use for `CMS` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetKodeDokter`

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
        "kodeprovider" : "214"
    }
}
```

```javascript
const raw = JSON.stringify({
     "data":{
        "kodeprovider" : "214"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetKodeDokter", requestOptions)
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
            "nama_dokter": " Agung Prihananto,dr ",
            "kode_dokter": "-717",
            "poliklinik": "KLINIK UMUM"
        },
        {
            "nama_dokter": " Christiani Inawati,drg ",
            "kode_dokter": "-719",
            "poliklinik": "KLINIK UMUM"
        },
        {
            "nama_dokter": " Dewi Purnamaningsih PS,dr ",
            "kode_dokter": "-720",
            "poliklinik": "KLINIK UMUM"
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
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
