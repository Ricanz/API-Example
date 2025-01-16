
# Cancel Reservasi API Documentation

This document explains how to make a post cancel reservation request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://admedika-api.example.com/api/v1/external/reservation/faskesCancel`

**Method**:  
`POST`

---

## Headers

Include the `Authorization` header with Bearer authentication credentials.

```javascript
const myHeaders = new Headers();
myHeaders.append("ad-api-key", " XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX");
```

---

## Body

Send the following form data in the request body:

```json
{
  "data": {
    "kode_booking": "24U10LZEN1",
    "description": "Faskes melakukan pembatalan perjanjian"
  }
}
```

```javascript
const raw = JSON.stringify({
    "data": {
        "kode_booking": "24U10LZEN1",
        "description": "Faskes melakukan pembatalan perjanjian"
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
fetch("https://admedika-api.example.com/api/v1/external/reservation/faskesCancel", requestOptions)
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
    "code": 1782,
    "status": "SUCCESS",
    "message": "Berhasil melakukan pembatalan reservasi.",
    "data": {
        "reservation_no": "24P10VBGC1",
        "reservation_status": "CANCELLED",
        "reservation_status_detail": "FASKESCANCELLED",
        "updated_at": "2024-10-08T08:57:36.450Z"
    }
}
```

### Example Response (Error)
```json
{
    "code": 404,
    "status": "Not Found",
    "message": "Kode booking tidak ditemukan"
}
```

---

## Notes
- Ensure you have the correct `Authorization` credentials.
- Replace the body request with the appropriate values for your use case.
- Replace the `kode_provider` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.