---
title: ContextMenu 元件概觀
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746194"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="69670-102">ContextMenu 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="69670-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="69670-103">雖然 <xref:System.Windows.Forms.MenuStrip> 和 <xref:System.Windows.Forms.ContextMenuStrip> 將功能取代並加入舊版的 <xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 控制項，但如果您選擇，<xref:System.Windows.Forms.MainMenu> 和 <xref:System.Windows.Forms.ContextMenu> 會保留供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="69670-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="69670-104">有了 Windows Forms <xref:System.Windows.Forms.ContextMenu> 元件，您可以為使用者提供與所選物件相關聯之常用命令的輕鬆存取快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="69670-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="69670-105">快捷方式功能表中的專案通常是主功能表中出現在應用程式其他位置之專案的子集。</span><span class="sxs-lookup"><span data-stu-id="69670-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="69670-106">使用者通常可以存取快捷方式功能表，方法是以滑鼠右鍵按一下滑鼠。</span><span class="sxs-lookup"><span data-stu-id="69670-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="69670-107">在 Windows Forms 上，快捷方式功能表會與控制項相關聯。</span><span class="sxs-lookup"><span data-stu-id="69670-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="69670-108">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="69670-108">Key Properties</span></span>  
 <span data-ttu-id="69670-109">您可以藉由將控制項的 [<xref:System.Windows.Forms.Control.ContextMenu%2A>] 屬性設定為 [<xref:System.Windows.Forms.ContextMenu>] 元件，將快捷方式功能表與控制項產生關聯。</span><span class="sxs-lookup"><span data-stu-id="69670-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="69670-110">單一快捷方式功能表可以與多個控制項建立關聯，但每個控制項只能有一個快捷方式功能表。</span><span class="sxs-lookup"><span data-stu-id="69670-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="69670-111"><xref:System.Windows.Forms.ContextMenu> 元件的索引鍵屬性是 <xref:System.Windows.Forms.Menu.MenuItems%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="69670-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="69670-112">您可以新增功能表項目，方法是以程式設計方式建立 <xref:System.Windows.Forms.MenuItem> 物件，並將它們加入快捷方式功能表的 [<xref:System.Windows.Forms.Menu.MenuItemCollection>]。</span><span class="sxs-lookup"><span data-stu-id="69670-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="69670-113">因為快捷方式功能表中的專案通常是從其他功能表繪製，所以您最常將專案複製到快捷方式功能表中。</span><span class="sxs-lookup"><span data-stu-id="69670-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69670-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69670-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
