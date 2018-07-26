---
title: 事件 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 5b844b20ac62b4cbc2a73931eecab95f22b4b1de
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199439"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="3fec4-102">事件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3fec4-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="3fec4-103">事件可讓 [類別](../../../csharp/language-reference/keywords/class.md) 或物件在某些相關的事情發生時，告知其他類別或物件。</span><span class="sxs-lookup"><span data-stu-id="3fec4-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="3fec4-104">傳送 (或 *「引發」*(raise)) 事件的類別稱為 *「發行者」* (publisher)，而接收 (或 *「處理」*(handle)) 事件的類別則稱為 *「訂閱者」*(subscriber)。</span><span class="sxs-lookup"><span data-stu-id="3fec4-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="3fec4-105">在典型的 C# Windows Forms 或 Web 應用程式中，您可訂閱由控制項 (如按鈕和清單方塊) 引發的事件。</span><span class="sxs-lookup"><span data-stu-id="3fec4-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="3fec4-106">您可以使用 Visual C# 整合式開發環境 (IDE) 來瀏覽控制項發行的事件，並選擇您想要處理的事件。</span><span class="sxs-lookup"><span data-stu-id="3fec4-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="3fec4-107">IDE 會自動新增空的事件處理常式方法和程式碼，以訂閱該事件。</span><span class="sxs-lookup"><span data-stu-id="3fec4-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="3fec4-108">如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec4-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="3fec4-109">事件概觀</span><span class="sxs-lookup"><span data-stu-id="3fec4-109">Events Overview</span></span>  
 <span data-ttu-id="3fec4-110">事件有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="3fec4-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="3fec4-111">發行者會判斷引發事件的時間，而訂閱者則決定要採取什麼動作來回應該事件。</span><span class="sxs-lookup"><span data-stu-id="3fec4-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="3fec4-112">一個事件可以有多個訂閱者，</span><span class="sxs-lookup"><span data-stu-id="3fec4-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="3fec4-113">而訂閱者可以處理來自多個發行者的多個事件。</span><span class="sxs-lookup"><span data-stu-id="3fec4-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="3fec4-114">沒有訂閱者的事件永遠不會被引發。</span><span class="sxs-lookup"><span data-stu-id="3fec4-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="3fec4-115">事件通常用於對使用者的動作 (例如在圖形化使用者介面內按一下按鈕或選取功能表) 發出信號。</span><span class="sxs-lookup"><span data-stu-id="3fec4-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="3fec4-116">當某事件擁有多個訂閱者時，便會在事件引發的同時叫用事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="3fec4-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="3fec4-117">若要以非同步方式叫用事件，請參閱 [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="3fec4-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="3fec4-118">在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 類別庫中，事件會以 <xref:System.EventHandler> 委派和 <xref:System.EventArgs> 基底類別為基礎。</span><span class="sxs-lookup"><span data-stu-id="3fec4-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3fec4-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="3fec4-119">Related Sections</span></span>  
 <span data-ttu-id="3fec4-120">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="3fec4-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3fec4-121">如何：訂閱及取消訂閱事件</span><span class="sxs-lookup"><span data-stu-id="3fec4-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="3fec4-122">如何：發行符合 .NET Framework 方針的事件</span><span class="sxs-lookup"><span data-stu-id="3fec4-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="3fec4-123">如何：在衍生類別中引發基底類別事件</span><span class="sxs-lookup"><span data-stu-id="3fec4-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="3fec4-124">如何：實作介面事件</span><span class="sxs-lookup"><span data-stu-id="3fec4-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="3fec4-125">執行緒同步處理</span><span class="sxs-lookup"><span data-stu-id="3fec4-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="3fec4-126">如何：使用字典儲存事件執行個體</span><span class="sxs-lookup"><span data-stu-id="3fec4-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="3fec4-127">如何：實作自訂事件存取子</span><span class="sxs-lookup"><span data-stu-id="3fec4-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3fec4-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="3fec4-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="3fec4-129">精選書籍章節</span><span class="sxs-lookup"><span data-stu-id="3fec4-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="3fec4-130">[C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) (C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案) 中的 [Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="3fec4-130">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
 <span data-ttu-id="3fec4-131">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="3fec4-131">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fec4-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="3fec4-132">See Also</span></span>  
 <xref:System.EventHandler>  
 [<span data-ttu-id="3fec4-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3fec4-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3fec4-134">委派</span><span class="sxs-lookup"><span data-stu-id="3fec4-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="3fec4-135">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="3fec4-135">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="3fec4-136">使用事件架構非同步模式設計多執行緒程式</span><span class="sxs-lookup"><span data-stu-id="3fec4-136">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
