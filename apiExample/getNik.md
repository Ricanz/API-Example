
# Get NIK API Documentation

This document explains how to make a get nik request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetDaftarNIK`

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
        "jenis_identitas": "2",
        "nik" :"3674014967548100"
    }
}
```

```javascript
const raw = JSON.stringify({
  "data":{
        "kodeprovider" : "214",
        "jenis_identitas": "2",
        "nik" :"3674014967548100"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetDaftarNIK", requestOptions)
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
    "response": {
        "no_rm": "00-42-72-62",
        "nama_lengkap_pasien": "IDA BAGUS CAESAR N   DR",
        "nama_panggilan": "-",
        "nomor_ktp": "3314071011860002",
        "email": "idabaguscaesar@gmail.com",
        "ttl": "BALI 10-11-1986",
        "jenis_kelamin": "Laki-Laki",
        "golongan_darah": null,
        "alamat": "BONOREJO RT 2/15",
        "provinsi": "-",
        "kota": "SURAKARTA",
        "kecamatan": "BANJARSARI",
        "kelurahan": "NUSUKAN",
        "kode_pos": ""
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
- Replace the `nik` or `rm` with the appropriate values for your use case.
- Replace the `jenis_identitas` with 1 for get data by nik or 2 for get data by rm
- Replace the `kode_provider` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
