---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620049"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="ef66a-101">現在會遵守 MinFreeMemoryPercentageToActiveService</span><span class="sxs-lookup"><span data-stu-id="ef66a-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="ef66a-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ef66a-102">Details</span></span>

<span data-ttu-id="ef66a-103">此設定建立伺服器上必須提供才能啟動 WCF 服務的最小記憶體。</span><span class="sxs-lookup"><span data-stu-id="ef66a-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="ef66a-104">其設計目的是為了防止發生 <xref:System.OutOfMemoryException?displayProperty=fullName> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ef66a-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="ef66a-105">在 .NET Framework 4.5 中，此設定不會造成影響。</span><span class="sxs-lookup"><span data-stu-id="ef66a-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="ef66a-106">在 .NET Framework 4.5.1 中，會遵守此設定。</span><span class="sxs-lookup"><span data-stu-id="ef66a-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ef66a-107">建議</span><span class="sxs-lookup"><span data-stu-id="ef66a-107">Suggestion</span></span>

<span data-ttu-id="ef66a-108">如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ef66a-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="ef66a-109">某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="ef66a-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="ef66a-110">名稱</span><span class="sxs-lookup"><span data-stu-id="ef66a-110">Name</span></span>    | <span data-ttu-id="ef66a-111">值</span><span class="sxs-lookup"><span data-stu-id="ef66a-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ef66a-112">影響範圍</span><span class="sxs-lookup"><span data-stu-id="ef66a-112">Scope</span></span>   |<span data-ttu-id="ef66a-113">Minor</span><span class="sxs-lookup"><span data-stu-id="ef66a-113">Minor</span></span>|
|<span data-ttu-id="ef66a-114">版本</span><span class="sxs-lookup"><span data-stu-id="ef66a-114">Version</span></span>|<span data-ttu-id="ef66a-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="ef66a-115">4.5.1</span></span>|
|<span data-ttu-id="ef66a-116">類型</span><span class="sxs-lookup"><span data-stu-id="ef66a-116">Type</span></span>|<span data-ttu-id="ef66a-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="ef66a-117">Runtime</span></span>|
