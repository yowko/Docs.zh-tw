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
ms.openlocfilehash: e4a6add5297ba7db606ca1891e9279141f8d6d20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962163"
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="728f2-102">ContextMenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="728f2-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
> <span data-ttu-id="728f2-103">控制項會取代並將功能<xref:System.Windows.Forms.ContextMenu>加入<xref:System.Windows.Forms.ContextMenu>控制項, 不過, 如果您選擇, 則會保留控制項以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="728f2-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="728f2-104">快捷方式功能表 (也稱為內容功能表) 會在使用者按一下滑鼠右鍵時出現在滑鼠位置。</span><span class="sxs-lookup"><span data-stu-id="728f2-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="728f2-105">快捷方式*功能表*會在滑鼠指標位置提供工作區或控制項的選項。</span><span class="sxs-lookup"><span data-stu-id="728f2-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="728f2-106">控制項<xref:System.Windows.Forms.ContextMenuStrip>的設計目的是要與新<xref:System.Windows.Forms.ToolStrip>的和相關的控制項順暢地搭配使用, <xref:System.Windows.Forms.ContextMenuStrip>但是您可以輕鬆地將與其他控制項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="728f2-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="728f2-107">下表顯示重要<xref:System.Windows.Forms.ContextMenuStrip>的伴隨類別。</span><span class="sxs-lookup"><span data-stu-id="728f2-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="728f2-108">類別</span><span class="sxs-lookup"><span data-stu-id="728f2-108">Class</span></span>|<span data-ttu-id="728f2-109">描述</span><span class="sxs-lookup"><span data-stu-id="728f2-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="728f2-110">表示顯示在<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ContextMenuStrip>上的可選取選項。</span><span class="sxs-lookup"><span data-stu-id="728f2-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="728f2-111">表示可讓使用者從清單中選取單一專案的控制項, 當使用者按一下<xref:System.Windows.Forms.ToolStripDropDownButton>或更高層級的功能表項目時, 就會顯示此清單。</span><span class="sxs-lookup"><span data-stu-id="728f2-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="728f2-112">提供在按一下時, 衍生自<xref:System.Windows.Forms.ToolStripItem>該顯示下拉式專案之控制項的基本功能。</span><span class="sxs-lookup"><span data-stu-id="728f2-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="728f2-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="728f2-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
