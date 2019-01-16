# oscript-jwt

## Использование

### Создание (encoding) токена
```bsl
payload = New Structure;
payload.Insert("name", "Administrator");
payload.Insert("admin", True);

secret = "SUPER_SECRET";

algorithm = new HMAC(HashFunction.SHA256);
serializer = new JwtJsonSerializer();
urlEncoder = new JwtBase64UrlEncoder();
encoder = new JwtEncoder(algorithm, serializer, urlEncoder);

token = encoder.Encode(secret, payload);
Message(token, MessageStatus.Attention);
```

### Разбор (decoding) и проверка токена

```bsl
token = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiQWRtaW5pc3RyYXRvciIsImFkbWluIjp0cnVlfQ.u3A-NIhT6op97ldy0yhqPdOJD8wvmvYo_muum-ZEjaQ";
secret = "SUPER_SECRET";

algorithm = new HMAC(HashFunction.SHA256);
serializer = new JwtJsonSerializer();
urlEncoder = new JwtBase64UrlEncoder();
decoder = new JwtDecoder(algorithm, serializer, urlEncoder);
    
json = decoder.Decode(token, secret);
Message(token, MessageStatus.Attention);
```

