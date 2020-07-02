---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620099"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="388fc-101">WPF TextBox 選取文字在文字方塊非作用中時，會以不同的色彩來顯示</span><span class="sxs-lookup"><span data-stu-id="388fc-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

#### <a name="details"></a><span data-ttu-id="388fc-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="388fc-102">Details</span></span>

<span data-ttu-id="388fc-103">在 .NET Framework 4.5 中，當 WPF 文字方塊控制項非作用中時 (沒有焦點)，方塊內的選取文字會以不同於控制項作用中的色彩來顯示。</span><span class="sxs-lookup"><span data-stu-id="388fc-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="388fc-104">建議</span><span class="sxs-lookup"><span data-stu-id="388fc-104">Suggestion</span></span>

<span data-ttu-id="388fc-105">將 <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> 屬性設為 <code>false</code> 可以還原舊有 (.NET Framework 4.0) 行為。</span><span class="sxs-lookup"><span data-stu-id="388fc-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>

| <span data-ttu-id="388fc-106">名稱</span><span class="sxs-lookup"><span data-stu-id="388fc-106">Name</span></span>    | <span data-ttu-id="388fc-107">值</span><span class="sxs-lookup"><span data-stu-id="388fc-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="388fc-108">影響範圍</span><span class="sxs-lookup"><span data-stu-id="388fc-108">Scope</span></span>   |<span data-ttu-id="388fc-109">Edge</span><span class="sxs-lookup"><span data-stu-id="388fc-109">Edge</span></span>|
|<span data-ttu-id="388fc-110">版本</span><span class="sxs-lookup"><span data-stu-id="388fc-110">Version</span></span>|<span data-ttu-id="388fc-111">4.5</span><span class="sxs-lookup"><span data-stu-id="388fc-111">4.5</span></span>|
|<span data-ttu-id="388fc-112">類型</span><span class="sxs-lookup"><span data-stu-id="388fc-112">Type</span></span>|<span data-ttu-id="388fc-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="388fc-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="388fc-114">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="388fc-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
