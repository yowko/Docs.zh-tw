---
title: 自訂存留期
ms.date: 03/30/2017
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: e41c970739b8036730fa601433ce7157e01d7e19
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809299"
---
# <a name="custom-lifetime"></a><span data-ttu-id="0d983-102">自訂存留期</span><span class="sxs-lookup"><span data-stu-id="0d983-102">Custom Lifetime</span></span>
<span data-ttu-id="0d983-103">這個範例示範如何撰寫 Windows Communication Foundation (WCF) 擴充程式以提供自訂存留時間服務共用的 WCF 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d983-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d983-104">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="0d983-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="shared-instancing"></a><span data-ttu-id="0d983-105">共用執行個體</span><span class="sxs-lookup"><span data-stu-id="0d983-105">Shared Instancing</span></span>  
 <span data-ttu-id="0d983-106">WCF 提供數個執行個體的模式，您的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d983-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="0d983-107">本主題中涵蓋的「共用執行個體」模式提供一種方式，可以在多個通道間共用服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d983-107">The Shared Instancing mode covered in this topic provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="0d983-108">用戶端可以在本機解析執行個體的端點位址，或連絡服務中的 Factory 方法，以取得執行中執行個體的端點位址。</span><span class="sxs-lookup"><span data-stu-id="0d983-108">Clients can either resolve the instance’s endpoint address locally or contact a factory method in the service to obtain the endpoint address of a running instance.</span></span> <span data-ttu-id="0d983-109">一旦擁有端點位址之後，它就可以建立新的通道並開始通訊。</span><span class="sxs-lookup"><span data-stu-id="0d983-109">Once it has the endpoint address, it can create a new channel and start communication.</span></span> <span data-ttu-id="0d983-110">下列程式碼片段示範用戶端應用程式如何針對現有的服務執行個體建立新的通道。</span><span class="sxs-lookup"><span data-stu-id="0d983-110">The following code snippet shows how a client application creates a new channel to an existing service instance.</span></span>  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 <span data-ttu-id="0d983-111">共用執行個體模式不像其他執行個體模式，前者擁有釋出服務執行個體的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="0d983-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="0d983-112">當執行個體，會關閉所有通道時，服務的 WCF 執行階段會啟動計時器。</span><span class="sxs-lookup"><span data-stu-id="0d983-112">When all the channels are closed for an instance, the service WCF runtime starts a timer.</span></span> <span data-ttu-id="0d983-113">如果沒有人會建立的連接逾時到期前，WCF 會釋出執行個體，並宣告資源。</span><span class="sxs-lookup"><span data-stu-id="0d983-113">If nobody makes a connection before the timeout expires, WCF releases the instance and claims the resources.</span></span> <span data-ttu-id="0d983-114">清除程序的一部分 WCF 會叫用<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法的所有<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>實作之前釋放執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d983-114">As a part of the teardown procedure WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of all <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementations before releasing the instance.</span></span> <span data-ttu-id="0d983-115">如果它們全部傳回 `true`，則會釋出執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d983-115">If all of them return `true` the instance is released.</span></span> <span data-ttu-id="0d983-116">否則，<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作會負責使用回呼方法，通知 `Dispatcher` 閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="0d983-116">Otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span>  
  
 <span data-ttu-id="0d983-117">根據預設，<xref:System.ServiceModel.InstanceContext> 的閒置逾時值為一分鐘。</span><span class="sxs-lookup"><span data-stu-id="0d983-117">By default, the idle timeout value of <xref:System.ServiceModel.InstanceContext> is one minute.</span></span> <span data-ttu-id="0d983-118">不過，此範例示範您可以如何使用自訂延伸模組擴充這個時間。</span><span class="sxs-lookup"><span data-stu-id="0d983-118">However this sample demonstrates how you can extend this using a custom extension.</span></span>  
  
