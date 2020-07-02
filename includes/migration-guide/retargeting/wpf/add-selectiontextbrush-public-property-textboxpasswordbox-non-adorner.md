---
ms.openlocfilehash: aade03c29ff16053a97683499cf719a98ae33f3f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617798"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a><span data-ttu-id="86e44-101">將 SelectionTextBrush 公用屬性新增至 TextBox/PasswordBox 非提示選取項目</span><span class="sxs-lookup"><span data-stu-id="86e44-101">Add SelectionTextBrush public property to TextBox/PasswordBox non-adorner selection</span></span>

#### <a name="details"></a><span data-ttu-id="86e44-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="86e44-102">Details</span></span>

<span data-ttu-id="86e44-103">在針對 <xref:System.Windows.Controls.TextBox> 和 <xref:System.Windows.Controls.PasswordBox> 使用[非提示型文字選取項目](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md)的 WPF 應用程式中，開發人員現在可以設定新增的 SelectionTextBrush 屬性，以變更所選文字的轉譯。</span><span class="sxs-lookup"><span data-stu-id="86e44-103">In WPF applications using [non-adorner based text selection](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) for <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox>, developers may now set the newly added SelectionTextBrush property in order to alter the rendering of the selected text.</span></span>  <span data-ttu-id="86e44-104">根據預設，此色彩會隨著 <xref:System.Windows.SystemColors.HighlightTextBrushKey> 而變更。</span><span class="sxs-lookup"><span data-stu-id="86e44-104">By default, this color changes with <xref:System.Windows.SystemColors.HighlightTextBrushKey>.</span></span>  <span data-ttu-id="86e44-105">如果未啟用非提示型文字選取範圍，則會忽略這個屬性。</span><span class="sxs-lookup"><span data-stu-id="86e44-105">If non-adorner based text selection is not enabled, this property does nothing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="86e44-106">建議</span><span class="sxs-lookup"><span data-stu-id="86e44-106">Suggestion</span></span>

<span data-ttu-id="86e44-107">啟用非提示型文字選取範圍後，您可以使用 <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> 屬性變更所選文字的外觀。</span><span class="sxs-lookup"><span data-stu-id="86e44-107">Once non-adorner based text selection is enabled, you can use the <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> and <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> property to change the appearance of the selected text.</span></span> <span data-ttu-id="86e44-108">此操作可以使用 XAML 完成：</span><span class="sxs-lookup"><span data-stu-id="86e44-108">This can be achieved using XAML:</span></span>

<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="86e44-109">名稱</span><span class="sxs-lookup"><span data-stu-id="86e44-109">Name</span></span>    | <span data-ttu-id="86e44-110">值</span><span class="sxs-lookup"><span data-stu-id="86e44-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="86e44-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="86e44-111">Scope</span></span>   | <span data-ttu-id="86e44-112">主要</span><span class="sxs-lookup"><span data-stu-id="86e44-112">Major</span></span>       |
| <span data-ttu-id="86e44-113">版本</span><span class="sxs-lookup"><span data-stu-id="86e44-113">Version</span></span> | <span data-ttu-id="86e44-114">4.8</span><span class="sxs-lookup"><span data-stu-id="86e44-114">4.8</span></span>         |
| <span data-ttu-id="86e44-115">類型</span><span class="sxs-lookup"><span data-stu-id="86e44-115">Type</span></span>    | <span data-ttu-id="86e44-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="86e44-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="86e44-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="86e44-117">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType>
- <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType>
- [<span data-ttu-id="86e44-118">System.Windows.Controls.TextBox</span><span class="sxs-lookup"><span data-stu-id="86e44-118">System.Windows.Controls.TextBox</span></span>](xref:System.Windows.Controls.TextBox)
- [<span data-ttu-id="86e44-119">System.Windows.Controls.PasswordBox</span><span class="sxs-lookup"><span data-stu-id="86e44-119">System.Windows.Controls.PasswordBox</span></span>](xref:System.Windows.Controls.PasswordBox)
