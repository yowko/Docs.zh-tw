---
title: 如何：使用設計工具搭配 Windows Form ListView 控制項加入和移除項目
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 0480c8980f0eba17229fff0c1e947cac5216fb9e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275271"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="46a35-102">如何：使用設計工具搭配 Windows Form ListView 控制項加入和移除項目</span><span class="sxs-lookup"><span data-stu-id="46a35-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="46a35-103">加入 Windows Form 中的項目中的程序<xref:System.Windows.Forms.ListView>控制主要包含指定的項目，並將屬性指派給它。</span><span class="sxs-lookup"><span data-stu-id="46a35-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="46a35-104">隨時都可以新增或移除清單項目。</span><span class="sxs-lookup"><span data-stu-id="46a35-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="46a35-105">下列程序需要**Windows 應用程式**表單，其中包含專案<xref:System.Windows.Forms.ListView>控制項。</span><span class="sxs-lookup"><span data-stu-id="46a35-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="46a35-106">如需這類專案的設定資訊，請參閱[如何： 建立 Windows 應用程式專案](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)並[如何： 將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="46a35-106">For information about setting up such a project, see [How to: Create a Windows Application Project](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46a35-107">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="46a35-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="46a35-108">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="46a35-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="46a35-109">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="46a35-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="46a35-110">若要新增或移除項目使用設計工具</span><span class="sxs-lookup"><span data-stu-id="46a35-110">To add or remove items using the designer</span></span>  
  
1.  <span data-ttu-id="46a35-111">選取 <xref:System.Windows.Forms.ListView> 控制項。</span><span class="sxs-lookup"><span data-stu-id="46a35-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2.  <span data-ttu-id="46a35-112">在 [**屬性**] 視窗中，按一下**省略符號**(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 下一步按鈕<xref:System.Windows.Forms.ListView.Items%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="46a35-112">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="46a35-113">**ListViewItem 集合編輯器**隨即出現。</span><span class="sxs-lookup"><span data-stu-id="46a35-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="46a35-114">若要加入的項目，按一下**新增** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="46a35-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="46a35-115">您可以再設定屬性的新的項目，例如<xref:System.Windows.Forms.ListView.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="46a35-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4.  <span data-ttu-id="46a35-116">若要移除的項目，請選取它，然後按一下**移除** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="46a35-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a35-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46a35-117">See Also</span></span>  
 [<span data-ttu-id="46a35-118">ListView 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="46a35-118">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="46a35-119">操作說明：將資料行加入至 Windows Forms ListView 控制項</span><span class="sxs-lookup"><span data-stu-id="46a35-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="46a35-120">操作說明：使用 Windows Forms ListView 控制項以資料行顯示子項目</span><span class="sxs-lookup"><span data-stu-id="46a35-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="46a35-121">操作說明：顯示 Windows Forms ListView 控制項的圖示</span><span class="sxs-lookup"><span data-stu-id="46a35-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="46a35-122">操作說明：將自訂資訊新增至 TreeView 或 ListView 控制項 (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="46a35-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [<span data-ttu-id="46a35-123">操作說明：在 Windows Forms ListView 控制項中群組項目</span><span class="sxs-lookup"><span data-stu-id="46a35-123">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
