# github使用出现的问题

## 第一次ssh连接github

$ ssh -T git@github.com	//l连接命令

The authenticity of host 'github.com (192.30.253.113)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? 	//第一次连接都会这样，输入yes就好了

yes

Warning: Permanently added 'github.com,192.30.253.113' (RSA) to the list of known hosts.
Hi bestgrc! You've successfully authenticated, but GitHub does not provide shell access.//连接成功