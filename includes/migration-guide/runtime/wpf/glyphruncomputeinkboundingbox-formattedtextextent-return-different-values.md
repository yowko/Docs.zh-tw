---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620084"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="1c9d9-101">從 .NET Framework 4.5 開始，GlyphRun.ComputeInkBoundingBox() 和 FormattedText.Extent 會傳回不同的值</span><span class="sxs-lookup"><span data-stu-id="1c9d9-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="1c9d9-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1c9d9-102">Details</span></span>

<span data-ttu-id="1c9d9-103">在 .NET Framework 4.5 中，已改善 <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> 和 <xref:System.Windows.Media.FormattedText.Extent>，以解決這些方塊在 .NET Framework 4.0 的某些情況下對包含的字符太小的問題。</span><span class="sxs-lookup"><span data-stu-id="1c9d9-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="1c9d9-104">因此，從 .NET Framework 4.5 開始，某些週框方塊會比較大，導致 UI 配置中有些微差異。</span><span class="sxs-lookup"><span data-stu-id="1c9d9-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1c9d9-105">建議</span><span class="sxs-lookup"><span data-stu-id="1c9d9-105">Suggestion</span></span>

<span data-ttu-id="1c9d9-106">請注意，某些字符週框方塊大小已增加。</span><span class="sxs-lookup"><span data-stu-id="1c9d9-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="1c9d9-107">這些變更通常會改進呈現方式和叫用方塊測試，但如果想要舊版 (.NET 4.5 之前) 行為，則可以將下列項目新增至 app.config 檔案來加入此行為：</span><span class="sxs-lookup"><span data-stu-id="1c9d9-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="1c9d9-108">名稱</span><span class="sxs-lookup"><span data-stu-id="1c9d9-108">Name</span></span>    | <span data-ttu-id="1c9d9-109">值</span><span class="sxs-lookup"><span data-stu-id="1c9d9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1c9d9-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="1c9d9-110">Scope</span></span>   |<span data-ttu-id="1c9d9-111">Edge</span><span class="sxs-lookup"><span data-stu-id="1c9d9-111">Edge</span></span>|
|<span data-ttu-id="1c9d9-112">版本</span><span class="sxs-lookup"><span data-stu-id="1c9d9-112">Version</span></span>|<span data-ttu-id="1c9d9-113">4.5</span><span class="sxs-lookup"><span data-stu-id="1c9d9-113">4.5</span></span>|
|<span data-ttu-id="1c9d9-114">類型</span><span class="sxs-lookup"><span data-stu-id="1c9d9-114">Type</span></span>|<span data-ttu-id="1c9d9-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="1c9d9-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1c9d9-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1c9d9-116">Affected APIs</span></span>

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
