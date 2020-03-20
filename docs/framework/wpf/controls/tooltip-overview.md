---
title: ToolTip 概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181941"
---
# <a name="tooltip-overview"></a><span data-ttu-id="c9669-102">ToolTip 概觀</span><span class="sxs-lookup"><span data-stu-id="c9669-102">ToolTip Overview</span></span>
<span data-ttu-id="c9669-103">工具提示是當使用者將滑鼠指標懸停在元素（如 在 上）時出現的一個小快顯視窗<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="c9669-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="c9669-104">本主題將介紹工具提示，並說明如何建立及自訂工具提示內容。</span><span class="sxs-lookup"><span data-stu-id="c9669-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a><span data-ttu-id="c9669-105">什麼是工具提示？</span><span class="sxs-lookup"><span data-stu-id="c9669-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="c9669-106">當使用者將滑鼠指標移到有工具提示的元素上時，包含工具提示內容 (例如，描述控制項功能的文字內容) 的視窗會出現並持續一段指定的時間。</span><span class="sxs-lookup"><span data-stu-id="c9669-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="c9669-107">如果使用者將滑鼠指標移離控制項，由於工具提示內容無法接收焦點，視窗便會消失。</span><span class="sxs-lookup"><span data-stu-id="c9669-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="c9669-108">工具提示的內容可包含一或多個文字行、影像、圖形或其他視覺內容。</span><span class="sxs-lookup"><span data-stu-id="c9669-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="c9669-109">您可以將下列其中一個屬性設為工具提示內容來定義控制項的工具提示。</span><span class="sxs-lookup"><span data-stu-id="c9669-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="c9669-110">您使用的屬性取決於定義工具提示的控制項是否從<xref:System.Windows.FrameworkContentElement>或<xref:System.Windows.FrameworkElement>類繼承。</span><span class="sxs-lookup"><span data-stu-id="c9669-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a><span data-ttu-id="c9669-111">建立 ToolTip</span><span class="sxs-lookup"><span data-stu-id="c9669-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="c9669-112">下面的示例演示如何通過將<xref:System.Windows.FrameworkElement.ToolTip%2A><xref:System.Windows.Controls.Button>控制項的屬性設置為文本字串來創建簡單的工具提示。</span><span class="sxs-lookup"><span data-stu-id="c9669-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="c9669-113">您還可以將工具提示定義為<xref:System.Windows.Controls.ToolTip>物件。</span><span class="sxs-lookup"><span data-stu-id="c9669-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="c9669-114">下面的示例用於[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]指定<xref:System.Windows.Controls.ToolTip>物件作為<xref:System.Windows.Controls.TextBox>元素的工具提示。</span><span class="sxs-lookup"><span data-stu-id="c9669-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="c9669-115">請注意，該示例<xref:System.Windows.Controls.ToolTip>通過設置 屬性指定<xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c9669-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="c9669-116">下面的示例使用代碼生成<xref:System.Windows.Controls.ToolTip>物件。</span><span class="sxs-lookup"><span data-stu-id="c9669-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="c9669-117">該示例創建<xref:System.Windows.Controls.ToolTip>一`tt`個 （ ，<xref:System.Windows.Controls.Button>並將其與 關聯它與 。</span><span class="sxs-lookup"><span data-stu-id="c9669-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="c9669-118">還可以通過將工具提示內容封閉在佈局元素（如<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.DockPanel>中）來創建未定義為物件的工具提示內容。</span><span class="sxs-lookup"><span data-stu-id="c9669-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="c9669-119">下面的示例演示如何將<xref:System.Windows.FrameworkElement.ToolTip%2A>中的 屬性<xref:System.Windows.Controls.TextBox>設置為包含在<xref:System.Windows.Controls.DockPanel>控制項中的內容。</span><span class="sxs-lookup"><span data-stu-id="c9669-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="c9669-120">使用 ToolTip 和 ToolTipService 類別的屬性</span><span class="sxs-lookup"><span data-stu-id="c9669-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="c9669-121">您可以透過設定視覺屬性並套用樣式，來自訂工具提示內容。</span><span class="sxs-lookup"><span data-stu-id="c9669-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="c9669-122">如果將工具提示內容定義為<xref:System.Windows.Controls.ToolTip>物件，則可以設置<xref:System.Windows.Controls.ToolTip>物件的可視屬性。</span><span class="sxs-lookup"><span data-stu-id="c9669-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="c9669-123">否則，必須在<xref:System.Windows.Controls.ToolTipService>類上設置等效的附加屬性。</span><span class="sxs-lookup"><span data-stu-id="c9669-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="c9669-124">有關如何設置屬性以便使用<xref:System.Windows.Controls.ToolTip>和<xref:System.Windows.Controls.ToolTipService>屬性指定工具提示內容的位置的示例，請參閱[定位工具提示](how-to-position-a-tooltip.md)。</span><span class="sxs-lookup"><span data-stu-id="c9669-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a><span data-ttu-id="c9669-125">設定 ToolTip 樣式</span><span class="sxs-lookup"><span data-stu-id="c9669-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="c9669-126">您可以通過定義自訂<xref:System.Windows.Style><xref:System.Windows.Controls.ToolTip>來設置 樣式 。</span><span class="sxs-lookup"><span data-stu-id="c9669-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="c9669-127">下面的<xref:System.Windows.Style>示例定義一個調用`Simple`，它演示如何通過設置<xref:System.Windows.Controls.ToolTip><xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.FontSize%2A>來抵消 的位置並更改其外觀。 <xref:System.Windows.Controls.Control.FontWeight%2A></span><span class="sxs-lookup"><span data-stu-id="c9669-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="c9669-128">使用 ToolTipService 的時間間隔屬性</span><span class="sxs-lookup"><span data-stu-id="c9669-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="c9669-129">該<xref:System.Windows.Controls.ToolTipService>類提供以下屬性，用於設置工具提示顯示時間：<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>和<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>。 <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A></span><span class="sxs-lookup"><span data-stu-id="c9669-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="c9669-130">使用<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>和<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>屬性指定<xref:System.Windows.Controls.ToolTip>出現之前的延遲（通常簡短），並指定<xref:System.Windows.Controls.ToolTip>保留的可見時間。</span><span class="sxs-lookup"><span data-stu-id="c9669-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="c9669-131">如需詳細資訊，請參閱[操作說明：延遲 ToolTip 的顯示](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="c9669-131">For more information, see [How to: Delay the Display of a ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).</span></span>  
  
 <span data-ttu-id="c9669-132">該<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>屬性確定在滑鼠指標之間快速移動滑鼠指標時，不同控制項的工具提示是否不會出現初始延遲。</span><span class="sxs-lookup"><span data-stu-id="c9669-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="c9669-133">有關該<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>屬性的詳細資訊，請參閱[使用"ShowDelay 之間"屬性](how-to-use-the-betweenshowdelay-property.md)。</span><span class="sxs-lookup"><span data-stu-id="c9669-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="c9669-134">下列範例顯示如何為工具提示設定這些屬性。</span><span class="sxs-lookup"><span data-stu-id="c9669-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="c9669-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9669-135">See also</span></span>

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [<span data-ttu-id="c9669-136">如何使用主題</span><span class="sxs-lookup"><span data-stu-id="c9669-136">How-to Topics</span></span>](tooltip-how-to-topics.md)
