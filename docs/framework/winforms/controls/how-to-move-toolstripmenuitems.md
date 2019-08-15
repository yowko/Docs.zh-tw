---
title: 作法：移動 ToolStripMenuItems
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
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039802"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="1e709-102">作法：移動 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="1e709-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="1e709-103">在設計階段, 您可以將整個最上層功能表及其功能表項目移至上<xref:System.Windows.Forms.MenuStrip>的不同位置。</span><span class="sxs-lookup"><span data-stu-id="1e709-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="1e709-104">您也可以在最上層功能表之間移動個別的功能表項目, 或變更功能表中功能表項目的位置。</span><span class="sxs-lookup"><span data-stu-id="1e709-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="1e709-105">將最上層功能表及其功能表項目移至另一個最上層位置</span><span class="sxs-lookup"><span data-stu-id="1e709-105">To move a top-level menu and its menu items to another top-level location</span></span>

1. <span data-ttu-id="1e709-106">在您要移動的功能表上, 按一下並按住滑鼠左鍵。</span><span class="sxs-lookup"><span data-stu-id="1e709-106">Click and hold down the left mouse button on the menu that you want to move.</span></span>

2. <span data-ttu-id="1e709-107">將插入點拖曳至所需新位置之前的最上層功能表, 然後放開滑鼠左鍵。</span><span class="sxs-lookup"><span data-stu-id="1e709-107">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>

     <span data-ttu-id="1e709-108">選取的功能表會移至插入點的右邊。</span><span class="sxs-lookup"><span data-stu-id="1e709-108">The selected menu moves to the right of the insertion point.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="1e709-109">將最上層功能表及其功能表項目移至下拉式位置</span><span class="sxs-lookup"><span data-stu-id="1e709-109">To move a top-level menu and its menu items to a drop-down location</span></span>

1. <span data-ttu-id="1e709-110">以滑鼠左鍵按一下您想要移動的功能表, 然後按 CTRL + X, 或以滑鼠右鍵按一下功能表, 然後從快捷方式功能表選取 [**剪**下]。</span><span class="sxs-lookup"><span data-stu-id="1e709-110">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="1e709-111">在目的地最上層功能表中, 以滑鼠左鍵按一下預定新位置上方的功能表項目, 然後按 CTRL + V, 或以滑鼠右鍵按一下預定新位置上方的功能表項目, 然後從快捷方式功能表選取 [**貼**上]。</span><span class="sxs-lookup"><span data-stu-id="1e709-111">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="1e709-112">您剪下的功能表會在選取的功能表項目之後插入。</span><span class="sxs-lookup"><span data-stu-id="1e709-112">The menu that you cut is inserted after the selected menu item.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="1e709-113">使用 Items 集合編輯器移動功能表中的功能表項目</span><span class="sxs-lookup"><span data-stu-id="1e709-113">To move a menu item within a menu using the Items Collection Editor</span></span>

1. <span data-ttu-id="1e709-114">以滑鼠右鍵按一下包含您要移動之功能表項目的功能表。</span><span class="sxs-lookup"><span data-stu-id="1e709-114">Right-click the menu that contains the menu item you want to move.</span></span>

2. <span data-ttu-id="1e709-115">從快捷方式功能表中, 選擇 [**編輯控制項 dropdownitems**]。</span><span class="sxs-lookup"><span data-stu-id="1e709-115">From the shortcut menu, choose **Edit DropDownItems**.</span></span>

3. <span data-ttu-id="1e709-116">在 [**專案集合編輯器**] 中, 以滑鼠左鍵按一下您要移動的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="1e709-116">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>

4. <span data-ttu-id="1e709-117">按一下向上箭號和向下鍵, 即可移動功能表中的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="1e709-117">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>

5. <span data-ttu-id="1e709-118">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1e709-118">Click **OK**.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="1e709-119">使用鍵盤移動功能表中的功能表項目</span><span class="sxs-lookup"><span data-stu-id="1e709-119">To move a menu item within a menu using the keyboard</span></span>

1. <span data-ttu-id="1e709-120">按住 ALT 鍵。</span><span class="sxs-lookup"><span data-stu-id="1e709-120">Press and hold down the ALT key.</span></span>

2. <span data-ttu-id="1e709-121">在您要移動的功能表項目上, 按一下並按住滑鼠左鍵。</span><span class="sxs-lookup"><span data-stu-id="1e709-121">Click and hold the left mouse button on the menu item that you want to move.</span></span>

3. <span data-ttu-id="1e709-122">將功能表項目拖曳至新位置, 然後放開滑鼠左鍵。</span><span class="sxs-lookup"><span data-stu-id="1e709-122">Drag the menu item to the new location and release the left mouse button.</span></span>

## <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="1e709-123">將功能表項目移至另一個功能表</span><span class="sxs-lookup"><span data-stu-id="1e709-123">To move a menu item to another menu</span></span>

1. <span data-ttu-id="1e709-124">以滑鼠左鍵按一下您想要移動的功能表項目, 然後按 CTRL + X, 或以滑鼠右鍵按一下功能表項目, 然後從快捷方式功能表選擇 [**剪**下]。</span><span class="sxs-lookup"><span data-stu-id="1e709-124">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="1e709-125">以滑鼠左鍵按一下將包含您剪下之功能表項目的功能表。</span><span class="sxs-lookup"><span data-stu-id="1e709-125">Left-click the menu that will contain the menu item that you cut.</span></span>

3. <span data-ttu-id="1e709-126">以滑鼠左鍵按一下預定新位置之前的功能表項目, 然後按 CTRL + V, 或以滑鼠右鍵按一下預定新位置之前的功能表項目, 然後從快捷方式功能表選取 [**貼**上]。</span><span class="sxs-lookup"><span data-stu-id="1e709-126">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="1e709-127">您剪下的功能表項目會插入選取的功能表項目之後。</span><span class="sxs-lookup"><span data-stu-id="1e709-127">The menu item that you cut is inserted after the selected menu item.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e709-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e709-128">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="1e709-129">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1e709-129">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
