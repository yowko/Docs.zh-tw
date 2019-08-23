---
title: MainMenu 元件概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: fe46683faee13bad951d5a7185aad8a687c290ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952140"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="7a898-102">MainMenu 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="7a898-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="7a898-103">雖然<xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenu>會取代並將功能加入舊版的和控制項, 但<xref:System.Windows.Forms.MainMenu>如果您選擇, 則會保留以供回溯相容性和未來使用。 <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="7a898-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="7a898-104">Windows Forms <xref:System.Windows.Forms.MainMenu>元件會在執行時間顯示功能表。</span><span class="sxs-lookup"><span data-stu-id="7a898-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="7a898-105">主功能表和個別專案的所有子功能表都<xref:System.Windows.Forms.MenuItem>是物件。</span><span class="sxs-lookup"><span data-stu-id="7a898-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="7a898-106">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="7a898-106">Key Properties</span></span>  
 <span data-ttu-id="7a898-107">藉由將<xref:System.Windows.Forms.MenuItem.DefaultItem%2A>屬性設定為`true`, 可以將功能表項目指定為預設專案。</span><span class="sxs-lookup"><span data-stu-id="7a898-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="7a898-108">按一下功能表時, 預設專案會以粗體文字顯示。</span><span class="sxs-lookup"><span data-stu-id="7a898-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="7a898-109">功能表項目的<xref:System.Windows.Forms.MenuItem.Checked%2A>屬性`true`為或`false`, 表示是否已選取功能表項目。</span><span class="sxs-lookup"><span data-stu-id="7a898-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="7a898-110">功能表項目<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>的屬性可自訂所選項目的外觀: 如果<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>設定為`true`, 則選項按鈕會出現在專案的旁邊; 如果<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>設為`false`, 則會在專案旁邊出現核取記號。</span><span class="sxs-lookup"><span data-stu-id="7a898-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a898-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a898-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="7a898-112">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="7a898-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
