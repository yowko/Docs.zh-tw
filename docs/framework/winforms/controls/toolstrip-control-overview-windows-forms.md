---
title: "ToolStrip 控制項概觀 (Windows Form)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15e24e0350071fabd32342402abdf497937ee90d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="toolstrip-control-overview-windows-forms"></a><span data-ttu-id="73acb-102">ToolStrip 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="73acb-102">ToolStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="73acb-103">Windows Form<xref:System.Windows.Forms.ToolStrip>控制項以及與其相關聯的類別提供一般架構合併工具列、 狀態列和功能表的使用者介面項目。</span><span class="sxs-lookup"><span data-stu-id="73acb-103">The Windows Forms <xref:System.Windows.Forms.ToolStrip> control and its associated classes provide a common framework for combining user interface elements into toolbars, status bars, and menus.</span></span> <span data-ttu-id="73acb-104"><xref:System.Windows.Forms.ToolStrip>控制項提供豐富的設計階段經驗，包括在就地啟用和編輯、 自訂配置] 和 [浮動定位，這是工具列共用水平或垂直空間的能力。</span><span class="sxs-lookup"><span data-stu-id="73acb-104"><xref:System.Windows.Forms.ToolStrip> controls offer a rich design-time experience that includes in-place activation and editing, custom layout, and rafting, which is the ability of toolbars to share horizontal or vertical space.</span></span>  
  
 <span data-ttu-id="73acb-105">雖然<xref:System.Windows.Forms.ToolStrip>取代，並將功能加入至較舊的版本中的控制項<xref:System.Windows.Forms.ToolBar>如果想要保留以提供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="73acb-105">Although <xref:System.Windows.Forms.ToolStrip> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
## <a name="features-of-the-toolstrip-controls"></a><span data-ttu-id="73acb-106">ToolStrip 控制項的功能</span><span class="sxs-lookup"><span data-stu-id="73acb-106">Features of the ToolStrip Controls</span></span>  
 <span data-ttu-id="73acb-107">使用<xref:System.Windows.Forms.ToolStrip>控制權傳輸至：</span><span class="sxs-lookup"><span data-stu-id="73acb-107">Use the <xref:System.Windows.Forms.ToolStrip> control to:</span></span>  
  
-   <span data-ttu-id="73acb-108">在容器存在通用使用者介面。</span><span class="sxs-lookup"><span data-stu-id="73acb-108">Present a common user interface across containers.</span></span>  
  
-   <span data-ttu-id="73acb-109">建立易於自訂，常採用支援的工具列進階使用者介面和版面配置功能，例如文字和影像、 下拉式按鈕和控制項的停駐、 浮動定位，按鈕，溢位按鈕和執行階段時重新排列<xref:System.Windows.Forms.ToolStrip>項目。</span><span class="sxs-lookup"><span data-stu-id="73acb-109">Create easily customized, commonly employed toolbars that support advanced user interface and layout features, such as docking, rafting, buttons with text and images, drop-down buttons and controls, overflow buttons, and run-time reordering of <xref:System.Windows.Forms.ToolStrip> items.</span></span>  
  
-   <span data-ttu-id="73acb-110">支援溢位和執行階段項目重新排列。</span><span class="sxs-lookup"><span data-stu-id="73acb-110">Support overflow and run-time item reordering.</span></span> <span data-ttu-id="73acb-111">溢位功能會移至下拉功能表項目時的空間不足以它們顯示在<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="73acb-111">The overflow feature moves items to a drop-down menu when there is not enough room to display them in a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
-   <span data-ttu-id="73acb-112">支援的典型的外觀和行為的作業系統，透過常見的轉譯模型。</span><span class="sxs-lookup"><span data-stu-id="73acb-112">Support the typical appearance and behavior of the operating system through a common rendering model.</span></span>  
  
