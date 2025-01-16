
# Get Resume API Documentation

This document explains how to make a get perusahaan request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetResume`

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
        "nik" :"32170259187628"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214",
        "nik" :"32170259187628"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetResume", requestOptions)
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
    "status": "OK",
    "response": {
        "1803310234": [
            {
                "dokter": "Ndarumurti Pangesti,dr.,SpPD-KEMD",
                "tgl_konsul": "31-03-2018",
                "nama_poli": "KLINIK SPESIALIS PENYAKIT DALAM",
                "resep": "Y",
                "resep": "Sudah pulang",
                "penjamin": "UMUM",
                "resume_medis": []
            }
        ],
        "1803290997": [
            {
                "dokter": "Ndarumurti Pangesti,dr.,SpPD-KEMD",
                "tgl_konsul": "29-03-2018",
                "nama_poli": "MEDICAL CHECK UP",
                "resep": "N",
                "resep": "Sudah pulang",
                "penjamin": "UMUM",
                "resume_medis": {
                    "tindakan": [
                        {
                            "nama_tindakan": "EKG",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "Administrasi MCU",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "Jasa Konsultasi Poliklinik Spesialis Pagi R2",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "Jasa Konsultasi Dokter Gigi Umum Pagi",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "Jasa Konsultasi Poliklinik Spesialis Pagi R2",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "Tread Mill",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "Thorax 1 Posisi (PA)",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "USG Abdomen",
                            "tgl_tindakan": "2018-03-29"
                        }
                    ]
                }
            }
        ],
        "1803290846": [
            {
                "dokter": "Nurcahya Ardian Bramantha,dr.,SpM",
                "tgl_konsul": "29-03-2018",
                "nama_poli": "POLIKLINIK SPESIALIS MATA",
                "resep": "N",
                "penjamin": "UMUM",
                "resume_medis": {
                    "tindakan": [
                        {
                            "nama_tindakan": "Pemeriksaan Rutin",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "Pendaftaran Poliklinik Spesialis Pagi",
                            "tgl_tindakan": "2018-03-29"
                        }
                    ],
                    "diagnosa": [
                        {
                            "nama": "H40.0 Glaucoma suspect",
                            "type_icd": "ICD10"
                        }
                    ]
                }
            }
        ],
        "1803290872": [
            {
                "dokter": "Kurniawan,MSc,dr.,SpPK",
                "tgl_konsul": "29-03-2018",
                "nama_poli": "LABORATORIUM",
                "resep": "N",
                "penjamin": "UMUM",
                "resume_medis": []
            }
        ],
        "1803290766": [
            {
                "dokter": "Ndarumurti Pangesti,dr.,SpPD-KEMD",
                "tgl_konsul": "29-03-2018",
                "nama_poli": "KLINIK SPESIALIS PENYAKIT DALAM",
                "resep": "N",
                "penjamin": "UMUM",
                "resume_medis": []
            }
        ],
        "1803290848": [
            {
                "dokter": "Putu Wijaya Kandhi,dr.,SpTHT-KL",
                "tgl_konsul": "29-03-2018",
                "nama_poli": "KLINIK SPESIALIS THT",
                "resep": "N",
                "penjamin": "UMUM",
                "resume_medis": {
                    "tindakan": [
                        {
                            "nama_tindakan": "Jasa Konsultasi Poliklinik Spesialis Sore & Minggu R2",
                            "tgl_tindakan": "2018-03-29"
                        },
                        {
                            "nama_tindakan": "Pendaftaran Poliklinik Spesialis Pagi",
                            "tgl_tindakan": "2018-03-29"
                        }
                    ]
                }
            }
        ]
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
- Replace the `nik` with the appropriate values for your use case.
- Replace the `kode_provider` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