## <a name="extending-the-instancecontext"></a><span data-ttu-id="0d983-119">擴充 InstanceContext</span><span class="sxs-lookup"><span data-stu-id="0d983-119">Extending the InstanceContext</span></span>  
 <span data-ttu-id="0d983-120">在 WCF 中，<xref:System.ServiceModel.InstanceContext>是服務執行個體之間的連結和`Dispatcher`。</span><span class="sxs-lookup"><span data-stu-id="0d983-120">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="0d983-121">WCF 可讓您擴充這個執行階段元件使用其可擴充物件模式加入新狀態或行為。</span><span class="sxs-lookup"><span data-stu-id="0d983-121">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="0d983-122">可擴充物件模式用在 WCF 中，搭配來擴充現有執行階段類別的新功能，或新增狀態功能到物件。</span><span class="sxs-lookup"><span data-stu-id="0d983-122">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="0d983-123">在可延伸物件模式中有三種介面：`IExtensibleObject<T>`、`IExtension<T>` 和 `IExtensionCollection<T>`。</span><span class="sxs-lookup"><span data-stu-id="0d983-123">There are three interfaces in the extensible object pattern: `IExtensibleObject<T>`, `IExtension<T>`, and `IExtensionCollection<T>`.</span></span>  
  
 <span data-ttu-id="0d983-124">`IExtensibleObject<T>` 介面是由允許自訂其功能的延伸模組所實作的。</span><span class="sxs-lookup"><span data-stu-id="0d983-124">The `IExtensibleObject<T>` interface is implemented by objects to allow extensions which customize their functionality.</span></span>  
  
 <span data-ttu-id="0d983-125">`IExtension<T>` 介面是由可以是型別 `T` 之類別延伸模組的物件所實作。</span><span class="sxs-lookup"><span data-stu-id="0d983-125">The `IExtension<T>` interface is implemented by objects that can be extensions of classes of type `T`.</span></span>  
  
 <span data-ttu-id="0d983-126">最後，`IExtensionCollection<T>` 介面則是 `IExtensions` 的集合，可允許依其型別擷取 `IExtensions`。</span><span class="sxs-lookup"><span data-stu-id="0d983-126">And finally, the `IExtensionCollection<T>` interface is a collection of `IExtensions` that allows for retrieving `IExtensions` by their type.</span></span>  
  
 <span data-ttu-id="0d983-127">因此，若要擴充 <xref:System.ServiceModel.InstanceContext>，您必須實作 `IExtension` 介面。</span><span class="sxs-lookup"><span data-stu-id="0d983-127">Therefore in order to extend the <xref:System.ServiceModel.InstanceContext> you must implement the `IExtension` interface.</span></span> <span data-ttu-id="0d983-128">在此範例專案中，`CustomLeaseExtension` 類別包含這個實作。</span><span class="sxs-lookup"><span data-stu-id="0d983-128">In this sample project the `CustomLeaseExtension` class contains this implementation.</span></span>  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 <span data-ttu-id="0d983-129">`IExtension` 介面擁有兩種方法：`Attach` 和 `Detach`。</span><span class="sxs-lookup"><span data-stu-id="0d983-129">The `IExtension` interface has two methods `Attach` and `Detach`.</span></span> <span data-ttu-id="0d983-130">顧名思義，當執行階段將延伸模組連接到 <xref:System.ServiceModel.InstanceContext> 類別的執行個體以及從其中斷時，會呼叫這兩個方法。</span><span class="sxs-lookup"><span data-stu-id="0d983-130">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="0d983-131">在此範例中，`Attach` 方法用於追蹤屬於目前延伸模組執行個體的 <xref:System.ServiceModel.InstanceContext> 物件。</span><span class="sxs-lookup"><span data-stu-id="0d983-131">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 <span data-ttu-id="0d983-132">此外，您必須將必要的實作加入至延伸模組，以提供延伸的存留時間支援。</span><span class="sxs-lookup"><span data-stu-id="0d983-132">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="0d983-133">因此，系統會使用所需的方法宣告 `ICustomLease` 介面，並在 `CustomLeaseExtension` 類別中實作。</span><span class="sxs-lookup"><span data-stu-id="0d983-133">Therefore the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 <span data-ttu-id="0d983-134">當叫用 WCF<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法中的<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>實作此呼叫會路由至<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法`CustomLeaseExtension`。</span><span class="sxs-lookup"><span data-stu-id="0d983-134">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="0d983-135">然後，`CustomLeaseExtension` 會檢查其私用狀態以查看 <xref:System.ServiceModel.InstanceContext> 是否閒置。</span><span class="sxs-lookup"><span data-stu-id="0d983-135">Then the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="0d983-136">如果閒置，則會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="0d983-136">If it is idle it returns `true`.</span></span> <span data-ttu-id="0d983-137">否則，它會啟動計時器一段指定的延伸存留時間。</span><span class="sxs-lookup"><span data-stu-id="0d983-137">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>  
  
