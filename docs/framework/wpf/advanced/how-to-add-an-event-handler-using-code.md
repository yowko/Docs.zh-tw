---
title: "如何：使用程式碼加入事件處理常式"
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
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 348136a1feaf6e0a0824cf183a2eeec4e10b77fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="37871-102">如何：使用程式碼加入事件處理常式</span><span class="sxs-lookup"><span data-stu-id="37871-102">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="37871-103">這個範例示範如何使用程式碼，將事件處理常式加入至項目。</span><span class="sxs-lookup"><span data-stu-id="37871-103">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="37871-104">如果您想要加入事件處理常式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目，並包含元素的標記頁面已載入，則必須新增使用程式碼的處理常式。</span><span class="sxs-lookup"><span data-stu-id="37871-104">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="37871-105">或者，如果您要建置應用程式完全使用程式碼和未宣告的任何項目使用的項目樹狀結構向上[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，您可以呼叫至建構的項目樹狀結構中加入事件處理常式的特定方法。</span><span class="sxs-lookup"><span data-stu-id="37871-105">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37871-106">範例</span><span class="sxs-lookup"><span data-stu-id="37871-106">Example</span></span>  
 <span data-ttu-id="37871-107">下列範例會將新<xref:System.Windows.Controls.Button>到現有的頁面中一開始定義[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="37871-107">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="37871-108">實作事件處理常式方法的程式碼後置檔案，並再將該方法做為新的事件處理常式加入上<xref:System.Windows.Controls.Button>。</span><span class="sxs-lookup"><span data-stu-id="37871-108">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="37871-109">[!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)]範例會使用`+=`運算子來指派到的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="37871-109">The [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="37871-110">這是用來指派中的處理常式的相同運算子[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]事件處理模型。</span><span class="sxs-lookup"><span data-stu-id="37871-110">This is the same operator that is used to assign a handler in the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] event handling model.</span></span> [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]<span data-ttu-id="37871-111">不支援此運算子來加入事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="37871-111"> does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="37871-112">它需要使用兩種技術的其中一個：</span><span class="sxs-lookup"><span data-stu-id="37871-112">It instead requires one of two techniques:</span></span>  
  
-   <span data-ttu-id="37871-113">使用<xref:System.Windows.UIElement.AddHandler%2A>方法搭配`AddressOf`運算子，以便參考的事件處理常式實作。</span><span class="sxs-lookup"><span data-stu-id="37871-113">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
-   <span data-ttu-id="37871-114">使用`Handles`關鍵字做為事件處理常式定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="37871-114">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="37871-115">這項技術不如下所示。請參閱[Visual Basic 和 WPF 的事件處理](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="37871-115">This technique is not shown here; see [Visual Basic and WPF Event Handling](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  <span data-ttu-id="37871-116">加入事件處理常式中一開始剖析[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面是更簡單。</span><span class="sxs-lookup"><span data-stu-id="37871-116">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="37871-117">在您要加入事件處理常式物件的項目，加入的屬性符合您想要處理之事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="37871-117">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="37871-118">然後指定該屬性的值做為您的程式碼後置檔案中定義的事件處理常式方法名稱[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="37871-118">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="37871-119">如需詳細資訊，請參閱[XAML 概觀 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)或[路由傳送事件概觀](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="37871-119">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) or [Routed Events Overview](../../../../docs/framework/wpf/advanced/routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37871-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37871-120">See Also</span></span>  
 [<span data-ttu-id="37871-121">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="37871-121">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="37871-122">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="37871-122">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
