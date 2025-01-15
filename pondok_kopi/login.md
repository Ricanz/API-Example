
# Login API Documentation

This document explains how to make a login request to the specified API endpoint using JavaScript's `fetch` API. 
`Make sure the endpoint, request and response is exact same!`

## Endpoint

**URL**:  
`https://simrs-api.example.com/api/v1/login`

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

| Field     | Value               |
|-----------|---------------------|
| `username`| `username`    |
| `password`| `password`         |

```javascript
const formdata = new FormData();
formdata.append("username", "username");
formdata.append("password", "password");
```

---

## Request Options

Set up the request with the appropriate method, headers, and body:

```javascript
const requestOptions = {
  method: "POST",
  headers: myHeaders,
  body: formdata,
  redirect: "follow"
};
```

---

## Fetch Example

Use the `fetch` API to send the request:

```javascript
fetch("https://simrs-api.example.com/api/v1/login", requestOptions)
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
  "token": "your-access-token",
}
```

### Example Response (Error)
```json
{
  "message": "Invalid username or password"
}
```

---

## Notes
- Ensure you have the correct `Authorization` credentials.
- Replace the `username` and `password` with the appropriate values for your use case.
- Handle sensitive information securely, avoiding hardcoding credentials in production environments.
