---
title: HOW TO：使用程式碼新增事件處理常式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 10f8e0899e61d5d54589c910bdcbcd92d8ee947c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777061"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="e1e73-102">HOW TO：使用程式碼新增事件處理常式</span><span class="sxs-lookup"><span data-stu-id="e1e73-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="e1e73-103">此範例示範如何使用程式碼，將事件處理常式新增至項目。</span><span class="sxs-lookup"><span data-stu-id="e1e73-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="e1e73-104">如果您想要新增事件處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目和包含的項目 [標記] 頁面已載入，您必須新增處理常式，使用程式碼。</span><span class="sxs-lookup"><span data-stu-id="e1e73-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="e1e73-105">或者，如果您正在建置應用程式完全使用程式碼和未宣告任何項目使用的項目樹狀結構中向上[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以呼叫特定方法，將事件處理常式新增至建構的項目樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e1e73-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1e73-106">範例</span><span class="sxs-lookup"><span data-stu-id="e1e73-106">Example</span></span>  
 <span data-ttu-id="e1e73-107">下列範例會將新<xref:System.Windows.Controls.Button>至現有的頁面，一開始會定義在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e1e73-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="e1e73-108">程式碼後置檔案會實作事件處理常式方法和上，然後將該方法新增為新的事件處理常式<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="e1e73-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="e1e73-109">C#範例會使用`+=`運算子來指派到的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e1e73-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="e1e73-110">這是用來指派中的處理常式的相同運算子[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]事件處理模型。</span><span class="sxs-lookup"><span data-stu-id="e1e73-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> <span data-ttu-id="e1e73-111">Microsoft Visual Basic 不支援這個運算子，來加入事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="e1e73-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="e1e73-112">它需要使用兩種技術之一：</span><span class="sxs-lookup"><span data-stu-id="e1e73-112">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="e1e73-113">使用<xref:System.Windows.UIElement.AddHandler%2A>方法，連同`AddressOf`運算子，以便參考事件處理常式實作。</span><span class="sxs-lookup"><span data-stu-id="e1e73-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="e1e73-114">使用`Handles`關鍵字做為事件處理常式定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="e1e73-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="e1e73-115">這項技術不討論;請參閱[Visual Basic 和 WPF 事件處理](visual-basic-and-wpf-event-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="e1e73-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="e1e73-116">加入事件處理常式中一開始剖析[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面是更簡單。</span><span class="sxs-lookup"><span data-stu-id="e1e73-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="e1e73-117">在您要加入事件處理常式的物件項目，新增符合您想要處理的事件名稱的屬性。</span><span class="sxs-lookup"><span data-stu-id="e1e73-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="e1e73-118">然後指定該屬性的值，做為您的程式碼後置檔案中定義的事件處理常式方法名稱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="e1e73-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="e1e73-119">如需詳細資訊，請參閱 < [XAML 概觀 (WPF)](xaml-overview-wpf.md)或是[路由事件概觀](routed-events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="e1e73-119">For more information, see [XAML Overview (WPF)](xaml-overview-wpf.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e73-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1e73-120">See also</span></span>

- [<span data-ttu-id="e1e73-121">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="e1e73-121">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="e1e73-122">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="e1e73-122">How-to Topics</span></span>](events-how-to-topics.md)
