---
ms.openlocfilehash: d32725b0d3063d3320b73e02039ff567090da932
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496738"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="b60f6-101">WCF PipeConnection.GetHashAlgorithm 現在會使用 SHA256</span><span class="sxs-lookup"><span data-stu-id="b60f6-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="b60f6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b60f6-102">Details</span></span>

<span data-ttu-id="b60f6-103">從 .NET Framework 4.7.1 開始，Windows Communication Foundation 會使用 SHA256 雜湊來產生具名管道的隨機名稱。</span><span class="sxs-lookup"><span data-stu-id="b60f6-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="b60f6-104">在 .NET Framework 4.7 和舊版中，它已使用 SHA1 雜湊。</span><span class="sxs-lookup"><span data-stu-id="b60f6-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b60f6-105">建議</span><span class="sxs-lookup"><span data-stu-id="b60f6-105">Suggestion</span></span>

<span data-ttu-id="b60f6-106">如果在 .NET Framework 4.7.1 或更新版本上遇到這項變更的相容性問題，您可以在 app.config 檔案的 <code>&lt;runtime&gt;</code> 區段中新增下列程式行來退出變更：</span><span class="sxs-lookup"><span data-stu-id="b60f6-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="b60f6-107">名稱</span><span class="sxs-lookup"><span data-stu-id="b60f6-107">Name</span></span>    | <span data-ttu-id="b60f6-108">值</span><span class="sxs-lookup"><span data-stu-id="b60f6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b60f6-109">範圍</span><span class="sxs-lookup"><span data-stu-id="b60f6-109">Scope</span></span>   |<span data-ttu-id="b60f6-110">Minor</span><span class="sxs-lookup"><span data-stu-id="b60f6-110">Minor</span></span>|
|<span data-ttu-id="b60f6-111">版本</span><span class="sxs-lookup"><span data-stu-id="b60f6-111">Version</span></span>|<span data-ttu-id="b60f6-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="b60f6-112">4.7.1</span></span>|
|<span data-ttu-id="b60f6-113">類型</span><span class="sxs-lookup"><span data-stu-id="b60f6-113">Type</span></span>|<span data-ttu-id="b60f6-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="b60f6-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b60f6-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b60f6-115">Affected APIs</span></span>

<span data-ttu-id="b60f6-116">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="b60f6-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
