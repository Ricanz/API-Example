
# Get Rekomendasi Dokter API Documentation

This document explains how to make a get doctor recomendation after reschedule request to the specified API endpoint using JavaScript's `fetch` API. This API currently use for `CMS` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetRekomendasiDokter`

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
        "kode_dokter": "435",
        "kode_poli": "857",
        "dsid": "6475",
        "tanggal_praktek": "01-01-2025"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "kode_dokter": "435",
        "kode_poli": "857",
        "dsid": "6475",
        "tanggal_praktek": "01-01-2025"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetRekomendasiDokter", requestOptions)
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
            "kode_dokter": "-793",
            "kode_poliklinik": "351",
            "status_dokter": "Praktek",
            "jam_praktek_awal": "12:00",
            "jam_praktek_akhir": "17:00",
            "dsid": "7171",
            "jenis_kelamin": "P",
            "kuota_pasien": {
                "total_kuota_dokter": null,
                "kuota_tersedia_dokter": null
            }
        },
        {
            "kode_dokter": "-793",
            "kode_poliklinik": "351",
            "status_dokter": "Praktek",
            "jam_praktek_awal": "12:00",
            "jam_praktek_akhir": "17:00",
            "dsid": "7171",
            "jenis_kelamin": "P",
            "kuota_pasien": {
                "total_kuota_dokter": null,
                "kuota_tersedia_dokter": null
            }
        },
        {
            "kode_dokter": "-793",
            "kode_poliklinik": "351",
            "status_dokter": "Praktek",
            "jam_praktek_awal": "12:00",
            "jam_praktek_akhir": "17:00",
            "dsid": "7171",
            "jenis_kelamin": "P",
            "kuota_pasien": {
                "total_kuota_dokter": null,
                "kuota_tersedia_dokter": null
            }
        },
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
