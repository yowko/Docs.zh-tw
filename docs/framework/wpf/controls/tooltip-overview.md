---
title: "ToolTip 概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bd56323e90368f850ae54854e6f50b63d5f7fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-overview"></a><span data-ttu-id="b0c4a-102">ToolTip 概觀</span><span class="sxs-lookup"><span data-stu-id="b0c4a-102">ToolTip Overview</span></span>
<span data-ttu-id="b0c4a-103">工具提示是小型的快顯視窗出現時，使用者將滑鼠指標停留在項目，例如為 [過度] <xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="b0c4a-104">本主題將介紹工具提示，並說明如何建立及自訂工具提示內容。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a><span data-ttu-id="b0c4a-105">什麼是工具提示？</span><span class="sxs-lookup"><span data-stu-id="b0c4a-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="b0c4a-106">當使用者將滑鼠指標移到有工具提示的元素上時，包含工具提示內容 (例如，描述控制項功能的文字內容) 的視窗會出現並持續一段指定的時間。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="b0c4a-107">如果使用者將滑鼠指標移離控制項，由於工具提示內容無法接收焦點，視窗便會消失。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="b0c4a-108">工具提示的內容可包含一或多個文字行、影像、圖形或其他視覺內容。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="b0c4a-109">您可以將下列其中一個屬性設為工具提示內容來定義控制項的工具提示。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="b0c4a-110">您使用哪一個屬性，取決於定義工具提示控制項繼承自<xref:System.Windows.FrameworkContentElement>或<xref:System.Windows.FrameworkElement>類別。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a><span data-ttu-id="b0c4a-111">建立 ToolTip</span><span class="sxs-lookup"><span data-stu-id="b0c4a-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="b0c4a-112">下列範例示範如何建立簡單的工具提示，藉由設定<xref:System.Windows.FrameworkElement.ToolTip%2A>屬性<xref:System.Windows.Controls.Button>控制項的文字字串。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="b0c4a-113">您也可以定義為工具提示<xref:System.Windows.Controls.ToolTip>物件。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="b0c4a-114">下列範例會使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]指定<xref:System.Windows.Controls.ToolTip>物件的工具提示為<xref:System.Windows.Controls.TextBox>項目。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="b0c4a-115">請注意，此範例會指定<xref:System.Windows.Controls.ToolTip>藉由設定<xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="b0c4a-116">下列範例會使用程式碼產生<xref:System.Windows.Controls.ToolTip>物件。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="b0c4a-117">此範例會建立<xref:System.Windows.Controls.ToolTip>(`tt`) 並將它與相關聯<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="b0c4a-118">您也可以建立為未定義的工具提示內容<xref:System.Windows.Controls.ToolTip>物件，只要將工具提示內容在版面配置項目，例如<xref:System.Windows.Controls.DockPanel>。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="b0c4a-119">下列範例示範如何設定<xref:System.Windows.FrameworkElement.ToolTip%2A>屬性<xref:System.Windows.Controls.TextBox>內容是包含在<xref:System.Windows.Controls.DockPanel>控制項。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="b0c4a-120">使用 ToolTip 和 ToolTipService 類別的屬性</span><span class="sxs-lookup"><span data-stu-id="b0c4a-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="b0c4a-121">您可以透過設定視覺屬性並套用樣式，來自訂工具提示內容。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="b0c4a-122">如果您定義的內容做為工具提示<xref:System.Windows.Controls.ToolTip>物件，您可以設定的視覺屬性<xref:System.Windows.Controls.ToolTip>物件。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="b0c4a-123">否則，您必須設定對等的附加的屬性上<xref:System.Windows.Controls.ToolTipService>類別。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="b0c4a-124">如需如何設定屬性來指定工具提示內容的位置使用的範例<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>屬性，請參閱[放置工具提示](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md)。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a><span data-ttu-id="b0c4a-125">設定 ToolTip 樣式</span><span class="sxs-lookup"><span data-stu-id="b0c4a-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="b0c4a-126">您可以設定樣式<xref:System.Windows.Controls.ToolTip>藉由定義自訂<xref:System.Windows.Style>。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="b0c4a-127">下列範例會定義<xref:System.Windows.Style>呼叫`Simple`，示範如何在位移位置的<xref:System.Windows.Controls.ToolTip>和設定以變更其外觀<xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.Foreground%2A>， <xref:System.Windows.Controls.Control.FontSize%2A>，和<xref:System.Windows.Controls.Control.FontWeight%2A>。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="b0c4a-128">使用 ToolTipService 的時間間隔屬性</span><span class="sxs-lookup"><span data-stu-id="b0c4a-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="b0c4a-129"><xref:System.Windows.Controls.ToolTipService>類別會提供下列屬性，以設定工具提示顯示時間： <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>， <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>，和<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="b0c4a-130">使用<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>和<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>屬性，以指定的延遲通常簡短，之前<xref:System.Windows.Controls.ToolTip>隨即出現，並且指定多久<xref:System.Windows.Controls.ToolTip>保持可見狀態。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="b0c4a-131">如需詳細資訊，請參閱[操作說明：延遲 ToolTip 的顯示](http://msdn.microsoft.com/en-us/618e05ef-f2bf-4a53-a0f4-aacb49918bd7)。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-131">For more information, see [How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/en-us/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span></span>  
  
 <span data-ttu-id="b0c4a-132"><xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>屬性會決定當您將滑鼠指標之間快速移動它們是否不同的控制項的工具提示顯示沒有初始的延遲。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="b0c4a-133">如需有關<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>屬性，請參閱[使用 BetweenShowDelay 屬性](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md)。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="b0c4a-134">下列範例顯示如何為工具提示設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b0c4a-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="b0c4a-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0c4a-135">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [<span data-ttu-id="b0c4a-136">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="b0c4a-136">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
