---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620084"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a>從 .NET Framework 4.5 開始，GlyphRun.ComputeInkBoundingBox() 和 FormattedText.Extent 會傳回不同的值

#### <a name="details"></a>詳細資料

在 .NET Framework 4.5 中，已改善 <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> 和 <xref:System.Windows.Media.FormattedText.Extent>，以解決這些方塊在 .NET Framework 4.0 的某些情況下對包含的字符太小的問題。 因此，從 .NET Framework 4.5 開始，某些週框方塊會比較大，導致 UI 配置中有些微差異。

#### <a name="suggestion"></a>建議

請注意，某些字符週框方塊大小已增加。 這些變更通常會改進呈現方式和叫用方塊測試，但如果想要舊版 (.NET 4.5 之前) 行為，則可以將下列項目新增至 app.config 檔案來加入此行為：<pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
