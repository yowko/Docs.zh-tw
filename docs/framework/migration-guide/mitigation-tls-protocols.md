---
title: 風險降低：TLS 通訊協定
description: 瞭解從 .NET Framework 4.6 開始的 TLS 通訊協定變更的影響和緩和措施。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 492315d43043c83d17eab330e8d589d1cffe7ad2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273863"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="ecc2f-103">風險降低：TLS 通訊協定</span><span class="sxs-lookup"><span data-stu-id="ecc2f-103">Mitigation: TLS Protocols</span></span>

<span data-ttu-id="ecc2f-104">從 .NET Framework 4.6 開始，<xref:System.Net.ServicePointManager?displayProperty=nameWithType> 和 <xref:System.Net.Security.SslStream?displayProperty=nameWithType> 類別可以使用 Tls1.0、Tls1.1 或 Tls 1.2 這三種通訊協定之一。</span><span class="sxs-lookup"><span data-stu-id="ecc2f-104">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="ecc2f-105">不支援 SSL3.0 通訊協定與 RC4 編碼器。</span><span class="sxs-lookup"><span data-stu-id="ecc2f-105">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="ecc2f-106">影響</span><span class="sxs-lookup"><span data-stu-id="ecc2f-106">Impact</span></span>  

 <span data-ttu-id="ecc2f-107">這項變更會影響：</span><span class="sxs-lookup"><span data-stu-id="ecc2f-107">This change affects:</span></span>  
  
- <span data-ttu-id="ecc2f-108">任何使用 SSL 與 HTTPS 伺服器通訊或與使用任何下列類型之通訊端伺服器通訊的應用程式：<xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient> 和 <xref:System.Net.Security.SslStream>。</span><span class="sxs-lookup"><span data-stu-id="ecc2f-108">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="ecc2f-109">無法升級到支援 Tls1.0、Tls1.1 或 Tls 1.2 的任何伺服器端應用程式。</span><span class="sxs-lookup"><span data-stu-id="ecc2f-109">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="ecc2f-110">降低</span><span class="sxs-lookup"><span data-stu-id="ecc2f-110">Mitigation</span></span>  

 <span data-ttu-id="ecc2f-111">建議的風險降低措施是將伺服器端應用程式升級至 Tls1.0、Tls1.1 或 Tls 1.2。</span><span class="sxs-lookup"><span data-stu-id="ecc2f-111">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="ecc2f-112">如果這並不可行，或是用戶端應用程式已中斷，則可使用 <xref:System.AppContext> 類別搭配下列兩種方式之一，停用這項功能：</span><span class="sxs-lookup"><span data-stu-id="ecc2f-112">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="ecc2f-113">以程式設計方式，利用如下所示的程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="ecc2f-113">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="ecc2f-114">因為 <xref:System.Net.ServicePointManager> 物件只能初始化一次，因此應用程式必須優先定義這些相容性設定。</span><span class="sxs-lookup"><span data-stu-id="ecc2f-114">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="ecc2f-115">在 app.config 檔案的區段中加入下列這一行 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) ：</span><span class="sxs-lookup"><span data-stu-id="ecc2f-115">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="ecc2f-116">但是請注意，我們並不建議您停用這項預設行為，因為這樣會讓應用程式較不安全。</span><span class="sxs-lookup"><span data-stu-id="ecc2f-116">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc2f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ecc2f-117">See also</span></span>

- [<span data-ttu-id="ecc2f-118">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="ecc2f-118">Application compatibility</span></span>](application-compatibility.md)
