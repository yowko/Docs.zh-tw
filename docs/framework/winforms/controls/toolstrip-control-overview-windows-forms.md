---
title: ToolStrip 控制項概觀
ms.date: 03/30/2017
f1_keywords:
- Toolstrip
helpviewer_keywords:
- ToolStrip control [Windows Forms], about ToolStrip control
- toolbars [Windows Forms], what's new in Windows Forms
- toolbars [Windows Forms]
- what's new [Windows Forms], toolbars
ms.assetid: 81d067ed-297c-4dad-90de-1bcac15336ec
ms.openlocfilehash: 931a6a0ea09f9b684b793c05cb1c3db8ee8fb7c7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741072"
---
# <a name="toolstrip-control-overview-windows-forms"></a><span data-ttu-id="8627d-102">ToolStrip 控制項概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="8627d-102">ToolStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="8627d-103">Windows Forms <xref:System.Windows.Forms.ToolStrip> 控制項和其相關聯的類別提供通用的架構，可將使用者介面專案與工具列、狀態列和功能表結合。</span><span class="sxs-lookup"><span data-stu-id="8627d-103">The Windows Forms <xref:System.Windows.Forms.ToolStrip> control and its associated classes provide a common framework for combining user interface elements into toolbars, status bars, and menus.</span></span> <span data-ttu-id="8627d-104"><xref:System.Windows.Forms.ToolStrip> 控制項提供豐富的設計階段經驗，包括就地啟用和編輯、自訂配置和浮動功能，這是工具列共用水準或垂直空間的能力。</span><span class="sxs-lookup"><span data-stu-id="8627d-104"><xref:System.Windows.Forms.ToolStrip> controls offer a rich design-time experience that includes in-place activation and editing, custom layout, and rafting, which is the ability of toolbars to share horizontal or vertical space.</span></span>  
  
 <span data-ttu-id="8627d-105">雖然 <xref:System.Windows.Forms.ToolStrip> 會取代並新增舊版中的功能，但如果有需要，<xref:System.Windows.Forms.ToolBar> 會保留供回溯相容性及未來使用。</span><span class="sxs-lookup"><span data-stu-id="8627d-105">Although <xref:System.Windows.Forms.ToolStrip> replaces and adds functionality to the control in previous versions, <xref:System.Windows.Forms.ToolBar> is retained for both backward compatibility and future use if desired.</span></span>  
  
## <a name="features-of-the-toolstrip-controls"></a><span data-ttu-id="8627d-106">ToolStrip 控制項的功能</span><span class="sxs-lookup"><span data-stu-id="8627d-106">Features of the ToolStrip Controls</span></span>  
 <span data-ttu-id="8627d-107">使用 <xref:System.Windows.Forms.ToolStrip> 控制項來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8627d-107">Use the <xref:System.Windows.Forms.ToolStrip> control to:</span></span>  
  
- <span data-ttu-id="8627d-108">在容器之間呈現通用的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="8627d-108">Present a common user interface across containers.</span></span>  
  
- <span data-ttu-id="8627d-109">建立可輕鬆自訂且常用的工具列，以支援「高級使用者介面」和「版面配置」功能，例如停駐、浮動、具有文字和影像的按鈕、下拉按鈕和控制項、溢位按鈕，以及 <xref:System.Windows.Forms.ToolStrip> 專案的執行時間重新排列。</span><span class="sxs-lookup"><span data-stu-id="8627d-109">Create easily customized, commonly employed toolbars that support advanced user interface and layout features, such as docking, rafting, buttons with text and images, drop-down buttons and controls, overflow buttons, and run-time reordering of <xref:System.Windows.Forms.ToolStrip> items.</span></span>  
  
- <span data-ttu-id="8627d-110">支援溢位和執行時間專案重新排列。</span><span class="sxs-lookup"><span data-stu-id="8627d-110">Support overflow and run-time item reordering.</span></span> <span data-ttu-id="8627d-111">當沒有足夠的空間可在 <xref:System.Windows.Forms.ToolStrip>中顯示時，溢位功能會將專案移至下拉式功能表。</span><span class="sxs-lookup"><span data-stu-id="8627d-111">The overflow feature moves items to a drop-down menu when there is not enough room to display them in a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
- <span data-ttu-id="8627d-112">透過常見的轉譯模型，支援作業系統的一般外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="8627d-112">Support the typical appearance and behavior of the operating system through a common rendering model.</span></span>  
  
