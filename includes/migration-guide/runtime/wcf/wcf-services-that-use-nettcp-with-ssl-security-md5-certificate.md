---
ms.openlocfilehash: fb9436ec9e525afb497033775e34b6b636ced22d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621155"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a><span data-ttu-id="74375-101">使用 NETTCP 進行 SSL 安全性和 MD5 憑證驗證的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="74375-101">WCF services that use NETTCP with SSL security and MD5 certificate authentication</span></span>

#### <a name="details"></a><span data-ttu-id="74375-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="74375-102">Details</span></span>

<span data-ttu-id="74375-103">.NET Framework 4.6 新增了 TLS 1.1 和 TLS 1.2 至 WCF SSL 的預設通訊協定清單。</span><span class="sxs-lookup"><span data-stu-id="74375-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL default protocol list.</span></span> <span data-ttu-id="74375-104">當用戶端和伺服器電腦安裝 .NET Framework 4.6 或更新版本時，會使用 TLS 1.2 進行交涉。TLS 1.2 不支援 MD5 憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="74375-104">When both client and server machines have the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="74375-105">因此，如果客戶使用 MD5 憑證，WCF 用戶端將無法連線到 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="74375-105">As a result, if a customer uses an MD5 certificate, the WCF client will fail to connect to the WCF service.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="74375-106">建議</span><span class="sxs-lookup"><span data-stu-id="74375-106">Suggestion</span></span>

<span data-ttu-id="74375-107">您可以執行下列其中一項動作來解決這個問題，使 WCF 用戶端可以連線到 WCF 伺服器︰</span><span class="sxs-lookup"><span data-stu-id="74375-107">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="74375-108">更新憑證為不使用 MD5 演算法。</span><span class="sxs-lookup"><span data-stu-id="74375-108">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="74375-109">這是建議的解決方案。</span><span class="sxs-lookup"><span data-stu-id="74375-109">This is the recommended solution.</span></span>
- <span data-ttu-id="74375-110">如果繫結在原始程式碼中不是以動態方式設定，請更新應用程式的組態檔，以使用 TLS 1.1 或舊版的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="74375-110">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="74375-111">這可讓您繼續使用執行 MD5 雜湊演算法的憑證。</span><span class="sxs-lookup"><span data-stu-id="74375-111">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

> [!WARNING]
> <span data-ttu-id="74375-112">我們不建議採取這項因應措施，因為使用 MD5 雜湊演算法的憑證並不安全。</span><span class="sxs-lookup"><span data-stu-id="74375-112">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

<span data-ttu-id="74375-113">下列組態檔示範如何進行：</span><span class="sxs-lookup"><span data-stu-id="74375-113">The following configuration file does this:</span></span>

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

- <span data-ttu-id="74375-114">如果繫結在原始程式碼中是以動態方式設定，請更新 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> 屬性，以在原始程式碼中使用 TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) 或舊版的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="74375-114">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType> or an earlier version of the protocol in the source code.</span></span>

> [!WARNING]
> <span data-ttu-id="74375-115">我們不建議採取這項因應措施，因為使用 MD5 雜湊演算法的憑證並不安全。</span><span class="sxs-lookup"><span data-stu-id="74375-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

| <span data-ttu-id="74375-116">名稱</span><span class="sxs-lookup"><span data-stu-id="74375-116">Name</span></span>    | <span data-ttu-id="74375-117">值</span><span class="sxs-lookup"><span data-stu-id="74375-117">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="74375-118">影響範圍</span><span class="sxs-lookup"><span data-stu-id="74375-118">Scope</span></span>   | <span data-ttu-id="74375-119">Minor</span><span class="sxs-lookup"><span data-stu-id="74375-119">Minor</span></span>   |
| <span data-ttu-id="74375-120">版本</span><span class="sxs-lookup"><span data-stu-id="74375-120">Version</span></span> | <span data-ttu-id="74375-121">4.6</span><span class="sxs-lookup"><span data-stu-id="74375-121">4.6</span></span>     |
| <span data-ttu-id="74375-122">類型</span><span class="sxs-lookup"><span data-stu-id="74375-122">Type</span></span>    | <span data-ttu-id="74375-123">執行階段</span><span class="sxs-lookup"><span data-stu-id="74375-123">Runtime</span></span> |
