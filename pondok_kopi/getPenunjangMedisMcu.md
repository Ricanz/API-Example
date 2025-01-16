
# Get MCU Penunjang Medis API Documentation

This document explains how to make a get perusahaan request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetMcuPenunjangMedis`

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
        "nik" :"3674014973468116",
        "jenis_penunjang_medis" : "1"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "nik" :"3674014973468116",
        "jenis_penunjang_medis" : "1"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetMcuPenunjangMedis", requestOptions)
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
    "success": 200,
    "data": {
        "kode_booking": "24W12QTNC1",
        "pemeriksaan": {
            "30945": {
                "tanggal_order": "02 December 2024 11:28",
                "nama_tindakan": "Uji Darah Lengkap",
                "pemeriksaan_lab": [
                    {
                        "nama_pemeriksaan": "Analisa Cairan Lambung"
                    }
                ],
                "hasil_lab": "http://172.10.0.47/devel/api_mobile.php?mod=api_mobile&cmd=GetPDFLab&id=30945",
                "hasil_pdf_api": "Tidak Ada File PDF dari Bridging"
            }
        }
    }
}
```

### Example Response (Error)
```json
{
    "success": 0,
    "message": "Tidak ada data order laboratorium"
}
```

---

## Notes
- Ensure you have the correct `Authorization` credentials.
- Replace the `nik` with the appropriate values for your use case.
- Replace the `jenis_penunjang_medis` with 1 for `mcu` and 2 for `outside the mcu`
- Replace the `kode_provider` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
