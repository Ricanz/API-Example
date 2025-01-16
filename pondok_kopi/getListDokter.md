
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

Include the `Authorization` header with Bearer authentication credentials.

```javascript
const myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX");
```

---

## Body

Send the following form data in the request body:

```json
{
    "data":{
        "kodeprovider" : "214",
        "hari" : "Senin",
        "kode_poli": "343",
        "jenis_kelamin": "P" // P = Perempuan, L = Laki-laki
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "hari" : "Senin",
        "kode_poli": "343",
        "jenis_kelamin": "P" // P = Perempuan, L = Laki-laki
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
- Replace the `hari` with the appropriate values for your use case.
- Replace the `kode_poli` with the appropriate values for your use case.
- Replace the `jenis_kelamin` with the appropriate values for your use case. `P` for `Perempuan / Female` and `L` for `Laki-laki`
- Fill the `status_praktek` on the response with the doctor status value, example: `Praktek`, `Tidak Praktek`, `Cuti`
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
