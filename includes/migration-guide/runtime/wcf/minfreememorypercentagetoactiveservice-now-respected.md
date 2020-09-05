---
ms.openlocfilehash: b23182ad1da8208a69b78fc7bc872780d386a59a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496878"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="320a6-101">現在會遵守 MinFreeMemoryPercentageToActiveService</span><span class="sxs-lookup"><span data-stu-id="320a6-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="320a6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="320a6-102">Details</span></span>

<span data-ttu-id="320a6-103">此設定建立伺服器上必須提供才能啟動 WCF 服務的最小記憶體。</span><span class="sxs-lookup"><span data-stu-id="320a6-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="320a6-104">其設計目的是為了防止發生 <xref:System.OutOfMemoryException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="320a6-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="320a6-105">在 .NET Framework 4.5 中，此設定不會造成影響。</span><span class="sxs-lookup"><span data-stu-id="320a6-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="320a6-106">在 .NET Framework 4.5.1 中，會遵守此設定。</span><span class="sxs-lookup"><span data-stu-id="320a6-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="320a6-107">建議</span><span class="sxs-lookup"><span data-stu-id="320a6-107">Suggestion</span></span>

<span data-ttu-id="320a6-108">如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="320a6-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="320a6-109">某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="320a6-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="320a6-110">名稱</span><span class="sxs-lookup"><span data-stu-id="320a6-110">Name</span></span>    | <span data-ttu-id="320a6-111">值</span><span class="sxs-lookup"><span data-stu-id="320a6-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="320a6-112">範圍</span><span class="sxs-lookup"><span data-stu-id="320a6-112">Scope</span></span>   |<span data-ttu-id="320a6-113">Minor</span><span class="sxs-lookup"><span data-stu-id="320a6-113">Minor</span></span>|
|<span data-ttu-id="320a6-114">版本</span><span class="sxs-lookup"><span data-stu-id="320a6-114">Version</span></span>|<span data-ttu-id="320a6-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="320a6-115">4.5.1</span></span>|
|<span data-ttu-id="320a6-116">類型</span><span class="sxs-lookup"><span data-stu-id="320a6-116">Type</span></span>|<span data-ttu-id="320a6-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="320a6-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="320a6-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="320a6-118">Affected APIs</span></span>

<span data-ttu-id="320a6-119">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="320a6-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
