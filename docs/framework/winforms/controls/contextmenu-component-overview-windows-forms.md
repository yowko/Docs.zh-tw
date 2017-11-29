---
title: "ContextMenu 元件概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6c2542ca7ee27bec96bb5010bcdb2fcd7416f72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="dfc4e-102">ContextMenu 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="dfc4e-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="dfc4e-103">雖然<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>取代，並將功能加入至<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>的舊版中，控制項<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>您選擇保留的回溯相容性及供未來使用。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="dfc4e-104">使用 Windows Form<xref:System.Windows.Forms.ContextMenu>元件，您可以提供使用者更容易存取的快顯功能表與選取的物件相關聯的常用命令。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="dfc4e-105">快顯功能表中的項目通常是從主應用程式中其他位置出現的功能表項目的子集。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="dfc4e-106">使用者通常可以存取捷徑功能表上按一下滑鼠右鍵。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="dfc4e-107">在 Windows Form 上快顯功能表與相關聯的控制項。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="dfc4e-108">索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="dfc4e-108">Key Properties</span></span>  
 <span data-ttu-id="dfc4e-109">您可以藉由設定控制項的捷徑功能表建立關聯的控制項一起<xref:System.Windows.Forms.Control.ContextMenu%2A>屬性<xref:System.Windows.Forms.ContextMenu>元件。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="dfc4e-110">單一的捷徑功能表可以是多個控制項，與相關聯，但每個控制項都可以有只有一個快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="dfc4e-111">索引鍵內容<xref:System.Windows.Forms.ContextMenu>元件是<xref:System.Windows.Forms.Menu.MenuItems%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="dfc4e-112">您可以加入功能表項目以程式設計方式建立<xref:System.Windows.Forms.MenuItem>物件並將它們加入至<xref:System.Windows.Forms.Menu.MenuItemCollection>的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="dfc4e-113">快顯功能表中的項目通常取自其他功能表，因為您會將它們複製，快顯功能表中最常加入項目。</span><span class="sxs-lookup"><span data-stu-id="dfc4e-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc4e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfc4e-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
