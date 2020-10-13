---
ms.openlocfilehash: d312ba2a22797ff6afff6b893f998c965e68e86e
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997762"
---
### <a name="default-tls-cipher-suites-for-net-on-linux"></a>Linux 上適用于 .NET 的預設 TLS 加密套件

.NET 在 Linux 上，現在會在透過 <xref:System.Net.Security.SslStream> 類別或更高層級的作業（例如透過類別的 HTTPS）進行 TLS/SSL 時，遵循預設加密套件的 OpenSSL 設定 <xref:System.Net.Http.HttpClient> 。 未明確設定預設的加密套件時，Linux 上的 .NET 會使用受嚴格限制的允許密碼套件清單。

#### <a name="change-description"></a>變更描述

在舊版的 .NET 中，.NET 不遵守預設加密套件的系統組態。 Linux 上適用于 .NET 的預設加密套件清單非常寬鬆。

從 .NET 5.0 開始，Linux 上的 .NET 在 *OpenSSL. my.cnf*中指定時，會遵循預設加密套件的 OpenSSL 設定。 未明確設定加密套件時，唯一允許的加密套件如下所示：

- TLS 1.3 加密套件
- TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
- TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
- TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
- TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256

因為此回復預設不包含任何與 TLS 1.0 或 TLS 1.1 相容的加密套件，所以這些較舊的通訊協定版本預設會有效停用。

針對特定會話提供 CipherSuitePolicy 值給 SslStream，仍會取代設定檔內容和/或 .NET 回預設值。

#### <a name="reason-for-change"></a>變更的原因

在 Linux 上執行 .NET 的使用者要求將預設設定 <xref:System.Net.Security.SslStream> 變更為從協力廠商評量工具提供高安全性評等的設定。

#### <a name="version-introduced"></a>引進的版本

5.0 RC1

#### <a name="recommended-action"></a>建議的動作

當與新式用戶端或伺服器通訊時，新的預設值可能會運作。 如果您需要展開預設的加密套件清單以接受舊版用戶端 (或要) 的舊版伺服器，請指定 `CipherSuitePolicy` 值或變更 OpenSSL 設定檔。 在許多 Linux 發行版本上，OpenSSL 設定檔位於 */etc/ssl/openssl.cnf*。

這個範例 *openssl. my.cnf* 檔案是最基本的檔案，相當於 Linux 上 .net 5.0 和更新版本的預設加密套件原則。 與其取代系統檔案，請將這些概念與系統上存在的檔案合併。

```ini
openssl_conf = default_conf

[default_conf]
ssl_conf = ssl_sect

[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256
```

在 Red Hat Enterprise Linux、CentOS 和 Fedora 發行版本上，.NET 應用程式預設為全系統密碼編譯原則所允許的加密套件。 在這些散發套件上，請使用加密原則設定，而不是 *openssl. my.cnf*。

#### <a name="category"></a>類別

- 密碼編譯
- 安全性

#### <a name="affected-apis"></a>受影響的 API

未透過 API 分析 detectible。

<!--

#### Affected APIs

- Not detectible via API analysis.

-->
