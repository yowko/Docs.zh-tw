---
title: 事件 - C# 程式設計手冊
description: 瞭解事件。 事件可讓類別或物件在某些相關的事情發生時，告知其他類別或物件。
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 86ded81de4b9191c50b993c08b0e87712ff69020
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545489"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="0a7c7-104">事件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="0a7c7-104">Events (C# Programming Guide)</span></span>
<span data-ttu-id="0a7c7-105">事件可讓 [類別](../../language-reference/keywords/class.md) 或物件在某些相關的事情發生時，告知其他類別或物件。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-105">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="0a7c7-106">傳送 (或 *引發*) 事件的類別稱為「 *發行者* 」，以及接收 (或 *處理*) 事件的類別，稱為「 *訂閱者*」。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-106">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="0a7c7-107">在典型的 C# Windows Forms 或 Web 應用程式中，您可訂閱由控制項 (如按鈕和清單方塊) 引發的事件。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-107">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="0a7c7-108">您可以使用 Visual C# 整合式開發環境 (IDE) 來瀏覽控制項發行的事件，並選擇您想要處理的事件。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-108">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="0a7c7-109">IDE 提供一種簡單的方式來自動新增空的事件處理常式方法，及用來訂閱該事件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-109">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="0a7c7-110">如需詳細資訊，請參閱 [如何訂閱和取消訂閱事件](./how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-110">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="0a7c7-111">事件概觀</span><span class="sxs-lookup"><span data-stu-id="0a7c7-111">Events Overview</span></span>  
 <span data-ttu-id="0a7c7-112">事件有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="0a7c7-112">Events have the following properties:</span></span>  
  
- <span data-ttu-id="0a7c7-113">發行者會判斷引發事件的時間，而訂閱者則決定要採取什麼動作來回應該事件。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-113">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="0a7c7-114">一個事件可以有多個訂閱者，</span><span class="sxs-lookup"><span data-stu-id="0a7c7-114">An event can have multiple subscribers.</span></span> <span data-ttu-id="0a7c7-115">而訂閱者可以處理來自多個發行者的多個事件。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-115">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="0a7c7-116">沒有訂閱者的事件永遠不會被引發。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-116">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="0a7c7-117">事件通常用於對使用者的動作 (例如在圖形化使用者介面內按一下按鈕或選取功能表) 發出信號。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-117">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="0a7c7-118">當某事件擁有多個訂閱者時，便會在事件引發的同時叫用事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-118">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="0a7c7-119">若要以非同步方式叫用事件，請參閱 [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-119">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="0a7c7-120">在 .NET 類別庫中，事件是以 <xref:System.EventHandler> 委派和基類為基礎 <xref:System.EventArgs> 。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-120">In the .NET class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0a7c7-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="0a7c7-121">Related Sections</span></span>  
 <span data-ttu-id="0a7c7-122">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="0a7c7-122">For more information, see:</span></span>  
  
- [<span data-ttu-id="0a7c7-123">如何訂閱及取消訂閱事件</span><span class="sxs-lookup"><span data-stu-id="0a7c7-123">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="0a7c7-124">如何發佈符合 .NET 指導方針的事件</span><span class="sxs-lookup"><span data-stu-id="0a7c7-124">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="0a7c7-125">如何在衍生類別中引發基底類別事件</span><span class="sxs-lookup"><span data-stu-id="0a7c7-125">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="0a7c7-126">如何實作介面事件</span><span class="sxs-lookup"><span data-stu-id="0a7c7-126">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="0a7c7-127">如何實作自訂事件存取子</span><span class="sxs-lookup"><span data-stu-id="0a7c7-127">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="0a7c7-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0a7c7-128">C# Language Specification</span></span>  

<span data-ttu-id="0a7c7-129">如需詳細資訊，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)中的[事件](~/_csharplang/spec/classes.md#events)。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-129">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="0a7c7-130">語言規格是 C# 語法及用法的限定來源。</span><span class="sxs-lookup"><span data-stu-id="0a7c7-130">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="0a7c7-131">精選書籍章節</span><span class="sxs-lookup"><span data-stu-id="0a7c7-131">Featured Book Chapters</span></span>  
 <span data-ttu-id="0a7c7-132">[C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) (C# 3.0 Cookbook 第三版：250 個以上 C# 3.0 程式設計人員適用的方案) 中的 [Delegates, Events, and Lambda Expressions](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="0a7c7-132">[Delegates, Events, and Lambda Expressions](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span></span>  
  
 <span data-ttu-id="0a7c7-133">[Delegates and Events](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) in [Learning C# 3.0: Master the fundamentals of C# 3.0](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="0a7c7-133">[Delegates and Events](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) in [Learning C# 3.0: Master the fundamentals of C# 3.0](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a7c7-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a7c7-134">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="0a7c7-135">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0a7c7-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0a7c7-136">委派</span><span class="sxs-lookup"><span data-stu-id="0a7c7-136">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="0a7c7-137">在 Windows Form 中建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="0a7c7-137">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
