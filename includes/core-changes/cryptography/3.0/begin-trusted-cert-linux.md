---
ms.openlocfilehash: 3c6142fd536bad5676f02570fecd4eb0605db829
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721163"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>Linux 上的根憑證已不再支援「開始受信任的憑證」語法

Linux 和其他 Unix 型系統上的根憑證 (但不是 macOS) 可以用兩種形式呈現：標準 `BEGIN CERTIFICATE` PEM 標頭，以及 OpenSSL 特定的 `BEGIN TRUSTED CERTIFICATE` pem 標頭。 第二個語法可進行其他設定，此設定會導致 .NET Core 類別的相容性問題 <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> 。 `BEGIN TRUSTED CERTIFICATE` 從 .NET Core 3.0 開始，鏈引擎不再載入根憑證內容。

#### <a name="change-description"></a>變更描述

先前， `BEGIN CERTIFICATE` 和語法都 `BEGIN TRUSTED CERTIFICATE` 是用來填入根信任清單。 如果 `BEGIN TRUSTED CERTIFICATE` 已使用此語法，並在檔案中指定其他選項， <xref:System.Security.Cryptography.X509Certificates.X509Chain> 可能會回報鏈信任明確不允許 (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>) 。 但是，如果憑證也使用先前載入的檔案 `BEGIN CERTIFICATE` 中的語法來指定，則允許鏈信任。

從 .NET Core 3.0 開始， `BEGIN TRUSTED CERTIFICATE` 將不再讀取內容。 如果憑證也不是透過標準 `BEGIN CERTIFICATE` 語法指定，則不會 <xref:System.Security.Cryptography.X509Certificates.X509Chain> 將根目錄 () 來報告 <xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType> 。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="recommended-action"></a>建議的動作

大部分的應用程式不會受到這項變更的影響，但因為許可權問題而無法同時看到根憑證來源的應用程式可能會在升級之後遇到未預期的 `UntrustedRoot` 錯誤。

許多 Linux 發行版本 (或散發版本) 將根憑證寫入兩個位置：一個憑證每個檔案的目錄，以及一個檔案的串連。 在某些散發版本中，每個檔案的單一憑證目錄會使用 `BEGIN TRUSTED CERTIFICATE` 語法，而檔案串連則使用標準 `BEGIN CERTIFICATE` 語法。 請確定任何自訂根憑證都已新增為 `BEGIN CERTIFICATE` 至少其中一個位置，而且您的應用程式可以讀取這兩個位置。

一般目錄為 */etc/ssl/certs/* ，而一般串連檔案為 */etc/ssl/cert.pem*。 使用命令 `openssl version -d` 來判斷平臺特定的根目錄，其可能不同于 */etc/ssl/*。 例如，在 Ubuntu 18.04 上，會 */usr/lib/ssl/certs/* 目錄並 */usr/lib/ssl/cert.pem* 檔案。 不過， */usr/lib/ssl/certs/* 是 */etc/ssl/certs/* 的符號連結，而且 */usr/lib/ssl/cert.pem* 不存在。

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
