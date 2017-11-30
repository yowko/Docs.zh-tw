---
title: "ToolBar 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dddf6940e180b3d997357390ead38f99f52994ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="toolbar-overview"></a><span data-ttu-id="4f207-102">ToolBar 概觀</span><span class="sxs-lookup"><span data-stu-id="4f207-102">ToolBar Overview</span></span>
<span data-ttu-id="4f207-103"><xref:System.Windows.Controls.ToolBar>控制項是一組命令或其函式中，通常與控制項的容器。</span><span class="sxs-lookup"><span data-stu-id="4f207-103"><xref:System.Windows.Controls.ToolBar> controls are containers for a group of commands or controls which are typically related in their function.</span></span> <span data-ttu-id="4f207-104">A<xref:System.Windows.Controls.ToolBar>通常包含按鈕就會叫用命令。</span><span class="sxs-lookup"><span data-stu-id="4f207-104">A <xref:System.Windows.Controls.ToolBar> usually contains buttons which invoke commands.</span></span>  
  
  
<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a><span data-ttu-id="4f207-105">ToolBar 控制項</span><span class="sxs-lookup"><span data-stu-id="4f207-105">ToolBar Control</span></span>  
 <span data-ttu-id="4f207-106"><xref:System.Windows.Controls.ToolBar>控制項接受的按鈕或其他控制項列類似的排列到單一資料列或資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="4f207-106">The <xref:System.Windows.Controls.ToolBar> control takes its name from the bar-like arrangement of buttons or other controls into a single row or column.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="4f207-107"><xref:System.Windows.Controls.ToolBar>控制項提供溢位機制，而放置容納不下自然大小限制的任何項目<xref:System.Windows.Controls.ToolBar>到特殊的溢位區域。</span><span class="sxs-lookup"><span data-stu-id="4f207-107"> <xref:System.Windows.Controls.ToolBar> controls provide an overflow mechanism which places any items that do not fit naturally within a size-constrained <xref:System.Windows.Controls.ToolBar> into a special overflow area.</span></span> <span data-ttu-id="4f207-108">此外， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar>控制項通常用來與相關<xref:System.Windows.Controls.ToolBarTray>提供特殊的配置行為，以及支援使用者起始調整大小和排列工具列的控制項。</span><span class="sxs-lookup"><span data-stu-id="4f207-108">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> controls are usually used with the related <xref:System.Windows.Controls.ToolBarTray> control, which provides special layout behavior as well as support for user-initiated sizing and arranging of toolbars.</span></span>  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a><span data-ttu-id="4f207-109">指定 ToolBar 在 ToolBarTray 中的位置</span><span class="sxs-lookup"><span data-stu-id="4f207-109">Specifying the Position of ToolBars in a ToolBarTray</span></span>  
 <span data-ttu-id="4f207-110">使用<xref:System.Windows.Controls.ToolBar.Band%2A>和<xref:System.Windows.Controls.ToolBar.BandIndex%2A>屬性來定位<xref:System.Windows.Controls.ToolBar>中<xref:System.Windows.Controls.ToolBarTray>。</span><span class="sxs-lookup"><span data-stu-id="4f207-110">Use the <xref:System.Windows.Controls.ToolBar.Band%2A> and <xref:System.Windows.Controls.ToolBar.BandIndex%2A> properties to position the <xref:System.Windows.Controls.ToolBar> in the <xref:System.Windows.Controls.ToolBarTray>.</span></span> <span data-ttu-id="4f207-111"><xref:System.Windows.Controls.ToolBar.Band%2A>表示所在位置<xref:System.Windows.Controls.ToolBar>放在其父代<xref:System.Windows.Controls.ToolBarTray>。</span><span class="sxs-lookup"><span data-stu-id="4f207-111"><xref:System.Windows.Controls.ToolBar.Band%2A> indicates the position in which the <xref:System.Windows.Controls.ToolBar> is placed within its parent <xref:System.Windows.Controls.ToolBarTray>.</span></span> <span data-ttu-id="4f207-112"><xref:System.Windows.Controls.ToolBar.BandIndex%2A>表示順序<xref:System.Windows.Controls.ToolBar>會放置在其範圍內。</span><span class="sxs-lookup"><span data-stu-id="4f207-112"><xref:System.Windows.Controls.ToolBar.BandIndex%2A> indicates the order in which the <xref:System.Windows.Controls.ToolBar> is placed within its band.</span></span> <span data-ttu-id="4f207-113">下列範例會示範如何使用這個屬性來放置<xref:System.Windows.Controls.ToolBar>內控制<xref:System.Windows.Controls.ToolBarTray>。</span><span class="sxs-lookup"><span data-stu-id="4f207-113">The following example shows how use this property to place <xref:System.Windows.Controls.ToolBar> controls inside a <xref:System.Windows.Controls.ToolBarTray>.</span></span>  
  
 [!code-xaml[ToolBarExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a><span data-ttu-id="4f207-114">具有溢位項目的 ToolBar</span><span class="sxs-lookup"><span data-stu-id="4f207-114">ToolBars with Overflow Items</span></span>  
 <span data-ttu-id="4f207-115">通常<xref:System.Windows.Controls.ToolBar>控制項包含比工具列的大小，可容納更多的項目。</span><span class="sxs-lookup"><span data-stu-id="4f207-115">Often <xref:System.Windows.Controls.ToolBar> controls contain more items than can fit into the toolbar's size.</span></span> <span data-ttu-id="4f207-116">當發生這種情況時，<xref:System.Windows.Controls.ToolBar>顯示溢位按鈕。</span><span class="sxs-lookup"><span data-stu-id="4f207-116">When this happens, the <xref:System.Windows.Controls.ToolBar> displays an overflow button.</span></span> <span data-ttu-id="4f207-117">若要查看的溢位項目，使用者按一下溢位按鈕和下列快顯視窗中顯示的項目<xref:System.Windows.Controls.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="4f207-117">To see the overflow items, a user clicks the overflow button and the items are shown in a pop-up window below the <xref:System.Windows.Controls.ToolBar>.</span></span> <span data-ttu-id="4f207-118">下圖顯示<xref:System.Windows.Controls.ToolBar>溢位項目。</span><span class="sxs-lookup"><span data-stu-id="4f207-118">The following graphic shows a <xref:System.Windows.Controls.ToolBar> with overflow items.</span></span>  
  
 <span data-ttu-id="4f207-119">![溢位的工具列](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")</span><span class="sxs-lookup"><span data-stu-id="4f207-119">![ToolBar with overflow](../../../../docs/framework/wpf/controls/media/toolbarwithoverflowitem.png "ToolbarWithOverflowItem")</span></span>  
<span data-ttu-id="4f207-120">具有溢位項目的工具列</span><span class="sxs-lookup"><span data-stu-id="4f207-120">Toolbar with Overflow Items</span></span>  
  
 <span data-ttu-id="4f207-121">您可以指定當工具列上的項目位於溢位面板設定<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType>附加屬性<xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>， <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>，或<xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4f207-121">You can specify when an item on a toolbar is placed on the overflow panel by setting the <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> attached property to <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, or <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4f207-122">下列範例指定工具列上的最後四個按鈕應該一律位於溢位面板上。</span><span class="sxs-lookup"><span data-stu-id="4f207-122">The following example specifies that the last four buttons on the toolbar should always be on the overflow panel.</span></span>  
  
 [!code-xaml[ToolBarExample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <span data-ttu-id="4f207-123"><xref:System.Windows.Controls.ToolBar>使用<xref:System.Windows.Controls.Primitives.ToolBarPanel>和<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>中其<xref:System.Windows.Controls.ControlTemplate>。</span><span class="sxs-lookup"><span data-stu-id="4f207-123">The <xref:System.Windows.Controls.ToolBar> uses a <xref:System.Windows.Controls.Primitives.ToolBarPanel> and a <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> in its <xref:System.Windows.Controls.ControlTemplate>.</span></span>  <span data-ttu-id="4f207-124"><xref:System.Windows.Controls.Primitives.ToolBarPanel>負責版面配置 工具列上的項目。</span><span class="sxs-lookup"><span data-stu-id="4f207-124">The <xref:System.Windows.Controls.Primitives.ToolBarPanel> is responsible for the layout of the items on the toolbar.</span></span>  <span data-ttu-id="4f207-125"><xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>負責可容納的項目配置<xref:System.Windows.Controls.ToolBar>。</span><span class="sxs-lookup"><span data-stu-id="4f207-125">The <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> is responsible for the layout of the items that do not fit on the <xref:System.Windows.Controls.ToolBar>.</span></span> <span data-ttu-id="4f207-126">如需<xref:System.Windows.Controls.ControlTemplate>如<xref:System.Windows.Controls.ToolBar>，請參閱</span><span class="sxs-lookup"><span data-stu-id="4f207-126">For an example of a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, see</span></span>  
  
 <span data-ttu-id="4f207-127">[ToolBar 樣式和範本](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md)。</span><span class="sxs-lookup"><span data-stu-id="4f207-127">[ToolBar Styles and Templates](../../../../docs/framework/wpf/controls/toolbar-styles-and-templates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f207-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f207-128">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
 <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
 [<span data-ttu-id="4f207-129">ToolBar 上的樣式控制項</span><span class="sxs-lookup"><span data-stu-id="4f207-129">Style Controls on a ToolBar</span></span>](../../../../docs/framework/wpf/controls/how-to-style-controls-on-a-toolbar.md)  
 [<span data-ttu-id="4f207-130">WPF 控制項陳列庫範例</span><span class="sxs-lookup"><span data-stu-id="4f207-130">WPF Controls Gallery Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160053)
