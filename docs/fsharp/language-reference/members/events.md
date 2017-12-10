---
title: "事件 (F#)"
description: "了解如何 F # 事件可讓您將函式呼叫與使用者動作，也就是很重要的 GUI 程式設計產生關聯。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 28b588f2-0c9e-4c0d-babf-901ed934638a
ms.openlocfilehash: 9465f33bac6fa8234f684ddefe24cbe4d6c71028
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="events"></a><span data-ttu-id="a03e0-104">事件</span><span class="sxs-lookup"><span data-stu-id="a03e0-104">Events</span></span>

> [!NOTE]
<span data-ttu-id="a03e0-105">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="a03e0-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="a03e0-106">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="a03e0-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="a03e0-107">事件可讓您產生函式呼叫與使用者動作的關聯，而且對 GUI 程式設計而言十分重要。</span><span class="sxs-lookup"><span data-stu-id="a03e0-107">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="a03e0-108">事件也可以由應用程式或作業系統觸發。</span><span class="sxs-lookup"><span data-stu-id="a03e0-108">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="a03e0-109">處理事件</span><span class="sxs-lookup"><span data-stu-id="a03e0-109">Handling Events</span></span>
<span data-ttu-id="a03e0-110">當您使用 GUI 程式庫如 Windows Forms 或 Windows Presentation Foundation (WPF) 時，應用程式中的大部分程式碼都會執行以回應程式庫預先定義的事件。</span><span class="sxs-lookup"><span data-stu-id="a03e0-110">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="a03e0-111">這些預先定義的事件是 GUI 類別的成員，例如表單和控制項。</span><span class="sxs-lookup"><span data-stu-id="a03e0-111">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="a03e0-112">您可以參考特定重要具名事件 (例如 `Click` 類別的 `Form` 事件)，以及叫用 `Add` 方法，將自訂行為加入至預先存在的事件 (例如按一下按鈕事件)，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a03e0-112">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="a03e0-113">如果您從 F# Interactive 執行此程式碼，請省略 `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a03e0-113">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="a03e0-114">`Add` 方法的類型為 `('a -> unit) -> unit`。</span><span class="sxs-lookup"><span data-stu-id="a03e0-114">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="a03e0-115">因此，事件處理常式方法會接受一個參數 (通常是事件引數)，並傳回 `unit`。</span><span class="sxs-lookup"><span data-stu-id="a03e0-115">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="a03e0-116">上述範例示範事件處理常式做為 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="a03e0-116">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="a03e0-117">事件處理常式也可以是函式值，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="a03e0-117">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="a03e0-118">範例中也會示範事件處理常式參數如何用來提供事件類型專屬資訊。</span><span class="sxs-lookup"><span data-stu-id="a03e0-118">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="a03e0-119">對於 `MouseMove` 事件，系統會傳遞 `System.Windows.Forms.MouseEventArgs` 物件，其中包含指標的 `X` 和 `Y` 位置。</span><span class="sxs-lookup"><span data-stu-id="a03e0-119">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]
    
## <a name="creating-custom-events"></a><span data-ttu-id="a03e0-120">建立自訂事件</span><span class="sxs-lookup"><span data-stu-id="a03e0-120">Creating Custom Events</span></span>
<span data-ttu-id="a03e0-121">F # 事件由 F #[事件](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9)類別，它會實作[IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862)介面。</span><span class="sxs-lookup"><span data-stu-id="a03e0-121">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="a03e0-122">`IEvent`本身是結合兩個其他介面的功能的介面`System.IObservable<'T>`和[IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a)。</span><span class="sxs-lookup"><span data-stu-id="a03e0-122">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="a03e0-123">因此，`Event` 具有相當於其他語言中委派的功能，加上來自 `IObservable` 的額外功能，這表示 F# 事件支援事件篩選，以及使用 F# 第一級函式和 Lambda 運算式做為事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a03e0-123">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="a03e0-124">這項功能提供[事件模組](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7)。</span><span class="sxs-lookup"><span data-stu-id="a03e0-124">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="a03e0-125">若要在類別上建立其運作方式與任何其他 .NET Framework 事件類似的事件，請將 `let` 繫結 (將 `Event` 定義為類別中的欄位) 加入至類別。</span><span class="sxs-lookup"><span data-stu-id="a03e0-125">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="a03e0-126">您可以指定所需的事件引數類型做為類型引數，或是空過，讓編譯器推斷適當類型。</span><span class="sxs-lookup"><span data-stu-id="a03e0-126">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="a03e0-127">您也必須定義將事件公開為 CLI 事件的事件成員。</span><span class="sxs-lookup"><span data-stu-id="a03e0-127">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="a03e0-128">這個成員應該有[CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333)屬性。</span><span class="sxs-lookup"><span data-stu-id="a03e0-128">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="a03e0-129">它會宣告屬性和它的實作就只是要呼叫[發行](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e)事件的屬性。</span><span class="sxs-lookup"><span data-stu-id="a03e0-129">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="a03e0-130">您類別的使用者可以使用已發行事件的 `Add` 方法加入處理常式。</span><span class="sxs-lookup"><span data-stu-id="a03e0-130">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="a03e0-131">`Add` 方法的引數可以是 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="a03e0-131">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="a03e0-132">您可以使用事件的 `Trigger` 屬性引發事件，將引數傳遞至處理函式。</span><span class="sxs-lookup"><span data-stu-id="a03e0-132">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="a03e0-133">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="a03e0-133">The following code example illustrates this.</span></span> <span data-ttu-id="a03e0-134">在此範例中，推斷的事件型別引數是 Tuple，代表 Lambda 運算式的引數。</span><span class="sxs-lookup"><span data-stu-id="a03e0-134">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="a03e0-135">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a03e0-135">The output is as follows.</span></span>

