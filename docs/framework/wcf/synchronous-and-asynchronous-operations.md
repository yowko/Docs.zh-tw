---
title: 同步和非同步作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 6c464dc79e0f38b72f724fafcef59916d766e2d0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="d7153-102">同步和非同步作業</span><span class="sxs-lookup"><span data-stu-id="d7153-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="d7153-103">本主題討論實作和呼叫非同步服務作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="d7153-104">許多應用程式會非同步呼叫方法，因為這麼做使應用程式可以在方法呼叫執行的同時繼續進行有用的工作。</span><span class="sxs-lookup"><span data-stu-id="d7153-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> <span data-ttu-id="d7153-105">Windows Communication Foundation (WCF) 服務和用戶端可以參與非同步作業呼叫兩個不同層級的應用程式，可提供更多的彈性來最大化輸送量互動性的權衡 WCF 應用程式.</span><span class="sxs-lookup"><span data-stu-id="d7153-105">Windows Communication Foundation (WCF) services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide WCF applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="d7153-106">非同步作業的類型</span><span class="sxs-lookup"><span data-stu-id="d7153-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="d7153-107">所有服務合約在 WCF 中，無論參數型別和傳回值，請使用 WCF 屬性來指定用戶端與服務之間的特定訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="d7153-107">All service contracts in WCF, no matter the parameters types and return values, use WCF attributes to specify a particular message exchange pattern between client and service.</span></span> <span data-ttu-id="d7153-108">WCF 會自動路由至適當的服務作業或執行用戶端程式碼的輸入和輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="d7153-108">WCF automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="d7153-109">用戶端僅擁有服務合約，而這個服務合約會指定特定作業的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="d7153-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="d7153-110">只要觀察到基礎訊息交換模式，用戶端便可以提供開發人員所選擇的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="d7153-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="d7153-111">同樣的，只要觀察到指定的訊息模式，服務便可以任何方式實作作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="d7153-112">服務合約的服務或用戶端實作的獨立性可讓 WCF 應用程式中的非同步執行的下列形式：</span><span class="sxs-lookup"><span data-stu-id="d7153-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in WCF applications:</span></span>  
  
