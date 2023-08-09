---
title: API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - python
  - shell

toc_footers:
  - <a href='https://beewant.com/landing#requestAccesForm'>Sign Up for a Developer Key</a>
  - <a href='https://beewant.com'>Documentation Powered by Beewant</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for Beewant API
---

# Overview

Welcome to the world of Beewant API! 🐝

The Beewant API opens the gateway to a realm of possibilities for seamless integration, innovation, and automation within the Beewant platform. Whether you're a developer, data scientist, or AI enthusiast, the Beewant API empowers you to interact programmatically with the heart of Beewant's collaborative and dynamic workspace environment.

With the Beewant API, you gain the ability to effortlessly manage projects, tasks, metadata, users, and more, all while harnessing the power of automation and customization. Unlock the potential to streamline workflows, extract insights, and create tailored solutions that align perfectly with your needs.

This documentation is your compass through the Beewant API landscape, offering clear and comprehensive guides, endpoints, and examples to help you embark on your journey of integrating Beewant's capabilities into your applications, workflows, and projects. So, whether you're seeking to supercharge your AI training process, enhance collaborative annotation, or build innovative AI-powered applications, the Beewant API is here to empower your creativity and efficiency.

Let's dive in and explore the endless horizons that the Beewant API has to offer! 🚀

## Response Format
> Here's an example of a JSON response structure:

```json
{
  "status_code": 200,
  "message": "Request successful",
  "data": {
    // Specific data related to the query
  }
}
```
When interacting with the Beewant API, the responses are provided in JSON format. JSON, or JavaScript Object Notation, is a widely adopted lightweight data-interchange format that offers simplicity and readability. This format is designed for both human understanding and easy machine parsing, making it an ideal choice for API responses.

The JSON response typically contains key-value pairs that provide valuable information about the outcome of your API request. Here's an overview of the common components you can expect in a Beewant API response:

- **status_code:** An HTTP status code that indicates the result of the API request. Common status codes include 200 (OK), 201 (Created), 400 (Bad Request), and 500 (Internal Server Error), among others.
- **message:** A human-readable message that accompanies the status code, offering additional context about the outcome of the request.
- **data:** This section contains the actual data payload returned by the API. The structure and content of this section vary based on the nature of the query. For instance, querying project details might return project-specific information, while a request for user profiles could include user-related data.

## Returned Attributes

When you make requests to the Beewant API, you will receive responses that contain various attributes providing information about the requested resource. These attributes offer valuable insights into the characteristics and details of the returned data. Below are some common attributes you might encounter in the API responses:

- **id:** A unique identifier assigned to the resource. This ID can be useful for referencing and further interactions.
- **name:** The name or title of the resource, providing a human-readable identifier.
- **created_at:** The timestamp indicating when the resource was created.
- **updated_at:** The timestamp indicating the last update to the resource.
- **status:** The status of the resource, indicating whether it's active, archived, or in another state.
- **description:** A brief description providing additional context about the resource.
- **metadata:** Additional metadata associated with the resource, which can include various custom fields or properties.

These attributes offer a consistent and standardized way to understand and manage the resources returned by the API.

> Example API Response

```json
{
  "status_code": 200,
  "message": "Request successful",
  "data": {
    "id": 123,
    "name": "Sample Project",
    "created_at": "2023-07-15T12:34:56Z",
    "updated_at": "2023-07-20T08:00:00Z",
    "status": "active",
    "description": "This is a sample project for demonstration purposes.",
    "metadata": {
      "custom_field": "value"
    }
  }
}
```




## Errors

<aside class="notice">
The error section is stored in a separate file located at <code>includes/_errors.md</code>. In Slate, you have the flexibility to organize your documentation into multiple files. Simply save them within the <code>includes</code> folder and include them in your <code>index.md</code> file's front matter. The files will be included in the order specified.
</aside>

When interacting with the Beewant API, you might encounter the following error codes and their meanings:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- The provided API token is incorrect or missing.
403 | Forbidden -- Access to the requested resource is restricted to administrators.
404 | Not Found -- The requested resource could not be located.
405 | Method Not Allowed -- The requested method is not supported for this resource.
406 | Not Acceptable -- The requested format is not supported (e.g., requesting a non-JSON response).
410 | Gone -- The requested resource has been permanently removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- Your request rate exceeds the allowed limit. Please slow down.
500 | Internal Server Error -- An issue occurred on our server. Please retry later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

If you encounter any of these error codes while interacting with the Beewant API, refer to this section for insights into their meanings and potential resolutions.

## Additional Resources and Tutorials

To further enhance your understanding of utilizing the Beewant API effectively, we offer a range of resources and tutorials:

