---
title: "如何：使用設計工具隱藏 ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ac840953e34ac6726bb1c240c062d0f17b8cb71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="88e4b-102">如何：使用設計工具隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="88e4b-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="88e4b-103">隱藏功能表項目是能夠控制您的應用程式的使用者介面 (UI)，並限制使用者命令。</span><span class="sxs-lookup"><span data-stu-id="88e4b-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="88e4b-104">通常，您要隱藏整個功能表，當所有在其上的功能表項目都無法使用。</span><span class="sxs-lookup"><span data-stu-id="88e4b-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="88e4b-105">這代表使用者的分心。</span><span class="sxs-lookup"><span data-stu-id="88e4b-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="88e4b-106">此外，您可能想要隱藏並停用功能表或功能表項目，如單獨隱藏不會阻止使用者使用快速鍵來存取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="88e4b-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="88e4b-107">如需有關如何停用功能表項目的詳細資訊，請參閱[如何： 停用 ToolStripMenuItems 使用設計工具](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="88e4b-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88e4b-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="88e4b-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="88e4b-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="88e4b-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="88e4b-110">如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)</span><span class="sxs-lookup"><span data-stu-id="88e4b-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="88e4b-111">若要隱藏最上層功能表及其子功能表項目</span><span class="sxs-lookup"><span data-stu-id="88e4b-111">To hide a top-level menu and its submenu items</span></span>  
  
1.  <span data-ttu-id="88e4b-112">選取最上層功能表項目，並設定其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>或<xref:System.Windows.Forms.ToolStripItem.Available%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="88e4b-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="88e4b-113">當您隱藏最上層功能表項目時，也會隱藏該功能表中的所有功能表項目。</span><span class="sxs-lookup"><span data-stu-id="88e4b-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="88e4b-114">如果您按一下以外的地方上<xref:System.Windows.Forms.MenuStrip>之後設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>至`false`，整個最上層功能表項目和它的子功能表項目會從您的表單，因此顯示您的動作的執行階段影響消失。</span><span class="sxs-lookup"><span data-stu-id="88e4b-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="88e4b-115">若要在設計階段顯示隱藏的最上層功能表項目，請按一下<xref:System.Windows.Forms.MenuStrip>中**元件匣**，請在**文件大綱**，或在屬性方格的頂端。</span><span class="sxs-lookup"><span data-stu-id="88e4b-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88e4b-116">您很少會隱藏整個功能表除了中合併多個文件介面 (MDI) 子功能表。</span><span class="sxs-lookup"><span data-stu-id="88e4b-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="88e4b-117">若要隱藏子功能表項目</span><span class="sxs-lookup"><span data-stu-id="88e4b-117">To hide a submenu item</span></span>  
  
1.  <span data-ttu-id="88e4b-118">選取的子功能表項目，並設定其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性`false`。</span><span class="sxs-lookup"><span data-stu-id="88e4b-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="88e4b-119">當您隱藏子功能表項目時，它仍會顯示在設計階段在表單上，因此您可以進一步的工作，輕鬆地選取它。</span><span class="sxs-lookup"><span data-stu-id="88e4b-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="88e4b-120">實際上會在執行階段隱藏。</span><span class="sxs-lookup"><span data-stu-id="88e4b-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e4b-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="88e4b-121">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [<span data-ttu-id="88e4b-122">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="88e4b-122">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="88e4b-123">操作說明：使用設計工具停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="88e4b-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
