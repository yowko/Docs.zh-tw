---
title: 事件簡介
description: 透過此概觀了解 .NET Core 中的事件，以及事件的語言設計目標。
ms.date: 06/20/2016
ms.assetid: 9b8d2a00-1584-4a5b-8994-5003d54d8e0c
ms.openlocfilehash: ceae2b9319a1de9f01102987735c7db2c2883f18
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138527"
---
# <a name="introduction-to-events"></a><span data-ttu-id="7cb56-103">事件簡介</span><span class="sxs-lookup"><span data-stu-id="7cb56-103">Introduction to events</span></span>

[<span data-ttu-id="7cb56-104">上一篇</span><span class="sxs-lookup"><span data-stu-id="7cb56-104">Previous</span></span>](delegates-patterns.md)

<span data-ttu-id="7cb56-105">事件就像委派，是「晚期繫結」機制。</span><span class="sxs-lookup"><span data-stu-id="7cb56-105">Events are, like delegates, a *late binding* mechanism.</span></span> <span data-ttu-id="7cb56-106">事實上，事件是建立在委派的語言支援上。</span><span class="sxs-lookup"><span data-stu-id="7cb56-106">In fact, events are built on the language support for delegates.</span></span>

<span data-ttu-id="7cb56-107">事件一種物件 (向系統中所有感興趣的元件) 廣播有事發生的方式。</span><span class="sxs-lookup"><span data-stu-id="7cb56-107">Events are a way for an object to broadcast (to all interested components in the system) that something has happened.</span></span> <span data-ttu-id="7cb56-108">任何其他元件皆可以訂閱事件，並在引發事件時收到通知。</span><span class="sxs-lookup"><span data-stu-id="7cb56-108">Any other component can subscribe to the event, and be notified when an event is raised.</span></span>

<span data-ttu-id="7cb56-109">您可能在自己的某些程式設計中使用過事件。</span><span class="sxs-lookup"><span data-stu-id="7cb56-109">You've probably used events in some of your programming.</span></span> <span data-ttu-id="7cb56-110">許多圖形系統都有報告使用者互動的事件模型。</span><span class="sxs-lookup"><span data-stu-id="7cb56-110">Many graphical systems have an event model to report user interaction.</span></span> <span data-ttu-id="7cb56-111">這些事件會報告滑鼠移動、按下按鈕和類似的互動。</span><span class="sxs-lookup"><span data-stu-id="7cb56-111">These events would report mouse movement, button presses and similar interactions.</span></span> <span data-ttu-id="7cb56-112">這是其中最常見的，但不是使用事件的唯一狀況。</span><span class="sxs-lookup"><span data-stu-id="7cb56-112">That's one of the most common, but certainly not the only scenario where events are used.</span></span>

<span data-ttu-id="7cb56-113">您可以為您的類別定義應該引發的事件。</span><span class="sxs-lookup"><span data-stu-id="7cb56-113">You can define events that should be raised for your classes.</span></span> <span data-ttu-id="7cb56-114">處理事件時有一項重要考量，就是特定事件可能沒有任何登錄的物件。</span><span class="sxs-lookup"><span data-stu-id="7cb56-114">One important consideration when working with events is that there may not be any object registered for a particular event.</span></span> <span data-ttu-id="7cb56-115">您必須撰寫程式碼，讓它在未設定任何接聽程式時不會引發事件。</span><span class="sxs-lookup"><span data-stu-id="7cb56-115">You must write your code so that it does not raise events when no listeners are configured.</span></span>

<span data-ttu-id="7cb56-116">訂閱事件也會建立兩個物件 (事件來源和事件接收) 的結合程度。</span><span class="sxs-lookup"><span data-stu-id="7cb56-116">Subscribing to an event also creates a coupling between two objects (the event source, and the event sink).</span></span> <span data-ttu-id="7cb56-117">您需要確保，對事件不再感興趣時，事件接收會取消訂閱事件來源。</span><span class="sxs-lookup"><span data-stu-id="7cb56-117">You need to ensure that the event sink unsubscribes from the event source when no longer interested in events.</span></span>

## <a name="design-goals-for-event-support"></a><span data-ttu-id="7cb56-118">事件支援的設計目標</span><span class="sxs-lookup"><span data-stu-id="7cb56-118">Design goals for event support</span></span>