- **Python Tutorials:** Our collection of Python tutorials has been crafted to provide step-by-step guidance on various aspects of working with the Beewant API. These tutorials cover essential topics like authentication, diverse request types, handling responses, and more. Delve into our [Python Tutorial Section](https://beewant.com/python-tutorials) to access these valuable resources.

- **API Documentation:** For a comprehensive exploration of the Beewant API's capabilities and endpoints, refer to our official [API Documentation](https://beewant.com/api-docs). This documentation provides intricate insights into each API endpoint, encompassing details about request parameters, response attributes, and practical usage examples.

Whether you're a newcomer embarking on your API journey or an experienced developer seeking advanced insights, our tutorials and documentation are designed to empower you with a deep understanding of the Beewant API. If you encounter queries or require further assistance, don't hesitate to engage with our dedicated support team or vibrant community forums.

Embrace these resources to expand your expertise in seamlessly integrating the Beewant API into your projects!


# Authentication


Authentication is an essential process to ensure the secure access of Beewant's API resources, safeguarding sensitive data and interactions. The API employs a robust Token-based authentication mechanism, which offers a sophisticated layer of security. With Token-based authentication, every interaction with the API mandates the inclusion of a unique API token within the headers of your HTTP requests. This token serves as a digital "key," granting authorized access to the API's functionality and data repositories.

Token-based authentication enhances the security of your API interactions by eliminating the need to expose sensitive credentials like usernames and passwords directly in the requests. Instead, your token acts as a secure, revocable authorization mechanism. By embedding the token in the request headers, you're effectively asserting your identity and authorization level with each interaction, ensuring that only authorized users gain access to the requested resources.

## Obtaining an API Token
To obtain an API token:

1. Log in to your Beewant account.
2. Go to your profile settings.
3. Generate a new API token.
4. Copy the generated API token.

![Alt Text](images/API_token.png)


## Using the API Token
> To authorize, use this code:

```python
import requests

def get_api_response(endpoint, headers):
    url = f"http://beewant.com/api/{endpoint}"
    response = requests.get(url, headers=headers)
    return response

# Replace 'Token <YOUR_TOKEN>' with your actual API token
api_token = 'Token <YOUR_TOKEN>'
headers = {
    'Authorization': api_token,
}

# Replace 'projects' with the appropriate API endpoint
response = get_api_response('projects', headers)

print(response)
print(response.json())

```

```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/projects' \
     --header 'Authorization: Token <YOUR_TOKEN>'  
```


> Make sure to replace `<YOUR_TOKEN>` with your API key.

Include the API token in the headers of your API requests as follows:


`GET /api/projects HTTP/1.1`
`Host: beewant.com`
`Authorization: Token YOUR_API_TOKEN`



### API Method

- Method: `GET`
- Endpoint: `/projects`

### Query Parameters
Parameter | Type | Description
--------- | ------- | -----------
endpoint  | (str) | The specific API endpoint you want to access, such as 'projects', 'tasks', etc. This determines the type of data you're interacting with.
headers  | (dict) | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized.

### Query Return
<code>requests.Response</code>: The response object containing the API response. This response object allows you to access various properties, such as status codes, headers, and response content.

<aside class="notice">
Remember to replace <code>YOUR_API_TOKEN</code> with the actual API token obtained from your Beewant account. This structure provides a clear explanation of how to authenticate, obtain an API token, and use it in API requests.
</aside>



# Users

In the realm of collaborative annotation and data labeling, managing users efficiently is pivotal. Beewant provides a robust set of features for user management, allowing you to invite, assign roles, and streamline access to projects. This section explores the various methods and endpoints available for managing users within the Beewant platform's API. Whether you're looking to create a seamless annotation workflow or maintain data privacy through role-based access, the user management capabilities offered by Beewant empower you to optimize your project's collaboration and security.

## Getting a user token

> To authorize, use this code:

```python
import requests
url = "http://13.39.148.224/api/current-user/token"
payload={}
files={}
headers = {
  'Authorization': 'Token 486cb857e5d044a8dedf2bf289f3f3074eea430e',
}
response = requests.request("GET", url, headers=headers, data=payload, files=files)
print(response)

response.json()
```


```shell
curl --location --request GET 'http://13.39.148.224/api/current-user/token' \
--header 'Authorization: Token 486cb857e5d044a8dedf2bf289f3f3074eea430e'
```
> Make sure to replace `<YOUR_TOKEN>` with your API key.


To obtain your current user token through the Beewant API, you can use the `GET` method on the `/api/current-user/token endpoint`. This token is essential for authentication and enables you to access various endpoints securely. By retrieving your current user token, you ensure that your interactions with the Beewant platform are authenticated and authorized.

### API Method

- Method: `GET`
- Endpoint: `/api/current-user/token`

### Query Parameters

| Parameter | Default | Description |
| --- | --- | --- |
| `headers` | - | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

## Getting current user (my user)

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/current-user/whoami"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/current-user/whoami' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

To fetch information about the current user through the Beewant API, you can use the GET method on the /api/current-user/whoami endpoint. This action provides you with details about the currently authenticated user, including their profile information, roles, and permissions.

### API Method

- Method: `GET`
- Endpoint: `/api/current-user/whoami`


### Query Parameters

| Parameter | Default | Description |
| --- | --- | --- |
| `headers` | - | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

<aside class="notice">
Replace <code>ORG_ID</code> with the actual ID of the organization you want to retrieve settings for.</aside>

## Listing users

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/users/"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response)

response.json()
```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/users/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```
> Make sure to replace `<YOUR_TOKEN>` with your API key.

To retrieve a list of users within the Beewant platform using the Beewant API, you can use the `GET` method on the `/api/users/ endpoint`. This action provides you with a list of users registered within the platform, including their profile information.

### API Method

- Method: `GET`
- Endpoint: `/api/users/`

### Query Parameters

| Parameter | Default | Description |
| --- | --- | --- |
| `headers` | - | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized |

<aside class="notice">
Replace <code>&lt;YOUR_TOKEN&gt;</code> with your actual token for authentication.</aside>

## Getting user info

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/users/USER_ID/"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/users/USER_ID/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

**API Method:** GET `/api/organizations/ORG_ID`

To retrieve the details of a specific user within the Beewant platform using the Beewant API, you can use the `GET` method on the `/api/users/USER_ID/ endpoint`. This action provides you with detailed information about a particular user's profile.

### API Method

- Method: `GET`
- Endpoint: `/api/users/USER_ID/`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `USER_ID` | The ID of the user for which you want to retrieve details. This ID uniquely identifies the specific user whose profile information you wish to view. |
| `headers` | The headers containing the Authorization token (e.g., 'Token &lt;YOUR_TOKEN&gt;'). This ensures your API requests are authenticated and authorized. |


<aside class="notice">
Replace <code>&lt;YOUR_TOKEN&gt;</code> with your actual token for authentication.</aside>

## Reseting user token

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/current-user/reset-token/"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("POST", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request POST 'http://beewant.com/api/current-user/reset-token/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

To reset the authentication token of the currently logged-in user within the Beewant platform using the Beewant API, you can use the `POST` method on the `/api/current-user/reset-token/` endpoint. This action allows you to generate a new token for the user, enhancing security and ensuring authorized access.

### API Method

- Method: `POST`
- Endpoint: `/api/current-user/reset-token/`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `headers` | The headers containing the Authorization token (e.g., 'Token &lt;YOUR_TOKEN&gt;'). This ensures your API requests are authenticated and authorized. |

<aside class="notice">
Replace <code>&lt;YOUR_TOKEN&gt;</code> with your actual token for authentication.</aside>

## Creating new user

> To authorize, use this code:

```python
import requests
import json
url = "http://beewant.com/api/users/"
payload = json.dumps({
  "first_name": "test",
  "last_name": "test",
  "username": "test test",
  "email": "user1@example.com",
  "phone": "07 00 00 00 00",
  "active_organization": ORG_ID
})
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
  'Content-Type': 'application/json',
}
response = requests.request("POST", url, headers=headers, data=payload)
print(response)

response.json()

```

```shell
# With shell, you can just pass the correct header with each request
curl --location --request POST 'http://beewant.com/api/users/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a' \
--header 'Content-Type: application/json' \
--data-raw '{
"first_name": "test",
"last_name": "test",
"username": "test test",
"email": "user1@example.com",
"phone": "07 00 00 00 00",
"active_organization": ORG_ID
}'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To create a new user within the Beewant platform using the Beewant API, you can use the `POST` method on the `/api/users/` endpoint. This action allows you to add a new user to the platform with specified details, such as name, email, phone number, and more.

### API Method

- Method: `POST`
- Endpoint: `/api/users/`

### Request Parameters

| Parameter | Description |
| --- | --- |
| `headers` | The headers containing the Authorization token (e.g., 'Token &lt;YOUR_TOKEN&gt;'). This ensures your API requests are authenticated and authorized. |
| `first_name` | The first name of the new user. |
| `last_name` | The last name of the new user. |
| `username` | The username for the new user. |
| `email` | The email address of the new user. |
| `phone` | The phone number of the new user. |
| `active_organization` | The ID of the organization to which the new user will be associated. |

<aside class="notice">
Replace <code>&lt;YOUR_TOKEN&gt;</code> with your actual token for authentication.<br>
Replace <code>&lt;ORG_ID&gt;</code> with the ID of the organization to which the user will be associated.</aside>

## Updating user details

> To authorize, use this code:

```python
import requests
import json
url = "http://beewant.com/api/users/USER_ID/"
payload = json.dumps({
  "first_name": "",
  "last_name": "",
  "username": "User2",
  "email": "test_user@beewant.fr",
  "last_activity": "2023-01-02T09:47:25.356680Z",
  "initials": "te",
  "phone": "",
  "active_organization": ORG_ID
})
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
  'Content-Type': 'application/json',
}
response = requests.request("PATCH", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request PATCH 'http://beewant.com/api/users/USER_ID/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a' \
--header 'Content-Type: application/json' \
--data-raw '{
    "first_name": "",
    "last_name": "",
    "username": "User2",
    "email": "test_user@beewant.fr",
    "last_activity": "2023-01-02T09:47:25.356680Z",
    "initials": "te",
    "phone": "",
    "active_organization": ORG_ID
}'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To update the details of a user within the Beewant platform using the Beewant API, you can use the `PATCH` method on the `/api/users/USER_ID/` endpoint. This action allows you to modify various information associated with a specific user, such as their name, email, phone number, and more.

