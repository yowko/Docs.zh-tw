---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235315"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="d523e-101">現在會遵守 MinFreeMemoryPercentageToActiveService</span><span class="sxs-lookup"><span data-stu-id="d523e-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d523e-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d523e-102">Details</span></span>|<span data-ttu-id="d523e-103">此設定建立伺服器上必須提供才能啟動 WCF 服務的最小記憶體。</span><span class="sxs-lookup"><span data-stu-id="d523e-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="d523e-104">其設計目的是為了防止發生 <xref:System.OutOfMemoryException?displayProperty=name> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d523e-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=name> exceptions.</span></span> <span data-ttu-id="d523e-105">在 .NET Framework 4.5 中，此設定不會造成影響。</span><span class="sxs-lookup"><span data-stu-id="d523e-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="d523e-106">在 .NET Framework 4.5.1 中，會遵守此設定。</span><span class="sxs-lookup"><span data-stu-id="d523e-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>|
|<span data-ttu-id="d523e-107">建議</span><span class="sxs-lookup"><span data-stu-id="d523e-107">Suggestion</span></span>|<span data-ttu-id="d523e-108">如果 Ｗeb 伺服器上可用的記憶體小於此組態設定所定義的百分比，則會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d523e-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="d523e-109">某些成功啟動並在有限記憶體環境下執行的 WCF 服務現在可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="d523e-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>|
|<span data-ttu-id="d523e-110">範圍</span><span class="sxs-lookup"><span data-stu-id="d523e-110">Scope</span></span>|<span data-ttu-id="d523e-111">次要</span><span class="sxs-lookup"><span data-stu-id="d523e-111">Minor</span></span>|
|<span data-ttu-id="d523e-112">版本</span><span class="sxs-lookup"><span data-stu-id="d523e-112">Version</span></span>|<span data-ttu-id="d523e-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d523e-113">4.5.1</span></span>|
|<span data-ttu-id="d523e-114">類型</span><span class="sxs-lookup"><span data-stu-id="d523e-114">Type</span></span>|<span data-ttu-id="d523e-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="d523e-115">Runtime</span></span>|
