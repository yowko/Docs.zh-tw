---
title: 作法：實作支援事件架構非同步模式的元件
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: bc19ee687b26025d3da4d66888902395b863f046
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64628920"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a><span data-ttu-id="a1d18-102">作法：實作支援事件架構非同步模式的元件</span><span class="sxs-lookup"><span data-stu-id="a1d18-102">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="a1d18-103">如果您正在撰寫的類別含有一些可能造成明顯延遲的作業，請考慮實作[事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)，來為它提供非同步功能。</span><span class="sxs-lookup"><span data-stu-id="a1d18-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="a1d18-104">本逐步解說說明如何建立實作「事件架構非同步模式」的元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-104">This walkthrough illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="a1d18-105">其實作方式是使用 <xref:System.ComponentModel?displayProperty=nameWithType> 命名空間中的協助程式類別，以確保此元件在任何應用程式模型下都能正常運作，包括 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、主控台應用程式及 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1d18-105">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications and Windows Forms applications.</span></span> <span data-ttu-id="a1d18-106">您也可以使用 <xref:System.Windows.Forms.PropertyGrid> 控制項和您自己的自訂設計工具來設計此元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-106">This component is also designable with a <xref:System.Windows.Forms.PropertyGrid> control and your own custom designers.</span></span>  
  
 <span data-ttu-id="a1d18-107">完成時，您將擁有一個以非同步方式計算質數的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1d18-107">When you are through, you will have an application that computes prime numbers asynchronously.</span></span> <span data-ttu-id="a1d18-108">您的應用程式將會有一個主要使用者介面 (UI) 執行緒，以及一個用來計算每個質數的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a1d18-108">Your application will have a main user interface (UI) thread and a thread for each prime number calculation.</span></span> <span data-ttu-id="a1d18-109">雖然測試一個大數是否為質數所需的時間很長，但主要 UI 執行緒並不會被此延遲打斷，在計算期間表單將能持續回應。</span><span class="sxs-lookup"><span data-stu-id="a1d18-109">Although testing whether a large number is prime can take a noticeable amount of time, the main UI thread will not be interrupted by this delay, and the form will be responsive during the calculations.</span></span> <span data-ttu-id="a1d18-110">您將能夠想要執行多少次計算就同時執行多少次計算，並選擇性地取消擱置中的計算。</span><span class="sxs-lookup"><span data-stu-id="a1d18-110">You will be able to run as many calculations as you like concurrently and selectively cancel pending calculations.</span></span>  
  
 <span data-ttu-id="a1d18-111">這個逐步解說中所述的工作包括：</span><span class="sxs-lookup"><span data-stu-id="a1d18-111">Tasks illustrated in this walkthrough include:</span></span>  
  
- <span data-ttu-id="a1d18-112">建立元件</span><span class="sxs-lookup"><span data-stu-id="a1d18-112">Creating the Component</span></span>  
  
- <span data-ttu-id="a1d18-113">定義公用非同步事件和委派</span><span class="sxs-lookup"><span data-stu-id="a1d18-113">Defining Public Asynchronous Events and Delegates</span></span>  
  
- <span data-ttu-id="a1d18-114">定義私用委派</span><span class="sxs-lookup"><span data-stu-id="a1d18-114">Defining Private Delegates</span></span>  
  
- <span data-ttu-id="a1d18-115">實作公用事件</span><span class="sxs-lookup"><span data-stu-id="a1d18-115">Implementing Public Events</span></span>  
  
- <span data-ttu-id="a1d18-116">實作完成方法</span><span class="sxs-lookup"><span data-stu-id="a1d18-116">Implementing the Completion Method</span></span>  
  
- <span data-ttu-id="a1d18-117">實作背景工作方法</span><span class="sxs-lookup"><span data-stu-id="a1d18-117">Implementing the Worker Methods</span></span>  
  
