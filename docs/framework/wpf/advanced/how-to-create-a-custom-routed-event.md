---
title: 作法：建立自訂路由事件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401462"
---
# <a name="how-to-create-a-custom-routed-event"></a><span data-ttu-id="e1d3e-102">作法：建立自訂路由事件</span><span class="sxs-lookup"><span data-stu-id="e1d3e-102">How to: Create a Custom Routed Event</span></span>
<span data-ttu-id="e1d3e-103">若要讓您的自訂事件支援事件路由, 您必須<xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>使用方法來註冊。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-103">For your custom event to support event routing, you need to register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="e1d3e-104">此範例示範建立自訂路由事件的基本概念。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-104">This example demonstrates the basics of creating a custom routed event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1d3e-105">範例</span><span class="sxs-lookup"><span data-stu-id="e1d3e-105">Example</span></span>  
 <span data-ttu-id="e1d3e-106">如下列範例所示, 您會先<xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>使用方法來註冊。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-106">As shown in the following example, you first register a <xref:System.Windows.RoutedEvent> using the <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> method.</span></span> <span data-ttu-id="e1d3e-107">依照慣例, <xref:System.Windows.RoutedEvent>靜態功能變數名稱應以後綴***事件***結尾。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-107">By convention, the <xref:System.Windows.RoutedEvent> static field name should end with the suffix ***Event***.</span></span> <span data-ttu-id="e1d3e-108">在此範例中, 事件的名稱是`Tap` , 而事件的路由策略是。 <xref:System.Windows.RoutingStrategy.Bubble></span><span class="sxs-lookup"><span data-stu-id="e1d3e-108">In this example, the name of the event is `Tap` and the routing strategy of the event is <xref:System.Windows.RoutingStrategy.Bubble>.</span></span> <span data-ttu-id="e1d3e-109">在註冊呼叫之後, 您可以為事件提供 add 和 remove common language runtime (CLR) 事件存取子。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-109">After the registration call, you can provide add-and-remove common language runtime (CLR) event accessors for the event.</span></span>  
  
 <span data-ttu-id="e1d3e-110">請注意，即使透過此特定範例中的 `OnTap` 虛擬方法引發事件，引發事件或事件回應變更的方式還是取決於您的需求。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-110">Note that even though the event is raised through the `OnTap` virtual method in this particular example, how you raise your event or how your event responds to changes depends on your needs.</span></span>  
  
 <span data-ttu-id="e1d3e-111">另請注意, 此範例基本上會執行的<xref:System.Windows.Controls.Button>整個子類別; 該子類別會建立為個別的元件, 然後在另[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]一個頁面上具現化為自訂類別。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-111">Note also that this example basically implements an entire subclass of <xref:System.Windows.Controls.Button>; that subclass is built as a separate assembly and then instantiated as a custom class on a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="e1d3e-112">這是為了說明下列概念：可將子類別控制項插入包含其他控制項的樹狀結構；然後，在此情況下，這些控制項上的自訂事件就會具有與任何原生 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 項目極為相同的事件路由功能。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-112">This is to illustrate the concept that subclassed controls can be inserted into trees composed of other controls, and that in this situation, custom events on these controls have the very same event routing capabilities as any native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element does.</span></span>  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 <span data-ttu-id="e1d3e-113">通道事件的建立方式相同, 但<xref:System.Windows.RoutedEvent.RoutingStrategy%2A>在註冊呼叫中設定為。 <xref:System.Windows.RoutingStrategy.Tunnel></span><span class="sxs-lookup"><span data-stu-id="e1d3e-113">Tunneling events are created the same way, but with <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> set to <xref:System.Windows.RoutingStrategy.Tunnel> in the registration call.</span></span> <span data-ttu-id="e1d3e-114">依照慣例，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的通道事件前面會加上 "Preview" 這個字。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-114">By convention, tunneling events in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] are prefixed with the word "Preview".</span></span>  
  
 <span data-ttu-id="e1d3e-115">若要查看事件反昇事件運作方式的範例，請參閱[處理路由事件](how-to-handle-a-routed-event.md)。</span><span class="sxs-lookup"><span data-stu-id="e1d3e-115">To see an example of how bubbling events work, see [Handle a Routed Event](how-to-handle-a-routed-event.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1d3e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1d3e-116">See also</span></span>

- [<span data-ttu-id="e1d3e-117">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="e1d3e-117">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="e1d3e-118">輸入概觀</span><span class="sxs-lookup"><span data-stu-id="e1d3e-118">Input Overview</span></span>](input-overview.md)
- [<span data-ttu-id="e1d3e-119">控制項撰寫概觀</span><span class="sxs-lookup"><span data-stu-id="e1d3e-119">Control Authoring Overview</span></span>](../controls/control-authoring-overview.md)
