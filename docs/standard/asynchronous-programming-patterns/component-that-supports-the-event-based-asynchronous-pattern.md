---
title: "逐步解說：實作支援事件架構非同步模式的元件"
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
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 150e4b27cc149774895574ddd196de5f9bc2acd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a><span data-ttu-id="c8412-102">逐步解說：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="c8412-102">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="c8412-103">如果您正在撰寫的類別可能會造成顯著的延遲某些作業，請考慮並賦予它所實作的非同步功能[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c8412-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="c8412-104">這個逐步解說將說明如何建立實作事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-104">This walkthrough illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="c8412-105">它使用中的 helper 類別來實作<xref:System.ComponentModel?displayProperty=nameWithType>命名空間，可確保元件如何在任何應用程式模式下正確運作，包括[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]，主控台應用程式和 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8412-105">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications and Windows Forms applications.</span></span> <span data-ttu-id="c8412-106">此元件也會與設計<xref:System.Windows.Forms.PropertyGrid>控制項和您自己自訂的設計工具。</span><span class="sxs-lookup"><span data-stu-id="c8412-106">This component is also designable with a <xref:System.Windows.Forms.PropertyGrid> control and your own custom designers.</span></span>  
  
 <span data-ttu-id="c8412-107">當您完成時，您必須以非同步方式計算質數的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8412-107">When you are through, you will have an application that computes prime numbers asynchronously.</span></span> <span data-ttu-id="c8412-108">您的應用程式必須在主要的使用者介面 (UI) 執行緒和執行緒的每一個質數計算。</span><span class="sxs-lookup"><span data-stu-id="c8412-108">Your application will have a main user interface (UI) thread and a thread for each prime number calculation.</span></span> <span data-ttu-id="c8412-109">雖然測試大型數字是否為質數需要相當長的時間、 主要 UI 執行緒不會中斷的這項延遲，而且進行計算時，表單會有回應。</span><span class="sxs-lookup"><span data-stu-id="c8412-109">Although testing whether a large number is prime can take a noticeable amount of time, the main UI thread will not be interrupted by this delay, and the form will be responsive during the calculations.</span></span> <span data-ttu-id="c8412-110">您可以執行多個計算要選擇性地同時取消擱置的計算。</span><span class="sxs-lookup"><span data-stu-id="c8412-110">You will be able to run as many calculations as you like concurrently and selectively cancel pending calculations.</span></span>  
  
 <span data-ttu-id="c8412-111">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="c8412-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="c8412-112">建立元件</span><span class="sxs-lookup"><span data-stu-id="c8412-112">Creating the Component</span></span>  
  
-   <span data-ttu-id="c8412-113">定義公用的非同步事件和委派</span><span class="sxs-lookup"><span data-stu-id="c8412-113">Defining Public Asynchronous Events and Delegates</span></span>  
  
-   <span data-ttu-id="c8412-114">定義私用委派</span><span class="sxs-lookup"><span data-stu-id="c8412-114">Defining Private Delegates</span></span>  
  
-   <span data-ttu-id="c8412-115">實作公用事件</span><span class="sxs-lookup"><span data-stu-id="c8412-115">Implementing Public Events</span></span>  
  
-   <span data-ttu-id="c8412-116">實作完成方法</span><span class="sxs-lookup"><span data-stu-id="c8412-116">Implementing the Completion Method</span></span>  
  
-   <span data-ttu-id="c8412-117">實作工作者方法</span><span class="sxs-lookup"><span data-stu-id="c8412-117">Implementing the Worker Methods</span></span>  
  
-   <span data-ttu-id="c8412-118">實作開始和取消方法</span><span class="sxs-lookup"><span data-stu-id="c8412-118">Implementing Start and Cancel Methods</span></span>  
  
 <span data-ttu-id="c8412-119">若要為單一列出本主題中複製的程式碼，請參閱[How to： 實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="c8412-119">To copy the code in this topic as a single listing, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="creating-the-component"></a><span data-ttu-id="c8412-120">建立元件</span><span class="sxs-lookup"><span data-stu-id="c8412-120">Creating the Component</span></span>  
 <span data-ttu-id="c8412-121">第一個步驟是建立會實作事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-121">The first step is to create the component that will implement the Event-based Asynchronous Pattern.</span></span>  
  
#### <a name="to-create-the-component"></a><span data-ttu-id="c8412-122">若要建立的元件</span><span class="sxs-lookup"><span data-stu-id="c8412-122">To create the component</span></span>  
  
-   <span data-ttu-id="c8412-123">建立類別，稱為`PrimeNumberCalculator`繼承自<xref:System.ComponentModel.Component>。</span><span class="sxs-lookup"><span data-stu-id="c8412-123">Create a class called `PrimeNumberCalculator` that inherits from <xref:System.ComponentModel.Component>.</span></span>  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a><span data-ttu-id="c8412-124">定義公用的非同步事件和委派</span><span class="sxs-lookup"><span data-stu-id="c8412-124">Defining Public Asynchronous Events and Delegates</span></span>  
 <span data-ttu-id="c8412-125">您的元件會使用事件的用戶端進行通訊。</span><span class="sxs-lookup"><span data-stu-id="c8412-125">Your component communicates to clients using events.</span></span> <span data-ttu-id="c8412-126">*MethodName* `Completed`事件警示用戶端已完成的非同步工作，而*MethodName* `ProgressChanged`事件會通知用戶端的非同步工作的進度。</span><span class="sxs-lookup"><span data-stu-id="c8412-126">The *MethodName*`Completed` event alerts clients to the completion of an asynchronous task, and the *MethodName*`ProgressChanged` event informs clients of the progress of an asynchronous task.</span></span>  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a><span data-ttu-id="c8412-127">若要為用戶端元件的定義非同步事件：</span><span class="sxs-lookup"><span data-stu-id="c8412-127">To define asynchronous events for clients of your component:</span></span>  
  
1.  <span data-ttu-id="c8412-128">匯入<xref:System.Threading?displayProperty=nameWithType>和<xref:System.Collections.Specialized?displayProperty=nameWithType>在您的檔案最上方的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c8412-128">Import the <xref:System.Threading?displayProperty=nameWithType> and <xref:System.Collections.Specialized?displayProperty=nameWithType> namespaces at the top of your file.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  <span data-ttu-id="c8412-129">之前`PrimeNumberCalculator`類別定義，宣告的進度與完成狀態事件的委派。</span><span class="sxs-lookup"><span data-stu-id="c8412-129">Before the `PrimeNumberCalculator` class definition, declare delegates for progress and completion events.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  <span data-ttu-id="c8412-130">在`PrimeNumberCalculator`類別定義中，宣告事件以報告進度和完成用戶端。</span><span class="sxs-lookup"><span data-stu-id="c8412-130">In the `PrimeNumberCalculator` class definition, declare events for reporting progress and completion to clients.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  <span data-ttu-id="c8412-131">之後`PrimeNumberCalculator`類別定義中，衍生`CalculatePrimeCompletedEventArgs`類別報告的每個用戶端事件處理常式的計算結果的`CalculatePrimeCompleted`.event。</span><span class="sxs-lookup"><span data-stu-id="c8412-131">After the `PrimeNumberCalculator` class definition, derive the `CalculatePrimeCompletedEventArgs` class for reporting the outcome of each calculation to the client's event handler for the `CalculatePrimeCompleted`.event.</span></span> <span data-ttu-id="c8412-132">除了`AsyncCompletedEventArgs`屬性，這個類別可讓用戶端判斷何種號碼已測試、 是否為質數，以及第一個除數是如果它不是主要。</span><span class="sxs-lookup"><span data-stu-id="c8412-132">In addition to the `AsyncCompletedEventArgs` properties, this class enables the client to determine what number was tested, whether it is prime, and what the first divisor is if it is not prime.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a><span data-ttu-id="c8412-133">檢查點</span><span class="sxs-lookup"><span data-stu-id="c8412-133">Checkpoint</span></span>  
 <span data-ttu-id="c8412-134">此時，您可以建立元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-134">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="c8412-135">若要測試您的元件</span><span class="sxs-lookup"><span data-stu-id="c8412-135">To test your component</span></span>  
  
-   <span data-ttu-id="c8412-136">編譯元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-136">Compile the component.</span></span>  
  
     <span data-ttu-id="c8412-137">您會收到兩個編譯器警告：</span><span class="sxs-lookup"><span data-stu-id="c8412-137">You will receive two compiler warnings:</span></span>  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     <span data-ttu-id="c8412-138">下一節中，將會清除這些警告。</span><span class="sxs-lookup"><span data-stu-id="c8412-138">These warnings will be cleared in the next section.</span></span>  
  
## <a name="defining-private-delegates"></a><span data-ttu-id="c8412-139">定義私用委派</span><span class="sxs-lookup"><span data-stu-id="c8412-139">Defining Private Delegates</span></span>  
 <span data-ttu-id="c8412-140">非同步層面`PrimeNumberCalculator`元件會在內部實作特殊的委派，又稱為<xref:System.Threading.SendOrPostCallback>。</span><span class="sxs-lookup"><span data-stu-id="c8412-140">The asynchronous aspects of the `PrimeNumberCalculator` component are implemented internally with a special delegate known as a <xref:System.Threading.SendOrPostCallback>.</span></span> <span data-ttu-id="c8412-141">A<xref:System.Threading.SendOrPostCallback>代表執行的回呼方法<xref:System.Threading.ThreadPool>執行緒。</span><span class="sxs-lookup"><span data-stu-id="c8412-141">A <xref:System.Threading.SendOrPostCallback> represents a callback method that executes on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="c8412-142">回呼方法必須接受類型的單一參數的簽章<xref:System.Object>，這表示您必須將包裝函式類別中的委派之間的狀態傳遞。</span><span class="sxs-lookup"><span data-stu-id="c8412-142">The callback method must have a signature that takes a single parameter of type <xref:System.Object>, which means you will need to pass state among delegates in a wrapper class.</span></span> <span data-ttu-id="c8412-143">如需詳細資訊，請參閱<xref:System.Threading.SendOrPostCallback>。</span><span class="sxs-lookup"><span data-stu-id="c8412-143">For more information, see <xref:System.Threading.SendOrPostCallback>.</span></span>  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a><span data-ttu-id="c8412-144">若要實作您的元件內部非同步行為：</span><span class="sxs-lookup"><span data-stu-id="c8412-144">To implement your component's internal asynchronous behavior:</span></span>  
  
1.  <span data-ttu-id="c8412-145">宣告和建立<xref:System.Threading.SendOrPostCallback>委派中`PrimeNumberCalculator`類別。</span><span class="sxs-lookup"><span data-stu-id="c8412-145">Declare and create the <xref:System.Threading.SendOrPostCallback> delegates in the `PrimeNumberCalculator` class.</span></span> <span data-ttu-id="c8412-146">建立<xref:System.Threading.SendOrPostCallback>公用程式方法的物件稱為`InitializeDelegates`。</span><span class="sxs-lookup"><span data-stu-id="c8412-146">Create the <xref:System.Threading.SendOrPostCallback> objects in a utility method called `InitializeDelegates`.</span></span>  
  
     <span data-ttu-id="c8412-147">您將需要兩個委派： 一個用戶端報告進度，一個用於報告用戶端來完成。</span><span class="sxs-lookup"><span data-stu-id="c8412-147">You will need two delegates: one for reporting progress to the client, and one for reporting completion to the client.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  <span data-ttu-id="c8412-148">呼叫`InitializeDelegates`元件的建構函式中的方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-148">Call the `InitializeDelegates` method in your component's constructor.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  <span data-ttu-id="c8412-149">宣告的委派`PrimeNumberCalculator`處理要以非同步方式進行的實際工作的類別。</span><span class="sxs-lookup"><span data-stu-id="c8412-149">Declare a delegate in the `PrimeNumberCalculator` class that handles the actual work to be done asynchronously.</span></span> <span data-ttu-id="c8412-150">這個委派會包裝測試數字是否為質數的工作者方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-150">This delegate wraps the worker method that tests whether a number is prime.</span></span> <span data-ttu-id="c8412-151">委派會採用<xref:System.ComponentModel.AsyncOperation>參數，將用來追蹤非同步作業的存留期。</span><span class="sxs-lookup"><span data-stu-id="c8412-151">The delegate takes an <xref:System.ComponentModel.AsyncOperation> parameter, which will be used to track the lifetime of the asynchronous operation.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  <span data-ttu-id="c8412-152">建立管理暫止的非同步作業的存留期的集合。</span><span class="sxs-lookup"><span data-stu-id="c8412-152">Create a collection for managing lifetimes of pending asynchronous operations.</span></span> <span data-ttu-id="c8412-153">用戶端需要追蹤作業，以及執行和完成時，此追蹤由要求用戶端時要傳遞的唯一的語彙基元或工作 ID、 用戶端提出的非同步方法呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-153">The client needs a way to track operations as they are executed and completed, and this tracking is done by requiring the client to pass a unique token, or task ID, when the client makes the call to the asynchronous method.</span></span> <span data-ttu-id="c8412-154">`PrimeNumberCalculator`元件必須追蹤的每個呼叫對應的引動過程與關聯工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="c8412-154">The `PrimeNumberCalculator` component must keep track of each call by associating the task ID with its corresponding invocation.</span></span> <span data-ttu-id="c8412-155">如果用戶端會傳遞不是唯一的工作識別碼`PrimeNumberCalculator`元件必須引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8412-155">If the client passes a task ID that is not unique, the `PrimeNumberCalculator` component must raise an exception.</span></span>  
  
     <span data-ttu-id="c8412-156">`PrimeNumberCalculator`元件會持續追蹤的工作識別碼使用一種特殊的集合類別，稱為<xref:System.Collections.Specialized.HybridDictionary>。</span><span class="sxs-lookup"><span data-stu-id="c8412-156">The `PrimeNumberCalculator` component keeps track of task ID by using a special collection class called a <xref:System.Collections.Specialized.HybridDictionary>.</span></span> <span data-ttu-id="c8412-157">在類別定義中，建立<xref:System.Collections.Specialized.HybridDictionary>呼叫`userTokenToLifetime`。</span><span class="sxs-lookup"><span data-stu-id="c8412-157">In the class definition, create a <xref:System.Collections.Specialized.HybridDictionary> called `userTokenToLifetime`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a><span data-ttu-id="c8412-158">實作公用事件</span><span class="sxs-lookup"><span data-stu-id="c8412-158">Implementing Public Events</span></span>  
 <span data-ttu-id="c8412-159">用戶端使用的事件實作事件架構非同步模式的元件進行通訊。</span><span class="sxs-lookup"><span data-stu-id="c8412-159">Components that implement the Event-based Asynchronous Pattern communicate to clients using events.</span></span> <span data-ttu-id="c8412-160">這些事件會搭配適當的執行緒上叫用<xref:System.ComponentModel.AsyncOperation>類別。</span><span class="sxs-lookup"><span data-stu-id="c8412-160">These events are invoked on the proper thread with the help of the <xref:System.ComponentModel.AsyncOperation> class.</span></span>  
  
#### <a name="to-raise-events-to-your-components-clients"></a><span data-ttu-id="c8412-161">若要引發事件給元件的用戶端：</span><span class="sxs-lookup"><span data-stu-id="c8412-161">To raise events to your component's clients:</span></span>  
  
1.  <span data-ttu-id="c8412-162">實作回報到用戶端的公用事件。</span><span class="sxs-lookup"><span data-stu-id="c8412-162">Implement public events for reporting to clients.</span></span> <span data-ttu-id="c8412-163">您必須為報告進度，另一個用於報告完成事件。</span><span class="sxs-lookup"><span data-stu-id="c8412-163">You will need an event for reporting progress and one for reporting completion.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a><span data-ttu-id="c8412-164">實作完成方法</span><span class="sxs-lookup"><span data-stu-id="c8412-164">Implementing the Completion Method</span></span>  
 <span data-ttu-id="c8412-165">完成委派為基礎、 無限制執行緒的非同步行為將會叫用時成功完成、 錯誤或取消非同步作業會結束方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-165">The completion delegate is the method that the underlying, free-threaded asynchronous behavior will invoke when the asynchronous operation ends by successful completion, error, or cancellation.</span></span> <span data-ttu-id="c8412-166">這個引動過程發生在任意的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c8412-166">This invocation happens on an arbitrary thread.</span></span>  
  
 <span data-ttu-id="c8412-167">這個方法是從內部集合的唯一用戶端語彙基元移除用戶端的工作識別碼的所在。</span><span class="sxs-lookup"><span data-stu-id="c8412-167">This method is where the client's task ID is removed from the internal collection of unique client tokens.</span></span> <span data-ttu-id="c8412-168">這個方法也會在特定的非同步作業的存留期結束藉由呼叫<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>方法在相對應<xref:System.ComponentModel.AsyncOperation>。</span><span class="sxs-lookup"><span data-stu-id="c8412-168">This method also ends the lifetime of a particular asynchronous operation by calling the <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> method on the corresponding <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="c8412-169">此呼叫引發完成事件適用於應用程式模型的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="c8412-169">This call raises the completion event on the thread that is appropriate for the application model.</span></span> <span data-ttu-id="c8412-170">之後<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>呼叫方法時，這個執行個體<xref:System.ComponentModel.AsyncOperation>不再可用，並使用它的任何後續嘗試將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8412-170">After the <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> method is called, this instance of <xref:System.ComponentModel.AsyncOperation> can no longer be used, and any subsequent attempts to use it will throw an exception.</span></span>  
  
 <span data-ttu-id="c8412-171">`CompletionMethod`簽章必須保留所有的狀態需要描述非同步作業的結果。</span><span class="sxs-lookup"><span data-stu-id="c8412-171">The `CompletionMethod` signature must hold all state necessary to describe the outcome of the asynchronous operation.</span></span> <span data-ttu-id="c8412-172">數字是否為質數，以及其第一個除數的值如果不是質數，它會保留數目所測試之這個特定非同步作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="c8412-172">It holds state for the number that was tested by this particular asynchronous operation, whether the number is prime, and the value of its first divisor if it is not a prime number.</span></span> <span data-ttu-id="c8412-173">它也包含說明發生任何例外狀況的狀態和<xref:System.ComponentModel.AsyncOperation>對應於這個特定工作。</span><span class="sxs-lookup"><span data-stu-id="c8412-173">It also holds state describing any exception that occurred, and the <xref:System.ComponentModel.AsyncOperation> corresponding to this particular task.</span></span>  
  
#### <a name="to-complete-an-asynchronous-operation"></a><span data-ttu-id="c8412-174">若要完成的非同步作業：</span><span class="sxs-lookup"><span data-stu-id="c8412-174">To complete an asynchronous operation:</span></span>  
  
-   <span data-ttu-id="c8412-175">實作完成的方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-175">Implement the completion method.</span></span> <span data-ttu-id="c8412-176">它會採用六個參數，用來填入`CalculatePrimeCompletedEventArgs`為傳回給用戶端透過用戶端`CalculatePrimeCompletedEventHandler`。</span><span class="sxs-lookup"><span data-stu-id="c8412-176">It takes six parameters, which it uses to populate a `CalculatePrimeCompletedEventArgs` that is returned to the client through the client's `CalculatePrimeCompletedEventHandler`.</span></span> <span data-ttu-id="c8412-177">移除內部的集合，用戶端的工作 ID 語彙基元和結束非同步作業的存留期呼叫<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>。</span><span class="sxs-lookup"><span data-stu-id="c8412-177">It removes the client's task ID token from the internal collection, and it ends the asynchronous operation's lifetime with a call to <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>.</span></span> <span data-ttu-id="c8412-178"><xref:System.ComponentModel.AsyncOperation>封送處理呼叫的執行緒或適用於應用程式模型的內容。</span><span class="sxs-lookup"><span data-stu-id="c8412-178">The <xref:System.ComponentModel.AsyncOperation> marshals the call to the thread or context that is appropriate for the application model.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a><span data-ttu-id="c8412-179">檢查點</span><span class="sxs-lookup"><span data-stu-id="c8412-179">Checkpoint</span></span>  
 <span data-ttu-id="c8412-180">此時，您可以建立元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-180">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="c8412-181">若要測試您的元件</span><span class="sxs-lookup"><span data-stu-id="c8412-181">To test your component</span></span>  
  
-   <span data-ttu-id="c8412-182">編譯元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-182">Compile the component.</span></span>  
  
     <span data-ttu-id="c8412-183">您會收到一個編譯器警告：</span><span class="sxs-lookup"><span data-stu-id="c8412-183">You will receive one compiler warning:</span></span>  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     <span data-ttu-id="c8412-184">將在下一節中解決這個警告。</span><span class="sxs-lookup"><span data-stu-id="c8412-184">This warning will be resolved in the next section.</span></span>  
  
## <a name="implementing-the-worker-methods"></a><span data-ttu-id="c8412-185">實作工作者方法</span><span class="sxs-lookup"><span data-stu-id="c8412-185">Implementing the Worker Methods</span></span>  
 <span data-ttu-id="c8412-186">目前為止，您已實作的支援非同步程式碼`PrimeNumberCalculator`元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-186">So far, you have implemented the supporting asynchronous code for the `PrimeNumberCalculator` component.</span></span> <span data-ttu-id="c8412-187">現在，您可以實作到實際執行工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c8412-187">Now you can implement the code that does the actual work.</span></span> <span data-ttu-id="c8412-188">您會實作三種方法： `CalculateWorker`， `BuildPrimeNumberList`，和`IsPrime`。</span><span class="sxs-lookup"><span data-stu-id="c8412-188">You will implement three methods: `CalculateWorker`, `BuildPrimeNumberList`, and `IsPrime`.</span></span> <span data-ttu-id="c8412-189">在一起，`BuildPrimeNumberList`和`IsPrime`組成已知的演算法，稱為 Sieve Eratosthenes，可判斷數字是否為質數藉由尋找所有質數最大數字為測試數字的平方根。</span><span class="sxs-lookup"><span data-stu-id="c8412-189">Together, `BuildPrimeNumberList` and `IsPrime` comprise a well-known algorithm called the Sieve of Eratosthenes, which determines if a number is prime by finding all the prime numbers up to the square root of the test number.</span></span> <span data-ttu-id="c8412-190">如果找不到該點的任何除數，測試數字是質數。</span><span class="sxs-lookup"><span data-stu-id="c8412-190">If no divisors are found by that point, the test number is prime.</span></span>  
  
 <span data-ttu-id="c8412-191">如果此元件所撰寫的最大效率，它會記住不同測試的數字的各種引動過程所探索到的所有質數。</span><span class="sxs-lookup"><span data-stu-id="c8412-191">If this component were written for maximum efficiency, it would remember all the prime numbers discovered by various invocations for different test numbers.</span></span> <span data-ttu-id="c8412-192">它也會檢查普通除數像是 2、 3 和 5。</span><span class="sxs-lookup"><span data-stu-id="c8412-192">It would also check for trivial divisors like 2, 3, and 5.</span></span> <span data-ttu-id="c8412-193">此範例的目的是為了示範如何耗時的作業可以是以非同步方式執行，不過，讓這些最佳化會為您保留做為練習。</span><span class="sxs-lookup"><span data-stu-id="c8412-193">The intent of this example is to demonstrate how time-consuming operations can be executed asynchronously, however, so these optimizations are left as an exercise for you.</span></span>  
  
 <span data-ttu-id="c8412-194">`CalculateWorker`方法會包裝在委派中，並會以非同步方式叫用呼叫`BeginInvoke`。</span><span class="sxs-lookup"><span data-stu-id="c8412-194">The `CalculateWorker` method is wrapped in a delegate and is invoked asynchronously with a call to `BeginInvoke`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8412-195">進度報表在實作`BuildPrimeNumberList`方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-195">Progress reporting is implemented in the `BuildPrimeNumberList` method.</span></span> <span data-ttu-id="c8412-196">在快速的電腦上`ProgressChanged`可以快速而連續引發事件。</span><span class="sxs-lookup"><span data-stu-id="c8412-196">On fast computers, `ProgressChanged` events can be raised in rapid succession.</span></span> <span data-ttu-id="c8412-197">用戶端執行緒，在其會引發這些事件，必須能夠處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="c8412-197">The client thread, on which these events are raised, must be able to handle this situation.</span></span> <span data-ttu-id="c8412-198">使用者介面程式碼可能會大量湧入訊息且無法跟上，因此產生懸置行為。</span><span class="sxs-lookup"><span data-stu-id="c8412-198">User interface code may be flooded with messages and unable to keep up, resulting in hanging behavior.</span></span> <span data-ttu-id="c8412-199">範例使用者介面會處理此情況，請參閱[How to： 實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="c8412-199">For an example user interface that handles this situation, see [How to: Implement a Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a><span data-ttu-id="c8412-200">若要以非同步方式執行質數計算：</span><span class="sxs-lookup"><span data-stu-id="c8412-200">To execute the prime number calculation asynchronously:</span></span>  
  
1.  <span data-ttu-id="c8412-201">實作`TaskCanceled`公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-201">Implement the `TaskCanceled` utility method.</span></span> <span data-ttu-id="c8412-202">這會檢查指定的工作識別碼的工作存留期集合並傳回`true`如果找不到工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="c8412-202">This checks the task lifetime collection for the given task ID, and returns `true` if the task ID is not found.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  <span data-ttu-id="c8412-203">實作 `CalculateWorker` 方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-203">Implement the `CalculateWorker` method.</span></span> <span data-ttu-id="c8412-204">它會採用兩個參數： 一個數字，若要測試，和<xref:System.ComponentModel.AsyncOperation>。</span><span class="sxs-lookup"><span data-stu-id="c8412-204">It takes two parameters: a number to test, and an <xref:System.ComponentModel.AsyncOperation>.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  <span data-ttu-id="c8412-205">實作 `BuildPrimeNumberList`。</span><span class="sxs-lookup"><span data-stu-id="c8412-205">Implement `BuildPrimeNumberList`.</span></span> <span data-ttu-id="c8412-206">它會採用兩個參數： 要測試的數字和<xref:System.ComponentModel.AsyncOperation>。</span><span class="sxs-lookup"><span data-stu-id="c8412-206">It takes two parameters: the number to test, and an <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="c8412-207">它會使用<xref:System.ComponentModel.AsyncOperation>報告進度和累加結果。</span><span class="sxs-lookup"><span data-stu-id="c8412-207">It uses the <xref:System.ComponentModel.AsyncOperation> to report progress and incremental results.</span></span> <span data-ttu-id="c8412-208">如此可確保用戶端事件處理常式會呼叫適當的執行緒或應用程式模型的內容。</span><span class="sxs-lookup"><span data-stu-id="c8412-208">This assures that the client's event handlers are called on the proper thread or context for the application model.</span></span> <span data-ttu-id="c8412-209">當`BuildPrimeNumberList`質數的數字，會發現，它將此報告累加結果用戶端事件處理常式`ProgressChanged`事件。</span><span class="sxs-lookup"><span data-stu-id="c8412-209">When `BuildPrimeNumberList` finds a prime number, it reports this as an incremental result to the client's event handler for the `ProgressChanged` event.</span></span> <span data-ttu-id="c8412-210">這需要一個衍生自類別<xref:System.ComponentModel.ProgressChangedEventArgs>，稱為`CalculatePrimeProgressChangedEventArgs`，其中已加入一個稱為屬性`LatestPrimeNumber`。</span><span class="sxs-lookup"><span data-stu-id="c8412-210">This requires a class derived from <xref:System.ComponentModel.ProgressChangedEventArgs>, called `CalculatePrimeProgressChangedEventArgs`, which has one added property called `LatestPrimeNumber`.</span></span>  
  
     <span data-ttu-id="c8412-211">`BuildPrimeNumberList`方法也會定期呼叫`TaskCanceled`方法，如果此方法傳回的結束`true`。</span><span class="sxs-lookup"><span data-stu-id="c8412-211">The `BuildPrimeNumberList` method also periodically calls the `TaskCanceled` method and exits if the method returns `true`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  <span data-ttu-id="c8412-212">實作 `IsPrime`。</span><span class="sxs-lookup"><span data-stu-id="c8412-212">Implement `IsPrime`.</span></span> <span data-ttu-id="c8412-213">它會採用三個參數： 一份已知的質數、 要測試的數字的第一個找到的除數的輸出參數。</span><span class="sxs-lookup"><span data-stu-id="c8412-213">It takes three parameters: a list of known prime numbers, the number to test, and an output parameter for the first divisor found.</span></span> <span data-ttu-id="c8412-214">它會假設質數清單時，判斷測試數目是否為質數。</span><span class="sxs-lookup"><span data-stu-id="c8412-214">Given the list of prime numbers, it determines if the test number is prime.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  <span data-ttu-id="c8412-215">衍生`CalculatePrimeProgressChangedEventArgs`從<xref:System.ComponentModel.ProgressChangedEventArgs>。</span><span class="sxs-lookup"><span data-stu-id="c8412-215">Derive `CalculatePrimeProgressChangedEventArgs` from <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span> <span data-ttu-id="c8412-216">這個類別是所需的用戶端事件處理常式報告累加結果`ProgressChanged`事件。</span><span class="sxs-lookup"><span data-stu-id="c8412-216">This class is necessary for reporting incremental results to the client's event handler for the `ProgressChanged` event.</span></span> <span data-ttu-id="c8412-217">它有一個加入的屬性稱為`LatestPrimeNumber`。</span><span class="sxs-lookup"><span data-stu-id="c8412-217">It has one added property called `LatestPrimeNumber`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a><span data-ttu-id="c8412-218">檢查點</span><span class="sxs-lookup"><span data-stu-id="c8412-218">Checkpoint</span></span>  
 <span data-ttu-id="c8412-219">此時，您可以建立元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-219">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="c8412-220">若要測試您的元件</span><span class="sxs-lookup"><span data-stu-id="c8412-220">To test your component</span></span>  
  
-   <span data-ttu-id="c8412-221">編譯元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-221">Compile the component.</span></span>  
  
     <span data-ttu-id="c8412-222">會維持為寫入所有的啟動和取消非同步作業，方法`CalculatePrimeAsync`和`CancelAsync`。</span><span class="sxs-lookup"><span data-stu-id="c8412-222">All that remains to be written are the methods to start and cancel asynchronous operations, `CalculatePrimeAsync` and `CancelAsync`.</span></span>  
  
## <a name="implementing-the-start-and-cancel-methods"></a><span data-ttu-id="c8412-223">實作的開始和取消方法</span><span class="sxs-lookup"><span data-stu-id="c8412-223">Implementing the Start and Cancel Methods</span></span>  
 <span data-ttu-id="c8412-224">您在自己的執行緒上啟動工作者方法藉由呼叫`BeginInvoke`包裝它的委派上。</span><span class="sxs-lookup"><span data-stu-id="c8412-224">You start the worker method on its own thread by calling `BeginInvoke` on the delegate that wraps it.</span></span> <span data-ttu-id="c8412-225">若要管理特定的非同步作業的存留期，請呼叫<xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>方法<xref:System.ComponentModel.AsyncOperationManager>協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="c8412-225">To manage the lifetime of a particular asynchronous operation, you call the <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> method on the <xref:System.ComponentModel.AsyncOperationManager> helper class.</span></span> <span data-ttu-id="c8412-226">這會傳回<xref:System.ComponentModel.AsyncOperation>，其封送處理至適當的執行緒或內容在用戶端事件處理常式上呼叫。</span><span class="sxs-lookup"><span data-stu-id="c8412-226">This returns an <xref:System.ComponentModel.AsyncOperation>, which marshals calls on the client's event handlers to the proper thread or context.</span></span>  
  
 <span data-ttu-id="c8412-227">您藉由呼叫取消暫止作業的特定<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>上其對應<xref:System.ComponentModel.AsyncOperation>。</span><span class="sxs-lookup"><span data-stu-id="c8412-227">You cancel a particular pending operation by calling <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> on its corresponding <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="c8412-228">這樣會結束該作業和任何後續呼叫其<xref:System.ComponentModel.AsyncOperation>將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8412-228">This ends that operation, and any subsequent calls to its <xref:System.ComponentModel.AsyncOperation> will throw an exception.</span></span>  
  
#### <a name="to-implement-start-and-cancel-functionality"></a><span data-ttu-id="c8412-229">若要實作啟動和取消功能：</span><span class="sxs-lookup"><span data-stu-id="c8412-229">To implement Start and Cancel functionality:</span></span>  
  
1.  <span data-ttu-id="c8412-230">實作 `CalculatePrimeAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-230">Implement the `CalculatePrimeAsync` method.</span></span> <span data-ttu-id="c8412-231">請確定用戶端提供的語彙基元 (工作 ID) 都是唯一代表目前暫止工作的所有語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c8412-231">Make sure the client-supplied token (task ID) is unique with respect to all the tokens representing currently pending tasks.</span></span> <span data-ttu-id="c8412-232">如果用戶端會在非唯一的權杖中，`CalculatePrimeAsync`引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8412-232">If the client passes in a non-unique token, `CalculatePrimeAsync` raises an exception.</span></span> <span data-ttu-id="c8412-233">否則，語彙基元加入工作識別碼集合。</span><span class="sxs-lookup"><span data-stu-id="c8412-233">Otherwise, the token is added to the task ID collection.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  <span data-ttu-id="c8412-234">實作 `CancelAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-234">Implement the `CancelAsync` method.</span></span> <span data-ttu-id="c8412-235">如果`taskId`語彙基元的集合中的參數存在，就會移除。</span><span class="sxs-lookup"><span data-stu-id="c8412-235">If the `taskId` parameter exists in the token collection, it is removed.</span></span> <span data-ttu-id="c8412-236">這可防止已取消的工作尚未開始執行的。</span><span class="sxs-lookup"><span data-stu-id="c8412-236">This prevents canceled tasks that have not started from running.</span></span> <span data-ttu-id="c8412-237">如果工作執行時，`BuildPrimeNumberList`方法結束時偵測到工作識別碼已從存留期集合中移除。</span><span class="sxs-lookup"><span data-stu-id="c8412-237">If the task is running, the `BuildPrimeNumberList` method exits when it detects that the task ID has been removed from the lifetime collection.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a><span data-ttu-id="c8412-238">檢查點</span><span class="sxs-lookup"><span data-stu-id="c8412-238">Checkpoint</span></span>  
 <span data-ttu-id="c8412-239">此時，您可以建立元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-239">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="c8412-240">若要測試您的元件</span><span class="sxs-lookup"><span data-stu-id="c8412-240">To test your component</span></span>  
  
-   <span data-ttu-id="c8412-241">編譯元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-241">Compile the component.</span></span>  
  
 <span data-ttu-id="c8412-242">`PrimeNumberCalculator`元件現在已完成且可供使用。</span><span class="sxs-lookup"><span data-stu-id="c8412-242">The `PrimeNumberCalculator` component is now complete and ready to use.</span></span>  
  
 <span data-ttu-id="c8412-243">範例用戶端使用`PrimeNumberCalculator`元件，請參閱[How to： 實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="c8412-243">For an example client that uses the `PrimeNumberCalculator` component, see [How to: Implement a Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c8412-244">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c8412-244">Next Steps</span></span>  
 <span data-ttu-id="c8412-245">您可以藉由撰寫填寫此範例`CalculatePrime`，相當於同步`CalculatePrimeAsync`方法。</span><span class="sxs-lookup"><span data-stu-id="c8412-245">You can fill out this example by writing `CalculatePrime`, the synchronous equivalent of `CalculatePrimeAsync` method.</span></span> <span data-ttu-id="c8412-246">這會讓`PrimeNumberCalculator`完全遵循事件架構非同步模式的元件。</span><span class="sxs-lookup"><span data-stu-id="c8412-246">This will make the `PrimeNumberCalculator` component fully compliant with the Event-based Asynchronous Pattern.</span></span>  
  
 <span data-ttu-id="c8412-247">您可以藉由保留不同的測試數字的各種引動過程所探索到的所有質數清單改善此範例。</span><span class="sxs-lookup"><span data-stu-id="c8412-247">You can improve this example by retaining the list of all the prime numbers discovered by various invocations for different test numbers.</span></span> <span data-ttu-id="c8412-248">使用這個方法，每項工作將受益於先前的工作所完成的工作。</span><span class="sxs-lookup"><span data-stu-id="c8412-248">Using this approach, each task will benefit from the work done by previous tasks.</span></span> <span data-ttu-id="c8412-249">謹慎保護這份清單與`lock`區域，所以由不同的執行緒清單的存取序列化的。</span><span class="sxs-lookup"><span data-stu-id="c8412-249">Be careful to protect this list with `lock` regions, so access to the list by different threads is serialized.</span></span>  
  
 <span data-ttu-id="c8412-250">您也可以改善這個範例藉由測試普通除數，例如 2、 3 和 5。</span><span class="sxs-lookup"><span data-stu-id="c8412-250">You can also improve this example by testing for trivial divisors, like 2, 3, and 5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8412-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8412-251">See Also</span></span>  
 [<span data-ttu-id="c8412-252">操作說明：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="c8412-252">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="c8412-253">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="c8412-253">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="c8412-254">不在組建中： Visual Basic 中的多執行緒</span><span class="sxs-lookup"><span data-stu-id="c8412-254">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="c8412-255">操作說明：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="c8412-255">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="c8412-256">使用事件架構非同步模式設計多執行緒程式</span><span class="sxs-lookup"><span data-stu-id="c8412-256">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