- <span data-ttu-id="a1d18-118">實作開始和取消方法</span><span class="sxs-lookup"><span data-stu-id="a1d18-118">Implementing Start and Cancel Methods</span></span>  
  
 <span data-ttu-id="a1d18-119">若要將此主題中的程式碼複製為單一清單，請參閱[如何：實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="a1d18-119">To copy the code in this topic as a single listing, see [How to: Implement a Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="creating-the-component"></a><span data-ttu-id="a1d18-120">建立元件</span><span class="sxs-lookup"><span data-stu-id="a1d18-120">Creating the Component</span></span>  
 <span data-ttu-id="a1d18-121">第一步是建立將會實作「事件架構非同步模式」的元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-121">The first step is to create the component that will implement the Event-based Asynchronous Pattern.</span></span>  
  
#### <a name="to-create-the-component"></a><span data-ttu-id="a1d18-122">建立元件</span><span class="sxs-lookup"><span data-stu-id="a1d18-122">To create the component</span></span>  
  
- <span data-ttu-id="a1d18-123">建立一個名為 `PrimeNumberCalculator` 且會從 <xref:System.ComponentModel.Component> 繼承的類別。</span><span class="sxs-lookup"><span data-stu-id="a1d18-123">Create a class called `PrimeNumberCalculator` that inherits from <xref:System.ComponentModel.Component>.</span></span>  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a><span data-ttu-id="a1d18-124">定義公用非同步事件和委派</span><span class="sxs-lookup"><span data-stu-id="a1d18-124">Defining Public Asynchronous Events and Delegates</span></span>  
 <span data-ttu-id="a1d18-125">您的元件會使用事件與用戶端進行通訊。</span><span class="sxs-lookup"><span data-stu-id="a1d18-125">Your component communicates to clients using events.</span></span> <span data-ttu-id="a1d18-126">_MethodName_**Completed** 事件會對用戶端發出已完成非同步工作的警示，而 _MethodName_**ProgressChanged** 事件則是會通知用戶端非同步工作的進度。</span><span class="sxs-lookup"><span data-stu-id="a1d18-126">The _MethodName_**Completed** event alerts clients to the completion of an asynchronous task, and the _MethodName_**ProgressChanged** event informs clients of the progress of an asynchronous task.</span></span>  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a><span data-ttu-id="a1d18-127">為元件的用戶端定義非同步事件：</span><span class="sxs-lookup"><span data-stu-id="a1d18-127">To define asynchronous events for clients of your component:</span></span>  
  
1. <span data-ttu-id="a1d18-128">在您檔案的頂端匯入 <xref:System.Threading?displayProperty=nameWithType> 和 <xref:System.Collections.Specialized?displayProperty=nameWithType> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="a1d18-128">Import the <xref:System.Threading?displayProperty=nameWithType> and <xref:System.Collections.Specialized?displayProperty=nameWithType> namespaces at the top of your file.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. <span data-ttu-id="a1d18-129">在 `PrimeNumberCalculator` 類別定義之前，宣告進度和完成事件的委派。</span><span class="sxs-lookup"><span data-stu-id="a1d18-129">Before the `PrimeNumberCalculator` class definition, declare delegates for progress and completion events.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. <span data-ttu-id="a1d18-130">在 `PrimeNumberCalculator` 類別定義中，宣告用來向用戶端回報進度和完成的事件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-130">In the `PrimeNumberCalculator` class definition, declare events for reporting progress and completion to clients.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. <span data-ttu-id="a1d18-131">在 `PrimeNumberCalculator` 類別定義之後，衍生用來向 `CalculatePrimeCompleted`. 事件的用戶端事件處理常式回報每個計算結果的 `CalculatePrimeCompletedEventArgs` 類別。</span><span class="sxs-lookup"><span data-stu-id="a1d18-131">After the `PrimeNumberCalculator` class definition, derive the `CalculatePrimeCompletedEventArgs` class for reporting the outcome of each calculation to the client's event handler for the `CalculatePrimeCompleted`.event.</span></span> <span data-ttu-id="a1d18-132">除了 `AsyncCompletedEventArgs` 屬性之外，此類別還可讓用戶端判斷所測試的數字為何、是否為質數，以及如果該數字不是質數，第一個除數為何。</span><span class="sxs-lookup"><span data-stu-id="a1d18-132">In addition to the `AsyncCompletedEventArgs` properties, this class enables the client to determine what number was tested, whether it is prime, and what the first divisor is if it is not prime.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a><span data-ttu-id="a1d18-133">檢查點</span><span class="sxs-lookup"><span data-stu-id="a1d18-133">Checkpoint</span></span>  
 <span data-ttu-id="a1d18-134">現在，您可以建置元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-134">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="a1d18-135">測試元件</span><span class="sxs-lookup"><span data-stu-id="a1d18-135">To test your component</span></span>  
  
- <span data-ttu-id="a1d18-136">編譯元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-136">Compile the component.</span></span>  
  
     <span data-ttu-id="a1d18-137">您將會收到兩個編譯器警告：</span><span class="sxs-lookup"><span data-stu-id="a1d18-137">You will receive two compiler warnings:</span></span>  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     <span data-ttu-id="a1d18-138">在下一節中將會清除這些警告。</span><span class="sxs-lookup"><span data-stu-id="a1d18-138">These warnings will be cleared in the next section.</span></span>  
  
## <a name="defining-private-delegates"></a><span data-ttu-id="a1d18-139">定義私用委派</span><span class="sxs-lookup"><span data-stu-id="a1d18-139">Defining Private Delegates</span></span>  
 <span data-ttu-id="a1d18-140">實作 `PrimeNumberCalculator` 元件的非同步層面時，會在內部使用稱為 <xref:System.Threading.SendOrPostCallback> 的特殊委派來實作。</span><span class="sxs-lookup"><span data-stu-id="a1d18-140">The asynchronous aspects of the `PrimeNumberCalculator` component are implemented internally with a special delegate known as a <xref:System.Threading.SendOrPostCallback>.</span></span> <span data-ttu-id="a1d18-141"><xref:System.Threading.SendOrPostCallback> 代表在 <xref:System.Threading.ThreadPool> 執行緒上執行的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-141">A <xref:System.Threading.SendOrPostCallback> represents a callback method that executes on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="a1d18-142">此回呼方法必須具有會採用 <xref:System.Object> 類型之單一參數的簽章，這意謂著您將必須在包裝函式類別中傳遞委派之間的狀態。</span><span class="sxs-lookup"><span data-stu-id="a1d18-142">The callback method must have a signature that takes a single parameter of type <xref:System.Object>, which means you will need to pass state among delegates in a wrapper class.</span></span> <span data-ttu-id="a1d18-143">如需詳細資訊，請參閱<xref:System.Threading.SendOrPostCallback>。</span><span class="sxs-lookup"><span data-stu-id="a1d18-143">For more information, see <xref:System.Threading.SendOrPostCallback>.</span></span>  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a><span data-ttu-id="a1d18-144">實作元件的內部非同步行為：</span><span class="sxs-lookup"><span data-stu-id="a1d18-144">To implement your component's internal asynchronous behavior:</span></span>  
  
1. <span data-ttu-id="a1d18-145">在 `PrimeNumberCalculator` 類別中宣告及建立 <xref:System.Threading.SendOrPostCallback> 委派。</span><span class="sxs-lookup"><span data-stu-id="a1d18-145">Declare and create the <xref:System.Threading.SendOrPostCallback> delegates in the `PrimeNumberCalculator` class.</span></span> <span data-ttu-id="a1d18-146">在名為 `InitializeDelegates` 的公用程式方法中建立 <xref:System.Threading.SendOrPostCallback> 物件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-146">Create the <xref:System.Threading.SendOrPostCallback> objects in a utility method called `InitializeDelegates`.</span></span>  
  
     <span data-ttu-id="a1d18-147">您將需要兩個委派：一個用來向用戶端回報進度，另一個用來向用戶端回報完成。</span><span class="sxs-lookup"><span data-stu-id="a1d18-147">You will need two delegates: one for reporting progress to the client, and one for reporting completion to the client.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. <span data-ttu-id="a1d18-148">在您元件的建構函式中呼叫 `InitializeDelegates` 方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-148">Call the `InitializeDelegates` method in your component's constructor.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. <span data-ttu-id="a1d18-149">在處理要非同步執行之實際工作的 `PrimeNumberCalculator` 類別中宣告委派。</span><span class="sxs-lookup"><span data-stu-id="a1d18-149">Declare a delegate in the `PrimeNumberCalculator` class that handles the actual work to be done asynchronously.</span></span> <span data-ttu-id="a1d18-150">這個委派會包裝測試數字是否為質數的背景工作方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-150">This delegate wraps the worker method that tests whether a number is prime.</span></span> <span data-ttu-id="a1d18-151">此委派會採用 <xref:System.ComponentModel.AsyncOperation> 參數，此參數將用來追蹤非同步作業的存留期。</span><span class="sxs-lookup"><span data-stu-id="a1d18-151">The delegate takes an <xref:System.ComponentModel.AsyncOperation> parameter, which will be used to track the lifetime of the asynchronous operation.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. <span data-ttu-id="a1d18-152">建立一個用來管理擱置中非同步作業的集合。</span><span class="sxs-lookup"><span data-stu-id="a1d18-152">Create a collection for managing lifetimes of pending asynchronous operations.</span></span> <span data-ttu-id="a1d18-153">用戶端需要一個可追蹤作業執行和完成狀態的方式，而此追蹤的執行方式是在用戶端對非同步方法發出呼叫時，要求用戶端傳遞唯一的權杖或工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="a1d18-153">The client needs a way to track operations as they are executed and completed, and this tracking is done by requiring the client to pass a unique token, or task ID, when the client makes the call to the asynchronous method.</span></span> <span data-ttu-id="a1d18-154">`PrimeNumberCalculator` 元件必須將工作識別碼與其對應的引動過程建立關聯，來追蹤每個呼叫。</span><span class="sxs-lookup"><span data-stu-id="a1d18-154">The `PrimeNumberCalculator` component must keep track of each call by associating the task ID with its corresponding invocation.</span></span> <span data-ttu-id="a1d18-155">如果用戶端傳遞的工作識別碼不是唯一的，`PrimeNumberCalculator` 元件必須引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1d18-155">If the client passes a task ID that is not unique, the `PrimeNumberCalculator` component must raise an exception.</span></span>  
  
     <span data-ttu-id="a1d18-156">`PrimeNumberCalculator` 元件會使用一個名為 <xref:System.Collections.Specialized.HybridDictionary> 的特殊集合類別來追蹤工作識別碼。</span><span class="sxs-lookup"><span data-stu-id="a1d18-156">The `PrimeNumberCalculator` component keeps track of task ID by using a special collection class called a <xref:System.Collections.Specialized.HybridDictionary>.</span></span> <span data-ttu-id="a1d18-157">在類別定義中，建立名為 `userTokenToLifetime` 的 <xref:System.Collections.Specialized.HybridDictionary>。</span><span class="sxs-lookup"><span data-stu-id="a1d18-157">In the class definition, create a <xref:System.Collections.Specialized.HybridDictionary> called `userTokenToLifetime`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a><span data-ttu-id="a1d18-158">實作公用事件</span><span class="sxs-lookup"><span data-stu-id="a1d18-158">Implementing Public Events</span></span>  
 <span data-ttu-id="a1d18-159">實作「事件架構非同步模式」的元件會使用事件與用戶端進行通訊。</span><span class="sxs-lookup"><span data-stu-id="a1d18-159">Components that implement the Event-based Asynchronous Pattern communicate to clients using events.</span></span> <span data-ttu-id="a1d18-160">叫用這些事件時，會在 <xref:System.ComponentModel.AsyncOperation> 類別的協助下，在適當的執行緒上叫用。</span><span class="sxs-lookup"><span data-stu-id="a1d18-160">These events are invoked on the proper thread with the help of the <xref:System.ComponentModel.AsyncOperation> class.</span></span>  
  
#### <a name="to-raise-events-to-your-components-clients"></a><span data-ttu-id="a1d18-161">向元件的用戶端引發事件：</span><span class="sxs-lookup"><span data-stu-id="a1d18-161">To raise events to your component's clients:</span></span>  
  
1. <span data-ttu-id="a1d18-162">實作可向用戶端進行回報的公用事件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-162">Implement public events for reporting to clients.</span></span> <span data-ttu-id="a1d18-163">您將需要一個事件來回報進度，另一個事件來回報完成。</span><span class="sxs-lookup"><span data-stu-id="a1d18-163">You will need an event for reporting progress and one for reporting completion.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a><span data-ttu-id="a1d18-164">實作完成方法</span><span class="sxs-lookup"><span data-stu-id="a1d18-164">Implementing the Completion Method</span></span>  
 <span data-ttu-id="a1d18-165">完成委派是當非同步作業以成功完成、發生錯誤或取消作為結束時，基礎無限制執行緒非同步行為將叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-165">The completion delegate is the method that the underlying, free-threaded asynchronous behavior will invoke when the asynchronous operation ends by successful completion, error, or cancellation.</span></span> <span data-ttu-id="a1d18-166">此引動過程會在任意的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="a1d18-166">This invocation happens on an arbitrary thread.</span></span>  
  
 <span data-ttu-id="a1d18-167">從唯一用戶端權杖的內部集合移除用戶端工作識別碼時，就是在此方法中進行。</span><span class="sxs-lookup"><span data-stu-id="a1d18-167">This method is where the client's task ID is removed from the internal collection of unique client tokens.</span></span> <span data-ttu-id="a1d18-168">此方法也會藉由呼叫對應之 <xref:System.ComponentModel.AsyncOperation> 上的 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 方法，來結束特定非同步作業的存留期。</span><span class="sxs-lookup"><span data-stu-id="a1d18-168">This method also ends the lifetime of a particular asynchronous operation by calling the <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> method on the corresponding <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="a1d18-169">此呼叫會在適用於應用程式模型的執行緒上引發完成事件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-169">This call raises the completion event on the thread that is appropriate for the application model.</span></span> <span data-ttu-id="a1d18-170">在呼叫 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 方法之後，即無法再使用這個 <xref:System.ComponentModel.AsyncOperation> 執行個體，後續所有嘗試使用它的行為都會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1d18-170">After the <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> method is called, this instance of <xref:System.ComponentModel.AsyncOperation> can no longer be used, and any subsequent attempts to use it will throw an exception.</span></span>  
  
 <span data-ttu-id="a1d18-171">`CompletionMethod` 簽章必須保存描述非同步作業結果所需的所有狀態。</span><span class="sxs-lookup"><span data-stu-id="a1d18-171">The `CompletionMethod` signature must hold all state necessary to describe the outcome of the asynchronous operation.</span></span> <span data-ttu-id="a1d18-172">它會保存此特定非同步作業所測試的數字、該數字是否為質數，以及該數字第一個除數的值 (如果該數字不是質數的話)。</span><span class="sxs-lookup"><span data-stu-id="a1d18-172">It holds state for the number that was tested by this particular asynchronous operation, whether the number is prime, and the value of its first divisor if it is not a prime number.</span></span> <span data-ttu-id="a1d18-173">它也會保存描述所發生之任何例外狀況的狀態，以及與此特定工作對應的 <xref:System.ComponentModel.AsyncOperation>。</span><span class="sxs-lookup"><span data-stu-id="a1d18-173">It also holds state describing any exception that occurred, and the <xref:System.ComponentModel.AsyncOperation> corresponding to this particular task.</span></span>  
  
#### <a name="to-complete-an-asynchronous-operation"></a><span data-ttu-id="a1d18-174">完成非同步作業：</span><span class="sxs-lookup"><span data-stu-id="a1d18-174">To complete an asynchronous operation:</span></span>  
  
- <span data-ttu-id="a1d18-175">實作完成方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-175">Implement the completion method.</span></span> <span data-ttu-id="a1d18-176">此方法採用六個參數，用來填入會透過用戶端的 `CalculatePrimeCompletedEventHandler`.傳回到用戶端的 `CalculatePrimeCompletedEventArgs`。</span><span class="sxs-lookup"><span data-stu-id="a1d18-176">It takes six parameters, which it uses to populate a `CalculatePrimeCompletedEventArgs` that is returned to the client through the client's `CalculatePrimeCompletedEventHandler`.</span></span> <span data-ttu-id="a1d18-177">它會從內部集合移除用戶端的工作識別碼權杖，然後藉由對 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> 的呼叫來結束非同步作業的存留期。</span><span class="sxs-lookup"><span data-stu-id="a1d18-177">It removes the client's task ID token from the internal collection, and it ends the asynchronous operation's lifetime with a call to <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>.</span></span> <span data-ttu-id="a1d18-178"><xref:System.ComponentModel.AsyncOperation> 會將呼叫封送處理至適用於應用程式模型的執行緒或內容。</span><span class="sxs-lookup"><span data-stu-id="a1d18-178">The <xref:System.ComponentModel.AsyncOperation> marshals the call to the thread or context that is appropriate for the application model.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a><span data-ttu-id="a1d18-179">檢查點</span><span class="sxs-lookup"><span data-stu-id="a1d18-179">Checkpoint</span></span>  
 <span data-ttu-id="a1d18-180">現在，您可以建置元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-180">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="a1d18-181">測試元件</span><span class="sxs-lookup"><span data-stu-id="a1d18-181">To test your component</span></span>  
  
- <span data-ttu-id="a1d18-182">編譯元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-182">Compile the component.</span></span>  
  
     <span data-ttu-id="a1d18-183">您將會收到一個編譯器警告：</span><span class="sxs-lookup"><span data-stu-id="a1d18-183">You will receive one compiler warning:</span></span>  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     <span data-ttu-id="a1d18-184">在下一節中將會解決此警告。</span><span class="sxs-lookup"><span data-stu-id="a1d18-184">This warning will be resolved in the next section.</span></span>  
  
## <a name="implementing-the-worker-methods"></a><span data-ttu-id="a1d18-185">實作背景工作方法</span><span class="sxs-lookup"><span data-stu-id="a1d18-185">Implementing the Worker Methods</span></span>  
 <span data-ttu-id="a1d18-186">到目前為止，您已經為 `PrimeNumberCalculator` 元件實作提供支援的非同步程式碼。</span><span class="sxs-lookup"><span data-stu-id="a1d18-186">So far, you have implemented the supporting asynchronous code for the `PrimeNumberCalculator` component.</span></span> <span data-ttu-id="a1d18-187">現在，您可以實作執行實際工作的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a1d18-187">Now you can implement the code that does the actual work.</span></span> <span data-ttu-id="a1d18-188">您將實作三個方法：`CalculateWorker``BuildPrimeNumberList` 及 `IsPrime`。</span><span class="sxs-lookup"><span data-stu-id="a1d18-188">You will implement three methods: `CalculateWorker`, `BuildPrimeNumberList`, and `IsPrime`.</span></span> <span data-ttu-id="a1d18-189">`BuildPrimeNumberList` 與 `IsPrime` 一起會構成稱為「埃拉托斯特尼篩法」(Sieve of Eratosthenes) 的著名演算法，此演算法可藉由尋找所有質數，最大可到測試數字的平方根為止，來判斷數字是否為質數。</span><span class="sxs-lookup"><span data-stu-id="a1d18-189">Together, `BuildPrimeNumberList` and `IsPrime` comprise a well-known algorithm called the Sieve of Eratosthenes, which determines if a number is prime by finding all the prime numbers up to the square root of the test number.</span></span> <span data-ttu-id="a1d18-190">如果到該點為止未發現任何除數，即表示該測試數字為質數。</span><span class="sxs-lookup"><span data-stu-id="a1d18-190">If no divisors are found by that point, the test number is prime.</span></span>  
  
 <span data-ttu-id="a1d18-191">如果此元件的撰寫目的是要發揮最高效率，它就會記住不同測試數字的各種引動過程所探索到的所有質數。</span><span class="sxs-lookup"><span data-stu-id="a1d18-191">If this component were written for maximum efficiency, it would remember all the prime numbers discovered by various invocations for different test numbers.</span></span> <span data-ttu-id="a1d18-192">此外，它也會檢查是否有平凡除數，例如 2、3 及 5。</span><span class="sxs-lookup"><span data-stu-id="a1d18-192">It would also check for trivial divisors like 2, 3, and 5.</span></span> <span data-ttu-id="a1d18-193">此範例的目的是要示範如何以非同步方式執行耗時的作業，不過，也因此這些最佳化會留給您作為練習。</span><span class="sxs-lookup"><span data-stu-id="a1d18-193">The intent of this example is to demonstrate how time-consuming operations can be executed asynchronously, however, so these optimizations are left as an exercise for you.</span></span>  
  
 <span data-ttu-id="a1d18-194">`CalculateWorker` 方法會包裝在委派中，且叫用此方法時，會藉由對 `BeginInvoke` 的呼叫以非同步方式叫用。</span><span class="sxs-lookup"><span data-stu-id="a1d18-194">The `CalculateWorker` method is wrapped in a delegate and is invoked asynchronously with a call to `BeginInvoke`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1d18-195">實作進度回報時，是在 `BuildPrimeNumberList` 方法中實作。</span><span class="sxs-lookup"><span data-stu-id="a1d18-195">Progress reporting is implemented in the `BuildPrimeNumberList` method.</span></span> <span data-ttu-id="a1d18-196">在執行速度快的電腦上，可以快速地連續引發 `ProgressChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-196">On fast computers, `ProgressChanged` events can be raised in rapid succession.</span></span> <span data-ttu-id="a1d18-197">作為這些事件之引發位置的用戶端執行緒必須能夠處理此情況。</span><span class="sxs-lookup"><span data-stu-id="a1d18-197">The client thread, on which these events are raised, must be able to handle this situation.</span></span> <span data-ttu-id="a1d18-198">使用者介面程式碼可能會湧入大量訊息而來不及處理，導致產生當機行為。</span><span class="sxs-lookup"><span data-stu-id="a1d18-198">User interface code may be flooded with messages and unable to keep up, resulting in hanging behavior.</span></span> <span data-ttu-id="a1d18-199">如需可處理此情形的使用者介面範例，請參閱[如何：實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="a1d18-199">For an example user interface that handles this situation, see [How to: Implement a Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a><span data-ttu-id="a1d18-200">以非同步方式執行質數計算：</span><span class="sxs-lookup"><span data-stu-id="a1d18-200">To execute the prime number calculation asynchronously:</span></span>  
  
1. <span data-ttu-id="a1d18-201">實作 `TaskCanceled` 公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-201">Implement the `TaskCanceled` utility method.</span></span> <span data-ttu-id="a1d18-202">這會檢查指定之工作識別碼的工作存留期集合，如果找不到該工作識別碼，就會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="a1d18-202">This checks the task lifetime collection for the given task ID, and returns `true` if the task ID is not found.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. <span data-ttu-id="a1d18-203">實作 `CalculateWorker` 方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-203">Implement the `CalculateWorker` method.</span></span> <span data-ttu-id="a1d18-204">此方法採用兩個參數：要測試的數字和 <xref:System.ComponentModel.AsyncOperation>。</span><span class="sxs-lookup"><span data-stu-id="a1d18-204">It takes two parameters: a number to test, and an <xref:System.ComponentModel.AsyncOperation>.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. <span data-ttu-id="a1d18-205">實作 `BuildPrimeNumberList`。</span><span class="sxs-lookup"><span data-stu-id="a1d18-205">Implement `BuildPrimeNumberList`.</span></span> <span data-ttu-id="a1d18-206">此方法採用兩個參數：要測試的數字和 <xref:System.ComponentModel.AsyncOperation>。</span><span class="sxs-lookup"><span data-stu-id="a1d18-206">It takes two parameters: the number to test, and an <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="a1d18-207">它會使用 <xref:System.ComponentModel.AsyncOperation> 來回報進度和累加結果。</span><span class="sxs-lookup"><span data-stu-id="a1d18-207">It uses the <xref:System.ComponentModel.AsyncOperation> to report progress and incremental results.</span></span> <span data-ttu-id="a1d18-208">這可確保在應用程式模型的適當執行緒或內容上呼叫用戶端的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a1d18-208">This assures that the client's event handlers are called on the proper thread or context for the application model.</span></span> <span data-ttu-id="a1d18-209">當 `BuildPrimeNumberList` 找到質數時，它會以累加結果的方式，向 `ProgressChanged` 事件的用戶端事件處理常式回報此質數。</span><span class="sxs-lookup"><span data-stu-id="a1d18-209">When `BuildPrimeNumberList` finds a prime number, it reports this as an incremental result to the client's event handler for the `ProgressChanged` event.</span></span> <span data-ttu-id="a1d18-210">這需要一個衍生自 <xref:System.ComponentModel.ProgressChangedEventArgs> 的類別 (稱為 `CalculatePrimeProgressChangedEventArgs`)，此類別具有一個稱為 `LatestPrimeNumber` 的附加屬性。</span><span class="sxs-lookup"><span data-stu-id="a1d18-210">This requires a class derived from <xref:System.ComponentModel.ProgressChangedEventArgs>, called `CalculatePrimeProgressChangedEventArgs`, which has one added property called `LatestPrimeNumber`.</span></span>  
  
     <span data-ttu-id="a1d18-211">`BuildPrimeNumberList` 方法也會定期呼叫 `TaskCanceled` 方法，如果此方法傳回 `true`，就會結束。</span><span class="sxs-lookup"><span data-stu-id="a1d18-211">The `BuildPrimeNumberList` method also periodically calls the `TaskCanceled` method and exits if the method returns `true`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. <span data-ttu-id="a1d18-212">實作 `IsPrime`。</span><span class="sxs-lookup"><span data-stu-id="a1d18-212">Implement `IsPrime`.</span></span> <span data-ttu-id="a1d18-213">此方法採用三個參數：已知的質數清單、要測試的數字，以及所找到之第一個除數的輸出參數。</span><span class="sxs-lookup"><span data-stu-id="a1d18-213">It takes three parameters: a list of known prime numbers, the number to test, and an output parameter for the first divisor found.</span></span> <span data-ttu-id="a1d18-214">在有質數清單的情況下，它會判斷測試數字是否為質數。</span><span class="sxs-lookup"><span data-stu-id="a1d18-214">Given the list of prime numbers, it determines if the test number is prime.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. <span data-ttu-id="a1d18-215">從 <xref:System.ComponentModel.ProgressChangedEventArgs>衍生 `CalculatePrimeProgressChangedEventArgs`。</span><span class="sxs-lookup"><span data-stu-id="a1d18-215">Derive `CalculatePrimeProgressChangedEventArgs` from <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span> <span data-ttu-id="a1d18-216">此類別是向 `ProgressChanged` 事件的用戶端事件處理常式回報累加結果的必要類別。</span><span class="sxs-lookup"><span data-stu-id="a1d18-216">This class is necessary for reporting incremental results to the client's event handler for the `ProgressChanged` event.</span></span> <span data-ttu-id="a1d18-217">它有一個稱為 `LatestPrimeNumber`的附加屬性。</span><span class="sxs-lookup"><span data-stu-id="a1d18-217">It has one added property called `LatestPrimeNumber`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a><span data-ttu-id="a1d18-218">檢查點</span><span class="sxs-lookup"><span data-stu-id="a1d18-218">Checkpoint</span></span>  
 <span data-ttu-id="a1d18-219">現在，您可以建置元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-219">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="a1d18-220">測試元件</span><span class="sxs-lookup"><span data-stu-id="a1d18-220">To test your component</span></span>  
  
- <span data-ttu-id="a1d18-221">編譯元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-221">Compile the component.</span></span>  
  
     <span data-ttu-id="a1d18-222">剩下要撰寫的只有用來開始和取消非同步作業的方法 `CalculatePrimeAsync` 和 `CancelAsync`。</span><span class="sxs-lookup"><span data-stu-id="a1d18-222">All that remains to be written are the methods to start and cancel asynchronous operations, `CalculatePrimeAsync` and `CancelAsync`.</span></span>  
  
## <a name="implementing-the-start-and-cancel-methods"></a><span data-ttu-id="a1d18-223">實作開始和取消方法</span><span class="sxs-lookup"><span data-stu-id="a1d18-223">Implementing the Start and Cancel Methods</span></span>  
 <span data-ttu-id="a1d18-224">開始背景工作方法的方式，是在背景工作方法自己的執行緒上，呼叫包裝它之委派上的 `BeginInvoke`。</span><span class="sxs-lookup"><span data-stu-id="a1d18-224">You start the worker method on its own thread by calling `BeginInvoke` on the delegate that wraps it.</span></span> <span data-ttu-id="a1d18-225">若要管理特定非同步作業的存留期，您需呼叫 <xref:System.ComponentModel.AsyncOperationManager> 協助程式類別上的 <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-225">To manage the lifetime of a particular asynchronous operation, you call the <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> method on the <xref:System.ComponentModel.AsyncOperationManager> helper class.</span></span> <span data-ttu-id="a1d18-226">這會傳回 <xref:System.ComponentModel.AsyncOperation> 以將用戶端事件處理常式上的呼叫封送處理至適當的執行緒或內容。</span><span class="sxs-lookup"><span data-stu-id="a1d18-226">This returns an <xref:System.ComponentModel.AsyncOperation>, which marshals calls on the client's event handlers to the proper thread or context.</span></span>  
  
 <span data-ttu-id="a1d18-227">取消特定擱置中作業的方式，是呼叫其對應之 <xref:System.ComponentModel.AsyncOperation> 上的 <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>。</span><span class="sxs-lookup"><span data-stu-id="a1d18-227">You cancel a particular pending operation by calling <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> on its corresponding <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="a1d18-228">這會結束該作業，後續對其 <xref:System.ComponentModel.AsyncOperation> 發出的呼叫都會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1d18-228">This ends that operation, and any subsequent calls to its <xref:System.ComponentModel.AsyncOperation> will throw an exception.</span></span>  
  
#### <a name="to-implement-start-and-cancel-functionality"></a><span data-ttu-id="a1d18-229">實作「開始」和「取消」功能：</span><span class="sxs-lookup"><span data-stu-id="a1d18-229">To implement Start and Cancel functionality:</span></span>  
  
1. <span data-ttu-id="a1d18-230">實作 `CalculatePrimeAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-230">Implement the `CalculatePrimeAsync` method.</span></span> <span data-ttu-id="a1d18-231">請確定就代表目前擱置中工作的所有權杖而言，用戶端所提供的權杖 (工作識別碼) 是唯一的。</span><span class="sxs-lookup"><span data-stu-id="a1d18-231">Make sure the client-supplied token (task ID) is unique with respect to all the tokens representing currently pending tasks.</span></span> <span data-ttu-id="a1d18-232">如果用戶端傳入的權杖不是唯一的，`CalculatePrimeAsync` 就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1d18-232">If the client passes in a non-unique token, `CalculatePrimeAsync` raises an exception.</span></span> <span data-ttu-id="a1d18-233">否則，該權杖會新增至工作識別碼集合中。</span><span class="sxs-lookup"><span data-stu-id="a1d18-233">Otherwise, the token is added to the task ID collection.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. <span data-ttu-id="a1d18-234">實作 `CancelAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="a1d18-234">Implement the `CancelAsync` method.</span></span> <span data-ttu-id="a1d18-235">如果 `taskId` 存在於權杖集合中，系統就會將它移除。</span><span class="sxs-lookup"><span data-stu-id="a1d18-235">If the `taskId` parameter exists in the token collection, it is removed.</span></span> <span data-ttu-id="a1d18-236">這可防止執行已取消但尚未開始的工作。</span><span class="sxs-lookup"><span data-stu-id="a1d18-236">This prevents canceled tasks that have not started from running.</span></span> <span data-ttu-id="a1d18-237">如果工作正在執行，當偵測到該工作識別碼已自存留期集合中移除時，`BuildPrimeNumberList` 方法就會結束。</span><span class="sxs-lookup"><span data-stu-id="a1d18-237">If the task is running, the `BuildPrimeNumberList` method exits when it detects that the task ID has been removed from the lifetime collection.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a><span data-ttu-id="a1d18-238">檢查點</span><span class="sxs-lookup"><span data-stu-id="a1d18-238">Checkpoint</span></span>  
 <span data-ttu-id="a1d18-239">現在，您可以建置元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-239">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="a1d18-240">測試元件</span><span class="sxs-lookup"><span data-stu-id="a1d18-240">To test your component</span></span>  
  
- <span data-ttu-id="a1d18-241">編譯元件。</span><span class="sxs-lookup"><span data-stu-id="a1d18-241">Compile the component.</span></span>  
  
 <span data-ttu-id="a1d18-242">`PrimeNumberCalculator` 元件現在已完整而可供使用。</span><span class="sxs-lookup"><span data-stu-id="a1d18-242">The `PrimeNumberCalculator` component is now complete and ready to use.</span></span>  
  
 <span data-ttu-id="a1d18-243">如需使用了 `PrimeNumberCalculator` 元件的用戶端範例，請參閱[如何：實作事件架構非同步模式的用戶端](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="a1d18-243">For an example client that uses the `PrimeNumberCalculator` component, see [How to: Implement a Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a1d18-244">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a1d18-244">Next Steps</span></span>  
 <span data-ttu-id="a1d18-245">您可以撰寫 `CalculatePrime` (`CalculatePrimeAsync` 方法的對等同步方法) 來填寫此範例。</span><span class="sxs-lookup"><span data-stu-id="a1d18-245">You can fill out this example by writing `CalculatePrime`, the synchronous equivalent of `CalculatePrimeAsync` method.</span></span> <span data-ttu-id="a1d18-246">這將可讓 `PrimeNumberCalculator` 元件完全符合「事件架構非同步模式」的規範。</span><span class="sxs-lookup"><span data-stu-id="a1d18-246">This will make the `PrimeNumberCalculator` component fully compliant with the Event-based Asynchronous Pattern.</span></span>  
  
 <span data-ttu-id="a1d18-247">您可以藉由保留不同測試數字的各種引動過程所探索到的所有質數清單，來改善此範例。</span><span class="sxs-lookup"><span data-stu-id="a1d18-247">You can improve this example by retaining the list of all the prime numbers discovered by various invocations for different test numbers.</span></span> <span data-ttu-id="a1d18-248">使用此做法時，每個工作都可從先前工作所完成的工作受益。</span><span class="sxs-lookup"><span data-stu-id="a1d18-248">Using this approach, each task will benefit from the work done by previous tasks.</span></span> <span data-ttu-id="a1d18-249">請使用 `lock` 區域來小心保護此清單，如此才能將不同執行緒對此清單的存取序列化。</span><span class="sxs-lookup"><span data-stu-id="a1d18-249">Be careful to protect this list with `lock` regions, so access to the list by different threads is serialized.</span></span>  
  
 <span data-ttu-id="a1d18-250">您也可以針對平凡除數 (例如 2、3 及 5) 進行測試來改善此範例。</span><span class="sxs-lookup"><span data-stu-id="a1d18-250">You can also improve this example by testing for trivial divisors, like 2, 3, and 5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1d18-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1d18-251">See also</span></span>

- [<span data-ttu-id="a1d18-252">如何：在背景執行作業</span><span class="sxs-lookup"><span data-stu-id="a1d18-252">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="a1d18-253">事件架構非同步模式概觀</span><span class="sxs-lookup"><span data-stu-id="a1d18-253">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="a1d18-254">事件架構非同步模式 (EAP)</span><span class="sxs-lookup"><span data-stu-id="a1d18-254">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