-   <span data-ttu-id="73acb-113">處理事件的所有容器和包含的項目，以一致的方式，您可以在相同的方式處理其他控制項的事件。</span><span class="sxs-lookup"><span data-stu-id="73acb-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
-   <span data-ttu-id="73acb-114">拖曳項目從某個<xref:System.Windows.Forms.ToolStrip>之間或<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="73acb-114">Drag items from one <xref:System.Windows.Forms.ToolStrip> to another or within a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
-   <span data-ttu-id="73acb-115">建立下拉式清單控制項和使用者介面的型別編輯器進階的配置的<xref:System.Windows.Forms.ToolStripDropDown>。</span><span class="sxs-lookup"><span data-stu-id="73acb-115">Create drop-down controls and user interface type editors with advanced layouts in a <xref:System.Windows.Forms.ToolStripDropDown>.</span></span>  
  
 <span data-ttu-id="73acb-116">使用<xref:System.Windows.Forms.ToolStripControlHost>類別上使用其他控制項<xref:System.Windows.Forms.ToolStrip>並取得<xref:System.Windows.Forms.ToolStrip>它們的功能。</span><span class="sxs-lookup"><span data-stu-id="73acb-116">Use the <xref:System.Windows.Forms.ToolStripControlHost> class to use other controls on a <xref:System.Windows.Forms.ToolStrip> and gain <xref:System.Windows.Forms.ToolStrip> functionality for them.</span></span>  
  
 <span data-ttu-id="73acb-117">您可以擴充功能，並使用修改的外觀和行為<xref:System.Windows.Forms.ToolStripRenderer>， <xref:System.Windows.Forms.ToolStripProfessionalRenderer>，和<xref:System.Windows.Forms.ToolStripManager>連同<xref:System.Windows.Forms.ToolStripRenderMode>和<xref:System.Windows.Forms.ToolStripManagerRenderMode>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="73acb-117">You can extend the functionality and modify the appearance and behavior by using the <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, and <xref:System.Windows.Forms.ToolStripManager> along with the <xref:System.Windows.Forms.ToolStripRenderMode> and <xref:System.Windows.Forms.ToolStripManagerRenderMode> enumerations.</span></span>  
  
 <span data-ttu-id="73acb-118"><xref:System.Windows.Forms.ToolStrip>控制項高度可設定且可延伸的而且它會提供許多屬性、 方法和事件，以自訂外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="73acb-118">The <xref:System.Windows.Forms.ToolStrip> control is highly configurable and extensible, and it provides many properties, methods, and events to customize appearance and behavior.</span></span> <span data-ttu-id="73acb-119">以下是一些值得注意的成員：</span><span class="sxs-lookup"><span data-stu-id="73acb-119">Below are some noteworthy members:</span></span>  
  
### <a name="important-toolstrip-members"></a><span data-ttu-id="73acb-120">重要的 ToolStrip 成員</span><span class="sxs-lookup"><span data-stu-id="73acb-120">Important ToolStrip Members</span></span>  
  
