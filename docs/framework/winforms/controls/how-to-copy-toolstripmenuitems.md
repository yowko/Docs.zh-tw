---
title: "如何：複製 ToolStripMenuItems"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77f48d7af76cc65092e9045ab76654c96a1a7c02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="55bc6-102">如何：複製 ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="55bc6-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="55bc6-103">在設計階段，您可以將整個最上層功能表及其子功能表項目複製到 <xref:System.Windows.Forms.MenuStrip>上的不同位置。</span><span class="sxs-lookup"><span data-stu-id="55bc6-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="55bc6-104">您也可以在最上層功能表之間複製個別功能表項目，或變更功能表內功能表項目的位置。</span><span class="sxs-lookup"><span data-stu-id="55bc6-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="55bc6-105">將最上層功能表及其子功能表項目複製到另一個最上層位置</span><span class="sxs-lookup"><span data-stu-id="55bc6-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="55bc6-106">以滑鼠左鍵按一下您要複製的功能表，然後按 CTRL+C，或以滑鼠右鍵按一下功能表，然後從捷徑功能表選取 [複製]  。</span><span class="sxs-lookup"><span data-stu-id="55bc6-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="55bc6-107">以滑鼠左鍵按一下預定新位置之後的最上層功能表，然後按 CTRL+V，或以滑鼠右鍵按一下預定新位置之前的最上層功能表項目，然後從捷徑功能表選取 [貼上]  。</span><span class="sxs-lookup"><span data-stu-id="55bc6-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="55bc6-108">您所複製的功能表會在選取的最上層功能表之前插入。</span><span class="sxs-lookup"><span data-stu-id="55bc6-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="55bc6-109">將最上層功能表及其子功能表項目複製到下拉式清單位置</span><span class="sxs-lookup"><span data-stu-id="55bc6-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="55bc6-110">以滑鼠左鍵按一下您要移動的功能表，然後按 CTRL+C，或以滑鼠右鍵按一下功能表，然後從捷徑功能表選取 [複製]  。</span><span class="sxs-lookup"><span data-stu-id="55bc6-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="55bc6-111">在目的地最上層功能表中，以滑鼠左鍵按一下預定新位置上方的的子功能表項目，然後按 CTRL+V，或以滑鼠右鍵按一下預定新位置上方的的子功能表項目，然後從捷徑功能表選取 [貼上]  。</span><span class="sxs-lookup"><span data-stu-id="55bc6-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="55bc6-112">您所複製的功能表會在選取的子功能表項目之前插入。</span><span class="sxs-lookup"><span data-stu-id="55bc6-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="55bc6-113">將子功能表項目複製到另一個功能表</span><span class="sxs-lookup"><span data-stu-id="55bc6-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="55bc6-114">以滑鼠左鍵按一下您要複製的子功能表項目，然後按 CTRL+C，或以滑鼠右鍵按一下子功能表項目，然後從捷徑功能表選擇 [複製]  。</span><span class="sxs-lookup"><span data-stu-id="55bc6-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="55bc6-115">以滑鼠左鍵按一下包含您剪下之子功能表項目的功能表。</span><span class="sxs-lookup"><span data-stu-id="55bc6-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="55bc6-116">以滑鼠左鍵按一下預定新位置之前的子功能表項目，然後按 CTRL+V，或以滑鼠右鍵按一下預定新位置之前的子功能表項目，然後從捷徑功能表選取 [貼上]  。</span><span class="sxs-lookup"><span data-stu-id="55bc6-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="55bc6-117">您所複製的子功能表項目會在選取的子功能表項目之前插入。</span><span class="sxs-lookup"><span data-stu-id="55bc6-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55bc6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55bc6-118">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="55bc6-119">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="55bc6-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
