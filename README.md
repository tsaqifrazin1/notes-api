# notes-api

## How To Use

### Public Endpoint

`http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com/`

## REST API

The REST API to the example notes-api is described below.

## User

- #### Create a User

  ##### Request

  `POST /users`

        curl --location --request POST 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com/' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "username": "1645270773-testing",
            "password": "secretpassword",
            "fullname": "Testing Account"
        }'

  ##### Response

        HTTP/1.1 201 Created
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 100
        Date: Sat, 19 Feb 2022 11:34:29 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"User berhasil ditambahkan","data":{"userId":"user-IYSgLD_Lhxn3nIiL"}}

- #### Get One User by Id

  ##### Request

  `GET /users/<UserId> `

        curl --location --request GET 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/users/user-IYSgLD_Lhxn3nIiL' \
        --data-raw ''

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 128
        accept-ranges: bytes
        Date: Sat, 19 Feb 2022 11:45:13 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","data":{"user":{"id":"user-IYSgLD_Lhxn3nIiL","username":"1645270469-testing","fullname":"Testing Account"}}}

- #### Get User by Username

  ##### Request

  `GET /users?username=testing`

        curl --location --request GET 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/users?username=testing'

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 131
        accept-ranges: bytes
        Date: Sat, 19 Feb 2022 11:50:41 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","data":{"users":[{"id":"user-IYSgLD_Lhxn3nIiL","username":"1645270469-testing","fullname":"Testing Account"}]}}

## Authentication

- #### Create Authentication data

  ##### Request

  `POST /authentications`

        curl --location --request POST 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/authentications' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "username": "testing",
            "password": "secretpassword"
        }'

  ##### Response

        HTTP/1.1 201 Created
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 400
        Date: Sat, 19 Feb 2022 12:07:14 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"Authentication berhasil ditambahkan","data":{"accessToken":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTI3MjQzNH0.qjEWHV949TO8zLWz6lD1bghvIe0gIA2KFyCEtqD2SDw","refreshToken":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTI3MjQzNH0.klVMwi5EGL95mdBTPPEONUW7LAWhDav504ej5zuS63g"}}

- #### Update Authentications

  ##### Request

  `PUT /authentications`

        curl --location --request PUT 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/authentications' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTI3MjQzNH0.klVMwi5EGL95mdBTPPEONUW7LAWhDav504ej5zuS63g"
        }'

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 235
        Date: Sat, 19 Feb 2022 12:11:38 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"Access Token berhasil diperbarui","data":{"accessToken":"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTI3MjY5OH0.DUinF7_rkyw88oK48Jh4TdaQBU8KE2nyqq8ivLr5GQw"}}

- #### Delete Authentications

  ##### Request

  `DELETE /authentications`

        curl --location --request DELETE 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/authentications' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTI3MjQzNH0.klVMwi5EGL95mdBTPPEONUW7LAWhDav504ej5zuS63g"
        }'

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 63
        Date: Sat, 19 Feb 2022 12:15:04 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"Refresh token berhasil dihapus"}

## Collaborations

- #### Create Collaborator

  ##### Request

  `POST /collaborations`

        curl --location --request POST 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/collaborations' \
        --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXItcTM1RXpLdWRsMFlST1NnOCIsImlhdCI6MTY0NTM1NjAxOH0.JVieu3I2DsLBes8bCtxtvvwLGV5X3cybASVKBMpNsFI' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "noteId": "WPHSj4GlC3Q8ZRaV",
            "userId": "user-eg6Kgtzq6s0-GlII"
        }'

  ##### Response

        HTTP/1.1 201 Created
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 117
        Date: Sun, 20 Feb 2022 11:20:32 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"Kolaborasi berhasil ditambahkan","data":{"collaborationId":"collab-C7Zjs2f3v8ZQ2lJ2"}}

