---
ms.openlocfilehash: fb9436ec9e525afb497033775e34b6b636ced22d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621155"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>使用 NETTCP 進行 SSL 安全性和 MD5 憑證驗證的 WCF 服務

#### <a name="details"></a>詳細資料

.NET Framework 4.6 新增了 TLS 1.1 和 TLS 1.2 至 WCF SSL 的預設通訊協定清單。 當用戶端和伺服器電腦安裝 .NET Framework 4.6 或更新版本時，會使用 TLS 1.2 進行交涉。TLS 1.2 不支援 MD5 憑證驗證。 因此，如果客戶使用 MD5 憑證，WCF 用戶端將無法連線到 WCF 服務。

#### <a name="suggestion"></a>建議

您可以執行下列其中一項動作來解決這個問題，使 WCF 用戶端可以連線到 WCF 伺服器︰

- 更新憑證為不使用 MD5 演算法。 這是建議的解決方案。
- 如果繫結在原始程式碼中不是以動態方式設定，請更新應用程式的組態檔，以使用 TLS 1.1 或舊版的通訊協定。 這可讓您繼續使用執行 MD5 雜湊演算法的憑證。

> [!WARNING]
> 我們不建議採取這項因應措施，因為使用 MD5 雜湊演算法的憑證並不安全。

下列組態檔示範如何進行：

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <netTcpBinding>
        <binding>
          <security mode= "None/Transport/Message/TransportWithMessageCredential" >
            <transport clientCredentialType="None/Windows/Certificate"
                       protectionLevel="None/Sign/EncryptAndSign"
                       sslProtocols="Ssl3/Tls1/Tls11">
            </transport>
          </security>
        </binding>
      </netTcpBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```

- 如果繫結在原始程式碼中是以動態方式設定，請更新 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> 屬性，以在原始程式碼中使用 TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) 或舊版的通訊協定。

> [!WARNING]
> 我們不建議採取這項因應措施，因為使用 MD5 雜湊演算法的憑證並不安全。

| 名稱    | 值   |
|:--------|:--------|
| 影響範圍   | Minor   |
| 版本 | 4.6     |
| 類型    | 執行階段 |
