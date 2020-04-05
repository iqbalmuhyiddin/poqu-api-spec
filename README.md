# API Spec POQU

**Table of Contents**

- [API Spec POQU](#api-spec-poqu)
  - [Auth](#auth)
    - [Register](#register)
    - [Login](#login)
    - [Refresh Token](#refresh-token)
  - [Podcast](#podcast)
    - [List](#list)
    - [Get by ID](#get-by-id)
  - [Category](#category)
    - [List](#list-1)

## Auth

### Register

**URL**:`/auth/register`

**Method**: `POST`

**Auth required** : NO

**Request Data**

```
{
  name,
  email,
  password,
  phone
}
```

**Response Data**

```
{
  success: true | false,
  message: "register success"
  data: null
}
```

### Login

**URL**:`/auth/login`

**Method**: `POST`

**Auth required** : NO

**Request Data**

```
{
  identifier,
  password
}
```

**Response Data**

```
{
  success: true | false,
  message: "login success",
  errors: "error stack",
  data: {
    token: {
      access,
      refresh,
      ttl
    },
    user
  }
}
```

### Refresh Token

**URL**:`/auth/refresh`

**Method**: `POST`

**Auth required** : NO

**Request Data**

```
{
  refresh_token
}
```

**Response Data**

```
{
  success: true | false,
  message: "refresh success",
  errors: "error stack",
  data: {
    access,
    refresh,
    ttl
  }
}
```

## Podcast

### List

**URL**:`/podcast`

**Method**: `GET`

**Query Params**

optional:

`category=[string]` (use category slug)

`page=[integer]`

`size=[integer]`

**Auth required** : YES

**Response Data**

```
{
  success: true | false,
  message: "data loaded"
  data: [
    {
      id,
      title,
      description,
      duration_time,
      duration_second,
      audio_link,
      cover_link,
      podcaster:{
        id,
        name,
        description,
        bio
      },
      categories: [name]
    }
  ]
}
```

### Get by ID

**URL**:`/podcast/:id`

**Method**: `GET`

**URL Params**

required: `id=[integer]`

**Auth required** : YES

**Response Data**

```
{
  success: true | false,
  message: "data loaded"
  data: {
      id,
      title,
      description,
      duration_second,
      audio_link,
      cover_link,
      podcaster:{
        id,
        name,
        description,
        bio
      },
      categories: [name]
    }
}
```

## Category

### List

**URL**:`/categories`

**Method**: `GET`

**Query Params**
optional:

`page=[integer]`

`size=[integer]`

**Auth required** : YES

**Response Data**

```
{
  success: true | false,
  message: "data loaded"
  data: [
    {
      id,
      slug,
      name
    }
  ]
}
```
