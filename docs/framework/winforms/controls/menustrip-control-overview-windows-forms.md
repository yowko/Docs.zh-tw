---
title: MenuStrip 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: 46a3a25415db77ee261f5fb1c3bf114b2275a2d4
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733451"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="7048a-102">MenuStrip 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="7048a-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="7048a-103">功能表會保存以通用主題分組的命令, 以向您的使用者公開功能。</span><span class="sxs-lookup"><span data-stu-id="7048a-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="7048a-104">此<xref:System.Windows.Forms.MenuStrip>控制項是在 .NET Framework 2.0 版中引進。</span><span class="sxs-lookup"><span data-stu-id="7048a-104">The <xref:System.Windows.Forms.MenuStrip> control was introduced in version 2.0 of the .NET Framework.</span></span> <span data-ttu-id="7048a-105">有了<xref:System.Windows.Forms.MenuStrip>這個控制項, 您就可以輕鬆地建立功能表, 就像在 Microsoft Office 中找到的一樣。</span><span class="sxs-lookup"><span data-stu-id="7048a-105">With the <xref:System.Windows.Forms.MenuStrip> control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="7048a-106"><xref:System.Windows.Forms.MenuStrip>控制項支援多重文件介面 (MDI) 和功能表合併、工具提示和溢位。</span><span class="sxs-lookup"><span data-stu-id="7048a-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="7048a-107">您可以藉由新增存取金鑰、快速鍵、核取記號、影像和分隔線, 來增強功能表的可用性和可讀性。</span><span class="sxs-lookup"><span data-stu-id="7048a-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="7048a-108">控制項會取代並將功能<xref:System.Windows.Forms.MainMenu>加入<xref:System.Windows.Forms.MainMenu>控制項, 不過, 如果您選擇, 則會保留控制項以提供回溯相容性及未來使用。 <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="7048a-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="7048a-109">使用 MenuStrip 控制項的方式</span><span class="sxs-lookup"><span data-stu-id="7048a-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="7048a-110"><xref:System.Windows.Forms.MenuStrip>使用控制項來執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="7048a-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
- <span data-ttu-id="7048a-111">建立可輕鬆自訂且常用的功能表, 其支援先進的使用者介面和版面配置功能, 例如文字和影像順序和對齊、拖放作業、MDI、溢位和存取功能表命令的替代模式。</span><span class="sxs-lookup"><span data-stu-id="7048a-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
- <span data-ttu-id="7048a-112">支援作業系統的一般外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="7048a-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
- <span data-ttu-id="7048a-113">針對所有容器和包含的專案, 以一致的方式處理事件, 與處理其他控制項的事件相同。</span><span class="sxs-lookup"><span data-stu-id="7048a-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="7048a-114">下表顯示和相關類別的<xref:System.Windows.Forms.MenuStrip>一些特別重要屬性。</span><span class="sxs-lookup"><span data-stu-id="7048a-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="7048a-115">屬性</span><span class="sxs-lookup"><span data-stu-id="7048a-115">Property</span></span>|<span data-ttu-id="7048a-116">描述</span><span class="sxs-lookup"><span data-stu-id="7048a-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="7048a-117">取得或設定<xref:System.Windows.Forms.ToolStripMenuItem> , 用來顯示 MDI 子表單的清單。</span><span class="sxs-lookup"><span data-stu-id="7048a-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="7048a-118">取得或設定子功能表在 MDI 應用程式中與父功能表合併的方式。</span><span class="sxs-lookup"><span data-stu-id="7048a-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="7048a-119">取得或設定在 MDI 應用程式的功能表中, 合併專案的位置。</span><span class="sxs-lookup"><span data-stu-id="7048a-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="7048a-120">取得或設定值, 指出表單是否為 MDI 子表單的容器。</span><span class="sxs-lookup"><span data-stu-id="7048a-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="7048a-121">取得或設定值, 指出是否會顯示的<xref:System.Windows.Forms.MenuStrip>工具提示。</span><span class="sxs-lookup"><span data-stu-id="7048a-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="7048a-122">取得或設定值，表示 <xref:System.Windows.Forms.MenuStrip> 是否支援溢位功能。</span><span class="sxs-lookup"><span data-stu-id="7048a-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="7048a-123">取得或設定與<xref:System.Windows.Forms.ToolStripMenuItem>相關聯的快速鍵。</span><span class="sxs-lookup"><span data-stu-id="7048a-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="7048a-124">取得或設定值, 表示與<xref:System.Windows.Forms.ToolStripMenuItem>相關聯的快速鍵是否會顯示在旁邊。 <xref:System.Windows.Forms.ToolStripMenuItem></span><span class="sxs-lookup"><span data-stu-id="7048a-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="7048a-125">下表顯示重要<xref:System.Windows.Forms.MenuStrip>的伴隨類別。</span><span class="sxs-lookup"><span data-stu-id="7048a-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="7048a-126">類別</span><span class="sxs-lookup"><span data-stu-id="7048a-126">Class</span></span>|<span data-ttu-id="7048a-127">描述</span><span class="sxs-lookup"><span data-stu-id="7048a-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="7048a-128">表示顯示在<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ContextMenuStrip>上的可選取選項。</span><span class="sxs-lookup"><span data-stu-id="7048a-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="7048a-129">代表捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="7048a-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="7048a-130">表示可讓使用者從清單中選取單一專案的控制項, 當使用者按一下<xref:System.Windows.Forms.ToolStripDropDownButton>或更高層級的功能表項目時, 就會顯示此清單。</span><span class="sxs-lookup"><span data-stu-id="7048a-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="7048a-131">提供在按一下時, 衍生自<xref:System.Windows.Forms.ToolStripItem>該顯示下拉式專案之控制項的基本功能。</span><span class="sxs-lookup"><span data-stu-id="7048a-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7048a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7048a-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
