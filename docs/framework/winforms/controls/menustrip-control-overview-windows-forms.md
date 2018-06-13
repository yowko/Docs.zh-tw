---
title: MenuStrip 控制項概觀 (Windows Form)
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: b09d653210c72a38bbc4dc0858ae2553ad9cbeef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537482"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="a4ce4-102">MenuStrip 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="a4ce4-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="a4ce4-103">功能表會公開給您的使用者功能，藉由在一般情況下分組的命令。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="a4ce4-104"><xref:System.Windows.Forms.MenuStrip>控制項是此版本的 Visual Studio 和.NET Framework 的新功能。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-104">The <xref:System.Windows.Forms.MenuStrip> control is new to this version of Visual Studio and the .NET Framework.</span></span> <span data-ttu-id="a4ce4-105">與控制項，您可以輕鬆建立類似 Microsoft Office 中的功能表。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-105">With the control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="a4ce4-106"><xref:System.Windows.Forms.MenuStrip>控制項支援多重文件介面 (MDI) 和功能表合併、 工具提示和溢位。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="a4ce4-107">您可以加入便捷鍵、 快速鍵、 核取記號、 影像和分隔線來增強可用性和功能表的可讀性。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="a4ce4-108"><xref:System.Windows.Forms.MenuStrip>控制項取代，並將功能加入<xref:System.Windows.Forms.MainMenu>控制項等控制項，不過，<xref:System.Windows.Forms.MainMenu>如果您選擇，將會保留以提供回溯相容性及未來使用的控制項。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="a4ce4-109">MenuStrip 控制項的使用方式</span><span class="sxs-lookup"><span data-stu-id="a4ce4-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="a4ce4-110">使用<xref:System.Windows.Forms.MenuStrip>控制權傳輸至：</span><span class="sxs-lookup"><span data-stu-id="a4ce4-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
-   <span data-ttu-id="a4ce4-111">建立易於自訂，常採用的功能表支援的進階使用者介面及版面配置功能，例如文字和影像的排序和對齊方式、 拖放作業、 MDI、 溢位，以及存取功能表命令的替代模式。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
-   <span data-ttu-id="a4ce4-112">支援的典型的外觀和行為的作業系統。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
-   <span data-ttu-id="a4ce4-113">處理事件的所有容器和包含的項目，以一致的方式，您可以在相同的方式處理其他控制項的事件。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="a4ce4-114">下表顯示一些特別重要的屬性<xref:System.Windows.Forms.MenuStrip>和相關聯的類別。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="a4ce4-115">屬性</span><span class="sxs-lookup"><span data-stu-id="a4ce4-115">Property</span></span>|<span data-ttu-id="a4ce4-116">描述</span><span class="sxs-lookup"><span data-stu-id="a4ce4-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="a4ce4-117">取得或設定<xref:System.Windows.Forms.ToolStripMenuItem>用來顯示 MDI 子表單的清單。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="a4ce4-118">取得或設定子功能表要如何與 MDI 應用程式中的父功能表合併。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="a4ce4-119">取得或設定 MDI 應用程式中的合併功能表中項目的位置。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="a4ce4-120">取得或設定值，指出表單是否為 MDI 子表單的容器。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="a4ce4-121">取得或設定值，指出是否顯示工具提示<xref:System.Windows.Forms.MenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="a4ce4-122">取得或設定值，表示 <xref:System.Windows.Forms.MenuStrip> 是否支援溢位功能。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="a4ce4-123">取得或設定與相關聯的快速鍵<xref:System.Windows.Forms.ToolStripMenuItem>。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="a4ce4-124">取得或設定值，指出是否快速鍵的相關聯<xref:System.Windows.Forms.ToolStripMenuItem>旁會顯示<xref:System.Windows.Forms.ToolStripMenuItem>。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="a4ce4-125">下表顯示重要<xref:System.Windows.Forms.MenuStrip>附屬類別。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="a4ce4-126">類別</span><span class="sxs-lookup"><span data-stu-id="a4ce4-126">Class</span></span>|<span data-ttu-id="a4ce4-127">描述</span><span class="sxs-lookup"><span data-stu-id="a4ce4-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="a4ce4-128">表示可選取選項，顯示在<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ContextMenuStrip>。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="a4ce4-129">代表捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="a4ce4-130">代表控制項，可讓使用者從顯示當使用者按一下清單中選取單一項目<xref:System.Windows.Forms.ToolStripDropDownButton>或更高層級的功能表項目。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="a4ce4-131">提供基本功能的控制項衍生自<xref:System.Windows.Forms.ToolStripItem>顯示時按下的下拉式清單項目。</span><span class="sxs-lookup"><span data-stu-id="a4ce4-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4ce4-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4ce4-132">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
