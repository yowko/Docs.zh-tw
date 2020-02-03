---
title: TabControl 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- TabControl
helpviewer_keywords:
- TabControl control [Windows Forms], about TabControl control
- tab pages [Windows Forms], about tab pages
- property pages [Windows Forms], Windows Forms
- Windows Forms dialog boxes [Windows Forms], tabs
ms.assetid: 2b4ea784-a39d-463c-81d8-af74ce068476
ms.openlocfilehash: 2668169488b4087673fbf2552650c23cda780642
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742823"
---
# <a name="tabcontrol-control-overview-windows-forms"></a><span data-ttu-id="43afb-102">TabControl 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="43afb-102">TabControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="43afb-103">Windows Form <xref:System.Windows.Forms.TabControl> 顯示多個索引標籤，像是在筆記本中的分隔線或在檔案櫃中一組資料夾的標籤。</span><span class="sxs-lookup"><span data-stu-id="43afb-103">The Windows Forms <xref:System.Windows.Forms.TabControl> displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="43afb-104">索引標籤可以包含圖片和其他控制項。</span><span class="sxs-lookup"><span data-stu-id="43afb-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="43afb-105">您可以使用 [選項卡] 控制項來產生多頁對話方塊，在 Windows 作業系統中出現許多位置，例如 [控制台] 顯示內容。</span><span class="sxs-lookup"><span data-stu-id="43afb-105">You can use the tab control to produce the kind of multiple-page dialog box that appears many places in the Windows operating system, such as the Control Panel Display Properties.</span></span> <span data-ttu-id="43afb-106">此外，<xref:System.Windows.Forms.TabControl> 可以用來建立屬性頁，用來設定一組相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="43afb-106">Additionally, the <xref:System.Windows.Forms.TabControl> can be used to create property pages, which are used to set a group of related properties.</span></span>  
  
## <a name="working-with-tabcontrol"></a><span data-ttu-id="43afb-107">使用 TabControl</span><span class="sxs-lookup"><span data-stu-id="43afb-107">Working with TabControl</span></span>  
 <span data-ttu-id="43afb-108"><xref:System.Windows.Forms.TabControl> 的最重要屬性是 <xref:System.Windows.Forms.TabControl.TabPages%2A>，其中包含個別的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="43afb-108">The most important property of the <xref:System.Windows.Forms.TabControl> is <xref:System.Windows.Forms.TabControl.TabPages%2A>, which contains the individual tabs.</span></span> <span data-ttu-id="43afb-109">每個個別的索引標籤都是 <xref:System.Windows.Forms.TabPage> 物件。</span><span class="sxs-lookup"><span data-stu-id="43afb-109">Each individual tab is a <xref:System.Windows.Forms.TabPage> object.</span></span> <span data-ttu-id="43afb-110">當您按一下索引標籤時，它會引發該 <xref:System.Windows.Forms.TabPage> 物件的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="43afb-110">When a tab is clicked, it raises the <xref:System.Windows.Forms.Control.Click> event for that <xref:System.Windows.Forms.TabPage> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43afb-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43afb-111">See also</span></span>

- <xref:System.Windows.Forms.TabControl>
- [<span data-ttu-id="43afb-112">TabControl 控制項</span><span class="sxs-lookup"><span data-stu-id="43afb-112">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="43afb-113">操作說明：變更 Windows Forms TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="43afb-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="43afb-114">操作說明：將控制項加入至索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="43afb-114">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="43afb-115">操作說明：使用 Windows Forms TabControl 加入和移除索引標籤</span><span class="sxs-lookup"><span data-stu-id="43afb-115">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="43afb-116">操作說明：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="43afb-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="43afb-117">Windows Forms 中的對話方塊</span><span class="sxs-lookup"><span data-stu-id="43afb-117">Dialog Boxes in Windows Forms</span></span>](../dialog-boxes-in-windows-forms.md)
