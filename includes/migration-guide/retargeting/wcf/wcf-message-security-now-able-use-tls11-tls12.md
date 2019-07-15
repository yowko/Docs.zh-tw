---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859171"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="e6886-101">WCF 訊息安全性現在能夠使用 TLS1.1 和 TLS1.2</span><span class="sxs-lookup"><span data-stu-id="e6886-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e6886-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e6886-102">Details</span></span>|<span data-ttu-id="e6886-103">從 .NET Framework 4.7 開始，除了 SSL3.0 和 TLS1.0 之外，客戶還可以透過應用程式組態設定，在 WCF 訊息安全性設定 TLS1.1 或 TLS1.2。</span><span class="sxs-lookup"><span data-stu-id="e6886-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="e6886-104">建議</span><span class="sxs-lookup"><span data-stu-id="e6886-104">Suggestion</span></span>|<span data-ttu-id="e6886-105">在 .NET Framework 4.7 中，預設會停用 WCF 訊息安全性中的 TLS1.1 和 TLS1.2 支援。</span><span class="sxs-lookup"><span data-stu-id="e6886-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="e6886-106">您可以將下行新增到 app.config 或 web.config 檔案的 <code>&lt;runtime&gt;</code> 區段來啟用它：</span><span class="sxs-lookup"><span data-stu-id="e6886-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="e6886-107">範圍</span><span class="sxs-lookup"><span data-stu-id="e6886-107">Scope</span></span>|<span data-ttu-id="e6886-108">Edge</span><span class="sxs-lookup"><span data-stu-id="e6886-108">Edge</span></span>|
|<span data-ttu-id="e6886-109">版本</span><span class="sxs-lookup"><span data-stu-id="e6886-109">Version</span></span>|<span data-ttu-id="e6886-110">4.7</span><span class="sxs-lookup"><span data-stu-id="e6886-110">4.7</span></span>|
|<span data-ttu-id="e6886-111">類型</span><span class="sxs-lookup"><span data-stu-id="e6886-111">Type</span></span>|<span data-ttu-id="e6886-112">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="e6886-112">Retargeting</span></span>|