- <span data-ttu-id="8627d-113">針對所有容器和包含的專案，以一致的方式處理事件，與處理其他控制項的事件相同。</span><span class="sxs-lookup"><span data-stu-id="8627d-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
- <span data-ttu-id="8627d-114">將專案從一個 <xref:System.Windows.Forms.ToolStrip> 拖曳至另一個或在 <xref:System.Windows.Forms.ToolStrip>中。</span><span class="sxs-lookup"><span data-stu-id="8627d-114">Drag items from one <xref:System.Windows.Forms.ToolStrip> to another or within a <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
- <span data-ttu-id="8627d-115">在 <xref:System.Windows.Forms.ToolStripDropDown>中，建立具有「高級」配置的下拉式控制項和使用者介面類別型編輯器。</span><span class="sxs-lookup"><span data-stu-id="8627d-115">Create drop-down controls and user interface type editors with advanced layouts in a <xref:System.Windows.Forms.ToolStripDropDown>.</span></span>  
  
 <span data-ttu-id="8627d-116">使用 <xref:System.Windows.Forms.ToolStripControlHost> 類別，在 <xref:System.Windows.Forms.ToolStrip> 上使用其他控制項，並為其取得 <xref:System.Windows.Forms.ToolStrip> 功能。</span><span class="sxs-lookup"><span data-stu-id="8627d-116">Use the <xref:System.Windows.Forms.ToolStripControlHost> class to use other controls on a <xref:System.Windows.Forms.ToolStrip> and gain <xref:System.Windows.Forms.ToolStrip> functionality for them.</span></span>  
  
 <span data-ttu-id="8627d-117">您可以使用 <xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>和 <xref:System.Windows.Forms.ToolStripManager> 以及 <xref:System.Windows.Forms.ToolStripRenderMode> 和 <xref:System.Windows.Forms.ToolStripManagerRenderMode> 列舉，來擴充功能及修改外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="8627d-117">You can extend the functionality and modify the appearance and behavior by using the <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, and <xref:System.Windows.Forms.ToolStripManager> along with the <xref:System.Windows.Forms.ToolStripRenderMode> and <xref:System.Windows.Forms.ToolStripManagerRenderMode> enumerations.</span></span>  
  
 <span data-ttu-id="8627d-118"><xref:System.Windows.Forms.ToolStrip> 控制項可高度設定和擴充，並提供許多屬性、方法和事件來自訂外觀和行為。</span><span class="sxs-lookup"><span data-stu-id="8627d-118">The <xref:System.Windows.Forms.ToolStrip> control is highly configurable and extensible, and it provides many properties, methods, and events to customize appearance and behavior.</span></span> <span data-ttu-id="8627d-119">以下是一些值得注意的成員：</span><span class="sxs-lookup"><span data-stu-id="8627d-119">Below are some noteworthy members:</span></span>  
  
### <a name="important-toolstrip-members"></a><span data-ttu-id="8627d-120">重要的 ToolStrip 成員</span><span class="sxs-lookup"><span data-stu-id="8627d-120">Important ToolStrip Members</span></span>  
  