```
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="a03e0-136">這裡會說明 `Event` 模組所提供的額外功能。</span><span class="sxs-lookup"><span data-stu-id="a03e0-136">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="a03e0-137">下列程式碼範例說明如何使用 `Event.create` 建立事件和觸發程序方法，並以 Lambda 運算式形式加入兩個事件處理常式，然後觸發事件以執行這兩個 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="a03e0-137">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="a03e0-138">上述程式碼的輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a03e0-138">The output of the previous code is as follows.</span></span>

```
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="a03e0-139">處理事件資料流</span><span class="sxs-lookup"><span data-stu-id="a03e0-139">Processing Event Streams</span></span>
<span data-ttu-id="a03e0-140">加入事件的事件處理常式使用[Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd)函式，您可以使用中的函式`Event`模組處理方式高度自訂的事件資料流。</span><span class="sxs-lookup"><span data-stu-id="a03e0-140">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="a03e0-141">若要這麼做，請使用正向管道 (`|>`) 與事件做為一連串函式呼叫中的第一個值，並且使用 `Event` 模組函式做為後續函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="a03e0-141">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="a03e0-142">下列程式碼範例顯示如何設定只在特定條件下才會呼叫其處理常式的事件。</span><span class="sxs-lookup"><span data-stu-id="a03e0-142">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="a03e0-143">[Observable 模組](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227)包含類似可觀察的物件運作的函式。</span><span class="sxs-lookup"><span data-stu-id="a03e0-143">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="a03e0-144">可預見物件與事件類似，但是只有在已訂閱可預見物件時，才會主動訂閱事件。</span><span class="sxs-lookup"><span data-stu-id="a03e0-144">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>


## <a name="implementing-an-interface-event"></a><span data-ttu-id="a03e0-145">實作介面事件</span><span class="sxs-lookup"><span data-stu-id="a03e0-145">Implementing an Interface Event</span></span>
<span data-ttu-id="a03e0-146">當您開發 UI 元件時，通常會從建立新表單或繼承自現有表單或控制項的新控制項開始進行。</span><span class="sxs-lookup"><span data-stu-id="a03e0-146">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="a03e0-147">事件經常是在介面上定義，在這種情況下，您必須實作介面才能實作事件。</span><span class="sxs-lookup"><span data-stu-id="a03e0-147">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="a03e0-148">`System.ComponentModel.INotifyPropertyChanged` 介面會定義單一 `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="a03e0-148">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="a03e0-149">下列程式碼將示範如何實作這個繼承的介面所定義的事件：</span><span class="sxs-lookup"><span data-stu-id="a03e0-149">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish


    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

<span data-ttu-id="a03e0-150">如果您要在建構函式中連接事件，程式碼會稍微複雜，因為事件連結必須位於另一個建構函式的 `then` 區塊內，如下面範例所示：</span><span class="sxs-lookup"><span data-stu-id="a03e0-150">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs -> this.Property1 <- "text2"
        this.Property2 <- "text3")


    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)


// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a><span data-ttu-id="a03e0-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a03e0-151">See Also</span></span>
[<span data-ttu-id="a03e0-152">成員</span><span class="sxs-lookup"><span data-stu-id="a03e0-152">Members</span></span>](index.md)

[<span data-ttu-id="a03e0-153">處理和引發事件</span><span class="sxs-lookup"><span data-stu-id="a03e0-153">Handling and Raising Events</span></span>](../../../../docs/standard/events/index.md)

[<span data-ttu-id="a03e0-154">Lambda 運算式：`fun`關鍵字</span><span class="sxs-lookup"><span data-stu-id="a03e0-154">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)

[<span data-ttu-id="a03e0-155">Control.Event 模組</span><span class="sxs-lookup"><span data-stu-id="a03e0-155">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)

[<span data-ttu-id="a03e0-156">Control.Event &#60;'T &#62;類別</span><span class="sxs-lookup"><span data-stu-id="a03e0-156">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)

[<span data-ttu-id="a03e0-157">Control.Event &#60;'委派 ' 引數 &#62;類別</span><span class="sxs-lookup"><span data-stu-id="a03e0-157">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
