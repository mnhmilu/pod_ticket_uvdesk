# pod_ticket_uvdesk
uvdesk ticketing tools 


```
version: '3'
services:
  db:
    image: "mysql:5.7"
    volumes:
      - ./uvdesk/db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_DATABASE: uvdesk
      MYSQL_ROOT_PASSWORD: "change-me-to-something-strong"
      MYSQL_USER: "uvdesk"
      MYSQL_PASSWORD: "change-me-to-something-strong-too"
  uvdesk:
    image: nuttcorp/uvdesk:latest
    depends_on:
      - db
    tty: true
    environment:
        MYSQL_USER: "uvdesk"
        MYSQL_PASSWORD: "change-me-to-something-strong-too"
        MYSQL_ROOT_PASSWORD: "change-me-to-something-strong"
        MYSQL_DATABASE: uvdesk
    ports:
        - 8085:80

volumes:
  db_data: {}

```




References:

[Youtube Tutorial with Docker compose](https://www.youtube.com/watch?v=jAG2U7fBilE&list=LL&index=1&t=1098s)

[Github](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbE5GaDMwVjZJNVRyWjFsaTNRTjI1OVAyTy1VQXxBQ3Jtc0trNzhxUEZfMjFlVmlBZWlUdlIxMERXQTdSVFNpTWZrWU1qdlBtR3cwM2FGS0Zhd3hHOTROV1Z4YWtCb1l4WllHQ0JiV2pMMzJPWjdxQ0YzZjFCZW4zRlAtTWVFV19ybGt0RGVQTzNhblVnMndUWldVUQ&q=https%3A%2F%2Fgithub.com%2Fuvdesk&v=jAG2U7fBilE)