|<span data-ttu-id="73acb-121">名稱</span><span class="sxs-lookup"><span data-stu-id="73acb-121">Name</span></span>|<span data-ttu-id="73acb-122">說明</span><span class="sxs-lookup"><span data-stu-id="73acb-122">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|<span data-ttu-id="73acb-123">取得或設定父容器的邊緣<xref:System.Windows.Forms.ToolStrip>停駐於。</span><span class="sxs-lookup"><span data-stu-id="73acb-123">Gets or sets which edge of the parent container a <xref:System.Windows.Forms.ToolStrip> is docked to.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|<span data-ttu-id="73acb-124">取得或設定值，表示拖放動作和項目的重新排序是否由 <xref:System.Windows.Forms.ToolStrip> 類別私下處理。</span><span class="sxs-lookup"><span data-stu-id="73acb-124">Gets or sets a value indicating whether drag-and-drop and item reordering are handled privately by the <xref:System.Windows.Forms.ToolStrip> class.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|<span data-ttu-id="73acb-125">取得或設定值，指出如何<xref:System.Windows.Forms.ToolStrip>配置其項目。</span><span class="sxs-lookup"><span data-stu-id="73acb-125">Gets or sets a value indicating how the <xref:System.Windows.Forms.ToolStrip> lays out its items.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|<span data-ttu-id="73acb-126">取得或設定是否<xref:System.Windows.Forms.ToolStripItem>附加至<xref:System.Windows.Forms.ToolStrip>或<xref:System.Windows.Forms.ToolStripOverflowButton>或兩者之間可以浮動。</span><span class="sxs-lookup"><span data-stu-id="73acb-126">Gets or sets whether a <xref:System.Windows.Forms.ToolStripItem> is attached to the <xref:System.Windows.Forms.ToolStrip> or <xref:System.Windows.Forms.ToolStripOverflowButton> or can float between the two.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|<span data-ttu-id="73acb-127">取得值，指出是否<xref:System.Windows.Forms.ToolStripItem>會顯示在下拉式清單中的其他項目清單時<xref:System.Windows.Forms.ToolStripItem>按下。</span><span class="sxs-lookup"><span data-stu-id="73acb-127">Gets a value indicating whether a <xref:System.Windows.Forms.ToolStripItem> displays other items in a drop-down list when the <xref:System.Windows.Forms.ToolStripItem> is clicked.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|<span data-ttu-id="73acb-128">取得 <xref:System.Windows.Forms.ToolStripItem>，它會在啟用溢位時做為 <xref:System.Windows.Forms.ToolStrip> 的溢位按鈕。</span><span class="sxs-lookup"><span data-stu-id="73acb-128">Gets the <xref:System.Windows.Forms.ToolStripItem> that is the overflow button for a <xref:System.Windows.Forms.ToolStrip> with overflow enabled.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|<span data-ttu-id="73acb-129">取得或設定<xref:System.Windows.Forms.ToolStripRenderer>用來自訂外觀和行為 （外觀及操作） <xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="73acb-129">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance and behavior (look and feel) of a <xref:System.Windows.Forms.ToolStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|<span data-ttu-id="73acb-130">取得或設定要套用至的繪製樣式<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="73acb-130">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|<span data-ttu-id="73acb-131">引發的時機<xref:System.Windows.Forms.ToolStrip.Renderer%2A>屬性變更。</span><span class="sxs-lookup"><span data-stu-id="73acb-131">Raised when the <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property changes.</span></span>|  
  
 <span data-ttu-id="73acb-132"><xref:System.Windows.Forms.ToolStrip>控制項的彈性達成附屬類別數目。</span><span class="sxs-lookup"><span data-stu-id="73acb-132">The <xref:System.Windows.Forms.ToolStrip> control's flexibility is achieved through the use of a number of companion classes.</span></span> <span data-ttu-id="73acb-133">以下是一些最值得注意：</span><span class="sxs-lookup"><span data-stu-id="73acb-133">Below are some of the most noteworthy:</span></span>  
  
### <a name="important-toolstrip-companion-classes"></a><span data-ttu-id="73acb-134">重要的 ToolStrip 附屬類別</span><span class="sxs-lookup"><span data-stu-id="73acb-134">Important ToolStrip Companion Classes</span></span>  
  