### API Method

- Method: `PATCH`
- Endpoint: `/api/users/USER_ID/`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `headers` | The headers containing the Authorization token (e.g., 'Token &lt;YOUR_TOKEN&gt;'). This ensures your API requests are authenticated and authorized. |
| `USER_ID` | The ID of the user whose details you want to update. |
| `first_name` | The updated first name of the user. |
| `last_name` | The updated last name of the user. |
| `username` | The updated username for the user. |
| `email` | The updated email address of the user. |
| `last_activity` | The updated last activity timestamp of the user. |
| `initials` | The updated initials of the user. |
| `phone` | The updated phone number of the user. |
| `active_organization` | The updated ID of the organization to which the user is associated. |

<aside class="notice">
Replace <code>&lt;YOUR_TOKEN&gt;</code> with your actual token for authentication.<br>
Replace <code>&lt;USER_ID&gt;</code> with the ID of the user whose details you want to update.</aside>


## Deleting a user

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/users/USER_ID"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("DELETE", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request DELETE 'http://beewant.com/api/users/USER_ID' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To update the settings of a workspace, you can use the `DELETE` method on the `/api/organizations/ORG_ID` endpoint. This action allows you to modify various attributes of the workspace, such as its title, token, and creator.

### API Method

- Method: `DELETE`
- Endpoint: `/api/users/USER_ID`

