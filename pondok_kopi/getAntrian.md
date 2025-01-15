
# Get Antrian API Documentation

This document explains how to make a get antrian request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetAntrian`

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
        "jenis_antrian" : "1"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "jenis_antrian" : "1"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetAntrian", requestOptions)
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
    "response": {
        "1": {
            "nama_dokter": "Agung Prihananto,dr",
            "no_antrian": "1",
            "ant_name": "POLIKLINIK HOME CARE",
            "estimasi": "14:01:00",
            "jenis_antrian": "1"
        },
        "2": {
            "nama_dokter": "Erwin Gunawan,dr.,SpOG",
            "no_antrian": "1",
            "ant_name": "POLIKLINIK SPESIALIS OBGYN",
            "estimasi": "11:30:00",
            "jenis_antrian": "1"
        },
        "3": {
            "nama_dokter": "Amru Sungkar,dr.,SpBP",
            "no_antrian": "1",
            "ant_name": "KLINIK Sp. BEDAH PLASTIK",
            "estimasi": "18:00:00"
        }
    }
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
