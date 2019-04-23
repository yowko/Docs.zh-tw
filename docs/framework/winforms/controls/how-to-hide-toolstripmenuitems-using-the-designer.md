---
title: HOW TO：使用設計工具隱藏 ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 31c597a0e2cbf41484f19c8d4179823e9fb929ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317671"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="b1cc9-102">HOW TO：使用設計工具隱藏 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="b1cc9-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="b1cc9-103">隱藏功能表項目是用來控制您的應用程式的使用者介面 (UI)，並限制使用者命令。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="b1cc9-104">通常，您要隱藏整個功能表無法使用時，所有在其上的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="b1cc9-105">這代表使用者分心。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="b1cc9-106">此外，您可能想要隱藏和停用功能表或功能表項目，為單獨的隱藏不會防止使用者使用攠摝坫存取功能表命令。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="b1cc9-107">如需有關如何停用功能表項目的詳細資訊，請參閱[How to:使用設計工具停用 ToolStripMenuItems](how-to-disable-toolstripmenuitems-using-the-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1cc9-108">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b1cc9-109">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b1cc9-110">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="b1cc9-111">若要隱藏最上層的功能表和它的子功能表項目</span><span class="sxs-lookup"><span data-stu-id="b1cc9-111">To hide a top-level menu and its submenu items</span></span>  
  
1. <span data-ttu-id="b1cc9-112">選取最上層的功能表項目，並設定其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>或是<xref:System.Windows.Forms.ToolStripItem.Available%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="b1cc9-113">當您隱藏最上層的功能表項目時，同時也會隱藏該功能表內的所有功能表項目。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="b1cc9-114">如果您按一下以外的地方上<xref:System.Windows.Forms.MenuStrip>設定之後<xref:System.Windows.Forms.ToolStripItem.Visible%2A>到`false`，整個最上層功能表項目和它的子功能表項目會消失從您的表單，因此顯示執行階段的影響您的動作。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="b1cc9-115">若要在設計階段顯示隱藏的最上層功能表項目，請按一下<xref:System.Windows.Forms.MenuStrip>中**元件匣**，在**文件大綱**，或在屬性方格的頂端。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1cc9-116">您很少會隱藏整個功能表除了中合併多個文件介面 (MDI) 子功能表。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="b1cc9-117">若要隱藏的子功能表項目</span><span class="sxs-lookup"><span data-stu-id="b1cc9-117">To hide a submenu item</span></span>  
  
1. <span data-ttu-id="b1cc9-118">選取子功能表項目，並設定其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>屬性設`false`。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="b1cc9-119">當您隱藏子功能表項目時，它仍會顯示在設計階段在表單上，讓您可以進一步的工作，輕鬆地選取它。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="b1cc9-120">實際上會在執行階段隱藏。</span><span class="sxs-lookup"><span data-stu-id="b1cc9-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cc9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1cc9-121">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [<span data-ttu-id="b1cc9-122">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="b1cc9-122">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
- [<span data-ttu-id="b1cc9-123">如何：使用設計工具停用 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="b1cc9-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](how-to-disable-toolstripmenuitems-using-the-designer.md)
