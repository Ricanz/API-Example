
# Get Info Jadwal Dokter API Documentation

This document explains how to make a get info jadwal dokter request to the specified API endpoint using JavaScript's `fetch` API. This API currently use for `Mobile` needed.
This API will retrieve data for the next 60 days to obtain information about days when doctors are not practicing.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetInfoJadwalDokter`

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
        "kode_dokter": "-721",
        "kode_poli": "347"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
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
fetch("https://simrs-api.example.com/api/v1/pass/GetInfoJadwalDokter", requestOptions)
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
            "tanggal_praktek": "18-01-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "19-01-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "20-01-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "25-01-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "26-01-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "27-01-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "01-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "02-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "03-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "08-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "09-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "10-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "15-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "16-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "17-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "22-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "23-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "24-02-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "01-03-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "02-03-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "03-03-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "08-03-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "09-03-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "10-03-2025",
            "status_praktek": "TP"
        },
        {
            "tanggal_praktek": "15-03-2025",
            "status_praktek": "TP"
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
- Fill the `status_praktek` with the doctor status value, example: `Praktek`, `Tidak Praktek`, `Cuti`
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
