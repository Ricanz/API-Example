
# Get List Dokter API Documentation

This document explains how to make a get list doctor request to the specified API endpoint using JavaScript's `fetch` API. This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetListDokter`

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
        "tanggal_praktik" : "29-11-2024"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "tanggal_praktik" : "29-11-2024"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetListDokter", requestOptions)
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
            "kuota_pasien": {
                "total_kuota_dokter": null,
                "kuota_tersedia_dokter": null
            }
        },
        {
            "kode_dokter": "-717",
            "kode_poliklinik": "332",
            "status_dokter": "Praktek",
            "jam_praktek_awal": "07:00",
            "jam_praktek_akhir": "14:00",
            "dsid": "6236",
            "kuota_pasien": {
                "total_kuota_dokter": null,
                "kuota_tersedia_dokter": null
            }
        },
        {
            "kode_dokter": "-717",
            "kode_poliklinik": "332",
            "status_dokter": "Praktek",
            "jam_praktek_awal": "14:01",
            "jam_praktek_akhir": "21:00",
            "dsid": "6386",
            "kuota_pasien": {
                "total_kuota_dokter": null,
                "kuota_tersedia_dokter": null
            }
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
