
# Get Data Pasien API Documentation

This document explains how to make a get patient data (post) request to the specified API endpoint using JavaScript's `fetch` API. 
This API currently use for `Mobile` needed and will be needed for `create` or `update` patient data.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetDataPasien`

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
  "data": {
    "kodeprovider": "214",
    "jenis_identitas": "1",
    "nomor_identitas": "36740149675481",
    "jenis_pasien": "2",
    "data_diri": {
      "nama_lengkap_pasien": "NAOMA IVANA",
      "nama_panggilan": "-",
      "nomor_ktp": "3674014967548100",
      "email": "naomaivnch@gmail.com",
      "tanggal_lahir": "1987-04-21",
      "tempat_lahir": "SURAKARTA",
      "jenis_kelamin": "M",
      "golongan_darah": "O",
      "hubungan_keluarga": "pribadi", // kakak, adik, ibu, ayah, etc
      "alamat": "PERUM KELAPA GADING RT 3 RW 11",
      "provinsi": "-",
      "kota": "SUKOHARJO",
      "kecamatan": "BAKI",
      "kelurahan": "PURBAYAN",
      "kode_pos": ""
    }
  }
}
```

```javascript
const raw = JSON.stringify({
    "data": {
    "kodeprovider": "214",
    "jenis_identitas": "1",
    "nomor_identitas": "36740149675481",
    "jenis_pasien": "2",
    "data_diri": {
      "nama_lengkap_pasien": "NAOMA IVANA",
      "nama_panggilan": "-",
      "nomor_ktp": "3674014967548100",
      "email": "naomaivnch@gmail.com",
      "tanggal_lahir": "1987-04-21",
      "tempat_lahir": "SURAKARTA",
      "jenis_kelamin": "M",
      "golongan_darah": "O",
      "hubungan_keluarga": "pribadi",// kakak, adik, ibu, ayah, etc
      "alamat": "PERUM KELAPA GADING RT 3 RW 11",
      "provinsi": "-",
      "kota": "SUKOHARJO",
      "kecamatan": "BAKI",
      "kelurahan": "PURBAYAN",
      "kode_pos": ""
    }
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
fetch("https://simrs-api.example.com/api/v1/pass/GetDataPasien", requestOptions)
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
    "status": "success",
    "message": "Berhasil di simpan"
}
```

### Example Response (Error)
```json
{
    "code": 404,
    "status": "Not Found",
    "message": "Data tersebut tidak ada"
}
```

---

## Notes
- Ensure you have the correct `Authorization` credentials.
- Replace the `body` with the appropriate values for your use case.
- Replace the `jenis_identitas` with 1 for get data by nik or 2 for get data by rm
- Replace the `jenis_pasien` with the appropriate values for your use case. 1 for `new patient` and 2 for `old patient`
- New patient won't get `no_rm`.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
