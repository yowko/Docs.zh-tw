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
ms.openlocfilehash: 00b12d9dc25e0704eb73d8bc727ae6647493f494
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401173"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="240a3-102">HOW TO：使用程式碼新增事件處理常式</span><span class="sxs-lookup"><span data-stu-id="240a3-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="240a3-103">這個範例示範如何使用程式碼, 將事件處理常式新增至專案。</span><span class="sxs-lookup"><span data-stu-id="240a3-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="240a3-104">如果您想要將事件處理常式加入至[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]專案, 而且已經載入包含該專案的標記頁面, 則必須使用程式碼加入處理常式。</span><span class="sxs-lookup"><span data-stu-id="240a3-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="240a3-105">或者, 如果您要完全使用程式碼來建立應用程式的專案樹狀結構, 而不使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]宣告任何專案, 您可以呼叫特定方法, 將事件處理常式加入至結構化專案樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="240a3-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="240a3-106">範例</span><span class="sxs-lookup"><span data-stu-id="240a3-106">Example</span></span>  
 <span data-ttu-id="240a3-107">下列範例會將新<xref:System.Windows.Controls.Button>的加入至一開始在中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義的現有頁面。</span><span class="sxs-lookup"><span data-stu-id="240a3-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="240a3-108">程式碼後置檔案會執行事件處理常式方法, 然後在上<xref:System.Windows.Controls.Button>加入該方法做為新的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="240a3-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="240a3-109">此C#範例會使用`+=`運算子來指派事件的處理常式。</span><span class="sxs-lookup"><span data-stu-id="240a3-109">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="240a3-110">這是用來在 common language runtime (CLR) 事件處理模型中指派處理常式的相同運算子。</span><span class="sxs-lookup"><span data-stu-id="240a3-110">This is the same operator that is used to assign a handler in the common language runtime (CLR) event handling model.</span></span> <span data-ttu-id="240a3-111">Microsoft Visual Basic 不支援此運算子做為新增事件處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="240a3-111">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="240a3-112">而是需要下列其中一種技術:</span><span class="sxs-lookup"><span data-stu-id="240a3-112">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="240a3-113">搭配使用`AddressOf`方法與運算子, 以參考事件處理常式的執行。 <xref:System.Windows.UIElement.AddHandler%2A></span><span class="sxs-lookup"><span data-stu-id="240a3-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="240a3-114">`Handles`使用關鍵字做為事件處理常式定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="240a3-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="240a3-115">這裡不會顯示這項技術;請參閱[Visual Basic 和 WPF 事件處理](visual-basic-and-wpf-event-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="240a3-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="240a3-116">在初始[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]剖析的頁面中新增事件處理常式會簡單許多。</span><span class="sxs-lookup"><span data-stu-id="240a3-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="240a3-117">在您要加入事件處理常式的物件專案中, 加入與您要處理的事件名稱相符的屬性。</span><span class="sxs-lookup"><span data-stu-id="240a3-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="240a3-118">然後指定該屬性的值, 做為您在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面的程式碼後置檔案中定義的事件處理常式方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="240a3-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="240a3-119">如需詳細資訊, 請參閱[XAML 總覽 (WPF)](xaml-overview-wpf.md)或[路由事件總覽](routed-events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="240a3-119">For more information, see [XAML Overview (WPF)](xaml-overview-wpf.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="240a3-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="240a3-120">See also</span></span>

- [<span data-ttu-id="240a3-121">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="240a3-121">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="240a3-122">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="240a3-122">How-to Topics</span></span>](events-how-to-topics.md)