### Request Parameters

| Parameter | Description |
| --- | --- |
| `headers` | The headers containing the Authorization token (e.g., 'Token &lt;YOUR_TOKEN&gt;'). This ensures your API requests are authenticated and authorized. |
| `USER_ID` | The ID of the user that you want to delete. |

<aside class="notice">
Replace <code>&lt;YOUR_TOKEN&gt;</code> with your actual token for authentication.<br>
Replace <code>&lt;USER_ID&gt;</code> with the ID of the user you want to delete.</aside>


# Workspace

This section provides information about managing your workspaces within the Beewant platform. 
Workspaces, at the heart of the Beewant API ecosystem, offer a dynamic and organized environment for effective project management. A workspace serves as a dedicated realm where projects are conceived, developed, and nurtured. Through the Beewant API, you can seamlessly access, create, modify, and monitor these workspaces, empowering your applications with the ability to orchestrate projects with precision and efficiency. Discover how the Beewant API empowers you to harness the power of workspaces, ensuring a structured and collaborative approach to project management and data annotation.

## Listing Your Workspaces

> To authorize, use this code:

```python
import requests

# Define the API endpoint URL
url = "http://beewant.com/api/organizations/"

# Replace 'YOUR_TOKEN_ID' with your actual API token
token_id = 'YOUR_TOKEN_ID'
headers = {
    'Authorization': f'Token {token_id}'
}

# Send a GET request to the API endpoint
response = requests.get(url, headers=headers)

# Print the response object, including status code and headers
print(response)

# Parse the JSON content from the response
data = response.json()

# Print the parsed JSON data
print(data)
```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/organizations/' \
    --header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a' 
```
> Make sure to replace `<YOUR_TOKEN>` with your API key.

**API Method:** GET `/projects`

To retrieve a list of your workspaces, you can use the `GET` method on the `/api/organizations/` endpoint. This action allows you to see all the workspaces associated with your account.

### API Method

- Method: `GET`
- Endpoint: `/api/organizations/`

### Query Parameters

| Parameter | Default | Description |
| --- | --- | --- |
| `headers` | - | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

## Getting the workspaces settings

> To authorize, use this code:

```python
import requests

# Define the API endpoint URL
url = "http://beewant.com/api/organizations/ORG_ID"

# Replace 'YOUR_TOKEN_ID' with your actual API token
token_id = 'YOUR_TOKEN_ID'
headers = {
    'Authorization': f'Token {token_id}'
}

# Send a GET request to the API endpoint
response = requests.get(url, headers=headers)

# Print the response object, including status code
print(response)

# Parse the JSON content from the response
data = response.json()

# Print the parsed JSON data
print(data)

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/organizations/ORG_ID' \
    --header 'Authorization: Token YOUR_TOKEN_ID'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

**API Method:** GET `/api/organizations/ORG_ID`

To retrieve workspace settings, you can use the `GET` method on the `/api/organizations/ORG_ID` endpoint. This action allows you to retrieve detailed information about a specific workspace associated with your account.

### API Method

- Method: `GET`
- Endpoint: `/api/organizations/ORG_ID`


### Query Parameters

| Parameter | Default | Description |
| --- | --- | --- |
| `headers` | - | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

<aside class="notice">
Replace <code>ORG_ID</code> with the actual ID of the organization you want to retrieve settings for.</aside>

## Listing Your Workspaces

> To authorize, use this code:

```python
import requests

# Define the API endpoint URL
url = "http://beewant.com/api/organizations/"

# Replace 'YOUR_TOKEN_ID' with your actual API token
token_id = 'YOUR_TOKEN_ID'
headers = {
    'Authorization': f'Token {token_id}'
}

# Send a GET request to the API endpoint
response = requests.get(url, headers=headers)

# Print the response object, including status code and headers
print(response)

# Parse the JSON content from the response
data = response.json()

# Print the parsed JSON data
print(data)
```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/organizations/' \
    --header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a' 
```
> Make sure to replace `<YOUR_TOKEN>` with your API key.

**API Method:** GET `/projects`

To retrieve a list of your workspaces, you can use the `GET` method on the `/api/organizations/` endpoint. This action allows you to see all the workspaces associated with your account.

### API Method

- Method: `GET`
- Endpoint: `/api/organizations/`

### Query Parameters

| Parameter | Default | Description |
| --- | --- | --- |
| `headers` | - | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

## Getting the workspaces settings

> To authorize, use this code:

```python
import requests

# Define the API endpoint URL
url = "http://beewant.com/api/organizations/ORG_ID"

# Replace 'YOUR_TOKEN_ID' with your actual API token
token_id = 'YOUR_TOKEN_ID'
headers = {
    'Authorization': f'Token {token_id}'
}

# Send a GET request to the API endpoint
response = requests.get(url, headers=headers)

# Print the response object, including status code
print(response)

# Print the parsed JSON data
print(response.json())

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/organizations/ORG_ID' \
    --header 'Authorization: Token YOUR_TOKEN_ID'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

**API Method:** GET `/api/organizations/ORG_ID`

