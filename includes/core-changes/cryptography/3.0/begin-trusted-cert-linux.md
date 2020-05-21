---
ms.openlocfilehash: 3c6142fd536bad5676f02570fecd4eb0605db829
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721163"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>Linux 上的根憑證不再支援「開始信任的憑證」語法

Linux 上的根憑證和其他類似 Unix 的系統（但不是 macOS）可以用兩種形式呈現：標準 `BEGIN CERTIFICATE` PEM 標頭和 OpenSSL 特定的 `BEGIN TRUSTED CERTIFICATE` pem 標頭。 後者的語法允許其他設定導致 .NET Core 的類別發生相容性問題 <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> 。 `BEGIN TRUSTED CERTIFICATE`從 .NET Core 3.0 開始，連鎖引擎不再載入根憑證內容。

#### <a name="change-description"></a>變更描述

之前， `BEGIN CERTIFICATE` 和語法都 `BEGIN TRUSTED CERTIFICATE` 是用來填入根信任清單。 如果 `BEGIN TRUSTED CERTIFICATE` 使用語法，並在檔案中指定了其他選項， <xref:System.Security.Cryptography.X509Certificates.X509Chain> 可能會報告已明確禁止鏈信任（ <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType> ）。 不過，如果憑證也以先前載入之檔案 `BEGIN CERTIFICATE` 中的語法指定，則允許鏈信任。

從 .NET Core 3.0 開始， `BEGIN TRUSTED CERTIFICATE` 將不會再讀取內容。 如果未透過標準語法指定憑證 `BEGIN CERTIFICATE` ，則會 <xref:System.Security.Cryptography.X509Certificates.X509Chain> 報告根不受信任（ <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType> ）。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

大部分的應用程式不會受到這項變更的影響，但因為許可權問題而無法看到兩個根憑證來源的應用程式，可能會在升級之後遇到未預期的 `UntrustedRoot` 錯誤。

許多 Linux 散發套件（或散發版本）會將根憑證寫入兩個位置：每個檔案一個憑證目錄，以及一個檔案串連。 在某些散發版本上， `BEGIN TRUSTED CERTIFICATE` 當檔案串連使用標準語法時，每個檔案的單一憑證目錄會使用語法 `BEGIN CERTIFICATE` 。 請確定已將任何自訂根憑證新增為其中 `BEGIN CERTIFICATE` 至少一個位置，而且您的應用程式可以讀取這兩個位置。

一般目錄是 */etc/ssl/certs/* ，而一般的串連檔案則是 */etc/ssl/cert.pem*。 使用命令 `openssl version -d` 來判斷平臺特定的根，這可能會與 */etc/ssl/* 不同。 例如，在 Ubuntu 18.04 上，目錄是 */usr/lib/ssl/certs/* ，而檔案是 */usr/lib/ssl/cert.pem*。 不過， */usr/lib/ssl/certs/* 是 */etc/ssl/certs/* 的符號，而且 */usr/lib/ssl/cert.pem*不存在。

```bash
$ openssl version -d
OPENSSLDIR: "/usr/lib/ssl"
$ ls -al /usr/lib/ssl
total 12
drwxr-xr-x  3 root root 4096 Dec 12 17:10 .
drwxr-xr-x 73 root root 4096 Feb 20 15:18 ..
lrwxrwxrwx  1 root root   14 Mar 27  2018 certs -> /etc/ssl/certs
drwxr-xr-x  2 root root 4096 Dec 12 17:10 misc
lrwxrwxrwx  1 root root   20 Nov 12 16:58 openssl.cnf -> /etc/ssl/openssl.cnf
lrwxrwxrwx  1 root root   16 Mar 27  2018 private -> /etc/ssl/private
```

#### <a name="category"></a>類別

密碼編譯

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
