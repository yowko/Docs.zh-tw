---
title: HOW TO：Move ToolStripMenuItems
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: 50b5fd16780147ad7592035a901d993495dcb878
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708947"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="704d6-102">HOW TO：Move ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="704d6-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="704d6-103">在設計階段，您可以移動整個最上層的功能表與他們的功能表項目到不同位置<xref:System.Windows.Forms.MenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="704d6-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="704d6-104">您也可以最上層的功能表間移動個別的功能表項目，或變更功能表中功能表項目的位置。</span><span class="sxs-lookup"><span data-stu-id="704d6-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="704d6-105">根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。</span><span class="sxs-lookup"><span data-stu-id="704d6-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="704d6-106">若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。</span><span class="sxs-lookup"><span data-stu-id="704d6-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="704d6-107">如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="704d6-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="704d6-108">若要將最上層的功能表和它的功能表項目移至另一個最上層的位置</span><span class="sxs-lookup"><span data-stu-id="704d6-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="704d6-109">按一下並按住滑鼠左鍵，在您想要移動的功能表上。</span><span class="sxs-lookup"><span data-stu-id="704d6-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="704d6-110">將插入點拖曳至想要的新位置之前的最上層功能表，然後放開滑鼠左的按鈕。</span><span class="sxs-lookup"><span data-stu-id="704d6-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="704d6-111">選取的功能表往右移動插入點。</span><span class="sxs-lookup"><span data-stu-id="704d6-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="704d6-112">若要將最上層的功能表和它的功能表項目移至 下拉式清單位置</span><span class="sxs-lookup"><span data-stu-id="704d6-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="704d6-113">以滑鼠左鍵按一下您想要移動並按下 CTRL + X，或以滑鼠右鍵按一下  功能表並選取  功能表**剪下**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="704d6-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="704d6-114">在目的地最上層功能表中，以滑鼠左鍵按一下預定新位置上方的功能表項目及按下 CTRL + V，或以滑鼠右鍵按一下預定新位置上方的功能表項目並選取**貼上**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="704d6-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="704d6-115">選取的功能表項目之後插入您剪下功能表。</span><span class="sxs-lookup"><span data-stu-id="704d6-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="704d6-116">若要移動的功能表項目集合編輯器的使用中的功能表項目</span><span class="sxs-lookup"><span data-stu-id="704d6-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="704d6-117">以滑鼠右鍵按一下含有您想要移動的功能表項目的功能表。</span><span class="sxs-lookup"><span data-stu-id="704d6-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="704d6-118">從捷徑功能表，選擇**編輯 DropDownItems**。</span><span class="sxs-lookup"><span data-stu-id="704d6-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="704d6-119">在 **項目集合編輯器**，以滑鼠左鍵按一下您想要移動的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="704d6-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="704d6-120">按一下向上和向下鍵移動的功能表中功能表項目。</span><span class="sxs-lookup"><span data-stu-id="704d6-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="704d6-121">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="704d6-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="704d6-122">若要移動使用鍵盤的功能表中功能表項目</span><span class="sxs-lookup"><span data-stu-id="704d6-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="704d6-123">按住 ALT 鍵。</span><span class="sxs-lookup"><span data-stu-id="704d6-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="704d6-124">按一下並按住滑鼠左鍵您想要移動的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="704d6-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="704d6-125">將功能表項目拖曳至新的位置，然後放開滑鼠左的按鈕。</span><span class="sxs-lookup"><span data-stu-id="704d6-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="704d6-126">若要移至另一個功能表的功能表項目</span><span class="sxs-lookup"><span data-stu-id="704d6-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="704d6-127">以滑鼠左鍵按一下您想要移動並按下 CTRL + X，或以滑鼠右鍵按一下功能表項目，然後選擇功能表項目**剪下**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="704d6-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="704d6-128">以滑鼠左鍵按一下的功能表中會包含您剪下功能表項目。</span><span class="sxs-lookup"><span data-stu-id="704d6-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="704d6-129">以滑鼠左鍵按一下預定新位置之前的功能表項目及按下 CTRL + V，或以滑鼠右鍵按一下預定新位置，然後選取之前的功能表項目**貼上**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="704d6-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="704d6-130">選取的功能表項目之後插入您剪下功能表項目。</span><span class="sxs-lookup"><span data-stu-id="704d6-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704d6-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="704d6-131">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="704d6-132">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="704d6-132">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
