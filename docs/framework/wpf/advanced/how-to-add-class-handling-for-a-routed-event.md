---
title: "如何：加入路由事件的類別處理"
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
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abbbdce0ca12c4d8bdd12f616bf49c3d6f66f441
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a><span data-ttu-id="1f5d8-102">如何：加入路由事件的類別處理</span><span class="sxs-lookup"><span data-stu-id="1f5d8-102">How to: Add Class Handling for a Routed Event</span></span>
<span data-ttu-id="1f5d8-103">依類別處理常式或路由中任何指定節點上的執行個體處理常式可以處理路由的事件。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-103">Routed events can be handled either by class handlers or instance handlers on any given node in the route.</span></span> <span data-ttu-id="1f5d8-104">首先，叫用與可用由類別實作來隱藏執行個體處理的事件，或引進其他事件的特定行為的基底類別所擁有的事件類別處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-104">Class handlers are invoked first, and can be used by class implementations to suppress events from instance handling or introduce other event specific behaviors on events that are owned by base classes.</span></span> <span data-ttu-id="1f5d8-105">此範例說明兩種密切相關的技術，實作類別處理常式。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-105">This example illustrates two closely related techniques for implementing class handlers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f5d8-106">範例</span><span class="sxs-lookup"><span data-stu-id="1f5d8-106">Example</span></span>  
 <span data-ttu-id="1f5d8-107">這個範例會使用為基礎的自訂類別<xref:System.Windows.Controls.Canvas>面板。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-107">This example uses a custom class based on the <xref:System.Windows.Controls.Canvas> panel.</span></span> <span data-ttu-id="1f5d8-108">應用程式的基本前提是自訂類別引進了其子項目，包括攔截任何滑鼠左鍵按一下和標示為已處理，才能將叫用子系項目類別或在其上的任何執行個體處理常式上的行為。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-108">The basic premise of the application is that the custom class introduces behaviors on its child elements, including intercepting any left mouse button clicks and marking them handled, before the child element class or any instance handlers on it will be invoked.</span></span>  
  
 <span data-ttu-id="1f5d8-109"><xref:System.Windows.UIElement>類別公開的虛擬方法，可讓類別處理<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>事件，只覆寫事件。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-109">The <xref:System.Windows.UIElement> class exposes a virtual method that enables class handling on the <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> event, by simply overriding the event.</span></span> <span data-ttu-id="1f5d8-110">這是最簡單的方式來實作類別處理，如果您的類別階層中某處有虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-110">This is the simplest way to implement class handling if such a virtual method is available somewhere in your class' hierarchy.</span></span> <span data-ttu-id="1f5d8-111">下列程式碼會示範<xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A>"MyEditContainer"衍生自的類別中實作<xref:System.Windows.Controls.Canvas>。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-111">The following code shows the <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementation in the "MyEditContainer" that is derived from <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="1f5d8-112">實作會將事件標記為已處理的引數中，並將某些程式碼，讓來源項目的基本明顯的變更。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-112">The implementation marks the event as handled in the arguments, and then adds some code to give the source element a basic visible change.</span></span>  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 <span data-ttu-id="1f5d8-113">如果沒有虛擬基底類別或針對該特定的方法，可以直接使用的公用程式方法加入類別處理<xref:System.Windows.EventManager>類別<xref:System.Windows.EventManager.RegisterClassHandler%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-113">If no virtual is available on base classes or for that particular method, class handling can be added directly using a utility method of the <xref:System.Windows.EventManager> class, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span></span> <span data-ttu-id="1f5d8-114">這個方法只能呼叫內的靜態初始設定的類別加入類別處理。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-114">This method should only be called within the static initialization of classes that are adding class handling.</span></span> <span data-ttu-id="1f5d8-115">這個範例會將另一個處理常式<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>，而在此情況下已註冊的類別是自訂的類別。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-115">This example adds another handler for <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , and in this case the registered class is the custom class.</span></span> <span data-ttu-id="1f5d8-116">相反地，使用虛擬函式，已註冊的類別時，真正<xref:System.Windows.UIElement>基底類別。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-116">In contrast, when using the virtuals, the registered class is really the <xref:System.Windows.UIElement> base class.</span></span> <span data-ttu-id="1f5d8-117">在基底類別和子類別化每個註冊類別處理的情況下，子類別處理常式會先叫用。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-117">In cases where base classes and subclass each register class handling, the subclass handlers are invoked first.</span></span> <span data-ttu-id="1f5d8-118">應用程式中的行為會是這個處理常式會先顯示其訊息方塊，並接著會顯示虛擬方法的處理常式中的可見變更。</span><span class="sxs-lookup"><span data-stu-id="1f5d8-118">The behavior in an application would be that first this handler would show its message box and then the visual change in the virtual method's handler would be shown.</span></span>  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a><span data-ttu-id="1f5d8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f5d8-119">See Also</span></span>  
 <xref:System.Windows.EventManager>  
 [<span data-ttu-id="1f5d8-120">將路由事件標記為已處理以及類別處理</span><span class="sxs-lookup"><span data-stu-id="1f5d8-120">Marking Routed Events as Handled, and Class Handling</span></span>](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [<span data-ttu-id="1f5d8-121">處理路由事件</span><span class="sxs-lookup"><span data-stu-id="1f5d8-121">Handle a Routed Event</span></span>](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [<span data-ttu-id="1f5d8-122">路由事件概觀</span><span class="sxs-lookup"><span data-stu-id="1f5d8-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
