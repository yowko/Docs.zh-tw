---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621956"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="fa6c6-101">使用自訂 DataTemplates 時，會斷斷續續無法捲動至 ItemsControls (例如 ListBox 和 DataGrid) 中的底部項目</span><span class="sxs-lookup"><span data-stu-id="fa6c6-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

#### <a name="details"></a><span data-ttu-id="fa6c6-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="fa6c6-102">Details</span></span>

<span data-ttu-id="fa6c6-103">在某些情況下，.NET Framework 4.5 中的 Bug 會導致在使用自訂 DataTemplates 時，ItemsControls (例如 <xref:System.Windows.Controls.ListBox?displayProperty=fullName>、<xref:System.Windows.Controls.ComboBox?displayProperty=fullName>、<xref:System.Windows.Controls.DataGrid?displayProperty=fullName> 等) 無法捲動至其底部項目。</span><span class="sxs-lookup"><span data-stu-id="fa6c6-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="fa6c6-104">如果嘗試捲動第二次 (在向上捲動之後)，則會再次運作。</span><span class="sxs-lookup"><span data-stu-id="fa6c6-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fa6c6-105">建議</span><span class="sxs-lookup"><span data-stu-id="fa6c6-105">Suggestion</span></span>

<span data-ttu-id="fa6c6-106">此問題在 .NET Framework 4.5.2 中已修正，因此可藉由升級至該版 .NET Framework (或更新版本) 來解決。</span><span class="sxs-lookup"><span data-stu-id="fa6c6-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="fa6c6-107">此外，使用者仍可將捲軸拖曳至這些集合中的最後一個項目，但可能需要嘗試兩次才能成功。</span><span class="sxs-lookup"><span data-stu-id="fa6c6-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>

| <span data-ttu-id="fa6c6-108">名稱</span><span class="sxs-lookup"><span data-stu-id="fa6c6-108">Name</span></span>    | <span data-ttu-id="fa6c6-109">值</span><span class="sxs-lookup"><span data-stu-id="fa6c6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fa6c6-110">影響範圍</span><span class="sxs-lookup"><span data-stu-id="fa6c6-110">Scope</span></span>   |<span data-ttu-id="fa6c6-111">Minor</span><span class="sxs-lookup"><span data-stu-id="fa6c6-111">Minor</span></span>|
|<span data-ttu-id="fa6c6-112">版本</span><span class="sxs-lookup"><span data-stu-id="fa6c6-112">Version</span></span>|<span data-ttu-id="fa6c6-113">4.5</span><span class="sxs-lookup"><span data-stu-id="fa6c6-113">4.5</span></span>|
|<span data-ttu-id="fa6c6-114">類型</span><span class="sxs-lookup"><span data-stu-id="fa6c6-114">Type</span></span>|<span data-ttu-id="fa6c6-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="fa6c6-115">Runtime</span></span>|