To retrieve workspace settings, you can use the `GET` method on the `/api/organizations/ORG_ID` endpoint. This action allows you to retrieve detailed information about a specific workspace associated with your account.

### API Method

- Method: `GET`
- Endpoint: `/api/organizations/ORG_ID`


### Query Parameters

| Parameter | Default | Description |
| --- | --- | --- |
| `headers` | - | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

<aside class="notice">
Replace <code>ORG_ID</code> with the actual ID of the organization you want to retrieve settings for.</aside>

## Getting the workspace members list

> To authorize, use this code:

```python
import requests

# Define the API endpoint URL
url = "http://beewant.com/api/organizations/ORG_ID/memberships"

# Replace 'YOUR_TOKEN_ID' and 'ORG_ID' with your actual API token and organization ID
token_id = 'YOUR_TOKEN_ID'
org_id = 'YOUR_ORG_ID'
headers = {
    'Authorization': f'Token {token_id}'
}

# Send a GET request to the API endpoint
response = requests.get(url, headers=headers)

# Print the response object, including status code and headers
print(response)

# Parse the JSON content from the response
data = response.json()

# Print the parsed JSON data
print(data)

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/organizations/ORG_ID/memberships' \
    --header 'Authorization: Token YOUR_TOKEN_ID'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

**API Method:** GET `/api/organizations/ORG_ID/memberships`

To retrieve a list of memberships within a specific workspace, you can use the `GET` method on the `/api/organizations/ORG_ID/memberships` endpoint. This action allows you to see all the members associated with the workspace, including their roles and permissions.


### API Method

- Method: `GET`
- Endpoint: `/api/organizations/ORG_ID/memberships`


### Query Parameters

| Parameter | Description |
| --- | --- |
| `ORG_ID` | The ID of the organization for which you want to retrieve memberships. This ID identifies the specific workspace for which you want to view membership details. |
| `headers` | The headers containing the Authorization token (e.g., 'Token &lt;YOUR_TOKEN&gt;'). This ensures your API requests are authenticated and authorized. |

<aside class="notice">
Replace <code>ORG_ID</code> with the actual ID of the organization you want to retrieve settings for.</aside>

## Getting a workspace member settings

> To authorize, use this code:

```python
import requests

# Define the API endpoint URL
url = "http://beewant.com/api/organizations/ORG_ID/memberships"

# Replace 'YOUR_TOKEN_ID' and 'ORG_ID' with your actual API token and organization ID
token_id = 'YOUR_TOKEN_ID'
org_id = 'YOUR_ORG_ID'
headers = {
    'Authorization': f'Token {token_id}'
}

# Send a GET request to the API endpoint
response = requests.get(url, headers=headers)

# Print the response object, including status code and headers
print(response)

# Parse the JSON content from the response
data = response.json()

# Print the parsed JSON data
print(data)

```

```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/organizations/ORG_ID/memberships/USER_ID' \
    --header 'Authorization: Token YOUR_TOKEN_ID'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To retrieve details about a user's membership within a specific organization, you can use the `GET` method on the `/api/organizations/ORG_ID/memberships/USER_ID` endpoint. This action allows you to view membership information for a particular user within a specified organization.

**API Method:**

- Method: `GET`
- Endpoint: `/api/organizations/ORG_ID/memberships/USER_ID`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `ORG_ID` | The ID of the organization to which the user belongs. This ID identifies the specific workspace for which you want to view membership details. |
| `USER_ID` | The ID of the user for whom you want to retrieve membership details. This ID specifies the user whose membership information you want to access. |
| `headers` | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |


<aside class="notice">
Make sure to replace `ORG_ID` and `USER_ID` with the actual IDs of the organization and user you are querying.</aside>

## Creating a workspace

> To authorize, use this code:

```python
import requests
import json

# Define the API endpoint URL
url = "http://beewant.com/api/organizations/"

# Replace 'USER_ID' with the actual user ID
USER_ID = 'YOUR_USER_ID'

# Define the payload data
payload = json.dumps({
    "title": "YOUR_WORKSPACE_TITLE",
    "token": "YOUR_TOKEN_VALUE",
    "created_by": USER_ID
})

# Define the headers with the API key and content type
headers = {
    'Authorization': 'Token YOUR_API_TOKEN',
    'Content-Type': 'application/json',
}

# Send a POST request to create a new workspace
response = requests.post(url, headers=headers, data=payload)

# Print the response object, including status code and headers
print(response)

# Parse the JSON content from the response
data = response.json()

# Print the parsed JSON data
print(data)

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/organizations/ORG_ID/memberships' \
    --header 'Authorization: Token YOUR_TOKEN_ID'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To create a new workspace within your organization, you can utilize the Beewant API's `POST` method on the `/api/organizations/` endpoint. This action requires you to provide certain parameters to successfully create the workspace.

**API Method:**

- Method: `GET`
- Endpoint: `/api/organizations/ORG_ID/memberships/USER_ID`

### Query Parameters

| Parameter    | Description                                                 |
|--------------|-------------------------------------------------------------|
| `title`      | Specifies the title or name of the resource.                |
| `description`| Provides a description or additional information about the resource. |
| `data`       | Contains the main data associated with the resource.        |
| `attributes` | Holds various attributes or properties of the resource.     |
| `relationships` | Defines relationships between the resource and other resources. |
| `meta`       | Contains metadata or additional contextual information.|


<aside class="notice">
Make sure to replace `ORG_ID` and `USER_ID` with the actual IDs of the organization and user you are querying.</aside>

## Updating team settings

> To authorize, use this code:

```python
import requests
import json

