---
title: "實作事件架構非同步模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b4df5e4df914d932c7413e9330e8663753456c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c11ec-102">實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="c11ec-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="c11ec-103">如果您正在撰寫某項類別，其擁有的一些作業可能會造成明顯延遲，請考慮實作[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)以賦予它非同步功能。</span><span class="sxs-lookup"><span data-stu-id="c11ec-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="c11ec-104">事件架構非同步模式提供標準化方式來封裝具有非同步功能的類別。</span><span class="sxs-lookup"><span data-stu-id="c11ec-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="c11ec-105">若使用協助程式類別實作，例如<xref:System.ComponentModel.AsyncOperationManager>，您的類別能夠正確地在任何應用程式模型，包括[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]，主控台應用程式和 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c11ec-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="c11ec-106">如需實作事件架構非同步模式的範例，請參閱[如何：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="c11ec-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="c11ec-107">簡單的非同步作業，您可能會發現<xref:System.ComponentModel.BackgroundWorker>適用的元件。</span><span class="sxs-lookup"><span data-stu-id="c11ec-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="c11ec-108">如需有關<xref:System.ComponentModel.BackgroundWorker>，請參閱[How to： 在背景執行作業](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)。</span><span class="sxs-lookup"><span data-stu-id="c11ec-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="c11ec-109">下列清單所描述的事件架構非同步模式功能，本主題會加以討論。</span><span class="sxs-lookup"><span data-stu-id="c11ec-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="c11ec-110">實作事件架構非同步模式的機會</span><span class="sxs-lookup"><span data-stu-id="c11ec-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="c11ec-111">為非同步方法命名</span><span class="sxs-lookup"><span data-stu-id="c11ec-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="c11ec-112">選擇性地支援取消方法</span><span class="sxs-lookup"><span data-stu-id="c11ec-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="c11ec-113">選擇性地支援 IsBusy 屬性</span><span class="sxs-lookup"><span data-stu-id="c11ec-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="c11ec-114">選擇性地提供進度報告支援</span><span class="sxs-lookup"><span data-stu-id="c11ec-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="c11ec-115">選擇性地提供可傳回累加結果的支援</span><span class="sxs-lookup"><span data-stu-id="c11ec-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="c11ec-116">在方法中處理 Out 和 Ref 參數</span><span class="sxs-lookup"><span data-stu-id="c11ec-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c11ec-117">實作事件架構非同步模式的機會</span><span class="sxs-lookup"><span data-stu-id="c11ec-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="c11ec-118">若有下列情況，請考慮實作事件架構非同步模式：</span><span class="sxs-lookup"><span data-stu-id="c11ec-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="c11ec-119">您類別的用戶端不需要<xref:System.Threading.WaitHandle>和<xref:System.IAsyncResult>物件可使用的非同步作業，這表示該輪詢和<xref:System.Threading.WaitHandle.WaitAll%2A>或<xref:System.Threading.WaitHandle.WaitAny%2A>必須設定用戶端所建立。</span><span class="sxs-lookup"><span data-stu-id="c11ec-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="c11ec-120">您想要由用戶端使用熟悉的事件/委派模型來管理非同步作業。</span><span class="sxs-lookup"><span data-stu-id="c11ec-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="c11ec-121">任何作業都適合進行非同步實作，但您應該考慮那些預期會產生較長延遲的作業。</span><span class="sxs-lookup"><span data-stu-id="c11ec-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="c11ec-122">用戶端會呼叫方法並在完成時收到通知的作業尤其適合，因為您不必進一步介入。</span><span class="sxs-lookup"><span data-stu-id="c11ec-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="c11ec-123">會持續執行，並定期將進度、累加結果或狀態變更通知用戶端的作業也很適合。</span><span class="sxs-lookup"><span data-stu-id="c11ec-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="c11ec-124">如需有關如何決定何時該支援事件架構非同步模式的詳細資訊，請參閱[決定何時實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="c11ec-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="c11ec-125">為非同步方法命名</span><span class="sxs-lookup"><span data-stu-id="c11ec-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="c11ec-126">對於您要為其提供非同步對應的每一個 MethodName 同步方法：</span><span class="sxs-lookup"><span data-stu-id="c11ec-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="c11ec-127">定義有下列情形的 MethodName`Async` 方法：</span><span class="sxs-lookup"><span data-stu-id="c11ec-127">Define a *MethodName*`Async` method that:</span></span>  
  
-   <span data-ttu-id="c11ec-128">傳回 `void`。</span><span class="sxs-lookup"><span data-stu-id="c11ec-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="c11ec-129">使用與 MethodName 方法相同的參數。</span><span class="sxs-lookup"><span data-stu-id="c11ec-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="c11ec-130">接受多個引動過程。</span><span class="sxs-lookup"><span data-stu-id="c11ec-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="c11ec-131">選擇性地定義 MethodName`Async` 多載，它會與 MethodName`Async` 相同，但是具有稱為 `userState` 的額外物件值參數。</span><span class="sxs-lookup"><span data-stu-id="c11ec-131">Optionally define a *MethodName*`Async` overload, identical to *MethodName*`Async`, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="c11ec-132">需要這麼做的前提是，您已準備好管理您擁有之方法的多個並行引動過程，在此情況下，`userState` 值會傳回給所有的事件處理常式，以供區別該方法的各個引動過程。</span><span class="sxs-lookup"><span data-stu-id="c11ec-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="c11ec-133">您也可以純粹為了能有位置可儲存使用者狀態以供日後擷取，而選擇這樣做。</span><span class="sxs-lookup"><span data-stu-id="c11ec-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="c11ec-134">對於每個個別的 MethodName`Async` 方法簽章：</span><span class="sxs-lookup"><span data-stu-id="c11ec-134">For each separate *MethodName*`Async` method signature:</span></span>  
  
1.  <span data-ttu-id="c11ec-135">在相同的類別中定義下列事件來作為方法︰</span><span class="sxs-lookup"><span data-stu-id="c11ec-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="c11ec-136">定義下列委派和<xref:System.ComponentModel.AsyncCompletedEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="c11ec-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="c11ec-137">此外，這些項目可能會在類別本身之外來定義，但會在相同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="c11ec-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   <span data-ttu-id="c11ec-138">確定 MethodName`CompletedEventArgs` 類別將其成員公開為唯讀屬性，而不是欄位，因為欄位會防止資料繫結。</span><span class="sxs-lookup"><span data-stu-id="c11ec-138">Ensure that the *MethodName*`CompletedEventArgs` class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="c11ec-139">未定義任何<xref:System.ComponentModel.AsyncCompletedEventArgs>-衍生的類別不會產生結果的方法。</span><span class="sxs-lookup"><span data-stu-id="c11ec-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="c11ec-140">想要使用的執行個體<xref:System.ComponentModel.AsyncCompletedEventArgs>本身。</span><span class="sxs-lookup"><span data-stu-id="c11ec-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="c11ec-141">它是完全可接受的當可行且適當，若要重複使用委派和<xref:System.ComponentModel.AsyncCompletedEventArgs>型別。</span><span class="sxs-lookup"><span data-stu-id="c11ec-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="c11ec-142">在此情況下，命名不會為一致的方法名稱，因為指定的委派和<xref:System.ComponentModel.AsyncCompletedEventArgs>將不會繫結至單一方法。</span><span class="sxs-lookup"><span data-stu-id="c11ec-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="c11ec-143">選擇性地支援取消方法</span><span class="sxs-lookup"><span data-stu-id="c11ec-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="c11ec-144">如果您的類別會支援取消非同步作業，請如下所述對用戶端公開取消方法。</span><span class="sxs-lookup"><span data-stu-id="c11ec-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="c11ec-145">請注意，在定義取消支援之前，您必須先達成兩個決策點︰</span><span class="sxs-lookup"><span data-stu-id="c11ec-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="c11ec-146">您的類別 (包括其未來預期的新增項目) 是否只有一個支援取消方法的非同步作業？</span><span class="sxs-lookup"><span data-stu-id="c11ec-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="c11ec-147">可支援取消方法的非同步作業能否支援多個暫止作業？</span><span class="sxs-lookup"><span data-stu-id="c11ec-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="c11ec-148">也就是說，MethodName`Async` 方法是否使用 `userState` 參數，而且是否在等候任何作業完成之前允許多個引動過程？</span><span class="sxs-lookup"><span data-stu-id="c11ec-148">That is, does the *MethodName*`Async` method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="c11ec-149">使用下表中對於這兩個問題的回答，來判斷您的取消方法應該使用的簽章。</span><span class="sxs-lookup"><span data-stu-id="c11ec-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="c11ec-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c11ec-150">Visual Basic</span></span>  
  
||<span data-ttu-id="c11ec-151">支援多個同時作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="c11ec-152">一次只有一個作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="c11ec-153">整個類別只有一個非同步作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="c11ec-154">類別中有多個非同步作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="c11ec-155">C#</span><span class="sxs-lookup"><span data-stu-id="c11ec-155">C#</span></span>  
  
||<span data-ttu-id="c11ec-156">支援多個同時作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="c11ec-157">一次只有一個作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="c11ec-158">整個類別只有一個非同步作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="c11ec-159">類別中有多個非同步作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="c11ec-160">如果您定義 `CancelAsync(object userState)` 方法，用戶端必須小心地選擇它們的狀態值，以便能夠區別物件上所叫用的所有非同步方法，而不只是能夠區別單一非同步方法的所有引動過程。</span><span class="sxs-lookup"><span data-stu-id="c11ec-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="c11ec-161">決定命名單一非同步作業版本 MethodName`AsyncCancel`，是基於能在像是 Visual Studio's IntelliSense 的設計環境中，更容易地探索到這項方法。</span><span class="sxs-lookup"><span data-stu-id="c11ec-161">The decision to name the single-async-operation version *MethodName*`AsyncCancel` is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="c11ec-162">這會將相關的成員群組在一起，並讓與非同步功能無關的其他成員可與它們區別開來。</span><span class="sxs-lookup"><span data-stu-id="c11ec-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="c11ec-163">如果您預期後續版本中可能會新增其他非同步作業，您最好要定義 `CancelAsync`。</span><span class="sxs-lookup"><span data-stu-id="c11ec-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="c11ec-164">請勿將上述表格中的多個方法定義到相同類別中。</span><span class="sxs-lookup"><span data-stu-id="c11ec-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="c11ec-165">這麼做毫無意義，而且類別介面也會因為方法數量暴增而變得雜亂。</span><span class="sxs-lookup"><span data-stu-id="c11ec-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="c11ec-166">這些方法通常會立即傳回，而且作業實際上不一定會取消。</span><span class="sxs-lookup"><span data-stu-id="c11ec-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="c11ec-167">在 MethodName`Completed` 事件的事件處理常式中，MethodName`CompletedEventArgs` 物件含有一個 `Cancelled` 欄位，可讓用戶端用來判斷是否已取消。</span><span class="sxs-lookup"><span data-stu-id="c11ec-167">In the event handler for the *MethodName*`Completed` event, the *MethodName*`CompletedEventArgs` object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="c11ec-168">請遵守[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)中所述的取消語意。</span><span class="sxs-lookup"><span data-stu-id="c11ec-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="c11ec-169">選擇性地支援 IsBusy 屬性</span><span class="sxs-lookup"><span data-stu-id="c11ec-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="c11ec-170">如果您的類別不支援多個並行引動過程，請考慮公開 `IsBusy` 屬性。</span><span class="sxs-lookup"><span data-stu-id="c11ec-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="c11ec-171">如此讓開發人員不需攔截 MethodName`Async` 方法中的例外狀況，就可以判斷是否有 MethodName`Async` 方法正在執行。</span><span class="sxs-lookup"><span data-stu-id="c11ec-171">This allows developers to determine whether a *MethodName*`Async` method is running without catching an exception from the *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="c11ec-172">請遵守[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)中所述的 `IsBusy` 語意。</span><span class="sxs-lookup"><span data-stu-id="c11ec-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="c11ec-173">選擇性地提供進度報告支援</span><span class="sxs-lookup"><span data-stu-id="c11ec-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="c11ec-174">非同步作業經常需要在其作業期間報告進度。</span><span class="sxs-lookup"><span data-stu-id="c11ec-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="c11ec-175">事件架構非同步模式提供了這方面的指導方針。</span><span class="sxs-lookup"><span data-stu-id="c11ec-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="c11ec-176">選擇性地定義要供非同步作業引發，並在適當的執行緒上叫用的事件。</span><span class="sxs-lookup"><span data-stu-id="c11ec-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="c11ec-177"><xref:System.ComponentModel.ProgressChangedEventArgs>物件會有必須是介於 0 到 100 之間的整數值的進度列指示器。</span><span class="sxs-lookup"><span data-stu-id="c11ec-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="c11ec-178">將此事件命名如下︰</span><span class="sxs-lookup"><span data-stu-id="c11ec-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="c11ec-179">`ProgressChanged`，如果類別具有多個非同步作業 (或預期會有成長，而會在未來的版本中包含多個非同步作業)。</span><span class="sxs-lookup"><span data-stu-id="c11ec-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="c11ec-180">MethodName `ProgressChanged`，如果類別具有單一非同步作業。</span><span class="sxs-lookup"><span data-stu-id="c11ec-180">*MethodName* `ProgressChanged` if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="c11ec-181">這個命名選擇和取消方法的選擇類似，後者在＜選擇性地支援取消方法＞一節中有所說明。</span><span class="sxs-lookup"><span data-stu-id="c11ec-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="c11ec-182">此事件應該使用<xref:System.ComponentModel.ProgressChangedEventHandler>委派簽章和<xref:System.ComponentModel.ProgressChangedEventArgs>類別。</span><span class="sxs-lookup"><span data-stu-id="c11ec-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="c11ec-183">或者，如果可以提供更特定的網域進度列指示器，（針對執行個體、 位元組讀取和下載作業的總位元組數），然後您應該定義的衍生的類別<xref:System.ComponentModel.ProgressChangedEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="c11ec-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="c11ec-184">請注意，不論一個類別支援多少非同步方法，每個類別都只有一個 `ProgressChanged` 或 MethodName`ProgressChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="c11ec-184">Note that there is only one `ProgressChanged` or *MethodName*`ProgressChanged` event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="c11ec-185">用戶端必須使用傳遞至 MethodName`Async` 方法的 `userState` 物件區分多個並行作業上的進度更新。</span><span class="sxs-lookup"><span data-stu-id="c11ec-185">Clients are expected to use the `userState` object that is passed to the *MethodName*`Async` methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="c11ec-186">有時候可能會有多個作業都支援進度報告，而各自傳回不同的進度指示器。</span><span class="sxs-lookup"><span data-stu-id="c11ec-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="c11ec-187">在此情況下，使用單一的 `ProgressChanged` 事件就不是合適的作法，因此您可能會考慮支援多個 `ProgressChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="c11ec-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="c11ec-188">在此情況下，請為每個 MethodName`Async` 方法使用 MethodName`ProgressChanged` 的命名模式。</span><span class="sxs-lookup"><span data-stu-id="c11ec-188">In this case use a naming pattern of *MethodName*`ProgressChanged` for each *MethodName*`Async` method.</span></span>  
  
 <span data-ttu-id="c11ec-189">請遵守[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)中所述的進度報告語意。</span><span class="sxs-lookup"><span data-stu-id="c11ec-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="c11ec-190">選擇性地提供可傳回累加結果的支援</span><span class="sxs-lookup"><span data-stu-id="c11ec-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="c11ec-191">有時候非同步作業會在完成之前傳回累加結果。</span><span class="sxs-lookup"><span data-stu-id="c11ec-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="c11ec-192">您有許多選項可用來支援這種情況。</span><span class="sxs-lookup"><span data-stu-id="c11ec-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="c11ec-193">下面有一些範例。</span><span class="sxs-lookup"><span data-stu-id="c11ec-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="c11ec-194">單一作業類別</span><span class="sxs-lookup"><span data-stu-id="c11ec-194">Single-operation Class</span></span>  
 <span data-ttu-id="c11ec-195">如果您的類別只支援單一非同步作業，而且該作業可傳回累加結果，則請︰</span><span class="sxs-lookup"><span data-stu-id="c11ec-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="c11ec-196">擴充<xref:System.ComponentModel.ProgressChangedEventArgs>輸入來執行累加式的結果資料，並定義*MethodName* `ProgressChanged`事件與這個擴充資料。</span><span class="sxs-lookup"><span data-stu-id="c11ec-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a *MethodName*`ProgressChanged` event with this extended data.</span></span>  
  
-   <span data-ttu-id="c11ec-197">在出現可報告的累加結果時，引發這個 MethodName`ProgressChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="c11ec-197">Raise this *MethodName*`ProgressChanged` event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="c11ec-198">這項方案特別適用於單一非同步作業類別，因為就像 MethodName`ProgressChanged` 事件一樣，相同事件在「所有作業」上發生並傳回累加結果時，並不會造成問題。</span><span class="sxs-lookup"><span data-stu-id="c11ec-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the *MethodName*`ProgressChanged` event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="c11ec-199">具有同質累加結果的多重作業類別</span><span class="sxs-lookup"><span data-stu-id="c11ec-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="c11ec-200">在此案例中，您的類別會支援多個非同步方法，每個方法都能傳回累加結果，而且這些累加結果全都有相同型別的資料。</span><span class="sxs-lookup"><span data-stu-id="c11ec-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="c11ec-201">請遵循上面所述，對於單一作業的類別，是相同的模型<xref:System.EventArgs>結構適用於所有累加結果。</span><span class="sxs-lookup"><span data-stu-id="c11ec-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="c11ec-202">定義 `ProgressChanged` 事件而非 MethodName`ProgressChanged` 事件，因為它會套用到多個非同步方法。</span><span class="sxs-lookup"><span data-stu-id="c11ec-202">Define a `ProgressChanged` event instead of a *MethodName*`ProgressChanged` event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="c11ec-203">具有異質累加結果的多重作業類別</span><span class="sxs-lookup"><span data-stu-id="c11ec-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="c11ec-204">如果您的類別支援多個非同步方法，而且各會傳回不同型別的資料，您應該︰</span><span class="sxs-lookup"><span data-stu-id="c11ec-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="c11ec-205">將累加結果報告和進度報告區隔開來。</span><span class="sxs-lookup"><span data-stu-id="c11ec-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="c11ec-206">定義個別*MethodName* `ProgressChanged`具有適當事件<xref:System.EventArgs>每個非同步方法來處理該方法的累加式的結果資料。</span><span class="sxs-lookup"><span data-stu-id="c11ec-206">Define a separate *MethodName*`ProgressChanged` event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="c11ec-207">如[實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)所述，在適當的執行緒上叫用該事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c11ec-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="c11ec-208">在方法中處理 Out 和 Ref 參數</span><span class="sxs-lookup"><span data-stu-id="c11ec-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="c11ec-209">一般而言，雖然我們不建議您在 .NET Framework 中使用 `out` 和 `ref`，但如果它們存在，請遵循以下規則︰</span><span class="sxs-lookup"><span data-stu-id="c11ec-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="c11ec-210">假設同步方法為 MethodName：</span><span class="sxs-lookup"><span data-stu-id="c11ec-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="c11ec-211">MethodName 的 `out` 參數不應成為 MethodName`Async` 的一部分。</span><span class="sxs-lookup"><span data-stu-id="c11ec-211">`out` parameters to *MethodName* should not be part of *MethodName*`Async`.</span></span> <span data-ttu-id="c11ec-212">相反地，這些參數應該成為 MethodName`CompletedEventArgs` 的一部分，其名稱會與 MethodName 中的對等參數相同 (除非還有更適當的名稱)。</span><span class="sxs-lookup"><span data-stu-id="c11ec-212">Instead, they should be part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="c11ec-213">MethodName 的 `ref` 參數應該為 MethodName`Async` 的一部分，並且也是 MethodName`CompletedEventArgs` 的一部分，其名稱會與 MethodName 中的對等參數相同 (除非還有更適當的名稱)。</span><span class="sxs-lookup"><span data-stu-id="c11ec-213">`ref` parameters to *MethodName* should appear as part of *MethodName*`Async`, and as part of *MethodName*`CompletedEventArgs` with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="c11ec-214">例如，假設︰</span><span class="sxs-lookup"><span data-stu-id="c11ec-214">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="c11ec-215">您的非同步方法並將其<xref:System.ComponentModel.AsyncCompletedEventArgs>類別會看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="c11ec-215">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c11ec-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c11ec-216">See Also</span></span>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [<span data-ttu-id="c11ec-217">操作說明：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="c11ec-217">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="c11ec-218">操作說明：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="c11ec-218">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="c11ec-219">操作說明：實作使用背景作業的表單</span><span class="sxs-lookup"><span data-stu-id="c11ec-219">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="c11ec-220">決定何時實作事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="c11ec-220">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="c11ec-221">使用事件架構非同步模式設計多執行緒程式</span><span class="sxs-lookup"><span data-stu-id="c11ec-221">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="c11ec-222">實作事件架構非同步模式的最佳作法</span><span class="sxs-lookup"><span data-stu-id="c11ec-222">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
