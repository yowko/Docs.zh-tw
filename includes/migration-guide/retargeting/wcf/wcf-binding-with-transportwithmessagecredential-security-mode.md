---
ms.openlocfilehash: ce7e2db3f74ec24f47b1c224335451c997c4c349
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760971"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="ffa4b-101">使用 TransportWithMessageCredential 安全性模式的 WCF 繫結</span><span class="sxs-lookup"><span data-stu-id="ffa4b-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ffa4b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ffa4b-102">Details</span></span>|<span data-ttu-id="ffa4b-103">從 .NET Framework 4.6.1 開始，使用 TransportWithMessageCredential 安全性模式的 WCF 繫結可以設定以接收具有不帶正負號 &quot;to&quot; 標頭的非對稱安全性金鑰訊息。根據預設，不帶正負號的 &quot;to&quot; 標頭會繼續在 .NET Framework 4.6.1 中遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="ffa4b-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET Framework 4.6.1.</span></span> <span data-ttu-id="ffa4b-104">其只有在應用程式使用 Switch.System.ServiceModel.AllowUnsignedToHeader 組態參數來接受此新的作業模式時才會接受。</span><span class="sxs-lookup"><span data-stu-id="ffa4b-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.</span></span>|
|<span data-ttu-id="ffa4b-105">建議</span><span class="sxs-lookup"><span data-stu-id="ffa4b-105">Suggestion</span></span>|<span data-ttu-id="ffa4b-106">由於這是可選擇加入的功能，因此不會影響現有應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="ffa4b-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span><br/><span data-ttu-id="ffa4b-107">若要控制是否使用新的行為，請使用下列組態設定：</span><span class="sxs-lookup"><span data-stu-id="ffa4b-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="ffa4b-108">範圍</span><span class="sxs-lookup"><span data-stu-id="ffa4b-108">Scope</span></span>|<span data-ttu-id="ffa4b-109">透明</span><span class="sxs-lookup"><span data-stu-id="ffa4b-109">Transparent</span></span>|
|<span data-ttu-id="ffa4b-110">版本</span><span class="sxs-lookup"><span data-stu-id="ffa4b-110">Version</span></span>|<span data-ttu-id="ffa4b-111">4.6.1</span><span class="sxs-lookup"><span data-stu-id="ffa4b-111">4.6.1</span></span>|
|<span data-ttu-id="ffa4b-112">類型</span><span class="sxs-lookup"><span data-stu-id="ffa4b-112">Type</span></span>|<span data-ttu-id="ffa4b-113">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="ffa4b-113">Retargeting</span></span>|
|<span data-ttu-id="ffa4b-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ffa4b-114">Affected APIs</span></span>|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