|<span data-ttu-id="8627d-121">名稱</span><span class="sxs-lookup"><span data-stu-id="8627d-121">Name</span></span>|<span data-ttu-id="8627d-122">描述</span><span class="sxs-lookup"><span data-stu-id="8627d-122">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStrip.Dock%2A>|<span data-ttu-id="8627d-123">取得或設定停駐 <xref:System.Windows.Forms.ToolStrip> 父容器的邊緣。</span><span class="sxs-lookup"><span data-stu-id="8627d-123">Gets or sets which edge of the parent container a <xref:System.Windows.Forms.ToolStrip> is docked to.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>|<span data-ttu-id="8627d-124">取得或設定值，表示拖放動作和項目的重新排序是否由 <xref:System.Windows.Forms.ToolStrip> 類別私下處理。</span><span class="sxs-lookup"><span data-stu-id="8627d-124">Gets or sets a value indicating whether drag-and-drop and item reordering are handled privately by the <xref:System.Windows.Forms.ToolStrip> class.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>|<span data-ttu-id="8627d-125">取得或設定值，指出 <xref:System.Windows.Forms.ToolStrip> 如何配置其專案。</span><span class="sxs-lookup"><span data-stu-id="8627d-125">Gets or sets a value indicating how the <xref:System.Windows.Forms.ToolStrip> lays out its items.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>|<span data-ttu-id="8627d-126">取得或設定 <xref:System.Windows.Forms.ToolStripItem> 是否附加至 <xref:System.Windows.Forms.ToolStrip> 或 <xref:System.Windows.Forms.ToolStripOverflowButton>，或可在兩者之間浮動。</span><span class="sxs-lookup"><span data-stu-id="8627d-126">Gets or sets whether a <xref:System.Windows.Forms.ToolStripItem> is attached to the <xref:System.Windows.Forms.ToolStrip> or <xref:System.Windows.Forms.ToolStripOverflowButton> or can float between the two.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.IsDropDown%2A>|<span data-ttu-id="8627d-127">取得值，指出當按一下 <xref:System.Windows.Forms.ToolStripItem> 時，<xref:System.Windows.Forms.ToolStripItem> 是否會在下拉式清單中顯示其他專案。</span><span class="sxs-lookup"><span data-stu-id="8627d-127">Gets a value indicating whether a <xref:System.Windows.Forms.ToolStripItem> displays other items in a drop-down list when the <xref:System.Windows.Forms.ToolStripItem> is clicked.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.OverflowButton%2A>|<span data-ttu-id="8627d-128">取得 <xref:System.Windows.Forms.ToolStripItem>，它會在啟用溢位時做為 <xref:System.Windows.Forms.ToolStrip> 的溢位按鈕。</span><span class="sxs-lookup"><span data-stu-id="8627d-128">Gets the <xref:System.Windows.Forms.ToolStripItem> that is the overflow button for a <xref:System.Windows.Forms.ToolStrip> with overflow enabled.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.Renderer%2A>|<span data-ttu-id="8627d-129">取得或設定用來自訂 <xref:System.Windows.Forms.ToolStrip>之外觀和行為（外觀與風格）的 <xref:System.Windows.Forms.ToolStripRenderer>。</span><span class="sxs-lookup"><span data-stu-id="8627d-129">Gets or sets a <xref:System.Windows.Forms.ToolStripRenderer> used to customize the appearance and behavior (look and feel) of a <xref:System.Windows.Forms.ToolStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.RenderMode%2A>|<span data-ttu-id="8627d-130">取得或設定套用至 <xref:System.Windows.Forms.ToolStrip> 的繪製樣式。</span><span class="sxs-lookup"><span data-stu-id="8627d-130">Gets or sets the painting styles to be applied to the <xref:System.Windows.Forms.ToolStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStrip.RendererChanged>|<span data-ttu-id="8627d-131">在 <xref:System.Windows.Forms.ToolStrip.Renderer%2A> 屬性變更時引發。</span><span class="sxs-lookup"><span data-stu-id="8627d-131">Raised when the <xref:System.Windows.Forms.ToolStrip.Renderer%2A> property changes.</span></span>|  
  
 <span data-ttu-id="8627d-132">透過使用一些附屬類別，就能達到 <xref:System.Windows.Forms.ToolStrip> 控制項的彈性。</span><span class="sxs-lookup"><span data-stu-id="8627d-132">The <xref:System.Windows.Forms.ToolStrip> control's flexibility is achieved through the use of a number of companion classes.</span></span> <span data-ttu-id="8627d-133">以下是一些最值得注意的部分：</span><span class="sxs-lookup"><span data-stu-id="8627d-133">Below are some of the most noteworthy:</span></span>  
  
### <a name="important-toolstrip-companion-classes"></a><span data-ttu-id="8627d-134">重要的 ToolStrip 附屬類別</span><span class="sxs-lookup"><span data-stu-id="8627d-134">Important ToolStrip Companion Classes</span></span>  
  
