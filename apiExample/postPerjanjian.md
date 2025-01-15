
# Post Perjanjian API Documentation

This document explains how to make a post perjanjian request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/postPerjanjian`

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
  "data": {
    "kodeprovider": "214",
    "nomor_ktp": "3674014967548100",
    "dsid": "6759",
    "tanggal_perjanjian": "15-01-2025",
    "jam_perjanjian": "07:00",
    "kode_perusahaan": "-",
    "admedika": "y"
  }
}
```

```javascript
const raw = JSON.stringify({
    "data": {
    "kodeprovider": "214",
    "nomor_ktp": "3674014967548100",
    "dsid": "6759",
    "tanggal_perjanjian": "15-01-2025",
    "jam_perjanjian": "07:00",
    "kode_perusahaan": "-",
    "admedika": "y"
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
fetch("https://simrs-api.example.com/api/v1/pass/postPerjanjian", requestOptions)
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
    "pesan": "Berhasil",
    "data": {
        "nomor_booking": "25I01GSIA1",
        "nomor_antrian_reservasi": 1,
        "nomor_antrian_aktif": 0,
        "kode_dokter": "-793",
        "kode_poli": "356"
    }
}
```

### Example Response (Error)
```json
{
    "code": 400,
    "status": "Not Found",
    "message": "Sudah ada jadwal"
}
```
```json
{
    "code": 400,
    "status": "Not Found",
    "message": "Jadwal ini hanya ada di hari Rabu"
}
```

---

## Notes
- Ensure you have the correct `Authorization` credentials.
- Replace the body request with the appropriate values for your use case.
- Replace the `kode_provider` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
