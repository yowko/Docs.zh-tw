---
ms.openlocfilehash: 9baca45de1c8994f610815e84fdee8ba3930eb04
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496096"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="76e86-101">WCF MsmqSecureHashAlgorithm 預設值現在是 SHA256</span><span class="sxs-lookup"><span data-stu-id="76e86-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="76e86-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="76e86-102">Details</span></span>

<span data-ttu-id="76e86-103">從 .NET Framework 4.7.1 開始，WCF 中用於 Msmq 訊息的預設訊息簽署演算法是 SHA256。</span><span class="sxs-lookup"><span data-stu-id="76e86-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="76e86-104">在 .NET Framework 4.7 和舊版中，預設的訊息簽署演算法是 SHA1。</span><span class="sxs-lookup"><span data-stu-id="76e86-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="76e86-105">建議</span><span class="sxs-lookup"><span data-stu-id="76e86-105">Suggestion</span></span>

<span data-ttu-id="76e86-106">如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來退出變更：</span><span class="sxs-lookup"><span data-stu-id="76e86-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="76e86-107">名稱</span><span class="sxs-lookup"><span data-stu-id="76e86-107">Name</span></span>    | <span data-ttu-id="76e86-108">值</span><span class="sxs-lookup"><span data-stu-id="76e86-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="76e86-109">範圍</span><span class="sxs-lookup"><span data-stu-id="76e86-109">Scope</span></span>   |<span data-ttu-id="76e86-110">Minor</span><span class="sxs-lookup"><span data-stu-id="76e86-110">Minor</span></span>|
|<span data-ttu-id="76e86-111">版本</span><span class="sxs-lookup"><span data-stu-id="76e86-111">Version</span></span>|<span data-ttu-id="76e86-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="76e86-112">4.7.1</span></span>|
|<span data-ttu-id="76e86-113">類型</span><span class="sxs-lookup"><span data-stu-id="76e86-113">Type</span></span>|<span data-ttu-id="76e86-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="76e86-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="76e86-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="76e86-115">Affected APIs</span></span>

<span data-ttu-id="76e86-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="76e86-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