```  
public bool IsIdle  
{  
  get  
  {  
    lock (thisLock)  
    {  
      if (isIdle)  
      {  
        return true;  
      }  
      else  
      {  
        StartTimer();  
        return false;  
      }  
    }  
  }  
}  
```  
  
 <span data-ttu-id="0d983-138">在計時器的 `Elapsed` 事件中，系統會呼叫 Dispatcher 中的回呼函式，以啟動另一個清除循環。</span><span class="sxs-lookup"><span data-stu-id="0d983-138">In the timer’s `Elapsed` event the callback function in the Dispatcher is called in order to start another clean up cycle.</span></span>  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 <span data-ttu-id="0d983-139">當移到閒置狀態的執行個體有新訊息時，無法更新執行中的計時器。</span><span class="sxs-lookup"><span data-stu-id="0d983-139">There is no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>  
  
 <span data-ttu-id="0d983-140">此範例會實作 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 以攔截對 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的呼叫，並將其路由至 `CustomLeaseExtension`。</span><span class="sxs-lookup"><span data-stu-id="0d983-140">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="0d983-141"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作包含在 `CustomLifetimeLease` 類別中。</span><span class="sxs-lookup"><span data-stu-id="0d983-141">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="0d983-142"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF 即將要釋放服務執行個體時，會叫用方法。</span><span class="sxs-lookup"><span data-stu-id="0d983-142">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="0d983-143">不過，在 ServiceBehavior 的 `ISharedSessionInstance` 集合中，只有一個特定 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d983-143">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="0d983-144">這表示沒有任何方式可以得知<xref:System.ServiceModel.InstanceContext>即將關閉的時間，WCF 會檢查<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="0d983-144">This means there is no way of knowing the <xref:System.ServiceModel.InstanceContext> being closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="0d983-145">因此，此範例使用執行緒封鎖來序列化 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的要求。</span><span class="sxs-lookup"><span data-stu-id="0d983-145">Therefore this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d983-146">使用執行緒封鎖並不是建議的方法，因為序列化可能會嚴重影響應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="0d983-146">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>  
  
 <span data-ttu-id="0d983-147">在 `CustomLeaseExtension` 類別中會使用一個私用成員變數來追蹤 `IsIdle` 值。</span><span class="sxs-lookup"><span data-stu-id="0d983-147">A private member variable is used in the `CustomLeaseExtension` class to track the `IsIdle` value.</span></span> <span data-ttu-id="0d983-148">每次系統擷取 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 的值時，就會傳回 `IsIdle` 私用成員，並重設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="0d983-148">Each time the value of <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is retrieved the `IsIdle` private member is returned and reset to `false`.</span></span> <span data-ttu-id="0d983-149">請務必將此值設定為 `false`，才能確保 Dispatcher 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0d983-149">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 <span data-ttu-id="0d983-150">如果 `ISharedSessionLifetime.IsIdle` 屬性傳回 `false`，Dispatcher 會使用 `NotifyIdle` 方法登錄一個回呼函式。</span><span class="sxs-lookup"><span data-stu-id="0d983-150">If the `ISharedSessionLifetime.IsIdle` property returns `false` the Dispatcher registers a callback function by using the `NotifyIdle` method.</span></span> <span data-ttu-id="0d983-151">此方法會接收要釋出之 <xref:System.ServiceModel.InstanceContext> 的參考。</span><span class="sxs-lookup"><span data-stu-id="0d983-151">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="0d983-152">因此，範例程式碼可以查詢 `ICustomLease` 型別擴充，然後在擴充的狀態下檢查 `ICustomLease.IsIdle` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0d983-152">Therefore the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>  
  
