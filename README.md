# Restaurant Table Booking System -- Authentication API

## Overview

This project provides authentication APIs for the Restaurant Table
Booking System.

### Features

-   User Registration
-   User Login
-   Forgot Password
-   Refresh JWT Token

## Base URL

``` text
http://localhost:5000/api/v1
```

## Endpoints

  Method   Endpoint                  Description
  -------- ------------------------- -----------------------------
  POST     `/auth/register`          Register a new user
  POST     `/auth/login`             Authenticate a user
  POST     `/auth/forgot-password`   Send password reset link
  POST     `/auth/refresh-token`     Generate a new access token

## Authentication Flow

``` text
                +----------------+
                |     User       |
                +----------------+
                        |
                        | Register
                        v
          +---------------------------+
          |  Account Created          |
          +---------------------------+
                        |
                        | Login
                        v
          +---------------------------+
          | Validate Credentials      |
          +---------------------------+
                        |
             Success    |    Failure
                        |
                        v
      +--------------------------------------+
      | Access Token + Refresh Token Issued  |
      +--------------------------------------+
                        |
                        | Authorization: Bearer <Access Token>
                        v
      +--------------------------------------+
      | Access Protected Endpoints           |
      +--------------------------------------+
                        |
            Access Token Expires
                        |
                        v
      +--------------------------------------+
      | POST /auth/refresh-token             |
      +--------------------------------------+
                        |
                        v
      +--------------------------------------+
      | New Access Token Returned            |
      +--------------------------------------+
                        |
                        v
              Continue Using APIs
```

## HTTP Status Codes

-   **200** -- Success
-   **201** -- Resource Created
-   **400** -- Bad Request
-   **401** -- Unauthorized
-   **404** -- Not Found
-   **409** -- Conflict

## Security

-   JWT Bearer Authentication
-   Stateless REST API
-   JSON Request/Response

## Example Authorization Header

``` http
Authorization: Bearer <access_token>
```
