---
title: ContextMenu 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956048"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="523f6-102">ContextMenu 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="523f6-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="523f6-103">雖然<xref:System.Windows.Forms.MenuStrip>並<xref:System.Windows.Forms.ContextMenuStrip>取代及新增功能<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>控制項的舊版本中，<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>會保留回溯相容性以及供未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="523f6-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="523f6-104">使用 Windows Form<xref:System.Windows.Forms.ContextMenu>元件，您可以提供使用者更容易存取的快顯功能表與所選物件相關聯的常用命令。</span><span class="sxs-lookup"><span data-stu-id="523f6-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="523f6-105">快顯功能表中的項目通常是從主應用程式中其他地方出現的功能表項目的子集。</span><span class="sxs-lookup"><span data-stu-id="523f6-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="523f6-106">使用者可以按一下滑鼠右鍵，通常存取捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="523f6-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="523f6-107">在 Windows Forms 上快顯功能表會與控制項相關聯。</span><span class="sxs-lookup"><span data-stu-id="523f6-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="523f6-108">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="523f6-108">Key Properties</span></span>  
 <span data-ttu-id="523f6-109">您可以與控制項關聯的捷徑功能表，設定控制項的<xref:System.Windows.Forms.Control.ContextMenu%2A>屬性設<xref:System.Windows.Forms.ContextMenu>元件。</span><span class="sxs-lookup"><span data-stu-id="523f6-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="523f6-110">單一的捷徑功能表可以與多個控制項，相關聯，但每個控制項都可以有只有一個快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="523f6-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="523f6-111">索引鍵內容<xref:System.Windows.Forms.ContextMenu>元件是<xref:System.Windows.Forms.Menu.MenuItems%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="523f6-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="523f6-112">您可以新增功能表項目以程式設計方式建立<xref:System.Windows.Forms.MenuItem>物件，並將它們加入至<xref:System.Windows.Forms.Menu.MenuItemCollection>的快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="523f6-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="523f6-113">快顯功能表中的項目通常取自其他功能表中，因為您將複製它們，以最常加入至捷徑功能表項目。</span><span class="sxs-lookup"><span data-stu-id="523f6-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523f6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="523f6-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
