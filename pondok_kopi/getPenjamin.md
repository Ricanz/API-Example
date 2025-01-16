
# Get Penjamin API Documentation

This document explains how to make a get penjamin request to the specified API endpoint using JavaScript's `fetch` API. 
 This API currently use for `Mobile` needed.
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/pass/GetPenjamin`

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
        "kodeprovider" : "214"
    }
}
```

```javascript
const raw = JSON.stringify({
    "data":{
        "kodeprovider" : "214"
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
fetch("https://simrs-api.example.com/api/v1/pass/GetPenjamin", requestOptions)
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
            "kode_asuransi": "PLN PURWOSARI",
            "nama_asuransi": "11645"
        },
        {
            "kode_asuransi": "BANK BRI",
            "nama_asuransi": "11660"
        },
        {
            "kode_asuransi": "PT. Sarana Usaha sejahtera Insan Palapa (TELKOMEDIKA)",
            "nama_asuransi": "11661"
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
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