# Define the API endpoint URL
url = "http://beewant/api/organizations/ORG_ID"

# Replace 'YOUR_TOKEN_ID', 'ORG_ID', and 'YOUR_USER_ID' with actual values
token_id = 'YOUR_TOKEN_ID'
org_id = 'YOUR_ORG_ID'
user_id = 'YOUR_USER_ID'

payload = json.dumps({
  "title": "My Group",
  "token": "862303f04524daeff",
  "created_by": user_id
})

headers = {
  'Authorization': f'Token {token_id}',
  'Content-Type': 'application/json',
}

# Send a PATCH request to the API endpoint
response = requests.patch(url, headers=headers, data=payload)

# Print the response object, including status code and headers
print(response)

# Parse the JSON content from the response
data = response.json()

# Print the parsed JSON data
print(data)

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request PATCH 'http://beewant/api/organizations/ORG_ID' \
--header 'Authorization: Token <YOUR_TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
        "title": "My Group",
        "token": "862303f04524daeff",
        "created_by": USER_ID
    }'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To update the settings of a workspace, you can use the `PATCH` method on the `/api/organizations/ORG_ID` endpoint. This action allows you to modify various attributes of the workspace, such as its title, token, and creator.

### API Method

- **Method:** `PATCH`
- **Endpoint:** `/api/organizations/ORG_ID`

### Query Parameters

| Parameter    | Description                                                 |
|--------------|-------------------------------------------------------------|
| `title`      | Specifies the title or name of the resource.                |
| `description`| Provides a description or additional information about the resource. |
| `data`       | Contains the main data associated with the resource.        |
| `attributes` | Holds various attributes or properties of the resource.     |
| `relationships` | Defines relationships between the resource and other resources. |
| `meta`       | Contains metadata or additional contextual information.|


<aside class="notice">
Replace <code>ORG_ID</code>, <code>YOUR_TOKEN_ID</code>, <code>YOUR_USER_ID</code>, and other placeholders with the actual values you want to use for the update.</aside>

## Updating team member settings

> To authorize, use this code:

```python
import requests
import json

# Define the API endpoint URL
url = "http://beewant/api/organizations/ORG_ID"

# Replace 'YOUR_TOKEN_ID', 'ORG_ID', and 'YOUR_USER_ID' with actual values
token_id = 'YOUR_TOKEN_ID'
org_id = 'YOUR_ORG_ID'
user_id = 'YOUR_USER_ID'

payload = json.dumps({
  "title": "My Group",
  "token": "862303f04524daeff",
  "created_by": user_id
})

headers = {
  'Authorization': f'Token {token_id}',
  'Content-Type': 'application/json',
}

# Send a PATCH request to the API endpoint
response = requests.patch(url, headers=headers, data=payload)

# Print the response object, including status code and headers
print(response)

# Parse the JSON content from the response
data = response.json()

# Print the parsed JSON data
print(data)

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request PATCH 'http://beewant/api/organizations/ORG_ID' \
--header 'Authorization: Token <YOUR_TOKEN>' \
--header 'Content-Type: application/json' \
--data-raw '{
        "title": "My Group",
        "token": "862303f04524daeff",
        "created_by": USER_ID
    }'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To update the settings of a workspace, you can use the `PATCH` method on the `/api/organizations/ORG_ID` endpoint. This action allows you to modify various attributes of the workspace, such as its title, token, and creator.

### API Method

- **Method:** `PATCH`
- **Endpoint:** `/api/organizations/ORG_ID`

### Query Parameters

| Parameter   | Description                                                   |
| ----------- | ------------------------------------------------------------- |
| `ORG_ID`    | The ID of the organization for which you want to update settings. This ID identifies the specific workspace for which you want to modify attributes. |
| `headers`   | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |
| `title`     | The updated title for the workspace.                          |
| `token`     | The updated token for the workspace.                          |
| `created_by`| The updated creator of the workspace (User ID).               |



<aside class="notice">
Replace <code>ORG_ID</code>, <code>YOUR_TOKEN_ID</code>, <code>YOUR_USER_ID</code>, and other placeholders with the actual values you want to use for the update.</aside>


## Deleting a Workspace

> To authorize, use this code:

```python
import requests

# Define the API endpoint URL
url = "http://beewant/api/organizations/ORG_ID"

# Replace 'YOUR_TOKEN_ID' and 'ORG_ID' with your actual API token and organization ID
token_id = 'YOUR_TOKEN_ID'
org_id = 'YOUR_ORG_ID'
headers = {
    'Authorization': f'Token {token_id}'
}

# Send a DELETE request to the API endpoint
response = requests.delete(url, headers=headers)

# Print the response object, including status code and headers
print(response)

```


```shell
# With shell, you can just pass the correct header with each request
# With shell, you can just pass the correct header with each request
curl --location --request DELETE 'http://beewant/api/organizations/ORG_ID' \
    --header 'Authorization: Token YOUR_TOKEN_ID'

```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To delete a specific workspace, you can use the `DELETE` method on the `/api/organizations/ORG_ID` endpoint. This action removes the workspace, including all associated data and settings.

### API Method

- **Method:** `DELETE`
- **Endpoint:** `/api/organizations/ORG_ID`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `ORG_ID` | The ID of the organization you want to delete. This ID identifies the specific workspace to be removed. |
| `headers` | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |


<aside class="notice">
Replace <code>ORG_ID</code> with the actual ID of the organization you want to delete.</aside>

## Deleting a Workspace Membership

> To authorize, use this code:

```python
import requests

