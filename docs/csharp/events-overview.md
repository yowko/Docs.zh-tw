---
title: "事件簡介"
description: "透過此概觀了解 .NET Core 中的事件，以及事件的語言設計目標。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: f81c2d9fc2ec69c295485fe06029b5de65335db0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-events"></a><span data-ttu-id="30390-104">事件簡介</span><span class="sxs-lookup"><span data-stu-id="30390-104">Introduction to Events</span></span>

[<span data-ttu-id="30390-105">上一篇</span><span class="sxs-lookup"><span data-stu-id="30390-105">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="30390-106">事件就像委派，是「晚期繫結」機制。</span><span class="sxs-lookup"><span data-stu-id="30390-106">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="30390-107">事實上，事件是建立在委派的語言支援上。</span><span class="sxs-lookup"><span data-stu-id="30390-107">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="30390-108">事件一種物件 (向系統中所有感興趣的元件) 廣播有事發生的方式。</span><span class="sxs-lookup"><span data-stu-id="30390-108">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="30390-109">任何其他元件皆可以訂閱事件，並在引發事件時收到通知。</span><span class="sxs-lookup"><span data-stu-id="30390-109">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="30390-110">您可能在自己的某些程式設計中使用過事件。</span><span class="sxs-lookup"><span data-stu-id="30390-110">You've probably used events in some of your programming.</span></span> <span data-ttu-id="30390-111">許多圖形系統都有報告使用者互動的事件模型。</span><span class="sxs-lookup"><span data-stu-id="30390-111">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="30390-112">這些事件會報告滑鼠移動、按下按鈕和類似的互動。</span><span class="sxs-lookup"><span data-stu-id="30390-112">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="30390-113">這是其中最常見的，但不是使用事件的唯一狀況。</span><span class="sxs-lookup"><span data-stu-id="30390-113">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="30390-114">您可以為您的類別定義應該引發的事件。</span><span class="sxs-lookup"><span data-stu-id="30390-114">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="30390-115">處理事件時有一項重要考量，就是特定事件可能沒有任何登錄的物件。</span><span class="sxs-lookup"><span data-stu-id="30390-115">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="30390-116">您必須撰寫程式碼，讓它在未設定任何接聽程式時不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="30390-116">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="30390-117">訂閱事件也會建立兩個物件 (事件來源和事件接收) 的結合程度。</span><span class="sxs-lookup"><span data-stu-id="30390-117">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="30390-118">您需要確保，對事件不再感興趣時，事件接收會取消訂閱事件來源。</span><span class="sxs-lookup"><span data-stu-id="30390-118">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="30390-119">事件支援的設計目標</span><span class="sxs-lookup"><span data-stu-id="30390-119">Design Goals for Event Support</span></span>

<span data-ttu-id="30390-120">事件的語言設計有這些目標。</span><span class="sxs-lookup"><span data-stu-id="30390-120">The language design for events targets these goals.</span></span>

<span data-ttu-id="30390-121">首先，讓事件來源和事件接收之間的結合程度降至最低。</span><span class="sxs-lookup"><span data-stu-id="30390-121">First, enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="30390-122">這兩個元件可能不是由相同的組織所撰寫，甚至可能依完全不同的排程更新。</span><span class="sxs-lookup"><span data-stu-id="30390-122">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

<span data-ttu-id="30390-123">其次，訂閱事件應該非常簡單，取消訂閱相同事件也一樣。</span><span class="sxs-lookup"><span data-stu-id="30390-123">Secondly, it should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

<span data-ttu-id="30390-124">最後，事件來源應該支援多個事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="30390-124">And finally, event sources should support multiple event subscribers.</span></span> <span data-ttu-id="30390-125">它也應該支援不附加任何事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="30390-125">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="30390-126">您可以看到事件的目標與委派的目標非常相似。</span><span class="sxs-lookup"><span data-stu-id="30390-126">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="30390-127">這就是事件語言支援建立在委派語言支援上的原因。</span><span class="sxs-lookup"><span data-stu-id="30390-127">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="30390-128">事件語言支援</span><span class="sxs-lookup"><span data-stu-id="30390-128">Language Support for Events</span></span>

<span data-ttu-id="30390-129">定義事件以及訂閱或取消訂閱事件的語法，是委派的語法延伸模組。</span><span class="sxs-lookup"><span data-stu-id="30390-129">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="30390-130">若要定義事件請使用 `event` 關鍵字︰</span><span class="sxs-lookup"><span data-stu-id="30390-130">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="30390-131">事件類型 (本例中為 `EventHandler<FileListArgs>`) 必須是委派類型。</span><span class="sxs-lookup"><span data-stu-id="30390-131">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="30390-132">宣告事件時應該遵循一些慣例。</span><span class="sxs-lookup"><span data-stu-id="30390-132">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="30390-133">一般而言，事件委派類型具有 void 傳回。</span><span class="sxs-lookup"><span data-stu-id="30390-133">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="30390-134">事件宣告應該是動詞或動詞片語。</span><span class="sxs-lookup"><span data-stu-id="30390-134">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="30390-135">當事件報告發生過事件時，請使用過去式 (如本例)。</span><span class="sxs-lookup"><span data-stu-id="30390-135">Use past tense (as in this example) when the event reports something that has happened.</span></span> <span data-ttu-id="30390-136">報告將要發生的事件時，請使用現在式動詞 (例如，`Closing`)。</span><span class="sxs-lookup"><span data-stu-id="30390-136">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="30390-137">通常使用現在式是表示您的類別支援某類的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="30390-137">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="30390-138">最常見的情況之一就是支援取消。</span><span class="sxs-lookup"><span data-stu-id="30390-138">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="30390-139">例如，`Closing` 事件可包括一個引數，指出關閉作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="30390-139">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="30390-140">其他情況可讓呼叫端更新事件引數的屬性以修改行為。</span><span class="sxs-lookup"><span data-stu-id="30390-140">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="30390-141">您可引發事件，指出演算法會採用的下一個提議動作。</span><span class="sxs-lookup"><span data-stu-id="30390-141">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="30390-142">事件處理常式可透過修改事件引數的屬性來要求不同的動作。</span><span class="sxs-lookup"><span data-stu-id="30390-142">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="30390-143">當您想要引發事件時，可使用委派引動過程語法呼叫事件處理常式︰</span><span class="sxs-lookup"><span data-stu-id="30390-143">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="30390-144">如上一節中討論的[委派](delegates-patterns.md)，?。</span><span class="sxs-lookup"><span data-stu-id="30390-144">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="30390-145">當該事件沒有訂閱者時，運算子讓您輕鬆確定不用嘗試引發事件。</span><span class="sxs-lookup"><span data-stu-id="30390-145">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="30390-146">使用 `+=` 運算子訂閱事件︰</span><span class="sxs-lookup"><span data-stu-id="30390-146">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);
lister.Progress += OnProgress;
```

<span data-ttu-id="30390-147">處理常式方法通常是前置詞 'On' 後面接事件名稱，如上所示。</span><span class="sxs-lookup"><span data-stu-id="30390-147">The handler method typically is the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="30390-148">使用 `-=` 運算子取消訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="30390-148">You unsubscribe using the `-=` operator:</span></span>

```csharp
lister.Progress -= onProgress;
```

<span data-ttu-id="30390-149">請務必注意，我宣告了表示事件處理常式的運算式區域變數。</span><span class="sxs-lookup"><span data-stu-id="30390-149">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="30390-150">這可確保取消訂閱移除處理常式。</span><span class="sxs-lookup"><span data-stu-id="30390-150">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="30390-151">但若改用 Lambda 運算式的主體，就要嘗試移除永遠不會附加的處理常式，其不執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="30390-151">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="30390-152">在下一篇文章中，您會深入了解一般的事件模式，以及本例的不同變化。</span><span class="sxs-lookup"><span data-stu-id="30390-152">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="30390-153">下一篇</span><span class="sxs-lookup"><span data-stu-id="30390-153">Next</span></span>](event-pattern.md)
