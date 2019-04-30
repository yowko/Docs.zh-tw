---
title: HOW TO：處理路由事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: edb3d6724af89b7e85986c50b579084e3c4e5070
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001503"
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="d7115-102">HOW TO：處理路由事件</span><span class="sxs-lookup"><span data-stu-id="d7115-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="d7115-103">此範例示範事件反昇事件運作方式，以及如何撰寫可處理路由事件資料的處理常式。</span><span class="sxs-lookup"><span data-stu-id="d7115-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7115-104">範例</span><span class="sxs-lookup"><span data-stu-id="d7115-104">Example</span></span>  
 <span data-ttu-id="d7115-105">在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中，項目會以項目樹狀結構排列。</span><span class="sxs-lookup"><span data-stu-id="d7115-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="d7115-106">父項目可以參與處理一開始是由項目樹狀結構中子項目所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="d7115-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="d7115-107">這可能是事件路由所造成。</span><span class="sxs-lookup"><span data-stu-id="d7115-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="d7115-108">路由事件通常會遵循兩個路由策略中的其中一個：事件反昇或通道。</span><span class="sxs-lookup"><span data-stu-id="d7115-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="d7115-109">此範例著重於事件反昇事件，並使用<xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType>事件，以顯示路由運作方式。</span><span class="sxs-lookup"><span data-stu-id="d7115-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="d7115-110">下列範例會建立兩個<xref:System.Windows.Controls.Button>控制項，並使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]屬性語法，以將事件處理常式附加至通用的父項目，這在此範例中是<xref:System.Windows.Controls.StackPanel>。</span><span class="sxs-lookup"><span data-stu-id="d7115-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="d7115-111">而不是每個附加個別的事件處理常式<xref:System.Windows.Controls.Button>子元素，此範例使用屬性語法來附加事件處理常式<xref:System.Windows.Controls.StackPanel>父項目。</span><span class="sxs-lookup"><span data-stu-id="d7115-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="d7115-112">此事件處理模式示範如何使用事件路由，作為減少已附加處理常式之項目數的技術。</span><span class="sxs-lookup"><span data-stu-id="d7115-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="d7115-113">每個的所有事件反昇事件<xref:System.Windows.Controls.Button>路由到父項目。</span><span class="sxs-lookup"><span data-stu-id="d7115-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="d7115-114">請注意，其父系<xref:System.Windows.Controls.StackPanel>項目，<xref:System.Windows.Controls.Primitives.ButtonBase.Click>指定為部分限定屬性所命名的事件名稱<xref:System.Windows.Controls.Button>類別。</span><span class="sxs-lookup"><span data-stu-id="d7115-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="d7115-115"><xref:System.Windows.Controls.Button>類別是<xref:System.Windows.Controls.Primitives.ButtonBase>衍生的類別具有<xref:System.Windows.Controls.Primitives.ButtonBase.Click>的成員清單中的事件。</span><span class="sxs-lookup"><span data-stu-id="d7115-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="d7115-116">如果所處理的事件不存在於附加路由事件處理常式之項目的成員清單中，則需要有附加事件處理常式的這個部分限定方法。</span><span class="sxs-lookup"><span data-stu-id="d7115-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="d7115-117">下列範例會處理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="d7115-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="d7115-118">此範例會報告哪些項目處理事件以及哪個項目引發事件。</span><span class="sxs-lookup"><span data-stu-id="d7115-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="d7115-119">使用者按一下任一按鈕時，就會執行事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d7115-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="d7115-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7115-120">See also</span></span>

- <xref:System.Windows.RoutedEvent>
- [<span data-ttu-id="d7115-121">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="d7115-121">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="d7115-122">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="d7115-122">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="d7115-123">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="d7115-123">How-to Topics</span></span>](events-how-to-topics.md)
- [<span data-ttu-id="d7115-124">XAML 語法詳細資料</span><span class="sxs-lookup"><span data-stu-id="d7115-124">XAML Syntax In Detail</span></span>](xaml-syntax-in-detail.md)