- #### Delete Collaborator

  ##### Request

  `DELETE /collaborations`

        curl --location --request DELETE 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/collaborations' \
        --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXItcTM1RXpLdWRsMFlST1NnOCIsImlhdCI6MTY0NTM1NjAxOH0.JVieu3I2DsLBes8bCtxtvvwLGV5X3cybASVKBMpNsFI' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "noteId": "WPHSj4GlC3Q8ZRaV",
            "userId": "user-eg6Kgtzq6s0-GlII"
        }'

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 60
        Date: Sun, 20 Feb 2022 11:28:36 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"Kolaborasi berhasil dihapus"}

## Notes

    CRUD Notes collection

- #### Create Notes data

  ##### Request

  `POST /notes`

        curl --location --request POST 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/notes' \
        --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTM1NTg5MH0.5NGYS6WmLhy1MFMZbXDmMdkJ1-NWhJJku8tBJzNa8to' \
        --header 'Content-Type: application/json' \
        --data-raw '{
        "title": "Catatan A",
        "tags": ["Android", "Web"],
        "body": "Isi dari catatan A"
        } '

  ##### Response

        HTTP/1.1 201 Created
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 98
        Date: Sun, 20 Feb 2022 11:37:42 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"Catatan berhasil ditambahkan","data":{"noteId":"bRO1h5NA_dSI3DDk"}}

- #### Read All Categories Data

  ##### Request

  `POST /notes`

        curl --location --request GET 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/notes' \
        --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTM1NTg5MH0.5NGYS6WmLhy1MFMZbXDmMdkJ1-NWhJJku8tBJzNa8to'

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 216
        accept-ranges: bytes
        Date: Sun, 20 Feb 2022 11:40:09 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","data":{"notes":[{"id":"bRO1h5NA_dSI3DDk","title":"Catatan A","body":"Isi dari catatan A","tags":["Android","Web"],"createdAt":"2022-02-20T11:37:42.419Z","updatedAt":"2022-02-20T11:37:42.419Z"}]}}

- #### Get One Notes data by id

  ##### Request

  `GET /notes/:notesId`

        curl --location --request GET 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/notes/bRO1h5NA_dSI3DDk' \
        --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTM1NTg5MH0.5NGYS6WmLhy1MFMZbXDmMdkJ1-NWhJJku8tBJzNa8to'

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 234
        accept-ranges: bytes
        Date: Sun, 20 Feb 2022 11:41:38 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","data":{"note":{"id":"bRO1h5NA_dSI3DDk","title":"Catatan A","body":"Isi dari catatan A","tags":["Android","Web"],"createdAt":"2022-02-20T11:37:42.419Z","updatedAt":"2022-02-20T11:37:42.419Z","username":"testing"}}}

- #### Update Notes data by id

  ##### Request

  `PUT /notes/:notesId`

        curl --location --request PUT 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/notes/bRO1h5NA_dSI3DDk' \
        --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTM1NTg5MH0.5NGYS6WmLhy1MFMZbXDmMdkJ1-NWhJJku8tBJzNa8to' \
        --header 'Content-Type: application/json' \
        --data-raw '{
            "title": "Catatan A Revised",
            "tags": ["Android", "Web"],
            "body": "Isi dari Catatan A Revised"
        }'

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 60
        Date: Sun, 20 Feb 2022 11:43:40 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"Catatan berhasil diperbarui"}

- #### Delete Notes data by id

  ##### Request

  `DELETE /notes/:notesId`

        curl --location --request DELETE 'http://ec2-54-251-69-22.ap-southeast-1.compute.amazonaws.com:5000/notes/bRO1h5NA_dSI3DDk' \
        --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6InVzZXIta09GN05uTEdBRGdnM3ZWWSIsImlhdCI6MTY0NTM3MTcwMn0.qFGS26sT5jCewXF5bIOlHnDt7vIodE4M5b0pbqETSH0'

  ##### Response

        HTTP/1.1 200 OK
        content-type: application/json; charset=utf-8
        vary: origin
        access-control-expose-headers: WWW-Authenticate,Server-Authorization
        cache-control: no-cache
        content-length: 57
        Date: Sun, 20 Feb 2022 15:41:50 GMT
        Connection: keep-alive
        Keep-Alive: timeout=5

        {"status":"success","message":"Catatan berhasil dihapus"}
