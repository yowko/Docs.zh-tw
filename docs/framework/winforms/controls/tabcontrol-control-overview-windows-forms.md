---
title: TabControl 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- TabControl
helpviewer_keywords:
- TabControl control [Windows Forms], about TabControl control
- tab pages [Windows Forms], about tab pages
- property pages [Windows Forms], Windows Forms
- Windows Forms dialog boxes [Windows Forms], tabs
ms.assetid: 2b4ea784-a39d-463c-81d8-af74ce068476
ms.openlocfilehash: 4511882aa4c7804e535f228dd150c26a8f7689f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971934"
---
# <a name="tabcontrol-control-overview-windows-forms"></a><span data-ttu-id="410aa-102">TabControl 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="410aa-102">TabControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="410aa-103">Windows Form <xref:System.Windows.Forms.TabControl> 顯示多個索引標籤，像是在筆記本中的分隔線或在檔案櫃中一組資料夾的標籤。</span><span class="sxs-lookup"><span data-stu-id="410aa-103">The Windows Forms <xref:System.Windows.Forms.TabControl> displays multiple tabs, like dividers in a notebook or labels in a set of folders in a filing cabinet.</span></span> <span data-ttu-id="410aa-104">索引標籤可以包含圖片和其他控制項。</span><span class="sxs-lookup"><span data-stu-id="410aa-104">The tabs can contain pictures and other controls.</span></span> <span data-ttu-id="410aa-105">您可以使用索引標籤控制項，以產生會顯示 Windows 作業系統，例如控制面板的顯示內容中的許多地方的多頁對話方塊中的類型。</span><span class="sxs-lookup"><span data-stu-id="410aa-105">You can use the tab control to produce the kind of multiple-page dialog box that appears many places in the Windows operating system, such as the Control Panel Display Properties.</span></span> <span data-ttu-id="410aa-106">此外，<xref:System.Windows.Forms.TabControl>可用來建立屬性頁，會用來設定一組相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="410aa-106">Additionally, the <xref:System.Windows.Forms.TabControl> can be used to create property pages, which are used to set a group of related properties.</span></span>  
  
## <a name="working-with-tabcontrol"></a><span data-ttu-id="410aa-107">使用 TabControl</span><span class="sxs-lookup"><span data-stu-id="410aa-107">Working with TabControl</span></span>  
 <span data-ttu-id="410aa-108">最重要的屬性<xref:System.Windows.Forms.TabControl>是<xref:System.Windows.Forms.TabControl.TabPages%2A>，其中包含的個別索引標籤。</span><span class="sxs-lookup"><span data-stu-id="410aa-108">The most important property of the <xref:System.Windows.Forms.TabControl> is <xref:System.Windows.Forms.TabControl.TabPages%2A>, which contains the individual tabs.</span></span> <span data-ttu-id="410aa-109">每個個別的索引標籤是<xref:System.Windows.Forms.TabPage>物件。</span><span class="sxs-lookup"><span data-stu-id="410aa-109">Each individual tab is a <xref:System.Windows.Forms.TabPage> object.</span></span> <span data-ttu-id="410aa-110">按一下索引標籤時，會引發<xref:System.Windows.Forms.Control.Click>事件，<xref:System.Windows.Forms.TabPage>物件。</span><span class="sxs-lookup"><span data-stu-id="410aa-110">When a tab is clicked, it raises the <xref:System.Windows.Forms.Control.Click> event for that <xref:System.Windows.Forms.TabPage> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410aa-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="410aa-111">See also</span></span>

- <xref:System.Windows.Forms.TabControl>
- [<span data-ttu-id="410aa-112">TabControl 控制項</span><span class="sxs-lookup"><span data-stu-id="410aa-112">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="410aa-113">如何：變更 Windows Form TabControl 的外觀</span><span class="sxs-lookup"><span data-stu-id="410aa-113">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="410aa-114">如何：將控制項加入索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="410aa-114">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="410aa-115">如何：新增和移除使用 Windows Form TabControl 的索引標籤</span><span class="sxs-lookup"><span data-stu-id="410aa-115">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="410aa-116">如何：停用索引標籤頁</span><span class="sxs-lookup"><span data-stu-id="410aa-116">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="410aa-117">Windows Forms 中的對話方塊</span><span class="sxs-lookup"><span data-stu-id="410aa-117">Dialog Boxes in Windows Forms</span></span>](../dialog-boxes-in-windows-forms.md)
