---
title: HOW TO：新增路由事件的類別處理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 7b897954cbdab461dc0305c6290e67c1af5282c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224263"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a><span data-ttu-id="2192c-102">HOW TO：新增路由事件的類別處理</span><span class="sxs-lookup"><span data-stu-id="2192c-102">How to: Add Class Handling for a Routed Event</span></span>
<span data-ttu-id="2192c-103">藉由類別處理常式或路由中任何指定節點上的執行個體處理常式可以處理路由的事件。</span><span class="sxs-lookup"><span data-stu-id="2192c-103">Routed events can be handled either by class handlers or instance handlers on any given node in the route.</span></span> <span data-ttu-id="2192c-104">類別處理常式會先叫用，而且可以由類別實作來隱藏執行個體處理的事件，或引進其他事件的特定行為的基底類別所擁有的事件。</span><span class="sxs-lookup"><span data-stu-id="2192c-104">Class handlers are invoked first, and can be used by class implementations to suppress events from instance handling or introduce other event specific behaviors on events that are owned by base classes.</span></span> <span data-ttu-id="2192c-105">此範例說明兩種密切相關的技術，實作類別處理常式。</span><span class="sxs-lookup"><span data-stu-id="2192c-105">This example illustrates two closely related techniques for implementing class handlers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2192c-106">範例</span><span class="sxs-lookup"><span data-stu-id="2192c-106">Example</span></span>  
 <span data-ttu-id="2192c-107">這個範例會使用自訂類別，根據<xref:System.Windows.Controls.Canvas>面板。</span><span class="sxs-lookup"><span data-stu-id="2192c-107">This example uses a custom class based on the <xref:System.Windows.Controls.Canvas> panel.</span></span> <span data-ttu-id="2192c-108">應用程式的基本前提是自訂類別導入了在其子項目，包括攔截任何滑鼠左的按鈕點選，以及標示為已處理，將會叫用子系項目類別或它的任何執行個體處理常式之前的行為。</span><span class="sxs-lookup"><span data-stu-id="2192c-108">The basic premise of the application is that the custom class introduces behaviors on its child elements, including intercepting any left mouse button clicks and marking them handled, before the child element class or any instance handlers on it will be invoked.</span></span>  
  
 <span data-ttu-id="2192c-109"><xref:System.Windows.UIElement>類別會公開虛擬方法，以允許的類別處理<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>事件，只覆寫事件。</span><span class="sxs-lookup"><span data-stu-id="2192c-109">The <xref:System.Windows.UIElement> class exposes a virtual method that enables class handling on the <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> event, by simply overriding the event.</span></span> <span data-ttu-id="2192c-110">這是最簡單的方式來實作類別處理，如果您的類別階層中某處的虛擬方法可用。</span><span class="sxs-lookup"><span data-stu-id="2192c-110">This is the simplest way to implement class handling if such a virtual method is available somewhere in your class' hierarchy.</span></span> <span data-ttu-id="2192c-111">下列程式碼示範<xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A>"MyEditContainer"衍生自的類別中實作<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="2192c-111">The following code shows the <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementation in the "MyEditContainer" that is derived from <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="2192c-112">實作會將事件標記為已處理的引數中，然後將 指定來源項目基本的可見變更一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="2192c-112">The implementation marks the event as handled in the arguments, and then adds some code to give the source element a basic visible change.</span></span>  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 <span data-ttu-id="2192c-113">如果沒有虛擬基底類別或該特定的方法，可以直接使用的公用程式方法加入類別處理<xref:System.Windows.EventManager>類別， <xref:System.Windows.EventManager.RegisterClassHandler%2A>。</span><span class="sxs-lookup"><span data-stu-id="2192c-113">If no virtual is available on base classes or for that particular method, class handling can be added directly using a utility method of the <xref:System.Windows.EventManager> class, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span></span> <span data-ttu-id="2192c-114">中的加入類別處理的類別的靜態初始設定時，應該只呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="2192c-114">This method should only be called within the static initialization of classes that are adding class handling.</span></span> <span data-ttu-id="2192c-115">這個範例會將另一個處理常式<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>，並在此情況下已註冊的類別是自訂類別。</span><span class="sxs-lookup"><span data-stu-id="2192c-115">This example adds another handler for <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , and in this case the registered class is the custom class.</span></span> <span data-ttu-id="2192c-116">相反地，當使用虛擬函式時，已註冊的類別其實不過是<xref:System.Windows.UIElement>基底類別。</span><span class="sxs-lookup"><span data-stu-id="2192c-116">In contrast, when using the virtuals, the registered class is really the <xref:System.Windows.UIElement> base class.</span></span> <span data-ttu-id="2192c-117">在基底類別和子類別中每個註冊類別處理的情況下，子類別處理常式會最先叫用。</span><span class="sxs-lookup"><span data-stu-id="2192c-117">In cases where base classes and subclass each register class handling, the subclass handlers are invoked first.</span></span> <span data-ttu-id="2192c-118">這個處理常式會先顯示它的訊息方塊，則會顯示虛擬方法的處理常式中的視覺化變更是在應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="2192c-118">The behavior in an application would be that first this handler would show its message box and then the visual change in the virtual method's handler would be shown.</span></span>  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a><span data-ttu-id="2192c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2192c-119">See also</span></span>

- <xref:System.Windows.EventManager>
- [<span data-ttu-id="2192c-120">將路由事件標記為已處理以及類別處理</span><span class="sxs-lookup"><span data-stu-id="2192c-120">Marking Routed Events as Handled, and Class Handling</span></span>](marking-routed-events-as-handled-and-class-handling.md)
- [<span data-ttu-id="2192c-121">處理路由事件</span><span class="sxs-lookup"><span data-stu-id="2192c-121">Handle a Routed Event</span></span>](how-to-handle-a-routed-event.md)
- [<span data-ttu-id="2192c-122">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="2192c-122">Routed Events Overview</span></span>](routed-events-overview.md)