<span data-ttu-id="7cb56-119">事件的語言設計以下列目標為目標：</span><span class="sxs-lookup"><span data-stu-id="7cb56-119">The language design for events targets these goals:</span></span>

- <span data-ttu-id="7cb56-120">在事件來源與事件接收器之間啟用極少的結合。</span><span class="sxs-lookup"><span data-stu-id="7cb56-120">Enable very minimal coupling between an event source and an event sink.</span></span> <span data-ttu-id="7cb56-121">這兩個元件可能不是由相同的組織所撰寫，甚至可能依完全不同的排程更新。</span><span class="sxs-lookup"><span data-stu-id="7cb56-121">These two components may not be written by the same organization, and may even be updated on totally different schedules.</span></span>

- <span data-ttu-id="7cb56-122">訂閱事件和取消訂閱該相同事件應該非常簡單。</span><span class="sxs-lookup"><span data-stu-id="7cb56-122">It should be very simple to subscribe to an event, and to unsubscribe from that same event.</span></span>

- <span data-ttu-id="7cb56-123">事件來源應該支援多個事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="7cb56-123">Event sources should support multiple event subscribers.</span></span> <span data-ttu-id="7cb56-124">它也應該支援不附加任何事件訂閱者。</span><span class="sxs-lookup"><span data-stu-id="7cb56-124">It should also support having no event subscribers attached.</span></span>

<span data-ttu-id="7cb56-125">您可以看到事件的目標與委派的目標非常相似。</span><span class="sxs-lookup"><span data-stu-id="7cb56-125">You can see that the goals for events are very similar to the goals for delegates.</span></span>
<span data-ttu-id="7cb56-126">這就是事件語言支援建立在委派語言支援上的原因。</span><span class="sxs-lookup"><span data-stu-id="7cb56-126">That's why the event language support is built on the delegate language support.</span></span>

## <a name="language-support-for-events"></a><span data-ttu-id="7cb56-127">事件的語言支援</span><span class="sxs-lookup"><span data-stu-id="7cb56-127">Language support for events</span></span>

<span data-ttu-id="7cb56-128">定義事件以及訂閱或取消訂閱事件的語法，是委派的語法延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7cb56-128">The syntax for defining events, and subscribing or unsubscribing from events is an extension of the syntax for delegates.</span></span>

<span data-ttu-id="7cb56-129">若要定義事件請使用 `event` 關鍵字︰</span><span class="sxs-lookup"><span data-stu-id="7cb56-129">To define an event you use the `event` keyword:</span></span>

```csharp
public event EventHandler<FileListArgs> Progress;
```

<span data-ttu-id="7cb56-130">事件類型 (本例中為 `EventHandler<FileListArgs>`) 必須是委派類型。</span><span class="sxs-lookup"><span data-stu-id="7cb56-130">The type of the event (`EventHandler<FileListArgs>` in this example) must be a delegate type.</span></span> <span data-ttu-id="7cb56-131">宣告事件時應該遵循一些慣例。</span><span class="sxs-lookup"><span data-stu-id="7cb56-131">There are a number of conventions that you should follow when declaring an event.</span></span> <span data-ttu-id="7cb56-132">一般而言，事件委派類型具有 void 傳回。</span><span class="sxs-lookup"><span data-stu-id="7cb56-132">Typically, the event delegate type has a void return.</span></span>
<span data-ttu-id="7cb56-133">事件宣告應該是動詞或動詞片語。</span><span class="sxs-lookup"><span data-stu-id="7cb56-133">Event declarations should be a verb, or a verb phrase.</span></span>
<span data-ttu-id="7cb56-134">當附隨報告已發生的專案時，請使用過去的時態。</span><span class="sxs-lookup"><span data-stu-id="7cb56-134">Use past tense when the event reports something that has happened.</span></span> <span data-ttu-id="7cb56-135">報告將要發生的事件時，請使用現在式動詞 (例如，`Closing`)。</span><span class="sxs-lookup"><span data-stu-id="7cb56-135">Use a present tense verb (for example, `Closing`) to report something that is about to happen.</span></span> <span data-ttu-id="7cb56-136">通常使用現在式是表示您的類別支援某類的自訂行為。</span><span class="sxs-lookup"><span data-stu-id="7cb56-136">Often, using present tense indicates that your class supports some kind of customization behavior.</span></span> <span data-ttu-id="7cb56-137">最常見的情況之一就是支援取消。</span><span class="sxs-lookup"><span data-stu-id="7cb56-137">One of the most common scenarios is to support cancellation.</span></span> <span data-ttu-id="7cb56-138">例如，`Closing` 事件可包括一個引數，指出關閉作業是否應該繼續。</span><span class="sxs-lookup"><span data-stu-id="7cb56-138">For example, a `Closing` event may include an argument that would indicate if the close operation should continue, or not.</span></span>  <span data-ttu-id="7cb56-139">其他情況可讓呼叫端更新事件引數的屬性以修改行為。</span><span class="sxs-lookup"><span data-stu-id="7cb56-139">Other scenarios may enable callers to modify behavior by updating properties of the event arguments.</span></span> <span data-ttu-id="7cb56-140">您可引發事件，指出演算法會採用的下一個提議動作。</span><span class="sxs-lookup"><span data-stu-id="7cb56-140">You may raise an event to indicate a proposed next action an algorithm will take.</span></span> <span data-ttu-id="7cb56-141">事件處理常式可透過修改事件引數的屬性來要求不同的動作。</span><span class="sxs-lookup"><span data-stu-id="7cb56-141">The event handler may mandate a different action by modifying  properties of the event argument.</span></span>