# Define the API endpoint URL
url = "http://13.39.148.224/api/organizations/ORG_ID/memberships/USER_ID"

# Replace 'YOUR_TOKEN_ID', 'ORG_ID', and 'USER_ID' with your actual API token, organization ID, and user ID
token_id = 'YOUR_TOKEN_ID'
org_id = 'YOUR_ORG_ID'
user_id = 'YOUR_USER_ID'
headers = {
    'Authorization': f'Token {token_id}'
}

# Send a DELETE request to the API endpoint
response = requests.delete(url, headers=headers)

# Print the response object, including status code and headers
print(response)

# Note: DELETE requests generally do not return content, so no need to parse JSON data

```


```shell
# With shell, you can just pass the correct header with each request
# With shell, you can just pass the correct header with each request
curl --location --request DELETE 'http://beewant/api/organizations/ORG_ID' \
    --header 'Authorization: Token YOUR_TOKEN_ID'

```

> Make sure to replace `<YOUR_TOKEN>` with your API key.


To remove a user's membership from a specific workspace, you can use the `DELETE` method on the `/api/organizations/ORG_ID/memberships/USER_ID` endpoint. This action allows you to remove a user from the membership list of the specified workspace.

### API Method

- **Method:** `DELETE`
- **Endpoint:** `/api/organizations/ORG_ID/memberships/USER_ID`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `ORG_ID` | The ID of the organization that contains the workspace from which you want to remove the membership. |
| `USER_ID` | The ID of the user you want to remove from the workspace's membership. |
| `headers` | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |


<aside class="notice">
Replace <code>ORG_ID</code> and <code>USER_ID</code> with the actual IDs of the organization and user you want to remove from the workspace's membership.</aside>

# Projects

Projects are a fundamental concept within the Beewant API that enable you to organize and manage your annotation and data labeling tasks effectively. A project represents a specific annotation task or a collection of related tasks. Projects in the Beewant API provide a structured environment to collaborate, assign roles, set up annotations, and gather insights from the annotated data. Each project is associated with a set of tasks, metadata, and settings that define how the annotation process should be carried out. Using the Beewant API, you can create, retrieve, update, and delete projects, allowing you to streamline your data annotation workflow and achieve accurate and valuable results.

## Listing your projects

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/projects/"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response)

response.json()
```


```shell
curl --location --request GET 'http://beewant.com/api/projects/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```
> Make sure to replace `<YOUR_TOKEN>` with your API key.


To retrieve a list of projects, you can use the `GET` method on the `/api/projects/ endpoint`. This action allows you to see all the projects associated with your account.

### API Method

- Method: `GET`
- Endpoint: `/api/projects/`

### Query Parameters

| Parameter | Default | Description |
| --- | --- | --- |
| `headers` | - | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

## Getting a project by ID

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/projects/PROJECT_ID/"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/projects/PROJECT_ID/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

To retrieve details of a specific project, you can use the `GET` method on the `/api/projects/PROJECT_ID/ endpoint`. This action allows you to view the specific details and configuration of the project.

### API Method

- Method: `GET`
- Endpoint: `/api/projects/PROJECT_ID/`


### Query Parameters

| Parameter   | Description |
| ----------- | ----------- |
| `PROJECT_ID` | The ID of the project for which you want to retrieve details. This ID identifies the specific project you want to view. |
| `headers`   | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

## Getting project tasks list

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/projects/PROJECT_ID/tasks/"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("GET", url, headers=headers, data=payload)
print(response)

response.json()
```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request GET 'http://beewant.com/api/projects/PROJECT_ID/tasks/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```
> Make sure to replace `<YOUR_TOKEN>` with your API key.

To retrieve a list of tasks within a specific project, you can use the `GET` method on the `/api/projects/PROJECT_ID/tasks endpoint`. This action allows you to see all the tasks associated with the project.

### API Method

- Method: `GET`
- Endpoint: `/api/projects/PROJECT_ID/tasks`

### Query Parameters

| Parameter   | Description |
| ----------- | ----------- |
| `PROJECT_ID` | The ID of the project for which you want to retrieve tasks. This ID identifies the specific project you want to view tasks for. |
| `headers`   | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

<aside class="notice">
Replace <code>PROJECT_ID</code> with the actual ID of the project you want to retrieve tasks for.</aside>

## Creating new project


> To authorize, use this code:

```python
import requests
import json
url = "http://beewant.com/api/projects/"
payload = json.dumps({
  "title": "New Project",
  "show_instruction": False,
  "show_skip_button": True,
  "enable_empty_annotation": True,
  "show_annotation_history": True,
  "organization": ORG_ID,
  "color": "#000000"
})
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
  'Content-Type': 'application/json',
}
response = requests.request("POST", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request POST 'http://beewant.com/api/projects/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a' \
--header 'Content-Type: application/json' \
--data-raw '{
            "title": "New Project",
            "show_instruction": false,
            "show_skip_button": true,
            "enable_empty_annotation": true,
            "show_annotation_history": true,
            "organization": ORG_ID,
            "color": "#000000"
}'
```
> Make sure to replace `<YOUR_TOKEN>` with your API key.

