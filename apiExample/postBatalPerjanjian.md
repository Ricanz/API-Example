
# Post Batal Perjanjian API Documentation

This document explains how to make a post batal perjanjian request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/PostBatalPerjanjian`

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
        "kode_booking":"24X10BHLS1",
        "alasan_batal":"Ganti Jadwal"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "kode_booking":"24X10BHLS1",
        "alasan_batal":"Ganti Jadwal"
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
fetch("https://simrs-api.example.com/api/v1/pass/PostBatalPerjanjian", requestOptions)
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
    "status": "Berhasil",
    "pesan": "Berhasil Dibatalkan"
}
```

### Example Response (Error)
```json
{
    "code": 400,
    "status": "Not Found",
    "message": "Kode Booking Tidak Di temukan"
}
```

---

## Notes
- Ensure you have the correct `Authorization` credentials.
- Replace the body request with the appropriate values for your use case.
- Replace the `kode_provider` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
