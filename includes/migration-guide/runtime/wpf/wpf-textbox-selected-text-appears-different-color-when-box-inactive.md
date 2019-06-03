---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379561"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a><span data-ttu-id="65407-101">WPF TextBox 選取文字在文字方塊非作用中時，會以不同的色彩來顯示</span><span class="sxs-lookup"><span data-stu-id="65407-101">WPF TextBox selected text appears a different color when the text box is inactive</span></span>

|   |   |
|---|---|
|<span data-ttu-id="65407-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="65407-102">Details</span></span>|<span data-ttu-id="65407-103">在 .NET Framework 4.5 中，當 WPF 文字方塊控制項非作用中時 (沒有焦點)，方塊內的選取文字會以不同於控制項作用中的色彩來顯示。</span><span class="sxs-lookup"><span data-stu-id="65407-103">In .NET Framework 4.5, when a WPF text box control is inactive (it doesn't have focus), the selected text inside the box will appear a different color than when the control is active.</span></span>|
|<span data-ttu-id="65407-104">建議</span><span class="sxs-lookup"><span data-stu-id="65407-104">Suggestion</span></span>|<span data-ttu-id="65407-105">將 <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> 屬性設為 <code>false</code> 可以還原舊有 (.NET Framework 4.0) 行為。</span><span class="sxs-lookup"><span data-stu-id="65407-105">The previous (.NET Framework 4.0) behavior may be restored by setting the <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> property to <code>false</code>.</span></span>|
|<span data-ttu-id="65407-106">範圍</span><span class="sxs-lookup"><span data-stu-id="65407-106">Scope</span></span>|<span data-ttu-id="65407-107">Edge</span><span class="sxs-lookup"><span data-stu-id="65407-107">Edge</span></span>|
|<span data-ttu-id="65407-108">版本</span><span class="sxs-lookup"><span data-stu-id="65407-108">Version</span></span>|<span data-ttu-id="65407-109">4.5</span><span class="sxs-lookup"><span data-stu-id="65407-109">4.5</span></span>|
|<span data-ttu-id="65407-110">類型</span><span class="sxs-lookup"><span data-stu-id="65407-110">Type</span></span>|<span data-ttu-id="65407-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="65407-111">Runtime</span></span>|
|<span data-ttu-id="65407-112">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="65407-112">Affected APIs</span></span>|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
