---
title: "風險降低︰WCF 服務和憑證驗證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1d6f78d24fc6411fca81fbbb8eb886d6d0a7fe9c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="25ee0-102">風險降低︰WCF 服務和憑證驗證</span><span class="sxs-lookup"><span data-stu-id="25ee0-102">Mitigation: WCF Services and Certificate Authentication</span></span>
<span data-ttu-id="25ee0-103">.NET Framework 4.6 新增了 TLS 1.1 和 TLS 1.2 至 WCF SSL 的通訊協定預設清單。</span><span class="sxs-lookup"><span data-stu-id="25ee0-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="25ee0-104">當用戶端和伺服器電腦安裝 .NET Framework 4.6 或更新版本時，會使用 TLS 1.2 進行交涉。</span><span class="sxs-lookup"><span data-stu-id="25ee0-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="25ee0-105">影響</span><span class="sxs-lookup"><span data-stu-id="25ee0-105">Impact</span></span>  
 <span data-ttu-id="25ee0-106">TLS 1.2 不支援 MD5 憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="25ee0-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="25ee0-107">因此，如果客戶使用的 SSL 憑證使用 MD5 執行雜湊演算法，WCF 用戶端就無法連線到 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="25ee0-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="25ee0-108">如需詳細資訊，請參閱[風險降低︰WCF 服務和憑證驗證](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="25ee0-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](../../../docs/framework/migration-guide/mitigation-wcf-services-and-certificate-authentication.md).</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="25ee0-109">緩和</span><span class="sxs-lookup"><span data-stu-id="25ee0-109">Mitigation</span></span>  
 <span data-ttu-id="25ee0-110">您可以執行下列其中一項動作來解決這個問題，使 WCF 用戶端可以連線到 WCF 伺服器︰</span><span class="sxs-lookup"><span data-stu-id="25ee0-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>  
  
-   <span data-ttu-id="25ee0-111">更新憑證為不使用 MD5 演算法。</span><span class="sxs-lookup"><span data-stu-id="25ee0-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="25ee0-112">這是建議的解決方案。</span><span class="sxs-lookup"><span data-stu-id="25ee0-112">This is the recommended solution.</span></span>  
  
-   <span data-ttu-id="25ee0-113">如果繫結在原始程式碼中不是以動態方式設定，請更新應用程式的組態檔，以使用 TLS 1.1 或舊版的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="25ee0-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="25ee0-114">這可讓您繼續使用執行 MD5 雜湊演算法的憑證。</span><span class="sxs-lookup"><span data-stu-id="25ee0-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="25ee0-115">我們不建議採取這項因應措施，因為使用 MD5 雜湊演算法的憑證並不安全。</span><span class="sxs-lookup"><span data-stu-id="25ee0-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
     <span data-ttu-id="25ee0-116">下列組態檔示範如何進行：</span><span class="sxs-lookup"><span data-stu-id="25ee0-116">The following configuration file does this:</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding>  
                        <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                            <transport clientCredentialType="None|Windows|Certificate"  
                                                protectionLevel="None|Sign|EncryptAndSign"  
                                                sslProtocols="Ssl3|Tls1|Tls11">  
                            </transport>  
                        </security>  
                    </binding>  
                </netTcpBinding>  
            </bindings>  
        </system.ServiceModel>  
    </configuration>  
    ```  
  
-   <span data-ttu-id="25ee0-117">如果繫結在原始程式碼中是以動態方式設定，請更新 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName> 屬性，以在原始程式碼中使用 TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=fullName>) 或舊版的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="25ee0-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=fullName>) or an  earlier version of the protocol in the source code.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="25ee0-118">我們不建議採取這項因應措施，因為使用 MD5 雜湊演算法的憑證並不安全。</span><span class="sxs-lookup"><span data-stu-id="25ee0-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ee0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25ee0-119">See Also</span></span>  
 [<span data-ttu-id="25ee0-120">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="25ee0-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)

