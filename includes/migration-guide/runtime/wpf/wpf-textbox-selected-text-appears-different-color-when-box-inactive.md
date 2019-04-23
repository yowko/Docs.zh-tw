---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803511"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="3bcfa-101">WPF TextBox 選取文字在文字方塊非作用中時，會以不同的色彩來顯示</span><span class="sxs-lookup"><span data-stu-id="3bcfa-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3bcfa-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3bcfa-102">Details</span></span>|<span data-ttu-id="3bcfa-103">在 .NET Framework 4.5 中，當 WPF 文字方塊控制項非作用中時 (沒有焦點)，方塊內的選取文字會以不同於控制項作用中的色彩來顯示。</span><span class="sxs-lookup"><span data-stu-id="3bcfa-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="3bcfa-104">建議</span><span class="sxs-lookup"><span data-stu-id="3bcfa-104">Suggestion</span></span>|<span data-ttu-id="3bcfa-105">將 <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> 屬性設為 <code>false</code> 可以還原舊有 (.NET Framework 4.0) 行為。</span><span class="sxs-lookup"><span data-stu-id="3bcfa-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="3bcfa-106">範圍</span><span class="sxs-lookup"><span data-stu-id="3bcfa-106">Scope</span></span>|<span data-ttu-id="3bcfa-107">Edge</span><span class="sxs-lookup"><span data-stu-id="3bcfa-107">Edge</span></span>|
|<span data-ttu-id="3bcfa-108">版本</span><span class="sxs-lookup"><span data-stu-id="3bcfa-108">Version</span></span>|<span data-ttu-id="3bcfa-109">4.5</span><span class="sxs-lookup"><span data-stu-id="3bcfa-109">4.5</span></span>|
|<span data-ttu-id="3bcfa-110">類型</span><span class="sxs-lookup"><span data-stu-id="3bcfa-110">Type</span></span>|<span data-ttu-id="3bcfa-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="3bcfa-111">Runtime</span></span>|
|<span data-ttu-id="3bcfa-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3bcfa-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