**API Method:** GET `/api/organizations/ORG_ID`

To create a new project, you can use the `POST` method on the `/api/projects/ endpoint`. This action allows you to configure various settings for the new project.

### API Method

- Method: `POST`
- Endpoint: `/api/projects/`

### Query Parameters

| Parameter               | Type    | Description                                                                                                                                                                                                                                                                                     |
| ----------------------- | ------- | ------------|
| `title`                 | string  | The title of the new project.|
| `show_instruction`      | boolean | Determines if the instruction should be displayed to users when annotating tasks in the project.|
| `show_skip_button`      | boolean | Determines if the "Skip" button should be displayed to users when annotating tasks in the project.|
| `enable_empty_annotation` | boolean | Determines if empty annotations are allowed in the project.|
| `show_annotation_history` | boolean | Determines if the annotation history should be visible to users in the project.                                                                                                                                                                                                                 |
| `organization`          | integer | The ID of the organization to which the project belongs.|
| `color`                 | string  | The color code of the project, expressed in hexadecimal format (e.g., `#FF5733`).|

<aside class="notice">
Please note that not all parameters are required. You can omit those that are not relevant to your project's configuration. Also, replace placeholders such as <code>ORG_ID</code> with actual values.</aside>

## Validating label config

> To authorize, use this code:

```python
import requests
import json
url = "http://beewant.com/api/projects/validate/"
payload = json.dumps({
  "label_config": "string"
})
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
  'Content-Type': 'application/json',
}
response = requests.request("POST", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request POST 'http://beewant.com/api/projects/validate/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a' \
--header 'Content-Type: application/json' \
--data-raw '{
"label_config": "string"
}'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

To validate a project's label configuration, you can use the `POST` method on the `/api/projects/validate/ endpoint`. This action allows you to check whether the provided label configuration is valid.

### API Method

- Method: `POST`
- Endpoint: `/api/projects/validate/`

### Query Parameters

| Parameter          | Type    | Description |
| ------------------ | ------- | ----------- |
| `label_config	`    | string  | The label configuration JSON string to validate.|

<aside class="notice">
Replace <code>string</code> in the <code>label_config</code> parameter with the actual JSON string of your label configuration.</aside>

## Updating a project

> To authorize, use this code:

```python
import requests
import json
url = "http://beewant.com/api/projects/PROJECT_ID/"
payload = json.dumps({
  "title": "New project 00"
})
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
  'Content-Type': 'application/json',
}
response = requests.request("PATCH", url, headers=headers, data=payload)
print(response)

response.json()

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request PATCH 'http://beewant.com/api/projects/PROJECT_ID/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a' \
--header 'Content-Type: application/json' \
--data-raw '{
    "title": "New project 00"
    }'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

To update project details, you can use the `PATCH` method on the `/api/projects/PROJECT_ID/ endpoint`. This action allows you to modify various project attributes.

### API Method

- Method: `PATCH`
- Endpoint: `/api/projects/PROJECT_ID/`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `PROJECT_ID` | The ID of the project you want to update. This ID identifies the specific project you're modifying. |
| `headers` | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |
| `Content-Type` | The content type of the request payload, set to 'application/json'. This ensures that the request payload is in JSON format. |


<aside class="notice">
Replace placeholders such as <code>PROJECT_ID</code> with the actual ID of the project you're updating.</aside>

## Deleting project

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/projects/PROJECT_ID/"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("DELETE", url, headers=headers, data=payload)
print(response)

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request DELETE 'http://beewant.com/api/projects/PROJECT_ID/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

To delete a project, you can use the `DELETE` method on the `/api/projects/PROJECT_ID/ endpoint`. This action removes the specified project from your account.

### API Method

- Method: `DELETE`
- Endpoint: `/api/projects/PROJECT_ID/`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `PROJECT_ID` | The ID of the project you want to delete. This ID identifies the specific project you're removing. |
| `headers` | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

<aside class="notice">
Replace <code>PROJECT_ID</code> with the actual ID of the project you want to delete.</aside>

## Deleting all porject tasks

> To authorize, use this code:

```python
import requests
url = "http://beewant.com/api/projects/PROJECT_ID/tasks/"
payload={}
headers = {
  'Authorization': 'Token 96fac556ee62e082d883f3c253789b099482061a',
}
response = requests.request("DELETE", url, headers=headers, data=payload)
print(response)

```


```shell
# With shell, you can just pass the correct header with each request
curl --location --request DELETE 'http://beewant.com/api/projects/PROJECT_ID/tasks/' \
--header 'Authorization: Token 96fac556ee62e082d883f3c253789b099482061a'
```

> Make sure to replace `<YOUR_TOKEN>` with your API key.

To delete tasks from a project, you can use the `DELETE` method on the `/api/projects/PROJECT_ID/tasks/ endpoint`. This action removes tasks associated with the specified project.

### API Method

- Method: `DELETE`
- Endpoint: `/api/projects/PROJECT_ID/tasks/`

### Query Parameters

| Parameter | Description |
| --- | --- |
| `PROJECT_ID` | The ID of the project from which you want to delete tasks. This ID identifies the specific project from which you want to remove tasks. |
| `headers` | The headers containing the Authorization token (e.g., 'Token <YOUR_TOKEN>'). This ensures your API requests are authenticated and authorized. |

<aside class="notice">
Replace <code>PROJECT_ID</code> with the actual ID of the project from which you want to delete tasks.</aside>