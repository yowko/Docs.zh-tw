---
title: "ContextMenuStrip 控制項概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ContextMenuStrip
helpviewer_keywords:
- context menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- shortcut menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- ContextMenuStrip control [Windows Forms], about ContextMenuStrip control
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 11d5de760b8a03d7bc35adabb631048a70e20264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="dc18d-102">ContextMenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="dc18d-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="dc18d-103"><xref:System.Windows.Forms.ContextMenuStrip>控制項取代，並將功能加入<xref:System.Windows.Forms.ContextMenu>控制項等控制項，不過，<xref:System.Windows.Forms.ContextMenu>如果您選擇，將會保留以提供回溯相容性及未來使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="dc18d-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="dc18d-104">當使用者按一下滑鼠右鍵在滑鼠位置會出現快顯功能表，也稱為操作功能表。</span><span class="sxs-lookup"><span data-stu-id="dc18d-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="dc18d-105">快顯*功能表*選項提供的工作區或滑鼠指標位置的控制項。</span><span class="sxs-lookup"><span data-stu-id="dc18d-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="dc18d-106"><xref:System.Windows.Forms.ContextMenuStrip>控制項用來與新能完美合作<xref:System.Windows.Forms.ToolStrip>和相關的控制項，但您可以將產生關聯<xref:System.Windows.Forms.ContextMenuStrip>以輕鬆地為其他控制項。</span><span class="sxs-lookup"><span data-stu-id="dc18d-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="dc18d-107">下表顯示重要<xref:System.Windows.Forms.ContextMenuStrip>附屬類別。</span><span class="sxs-lookup"><span data-stu-id="dc18d-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="dc18d-108">類別</span><span class="sxs-lookup"><span data-stu-id="dc18d-108">Class</span></span>|<span data-ttu-id="dc18d-109">描述</span><span class="sxs-lookup"><span data-stu-id="dc18d-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="dc18d-110">表示可選取選項，顯示在<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="dc18d-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="dc18d-111">代表可讓使用者選取單一項目從清單中會顯示當使用者按一下控制項<xref:System.Windows.Forms.ToolStripDropDownButton>或更高層級的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="dc18d-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="dc18d-112">提供基本功能的控制項衍生自<xref:System.Windows.Forms.ToolStripItem>顯示時按下的下拉式清單項目。</span><span class="sxs-lookup"><span data-stu-id="dc18d-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc18d-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="dc18d-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