|<span data-ttu-id="8627d-135">名稱</span><span class="sxs-lookup"><span data-stu-id="8627d-135">Name</span></span>|<span data-ttu-id="8627d-136">描述</span><span class="sxs-lookup"><span data-stu-id="8627d-136">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip>|<span data-ttu-id="8627d-137">取代並加入 <xref:System.Windows.Forms.MainMenu> 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="8627d-137">Replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> class.</span></span>|  
|<xref:System.Windows.Forms.StatusStrip>|<span data-ttu-id="8627d-138">取代並加入 <xref:System.Windows.Forms.StatusBar> 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="8627d-138">Replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> class.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="8627d-139">取代並加入 <xref:System.Windows.Forms.ContextMenu> 類別的功能。</span><span class="sxs-lookup"><span data-stu-id="8627d-139">Replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> class.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem>|<span data-ttu-id="8627d-140">針對 <xref:System.Windows.Forms.ToolStrip>、<xref:System.Windows.Forms.ToolStripControlHost>或 <xref:System.Windows.Forms.ToolStripDropDown> 可以包含的所有元素，管理事件和配置的抽象基類。</span><span class="sxs-lookup"><span data-stu-id="8627d-140">Abstract base class that manages events and layout for all the elements that a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripControlHost>, or <xref:System.Windows.Forms.ToolStripDropDown> can contain.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="8627d-141">會在表單的每一端提供一個面板，其中控制項可透過各種方式排列。</span><span class="sxs-lookup"><span data-stu-id="8627d-141">Provides a container with a panel on each side of the form in which controls can be arranged in various ways.</span></span>|  
|<xref:System.Windows.Forms.ToolStripRenderer>|<span data-ttu-id="8627d-142">處理 <xref:System.Windows.Forms.ToolStrip> 物件的繪製功能。</span><span class="sxs-lookup"><span data-stu-id="8627d-142">Handles the painting functionality for <xref:System.Windows.Forms.ToolStrip> objects.</span></span>|  
|<xref:System.Windows.Forms.ToolStripProfessionalRenderer>|<span data-ttu-id="8627d-143">提供 Microsoft Office 樣式的外觀。</span><span class="sxs-lookup"><span data-stu-id="8627d-143">Provides Microsoft Office-style appearance.</span></span>|  
|<xref:System.Windows.Forms.ToolStripManager>|<span data-ttu-id="8627d-144">控制 <xref:System.Windows.Forms.ToolStrip> 的呈現和浮動定位，以及 <xref:System.Windows.Forms.MenuStrip>、<xref:System.Windows.Forms.ToolStripDropDownMenu> 和 <xref:System.Windows.Forms.ToolStripMenuItem> 物件的合併。</span><span class="sxs-lookup"><span data-stu-id="8627d-144">Controls <xref:System.Windows.Forms.ToolStrip> rendering and rafting, and the merging of <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, and <xref:System.Windows.Forms.ToolStripMenuItem> objects.</span></span>|  
|<xref:System.Windows.Forms.ToolStripManagerRenderMode>|<span data-ttu-id="8627d-145">指定套用至包含在表單中之多個 <xref:System.Windows.Forms.ToolStrip> 物件的繪製樣式（自訂、Windows XP 或 Microsoft Office Professional）。</span><span class="sxs-lookup"><span data-stu-id="8627d-145">Specifies the painting style (custom, Windows XP, or Microsoft Office Professional) applied to multiple <xref:System.Windows.Forms.ToolStrip> objects contained in a form.</span></span>|  
|<xref:System.Windows.Forms.ToolStripRenderMode>|<span data-ttu-id="8627d-146">指定套用至表單所包含之一個 <xref:System.Windows.Forms.ToolStrip> 物件的繪製樣式（自訂、Windows XP 或 Microsoft Office Professional）。</span><span class="sxs-lookup"><span data-stu-id="8627d-146">Specifies the painting style (custom, Windows XP, or Microsoft Office Professional) applied to one <xref:System.Windows.Forms.ToolStrip> object contained in a form.</span></span>|  
|<xref:System.Windows.Forms.ToolStripControlHost>|<span data-ttu-id="8627d-147">裝載其他不是特別 <xref:System.Windows.Forms.ToolStrip> 控制項，但您想要 <xref:System.Windows.Forms.ToolStrip> 功能的控制項。</span><span class="sxs-lookup"><span data-stu-id="8627d-147">Hosts other controls that are not specifically <xref:System.Windows.Forms.ToolStrip> controls but for which you want <xref:System.Windows.Forms.ToolStrip> functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItemPlacement>|<span data-ttu-id="8627d-148">指定是否要在主要 <xref:System.Windows.Forms.ToolStrip>、溢位 <xref:System.Windows.Forms.ToolStrip>或兩者皆配置 <xref:System.Windows.Forms.ToolStripItem>。</span><span class="sxs-lookup"><span data-stu-id="8627d-148">Specifies whether a <xref:System.Windows.Forms.ToolStripItem> is to be laid out on the main <xref:System.Windows.Forms.ToolStrip>, on the overflow <xref:System.Windows.Forms.ToolStrip>, or neither.</span></span>|  
  
 <span data-ttu-id="8627d-149">如需詳細資訊，請參閱[Toolstrip 技術摘要](toolstrip-technology-summary.md)和[toolstrip 控制項架構](toolstrip-control-architecture.md)。</span><span class="sxs-lookup"><span data-stu-id="8627d-149">For more information, see [ToolStrip Technology Summary](toolstrip-technology-summary.md) and [ToolStrip Control Architecture](toolstrip-control-architecture.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8627d-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8627d-150">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