```  
public void NotifyIdle(InstanceContextIdleCallback callback,   
            InstanceContext instanceContext)  
{  
    lock (thisLock)  
    {  
       ICustomLease customLease =  
           instanceContext.Extensions.Find<ICustomLease>();  
       customLease.Callback = callback;   
       isIdle = customLease.IsIdle;  
       if (isIdle)  
       {  
             callback(instanceContext);  
       }  
    }   
}  
```  
  
 <span data-ttu-id="0d983-153">在 `ICustomLease.IsIdle` 屬性進行檢查之前，必須設定回呼屬性，因為這在 `CustomLeaseExtension` 通知 Dispatcher 它變成閒置時相當重要。</span><span class="sxs-lookup"><span data-stu-id="0d983-153">Before the `ICustomLease.IsIdle` property is checked the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="0d983-154">如果 `ICustomLease.IsIdle` 傳回 `true`，`isIdle` 私用成員只會在 `CustomLifetimeLease` 中設定為 `true`，並呼叫回呼方法。</span><span class="sxs-lookup"><span data-stu-id="0d983-154">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="0d983-155">由於程式碼保留鎖定，因此其他執行緒無法變更此私用成員的值。</span><span class="sxs-lookup"><span data-stu-id="0d983-155">Because the code holds a lock, other threads cannot change the value of this private member.</span></span> <span data-ttu-id="0d983-156">此外，在 Dispatcher 下次檢查 `ISharedSessionLifetime.IsIdle` 時，它會傳回 `true`，然後讓 Dispatcher 釋出執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d983-156">And the next time Dispatcher checks the `ISharedSessionLifetime.IsIdle`, it returns `true` and lets Dispatcher release the instance.</span></span>  
  
 <span data-ttu-id="0d983-157">既然自訂延伸模組的基礎已完成，現在必須將其連結至服務模型。</span><span class="sxs-lookup"><span data-stu-id="0d983-157">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="0d983-158">連結`CustomLeaseExtension`實作<xref:System.ServiceModel.InstanceContext>，WCF 會提供<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>介面來執行的啟動載入<xref:System.ServiceModel.InstanceContext>。</span><span class="sxs-lookup"><span data-stu-id="0d983-158">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="0d983-159">在此範例中，`CustomLeaseInitializer` 類別會實作此介面，並將 `CustomLeaseExtension` 的執行個體從唯一的方法初始化加入至 <xref:System.ServiceModel.InstanceContext.Extensions%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="0d983-159">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="0d983-160">初始化 <xref:System.ServiceModel.InstanceContext> 時，Dispatcher 會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="0d983-160">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 <span data-ttu-id="0d983-161">最後`System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime`和<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>實作是最多使用服務模型塊狀<xref:System.ServiceModel.Description.IServiceBehavior>實作。</span><span class="sxs-lookup"><span data-stu-id="0d983-161">Finally the `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` and <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementations are is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="0d983-162">此實作放在 `CustomLeaseTimeAttribute` 類別中，而且它也衍生自 `Attribute` 基底類別，以便當做屬性公開此行為。</span><span class="sxs-lookup"><span data-stu-id="0d983-162">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span> <span data-ttu-id="0d983-163">在 `IServiceBehavior.ApplyBehavior` 方法中，<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> 和 `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` 實作的執行個體會分別加入至 `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` 的 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> 和 <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> 集合中。</span><span class="sxs-lookup"><span data-stu-id="0d983-163">In the `IServiceBehavior.ApplyBehavior` method, instances of <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> and `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementations are added to the `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` and <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> collections of the <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectively.</span></span>  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 <span data-ttu-id="0d983-164">您可以使用 `CustomLeaseTime` 屬性加上註解，以便將此行為加入至範例服務類別。</span><span class="sxs-lookup"><span data-stu-id="0d983-164">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 <span data-ttu-id="0d983-165">當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="0d983-165">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="0d983-166">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="0d983-166">Press ENTER in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d983-167">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="0d983-167">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0d983-168">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0d983-168">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0d983-169">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="0d983-169">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0d983-170">若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="0d983-170">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0d983-171">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0d983-171">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0d983-172">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0d983-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0d983-173">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0d983-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0d983-174">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0d983-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a><span data-ttu-id="0d983-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d983-175">See Also</span></span>
