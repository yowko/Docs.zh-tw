---
title: ContextMenuStrip 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- ContextMenuStrip
helpviewer_keywords:
- context menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- shortcut menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- ContextMenuStrip control [Windows Forms], about ContextMenuStrip control
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
ms.openlocfilehash: f26fcf259e9c56ffe17c7d7f5a80428ffbbb27c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712453"
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="6301e-102">ContextMenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="6301e-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="6301e-103"><xref:System.Windows.Forms.ContextMenuStrip>會取代並將功能加入至<xref:System.Windows.Forms.ContextMenu>控制; 不過，<xref:System.Windows.Forms.ContextMenu>如果您選擇，將會保留回溯相容性以及供未來使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="6301e-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="6301e-104">當使用者按一下滑鼠右鍵捷徑功能表，也稱為操作功能表，就會出現在滑鼠位置。</span><span class="sxs-lookup"><span data-stu-id="6301e-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="6301e-105">快顯*功能表*提供工作區，還是在滑鼠指標位置的控制項的選項。</span><span class="sxs-lookup"><span data-stu-id="6301e-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="6301e-106"><xref:System.Windows.Forms.ContextMenuStrip>控制項用來與新完美配合運作<xref:System.Windows.Forms.ToolStrip>和相關的控制項，但是您可以建立關聯<xref:System.Windows.Forms.ContextMenuStrip>與輕鬆地為其他控制項。</span><span class="sxs-lookup"><span data-stu-id="6301e-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="6301e-107">下表顯示重要<xref:System.Windows.Forms.ContextMenuStrip>附屬類別。</span><span class="sxs-lookup"><span data-stu-id="6301e-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="6301e-108">類別</span><span class="sxs-lookup"><span data-stu-id="6301e-108">Class</span></span>|<span data-ttu-id="6301e-109">描述</span><span class="sxs-lookup"><span data-stu-id="6301e-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="6301e-110">表示可選取的選項，顯示在<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="6301e-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="6301e-111">代表可讓使用者選取單一項目從清單中會顯示當使用者按一下控制項<xref:System.Windows.Forms.ToolStripDropDownButton>或更高層級的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="6301e-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="6301e-112">提供基本功能，控制項衍生自<xref:System.Windows.Forms.ToolStripItem>顯示時按下的下拉式清單項目。</span><span class="sxs-lookup"><span data-stu-id="6301e-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6301e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6301e-113">See also</span></span>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
