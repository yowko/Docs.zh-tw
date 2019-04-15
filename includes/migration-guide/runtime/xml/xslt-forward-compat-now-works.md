---
ms.openlocfilehash: 2dd97fcce13ed1ac7baf4cd02f5881d31d7a9c4b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235133"
---
### <a name="xslt-forward-compat-now-works"></a><span data-ttu-id="dac00-101">XSLT 往後相容性現在可運作</span><span class="sxs-lookup"><span data-stu-id="dac00-101">XSLT forward compat now works</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dac00-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dac00-102">Details</span></span>|<span data-ttu-id="dac00-103">在 .NET Framework 4 中，XSLT 1.0 往後相容性有下列問題：</span><span class="sxs-lookup"><span data-stu-id="dac00-103">In the .NET Framework 4, XSLT 1.0 forward compatibility had the following issues:</span></span><ul><li><span data-ttu-id="dac00-104">如果樣式表的版本設為 2.0，而且剖析器遇到無法辨識的 XSLT 1.0 結構，則載入樣式表會失敗。</span><span class="sxs-lookup"><span data-stu-id="dac00-104">Loading a style sheet failed if its version was set to 2.0 and the parser encountered an unrecognized XSLT 1.0 construct.</span></span></li><li><span data-ttu-id="dac00-105">如果樣式表版本設為 1.1，<code>xsl:sort</code> 結構就無法排序資料。</span><span class="sxs-lookup"><span data-stu-id="dac00-105">The <code>xsl:sort</code> construct failed to sort data if the style sheet version was set to 1.1.</span></span></li></ul><span data-ttu-id="dac00-106">在 .NET Framework 4.5 中，這些問題已獲得修正，而且 XSLT 1.0 往後相容性模式可正常運作。</span><span class="sxs-lookup"><span data-stu-id="dac00-106">In the .NET Framework 4.5, these issues have been fixed, and XSLT 1.0 forward compatibility mode works properly.</span></span>|
|<span data-ttu-id="dac00-107">建議</span><span class="sxs-lookup"><span data-stu-id="dac00-107">Suggestion</span></span>|<span data-ttu-id="dac00-108">大部分的應用程式應該不會受到影響，不過在某些情況下，資料的排序方式將不同於 xsl:sort 現在遵守的方式。</span><span class="sxs-lookup"><span data-stu-id="dac00-108">Most apps should be unaffected, however data will be sorted differently in some cases now that xsl:sort is respected.</span></span> <span data-ttu-id="dac00-109">如果在 1.1 樣式表中使用 <code>xsl:sort</code>，確認應用程式不會依據未排序的資料順序。</span><span class="sxs-lookup"><span data-stu-id="dac00-109">If <code>xsl:sort</code> is used in 1.1 style sheets, confirm that apps were not depending on the unsorted order of data.</span></span> <span data-ttu-id="dac00-110">如果應用程式依賴 4.0 排序行為，請從樣式表中移除 <code>xsl:sort</code>。</span><span class="sxs-lookup"><span data-stu-id="dac00-110">If apps rely on the 4.0 sorting behavior, remove <code>xsl:sort</code> from the style sheet.</span></span>|
|<span data-ttu-id="dac00-111">範圍</span><span class="sxs-lookup"><span data-stu-id="dac00-111">Scope</span></span>|<span data-ttu-id="dac00-112">Edge</span><span class="sxs-lookup"><span data-stu-id="dac00-112">Edge</span></span>|
|<span data-ttu-id="dac00-113">版本</span><span class="sxs-lookup"><span data-stu-id="dac00-113">Version</span></span>|<span data-ttu-id="dac00-114">4.5</span><span class="sxs-lookup"><span data-stu-id="dac00-114">4.5</span></span>|
|<span data-ttu-id="dac00-115">類型</span><span class="sxs-lookup"><span data-stu-id="dac00-115">Type</span></span>|<span data-ttu-id="dac00-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="dac00-116">Runtime</span></span>|
|<span data-ttu-id="dac00-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dac00-117">Affected APIs</span></span>|<ul><li><xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
