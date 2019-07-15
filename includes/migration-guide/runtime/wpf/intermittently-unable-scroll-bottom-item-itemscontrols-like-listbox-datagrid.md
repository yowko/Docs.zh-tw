---
ms.openlocfilehash: 2674edc595d8e4e1e4c2ee42b39aa59265127462
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803226"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="4a3ae-101">使用自訂 DataTemplates 時，會斷斷續續無法捲動至 ItemsControls (例如 ListBox 和 DataGrid) 中的底部項目</span><span class="sxs-lookup"><span data-stu-id="4a3ae-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4a3ae-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4a3ae-102">Details</span></span>|<span data-ttu-id="4a3ae-103">在某些情況下，.NET Framework 4.5 中的 Bug 會導致在使用自訂 DataTemplates 時，ItemsControls (例如 <xref:System.Windows.Controls.ListBox?displayProperty=name>、<xref:System.Windows.Controls.ComboBox?displayProperty=name>、<xref:System.Windows.Controls.DataGrid?displayProperty=name> 等) 無法捲動至其底部項目。</span><span class="sxs-lookup"><span data-stu-id="4a3ae-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="4a3ae-104">如果嘗試捲動第二次 (在向上捲動之後)，則會再次運作。</span><span class="sxs-lookup"><span data-stu-id="4a3ae-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>|
|<span data-ttu-id="4a3ae-105">建議</span><span class="sxs-lookup"><span data-stu-id="4a3ae-105">Suggestion</span></span>|<span data-ttu-id="4a3ae-106">此問題在 .NET Framework 4.5.2 中已修正，因此可藉由升級至該版 .NET Framework (或更新版本) 來解決。</span><span class="sxs-lookup"><span data-stu-id="4a3ae-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="4a3ae-107">此外，使用者仍可將捲軸拖曳至這些集合中的最後一個項目，但可能需要嘗試兩次才能成功。</span><span class="sxs-lookup"><span data-stu-id="4a3ae-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>|
|<span data-ttu-id="4a3ae-108">範圍</span><span class="sxs-lookup"><span data-stu-id="4a3ae-108">Scope</span></span>|<span data-ttu-id="4a3ae-109">次要</span><span class="sxs-lookup"><span data-stu-id="4a3ae-109">Minor</span></span>|
|<span data-ttu-id="4a3ae-110">版本</span><span class="sxs-lookup"><span data-stu-id="4a3ae-110">Version</span></span>|<span data-ttu-id="4a3ae-111">4.5</span><span class="sxs-lookup"><span data-stu-id="4a3ae-111">4.5</span></span>|
|<span data-ttu-id="4a3ae-112">類型</span><span class="sxs-lookup"><span data-stu-id="4a3ae-112">Type</span></span>|<span data-ttu-id="4a3ae-113">執行階段</span><span class="sxs-lookup"><span data-stu-id="4a3ae-113">Runtime</span></span>|

