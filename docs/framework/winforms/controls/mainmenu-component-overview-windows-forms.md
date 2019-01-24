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
ms.openlocfilehash: 529b57ed443791b87331358a7e6c420dd63933a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700620"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="e12fd-102">MainMenu 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="e12fd-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="e12fd-103">雖然<xref:System.Windows.Forms.MenuStrip>並<xref:System.Windows.Forms.ContextMenuStrip>取代及新增功能<xref:System.Windows.Forms.MainMenu>並<xref:System.Windows.Forms.ContextMenu>控制項的舊版本中，<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>會保留回溯相容性以及供未來使用，如果您選擇。</span><span class="sxs-lookup"><span data-stu-id="e12fd-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="e12fd-104">Windows Form<xref:System.Windows.Forms.MainMenu>元件會在執行階段顯示功能表。</span><span class="sxs-lookup"><span data-stu-id="e12fd-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="e12fd-105">所有的個別項目與主功能表的子功能表卻<xref:System.Windows.Forms.MenuItem>物件。</span><span class="sxs-lookup"><span data-stu-id="e12fd-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="e12fd-106">索引鍵內容</span><span class="sxs-lookup"><span data-stu-id="e12fd-106">Key Properties</span></span>  
 <span data-ttu-id="e12fd-107">功能表項目可以指定為預設的項目，藉由設定<xref:System.Windows.Forms.MenuItem.DefaultItem%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="e12fd-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="e12fd-108">按一下 [] 功能表時以粗體文字顯示預設項目。</span><span class="sxs-lookup"><span data-stu-id="e12fd-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="e12fd-109">功能表項目的<xref:System.Windows.Forms.MenuItem.Checked%2A>屬性是`true`或`false`，並指出是否已選取功能表項目。</span><span class="sxs-lookup"><span data-stu-id="e12fd-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="e12fd-110">功能表項目的<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>屬性自訂所選取項目的外觀： 如果<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>設為`true`，選項按鈕旁邊的項目; 如果<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>設定為`false`，項目旁的核取記號隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e12fd-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12fd-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e12fd-111">See also</span></span>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="e12fd-112">MenuStrip 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="e12fd-112">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