|<span data-ttu-id="73acb-135">名稱</span><span class="sxs-lookup"><span data-stu-id="73acb-135">Name</span></span>|<span data-ttu-id="73acb-136">說明</span><span class="sxs-lookup"><span data-stu-id="73acb-136">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|<span data-ttu-id="73acb-137">取代，並將功能加入<xref:System.Windows.Forms.MainMenu>類別。</span><span class="sxs-lookup"><span data-stu-id="73acb-137">Replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> class.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip>|<span data-ttu-id="73acb-138">取代，並將功能加入<xref:System.Windows.Forms.StatusBar>類別。</span><span class="sxs-lookup"><span data-stu-id="73acb-138">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> class.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="73acb-139">取代，並將功能加入<xref:System.Windows.Forms.ContextMenu>類別。</span><span class="sxs-lookup"><span data-stu-id="73acb-139">Replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> class.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem>|<span data-ttu-id="73acb-140">抽象基底類別，可管理事件和配置的所有項目， <xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.ToolStripControlHost>，或<xref:System.Windows.Forms.ToolStripDropDown>可以包含。</span><span class="sxs-lookup"><span data-stu-id="73acb-140">Abstract base class that manages events and layout for all the elements that a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, or <xref:System.Windows.Forms.ToolStripDropDown> can contain.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="73acb-141">提供的表單可以以各種方式排列控制項中的每一端上的面板的容器。</span><span class="sxs-lookup"><span data-stu-id="73acb-141">Provides a container with a panel on each side of the form in which controls can be arranged in various ways.</span></span>|  
|<xref:System.Windows.Forms.ToolStripRenderer>|<span data-ttu-id="73acb-142">處理的繪製功能<xref:System.Windows.Forms.ToolStrip>物件。</span><span class="sxs-lookup"><span data-stu-id="73acb-142">Handles the painting functionality for <xref:System.Windows.Forms.ToolStrip> objects.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|<span data-ttu-id="73acb-143">提供 Microsoft Office 樣式外觀。</span><span class="sxs-lookup"><span data-stu-id="73acb-143">Provides Microsoft Office-style appearance.</span></span>|  
|<xref:System.Windows.Forms.ToolStripManager>|<span data-ttu-id="73acb-144">控制項<xref:System.Windows.Forms.ToolStrip>轉譯和浮動定位，及合併<xref:System.Windows.Forms.MenuStrip>， <xref:System.Windows.Forms.ToolStripDropDownMenu>，和<xref:System.Windows.Forms.ToolStripMenuItem>物件。</span><span class="sxs-lookup"><span data-stu-id="73acb-144">Controls <xref:System.Windows.Forms.ToolStrip> rendering and rafting, and the merging of <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, and <xref:System.Windows.Forms.ToolStripMenuItem> objects.</span></span>|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|<span data-ttu-id="73acb-145">指定套用至多個的繪製樣式 （自訂，Windows XP 或 Microsoft Office Professional）<xref:System.Windows.Forms.ToolStrip>表單中所包含的物件。</span><span class="sxs-lookup"><span data-stu-id="73acb-145">Specifies the painting style (custom, Windows XP, or Microsoft Office Professional) applied to multiple <xref:System.Windows.Forms.ToolStrip> objects contained in a form.</span></span>|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|<span data-ttu-id="73acb-146">指定套用至其中的繪製樣式 （自訂，Windows XP 或 Microsoft Office Professional）<xref:System.Windows.Forms.ToolStrip>表單中所包含的物件。</span><span class="sxs-lookup"><span data-stu-id="73acb-146">Specifies the painting style (custom, Windows XP, or Microsoft Office Professional) applied to one <xref:System.Windows.Forms.ToolStrip> object contained in a form.</span></span>|  
|<xref:System.Windows.Forms.ToolStripControlHost>|<span data-ttu-id="73acb-147">裝載其他控制項，不會特別<xref:System.Windows.Forms.ToolStrip>控制項但要為其<xref:System.Windows.Forms.ToolStrip>功能。</span><span class="sxs-lookup"><span data-stu-id="73acb-147">Hosts other controls that are not specifically <xref:System.Windows.Forms.ToolStrip> controls but for which you want <xref:System.Windows.Forms.ToolStrip> functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|<span data-ttu-id="73acb-148">指定是否<xref:System.Windows.Forms.ToolStripItem>是配置在主要<xref:System.Windows.Forms.ToolStrip>，溢位<xref:System.Windows.Forms.ToolStrip>，或兩者都關閉。</span><span class="sxs-lookup"><span data-stu-id="73acb-148">Specifies whether a <xref:System.Windows.Forms.ToolStripItem> is to be laid out on the main <xref:System.Windows.Forms.ToolStrip>, on the overflow <xref:System.Windows.Forms.ToolStrip>, or neither.</span></span>|  
  
 <span data-ttu-id="73acb-149">如需詳細資訊，請參閱[ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)和[ToolStrip 控制項架構](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="73acb-149">For more information, see [ToolStrip Technology Summary](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md) and [ToolStrip Control Architecture](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73acb-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73acb-150">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