<span data-ttu-id="7cb56-142">當您想要引發事件時，可使用委派引動過程語法呼叫事件處理常式︰</span><span class="sxs-lookup"><span data-stu-id="7cb56-142">When you want to raise the event, you call the event handlers using the delegate invocation syntax:</span></span>

```csharp
Progress?.Invoke(this, new FileListArgs(file));
```

<span data-ttu-id="7cb56-143">如上一節中討論的[委派](delegates-patterns.md)，?。</span><span class="sxs-lookup"><span data-stu-id="7cb56-143">As discussed in the section on [delegates](delegates-patterns.md), the ?.</span></span>
<span data-ttu-id="7cb56-144">當該事件沒有訂閱者時，運算子讓您輕鬆確定不用嘗試引發事件。</span><span class="sxs-lookup"><span data-stu-id="7cb56-144">operator makes it easy to ensure that you do not attempt to raise the event when there are no subscribers to that event.</span></span>
 
<span data-ttu-id="7cb56-145">使用 `+=` 運算子訂閱事件︰</span><span class="sxs-lookup"><span data-stu-id="7cb56-145">You subscribe to an event by using the `+=` operator:</span></span>

```csharp
EventHandler<FileListArgs> onProgress = (sender, eventArgs) => 
    Console.WriteLine(eventArgs.FoundFile);

fileLister.Progress += onProgress;
```

<span data-ttu-id="7cb56-146">處理常式方法的前置詞前面通常會加上事件名稱，如上所示。</span><span class="sxs-lookup"><span data-stu-id="7cb56-146">The handler method typically has the prefix 'On' followed by the event name, as shown above.</span></span>

<span data-ttu-id="7cb56-147">使用 `-=` 運算子取消訂閱事件：</span><span class="sxs-lookup"><span data-stu-id="7cb56-147">You unsubscribe using the `-=` operator:</span></span>

```csharp
fileLister.Progress -= onProgress;
```

<span data-ttu-id="7cb56-148">請務必注意，我宣告了表示事件處理常式的運算式區域變數。</span><span class="sxs-lookup"><span data-stu-id="7cb56-148">It's important to note that I declared a local variable for the expression that represents the event handler.</span></span> <span data-ttu-id="7cb56-149">這可確保取消訂閱移除處理常式。</span><span class="sxs-lookup"><span data-stu-id="7cb56-149">That ensures the unsubscribe removes the handler.</span></span>
<span data-ttu-id="7cb56-150">但若改用 Lambda 運算式的主體，就要嘗試移除永遠不會附加的處理常式，其不執行任何作業。</span><span class="sxs-lookup"><span data-stu-id="7cb56-150">If, instead, you used the body of the lambda expression, you are attempting to remove a handler that has never been attached, which does nothing.</span></span>

<span data-ttu-id="7cb56-151">在下一篇文章中，您會深入了解一般的事件模式，以及本例的不同變化。</span><span class="sxs-lookup"><span data-stu-id="7cb56-151">In the next article, you'll learn more about typical event patterns, and different variations on this example.</span></span>

[<span data-ttu-id="7cb56-152">下一步</span><span class="sxs-lookup"><span data-stu-id="7cb56-152">Next</span></span>](event-pattern.md)