-   <span data-ttu-id="d7153-113">用戶端可以使用同步訊息交換，以非同步方式叫用要求/回應作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="d7153-114">服務可以使用同步訊息交換，來以非同步方式實作要求/回應作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="d7153-115">不管用戶端或服務的實作如何，訊息交換可以是單向。</span><span class="sxs-lookup"><span data-stu-id="d7153-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="d7153-116">建議的非同步案例</span><span class="sxs-lookup"><span data-stu-id="d7153-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="d7153-117">如果作業服務實作發出封鎖呼叫 (例如進行 I/O 工作)，這時請在服務作業實作中使用非同步方法。</span><span class="sxs-lookup"><span data-stu-id="d7153-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="d7153-118">當您處於非同步作業實作中時，請嘗試呼叫非同步作業和方法，盡可能地延伸非同步呼叫路徑。</span><span class="sxs-lookup"><span data-stu-id="d7153-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="d7153-119">例如，從 `BeginOperationTwo()` 內呼叫 `BeginOperationOne()`。</span><span class="sxs-lookup"><span data-stu-id="d7153-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
-   <span data-ttu-id="d7153-120">在下列情況中，在用戶端中使用非同步化方法或呼叫應用程式：</span><span class="sxs-lookup"><span data-stu-id="d7153-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
-   <span data-ttu-id="d7153-121">如果您是從中介層應用程式叫用作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="d7153-122">(如需這種情況的詳細資訊，請參閱[中介層用戶端應用程式](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)。)</span><span class="sxs-lookup"><span data-stu-id="d7153-122">(For more information about such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
-   <span data-ttu-id="d7153-123">如果您是叫用 ASP.NET 頁面內的作業，請使用非同步頁面。</span><span class="sxs-lookup"><span data-stu-id="d7153-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
-   <span data-ttu-id="d7153-124">如果您叫用作業，從任何為單一執行緒，例如 Windows Form 或 Windows Presentation Foundation (WPF) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d7153-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="d7153-125">使用事件架構非同步呼叫模型時，結果事件會在 UI 執行緒上引發，並將回應新增至應用程式中，而不需要您自己去處理多個執行緒。</span><span class="sxs-lookup"><span data-stu-id="d7153-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
-   <span data-ttu-id="d7153-126">一般而言，如果您在同步與非同步呼叫之間有選擇，請選擇非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="d7153-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="d7153-127">實作非同步服務作業</span><span class="sxs-lookup"><span data-stu-id="d7153-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="d7153-128">您可以使用下列三個方法的其中一個來實作非同步服務作業：</span><span class="sxs-lookup"><span data-stu-id="d7153-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1.  <span data-ttu-id="d7153-129">工作架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="d7153-129">The task-based asynchronous pattern</span></span>  
  
2.  <span data-ttu-id="d7153-130">事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="d7153-130">The event-based asynchronous pattern</span></span>  
  
3.  <span data-ttu-id="d7153-131">IAsyncResult 非同步模式</span><span class="sxs-lookup"><span data-stu-id="d7153-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="d7153-132">以工作為基礎的非同步模式</span><span class="sxs-lookup"><span data-stu-id="d7153-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="d7153-133">工作架構非同步模式是實作非同步作業的慣用方式，因為這是最簡單且最直接的方式。</span><span class="sxs-lookup"><span data-stu-id="d7153-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="d7153-134">若要使用這個方法只需實作服務作業，並指定工作的傳回型別\<T >，其中 T 是邏輯作業傳回的型別。</span><span class="sxs-lookup"><span data-stu-id="d7153-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="d7153-135">例如: </span><span class="sxs-lookup"><span data-stu-id="d7153-135">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="d7153-136">SampleMethodTaskAsync 作業會傳回工作\<字串 > 因為邏輯作業傳回的字串。</span><span class="sxs-lookup"><span data-stu-id="d7153-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="d7153-137">如需工作架構非同步模式的詳細資訊，請參閱[工作架構非同步模式](http://go.microsoft.com/fwlink/?LinkId=232504)。</span><span class="sxs-lookup"><span data-stu-id="d7153-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="d7153-138">使用工作架構非同步模式時，如果在等待作業完成期間發生例外狀況，則可能擲回 T:System.AggregateException。</span><span class="sxs-lookup"><span data-stu-id="d7153-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="d7153-139">這個例外狀況可能在用戶端或服務上發生</span><span class="sxs-lookup"><span data-stu-id="d7153-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="d7153-140">事件架構非同步模式</span><span class="sxs-lookup"><span data-stu-id="d7153-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="d7153-141">支援事件架構非同步模式的服務會有一個或多個名為 MethodNameAsync 的方法。</span><span class="sxs-lookup"><span data-stu-id="d7153-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="d7153-142">這些方法可能鏡像在目前執行緒上執行相同作業的同步版本。</span><span class="sxs-lookup"><span data-stu-id="d7153-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="d7153-143">這個類別可能也具有 MethodNameCompleted 事件，並且具有 MethodNameAsyncCancel (或簡單地說 CancelAsync) 方法。</span><span class="sxs-lookup"><span data-stu-id="d7153-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="d7153-144">想要呼叫作業的用戶端將會定義要在作業完成時呼叫的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d7153-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="d7153-145">下列程式碼片段示範如何使用事件架構非同步模式宣告非同步作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="d7153-146">如需事件架構非同步模式的詳細資訊，請參閱[事件架構非同步模式](http://go.microsoft.com/fwlink/?LinkId=232515)。</span><span class="sxs-lookup"><span data-stu-id="d7153-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="d7153-147">IAsyncResult 非同步模式</span><span class="sxs-lookup"><span data-stu-id="d7153-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="d7153-148">使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 非同步程式設計模式並使 `<Begin>` 方法的 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 屬性設定為 `true`，即可以非同步方式實作服務作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-148">A service operation can be implemented in an asynchronous fashion using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="d7153-149">在此情況下，會使用和同步作業相同的形式，在中繼資料中公開非同步作業：非同步作業會公開為具有要求訊息和相關聯之回應訊息的單一作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="d7153-150">用戶端程式設計模型接著就會做出選擇。</span><span class="sxs-lookup"><span data-stu-id="d7153-150">Client programming models then have a choice.</span></span> <span data-ttu-id="d7153-151">只要在叫用服務時發生要求/回應訊息交換，這些程式設計模型就會將此模式表示為同步作業或非同步作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="d7153-152">一般而言，基於系統的非同步本質，您不應該相依於執行緒。</span><span class="sxs-lookup"><span data-stu-id="d7153-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="d7153-153">將資料傳遞至作業分派處理之各種階段最可靠的方式就是使用延伸模組。</span><span class="sxs-lookup"><span data-stu-id="d7153-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="d7153-154">如需範例，請參閱[How to： 實作非同步服務作業](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="d7153-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="d7153-155">若不管在用戶端應用程式中呼叫合約作業的方式，而要定義以非同步方式執行的合約作業 `X`：</span><span class="sxs-lookup"><span data-stu-id="d7153-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
-   <span data-ttu-id="d7153-156">使用模式 `BeginOperation` 和 `EndOperation` 定義兩種方法。</span><span class="sxs-lookup"><span data-stu-id="d7153-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
-   <span data-ttu-id="d7153-157">`BeginOperation` 方法包含用於作業的 `in` 和 `ref` 參數，並會傳回 <xref:System.IAsyncResult> 型別。</span><span class="sxs-lookup"><span data-stu-id="d7153-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
-   <span data-ttu-id="d7153-158">`EndOperation` 方法包含 <xref:System.IAsyncResult> 參數、`out` 和 `ref` 參數，並會傳回作業的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="d7153-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="d7153-159">以下列方法為例：</span><span class="sxs-lookup"><span data-stu-id="d7153-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="d7153-160">若要建立非同步作業，這兩個方法將會：</span><span class="sxs-lookup"><span data-stu-id="d7153-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]IAsyncResult BeginDoWork(string data,                           ref string inout,                           AsyncCallback callback,                           object state);int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>  _Function BeginDoWork(ByVal data As String, _                 ByRef inout As String, _                 ByVal callback As AsyncCallback, _                 ByVal state As Object) _As IAsyncResult Function EndDoWork(ByRef inout As String, _        ByRef outonly As String, _        ByVal result As IAsyncResult) _As Integer  
```  
  
> [!NOTE]
>  <span data-ttu-id="d7153-161"><xref:System.ServiceModel.OperationContractAttribute> 屬性只會套用至 `BeginDoWork` 方法。</span><span class="sxs-lookup"><span data-stu-id="d7153-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="d7153-162">產生的合約具有一個名為 `DoWork` 的 WSDL 作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="d7153-163">用戶端非同步叫用</span><span class="sxs-lookup"><span data-stu-id="d7153-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="d7153-164">WCF 用戶端應用程式可以使用任何三個非同步呼叫模型中先前所述</span><span class="sxs-lookup"><span data-stu-id="d7153-164">A WCF client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="d7153-165">使用工作架構模型時，只需使用 await 關鍵字呼叫作業，如下列程式碼片段所示。</span><span class="sxs-lookup"><span data-stu-id="d7153-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="d7153-166">使用事件架構非同步模式時，只需要加入事件處理常式以接收回應的通知 -- 結果事件會自動在使用者介面執行緒上引發。</span><span class="sxs-lookup"><span data-stu-id="d7153-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="d7153-167">若要使用此方法，同時指定 **/async**和 **/tcv:Version35**命令與選項[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，如下列範例。</span><span class="sxs-lookup"><span data-stu-id="d7153-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="d7153-168">完成此動作後，Svcutil.exe 會產生 WCF 用戶端類別與事件基礎結構，可讓呼叫的應用程式去實作與指派事件處理常式以接收回應並採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="d7153-168">When this is done, Svcutil.exe generates a WCF client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="d7153-169">如需完整範例，請參閱[如何： 非同步呼叫服務作業](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。</span><span class="sxs-lookup"><span data-stu-id="d7153-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="d7153-170">但是，事件架構非同步呼叫只能在 [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] 中使用。</span><span class="sxs-lookup"><span data-stu-id="d7153-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="d7153-171">此外，它不支援在即使[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]WCF 用戶端通道建立時使用<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d7153-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a WCF client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d7153-172">使用 WCF 用戶端通道物件，您必須使用<xref:System.IAsyncResult?displayProperty=nameWithType>物件以非同步方式叫用您的作業。</span><span class="sxs-lookup"><span data-stu-id="d7153-172">With WCF client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="d7153-173">若要使用此方法，指定 **/async**命令選項加[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d7153-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="d7153-174">這會產生服務合約，其中的每個作業會模型化為其 `<Begin>` 屬性會設為 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 的 `true` 方法，和對應的 `<End>` 方法。</span><span class="sxs-lookup"><span data-stu-id="d7153-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="d7153-175">完整範例，使用<xref:System.ServiceModel.ChannelFactory%601>，請參閱[如何： 呼叫作業以非同步方式使用通道處理站](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)。</span><span class="sxs-lookup"><span data-stu-id="d7153-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="d7153-176">無論何種情況下，即使是以同步方式實作服務，應用程式仍可以使用非同步方式叫用作業，而透過相同的方式，應用程式可以使用相同的模式，以非同步方式叫用本機同步方法。</span><span class="sxs-lookup"><span data-stu-id="d7153-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="d7153-177">實作作業的方式對用戶端來說並不重要；回應訊息送達時，其內容會分派至用戶端的非同步 <`End`> 方法，而用戶端便會擷取該資訊。</span><span class="sxs-lookup"><span data-stu-id="d7153-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="d7153-178">單向訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="d7153-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="d7153-179">您也可以建立非同步訊息交換模式，而在這個模式中，用戶端或服務可以不管另一端，以任何方向傳送單向作業 (這是 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> 為 `true` 的作業，而且沒有相關聯的回應) </span><span class="sxs-lookup"><span data-stu-id="d7153-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="d7153-180">(這會使用具有單向訊息的雙工訊息交換模式)。在這個情況下，服務合約會指定單向訊息交換，這表示每一端都可在適當時，選擇是否要實作為非同步呼叫或實作。</span><span class="sxs-lookup"><span data-stu-id="d7153-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="d7153-181">一般來說，當合約為單向訊息交換時，就可以大量地非同步實作，因為一旦傳送訊息時，應用程式不會等待回覆就可繼續執行其他工作。</span><span class="sxs-lookup"><span data-stu-id="d7153-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="d7153-182">事件架構非同步用戶端和訊息合約</span><span class="sxs-lookup"><span data-stu-id="d7153-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="d7153-183">事件架構非同步模型的設計方針指出，如果傳回多個值，則其中一個值會傳回做為 `Result` 屬性，其他值則傳回做為 <xref:System.EventArgs> 物件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="d7153-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="d7153-184">這麼做的結果就是，如果用戶端使用事件架構非同步命令選項匯入中繼資料，且作業傳回多個值，則預設 <xref:System.EventArgs> 物件會傳回一個值做為 `Result` 屬性，而其餘則做為 <xref:System.EventArgs> 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="d7153-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="d7153-185">如果您想要接收的訊息物件做為`Result`屬性，並沒有傳回的值物件，該物件上的屬性，請使用 **/messageContract**命令選項。</span><span class="sxs-lookup"><span data-stu-id="d7153-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="d7153-186">這會產生一個簽章，此簽章會將回應訊息傳回做為 `Result` 物件的 <xref:System.EventArgs> 屬性。</span><span class="sxs-lookup"><span data-stu-id="d7153-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="d7153-187">然後，所有的內部傳回值都成為回應訊息物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="d7153-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7153-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7153-188">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
