## Running the service

```bash
docker build -t whtmltopdf .
docker run -t -name JDG32_wkhtmltopdf-e USER='gooduser' -e PASS='secretpassword' -p 127.0.0.1:80:5555 wkhtmltopdf
```

#### PHP example
```php
$url = 'https://"+user+":"+pass+"@<docker_host>:<port>/';
$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_HTTPHEADER, array('Content-type: application/json'));
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$html = "<h1>Test</h1>";
$body = json_encode([
    'contents' => base64_encode($html),
]);
# print response
curl_setopt($ch, CURLOPT_POSTFIELDS, $body);
header("Content-type:application/pdf");
echo curl_exec($ch);
```