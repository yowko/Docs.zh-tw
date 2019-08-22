---
title: 事件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 7a8a8e6b6a393f151d69d1879f475e04f44df5fa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590376"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="6e23d-102">事件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6e23d-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="6e23d-103">事件可讓 [類別](../../language-reference/keywords/class.md) 或物件在某些相關的事情發生時，告知其他類別或物件。</span><span class="sxs-lookup"><span data-stu-id="6e23d-103">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="6e23d-104">傳送 (或 *「引發」* (raise)) 事件的類別稱為 *「發行者」* (publisher)，而接收 (或 *「處理」* (handle)) 事件的類別則稱為 *「訂閱者」* (subscriber)。</span><span class="sxs-lookup"><span data-stu-id="6e23d-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="6e23d-105">在典型的 C# Windows Forms 或 Web 應用程式中，您可訂閱由控制項 (如按鈕和清單方塊) 引發的事件。</span><span class="sxs-lookup"><span data-stu-id="6e23d-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="6e23d-106">您可以使用 Visual C# 整合式開發環境 (IDE) 來瀏覽控制項發行的事件，並選擇您想要處理的事件。</span><span class="sxs-lookup"><span data-stu-id="6e23d-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="6e23d-107">IDE 提供一種簡單的方式來自動新增空的事件處理常式方法，及用來訂閱該事件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6e23d-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="6e23d-108">如需詳細資訊，請參閱[如何：訂閱及取消訂閱事件](./how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="6e23d-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="6e23d-109">事件概觀</span><span class="sxs-lookup"><span data-stu-id="6e23d-109">Events Overview</span></span>  
 <span data-ttu-id="6e23d-110">事件有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6e23d-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="6e23d-111">發行者會判斷引發事件的時間，而訂閱者則決定要採取什麼動作來回應該事件。</span><span class="sxs-lookup"><span data-stu-id="6e23d-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="6e23d-112">一個事件可以有多個訂閱者，</span><span class="sxs-lookup"><span data-stu-id="6e23d-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="6e23d-113">而訂閱者可以處理來自多個發行者的多個事件。</span><span class="sxs-lookup"><span data-stu-id="6e23d-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="6e23d-114">沒有訂閱者的事件永遠不會被引發。</span><span class="sxs-lookup"><span data-stu-id="6e23d-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="6e23d-115">事件通常用於對使用者的動作 (例如在圖形化使用者介面內按一下按鈕或選取功能表) 發出信號。</span><span class="sxs-lookup"><span data-stu-id="6e23d-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="6e23d-116">當某事件擁有多個訂閱者時，便會在事件引發的同時叫用事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6e23d-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="6e23d-117">若要以非同步方式叫用事件，請參閱 [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="6e23d-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="6e23d-118">在 .NET Framework 類別庫中，事件取決於 <xref:System.EventHandler> 委派以及 <xref:System.EventArgs> 基底類別。</span><span class="sxs-lookup"><span data-stu-id="6e23d-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6e23d-119">相關章節</span><span class="sxs-lookup"><span data-stu-id="6e23d-119">Related Sections</span></span>  
 <span data-ttu-id="6e23d-120">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="6e23d-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="6e23d-121">如何：訂閱及取消訂閱事件</span><span class="sxs-lookup"><span data-stu-id="6e23d-121">How to: Subscribe to and Unsubscribe from Events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
- [<span data-ttu-id="6e23d-122">如何：發行符合 .NET Framework 指導方針的事件</span><span class="sxs-lookup"><span data-stu-id="6e23d-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
- [<span data-ttu-id="6e23d-123">如何：在衍生類別中引發基底類別事件</span><span class="sxs-lookup"><span data-stu-id="6e23d-123">How to: Raise Base Class Events in Derived Classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)  
  
- [<span data-ttu-id="6e23d-124">如何：實作介面事件</span><span class="sxs-lookup"><span data-stu-id="6e23d-124">How to:  Implement Interface Events</span></span>](./how-to-implement-interface-events.md)  
  
- [<span data-ttu-id="6e23d-125">如何：實作自訂事件存取子</span><span class="sxs-lookup"><span data-stu-id="6e23d-125">How to: Implement Custom Event Accessors</span></span>](./how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6e23d-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6e23d-126">C# Language Specification</span></span>  

<span data-ttu-id="6e23d-127">如需詳細資訊，請參閱 [C# 語言規格](../../language-reference/language-specification/index.md)中的[事件](~/_csharplang/spec/classes.md#events)。</span><span class="sxs-lookup"><span data-stu-id="6e23d-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="6e23d-128">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="6e23d-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="6e23d-129">精選書籍章節</span><span class="sxs-lookup"><span data-stu-id="6e23d-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="6e23d-130">[C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)中的[委派、事件與 Lambda 運算式](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="6e23d-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="6e23d-131">[了解 C# 3.0：掌握 C# 3.0 的基本概念](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)中的[委派與事件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="6e23d-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e23d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6e23d-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="6e23d-133">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6e23d-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6e23d-134">委派</span><span class="sxs-lookup"><span data-stu-id="6e23d-134">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="6e23d-135">在 Windows Forms 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="6e23d-135">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
