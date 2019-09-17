---
title: 執行個體初始化
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: ca135aca8f84ddf79ec7447e7fa7814f61984419
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989836"
---
# <a name="instancing-initialization"></a><span data-ttu-id="e8b54-102">執行個體初始化</span><span class="sxs-lookup"><span data-stu-id="e8b54-102">Instancing Initialization</span></span>
<span data-ttu-id="e8b54-103">這個範例會藉由定義介面來擴充[共用](../../../../docs/framework/wcf/samples/pooling.md)樣本，`IObjectControl`，這會藉由啟用和停用來自訂物件的初始化。</span><span class="sxs-lookup"><span data-stu-id="e8b54-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="e8b54-104">用戶端會叫用將物件傳回集區的方法，以及不將物件傳回集區的方法。</span><span class="sxs-lookup"><span data-stu-id="e8b54-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8b54-105">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="e8b54-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="e8b54-106">擴充點</span><span class="sxs-lookup"><span data-stu-id="e8b54-106">Extensibility Points</span></span>  
 <span data-ttu-id="e8b54-107">建立 Windows Communication Foundation （WCF）延伸模組的第一個步驟是決定要使用的擴充點。</span><span class="sxs-lookup"><span data-stu-id="e8b54-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="e8b54-108">在 WCF 中， *EndpointDispatcher*一詞指的是執行時間元件，負責將傳入訊息轉換成使用者服務上的方法調用，以及將該方法的傳回值轉換成外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="e8b54-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="e8b54-109">WCF 服務會為每個端點建立 EndpointDispatcher。</span><span class="sxs-lookup"><span data-stu-id="e8b54-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="e8b54-110">EndpointDispatcher 會使用 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 類別，為端點範圍 (針對服務已接收或傳送的所有訊息) 提供擴充性。</span><span class="sxs-lookup"><span data-stu-id="e8b54-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="e8b54-111">這個類別可讓您自訂各種屬性，以控制 EndpointDispatcher 的行為。</span><span class="sxs-lookup"><span data-stu-id="e8b54-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="e8b54-112">此範例著重於 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 屬性，這個屬性會指向提供服務類別之執行個體的物件。</span><span class="sxs-lookup"><span data-stu-id="e8b54-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="e8b54-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="e8b54-113">IInstanceProvider</span></span>  
 <span data-ttu-id="e8b54-114">在 WCF 中，EndpointDispatcher 會<xref:System.ServiceModel.Dispatcher.IInstanceProvider>使用執行介面的執行個體提供者，建立服務類別的實例。</span><span class="sxs-lookup"><span data-stu-id="e8b54-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="e8b54-115">這個介面只有兩個方法：</span><span class="sxs-lookup"><span data-stu-id="e8b54-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="e8b54-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>：當訊息抵達時，發送器會呼叫<xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>方法來建立服務類別的實例來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="e8b54-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="e8b54-117">呼叫此方法的頻率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性決定。</span><span class="sxs-lookup"><span data-stu-id="e8b54-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="e8b54-118">例如，如果 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性設定為 <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>，則會建立服務類別的執行個體來處理送達的每個訊息，這表示只要訊息一送達就會呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>。</span><span class="sxs-lookup"><span data-stu-id="e8b54-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="e8b54-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>：當服務實例完成訊息的處理時，EndpointDispatcher 會呼叫<xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="e8b54-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="e8b54-120">如同 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法，呼叫此方法的頻率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性決定。</span><span class="sxs-lookup"><span data-stu-id="e8b54-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="e8b54-121">物件集區</span><span class="sxs-lookup"><span data-stu-id="e8b54-121">The Object Pool</span></span>  
 <span data-ttu-id="e8b54-122">`ObjectPoolInstanceProvider` 類別包含物件集區 (Object Pool) 的實作。</span><span class="sxs-lookup"><span data-stu-id="e8b54-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="e8b54-123">這個類別會實作 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 介面，以便與服務模型層互動。</span><span class="sxs-lookup"><span data-stu-id="e8b54-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="e8b54-124">當 EndpointDispatcher 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法而不是建立新執行個體時，自訂實作會在記憶體中集區尋找現有的物件。</span><span class="sxs-lookup"><span data-stu-id="e8b54-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="e8b54-125">如果找到了，就會將物件傳回。</span><span class="sxs-lookup"><span data-stu-id="e8b54-125">If one is available, it is returned.</span></span> <span data-ttu-id="e8b54-126">否則，`ObjectPoolInstanceProvider` 會檢查 `ActiveObjectsCount` 屬性 (從集區傳回的物件數目) 是否已達到集區的大小上限。</span><span class="sxs-lookup"><span data-stu-id="e8b54-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="e8b54-127">如果未達到，則會建立新執行個體並傳回至呼叫者，接著 `ActiveObjectsCount` 就會遞增。</span><span class="sxs-lookup"><span data-stu-id="e8b54-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="e8b54-128">否則，物件建立要求會在預先設定的期間內加入佇列。</span><span class="sxs-lookup"><span data-stu-id="e8b54-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="e8b54-129">下列範例程式碼會示範 `GetObjectFromThePool` 實作。</span><span class="sxs-lookup"><span data-stu-id="e8b54-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp  
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="e8b54-130">自訂 `ReleaseInstance` 實作會將釋放的執行個體新增回集區，並遞減 `ActiveObjectsCount` 值。</span><span class="sxs-lookup"><span data-stu-id="e8b54-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="e8b54-131">EndpointDispatcher 可以從不同的執行緒來呼叫這些方法，因此便需要在 `ObjectPoolInstanceProvider` 類別中同步存取類別層級的成員。</span><span class="sxs-lookup"><span data-stu-id="e8b54-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp  
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="e8b54-132">方法會提供*清除初始化*功能。 `ReleaseInstance`</span><span class="sxs-lookup"><span data-stu-id="e8b54-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="e8b54-133">集區通常會在集區的存留期中保留最低限度數目的物件。</span><span class="sxs-lookup"><span data-stu-id="e8b54-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="e8b54-134">不過，可能有些時段會出現過度使用的情形，因而需要在集區中建立其他物件以達到組態中指定的上限。</span><span class="sxs-lookup"><span data-stu-id="e8b54-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="e8b54-135">最後當集區的活動變少時，這些多餘的物件可能會變成額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="e8b54-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="e8b54-136">因此，當 `activeObjectsCount` 成為零時，閒置計時器就會啟動，以觸發並執行清除循環。</span><span class="sxs-lookup"><span data-stu-id="e8b54-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="e8b54-137">您可以使用下列行為來連結 ServiceModel 層的延伸項目：</span><span class="sxs-lookup"><span data-stu-id="e8b54-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="e8b54-138">服務行為：這些行為允許自訂整個服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="e8b54-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="e8b54-139">端點行為：這些可讓您自訂特定的服務端點，包括 EndpointDispatcher。</span><span class="sxs-lookup"><span data-stu-id="e8b54-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="e8b54-140">合約行為：這些可讓您分別在客戶<xref:System.ServiceModel.Dispatcher.ClientRuntime>端<xref:System.ServiceModel.Dispatcher.DispatchRuntime>或服務上自訂或類別。</span><span class="sxs-lookup"><span data-stu-id="e8b54-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="e8b54-141">作業行為：這些可讓您分別在客戶<xref:System.ServiceModel.Dispatcher.ClientOperation>端<xref:System.ServiceModel.Dispatcher.DispatchOperation>或服務上自訂或類別。</span><span class="sxs-lookup"><span data-stu-id="e8b54-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="e8b54-142">若要做為物件共用延伸項目的用途，可以建立端點行為或服務行為。</span><span class="sxs-lookup"><span data-stu-id="e8b54-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="e8b54-143">這個範例採用服務行為，服務行為可以將物件共用能力套用至服務的每個端點。</span><span class="sxs-lookup"><span data-stu-id="e8b54-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="e8b54-144">服務行為是藉由實作 <xref:System.ServiceModel.Description.IServiceBehavior> 介面來建立。</span><span class="sxs-lookup"><span data-stu-id="e8b54-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="e8b54-145">有一些方法可以讓 ServiceModel 察覺自訂行為：</span><span class="sxs-lookup"><span data-stu-id="e8b54-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="e8b54-146">使用自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="e8b54-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="e8b54-147">以命令方式將它加入至服務描述的行為集合。</span><span class="sxs-lookup"><span data-stu-id="e8b54-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="e8b54-148">延伸組態檔。</span><span class="sxs-lookup"><span data-stu-id="e8b54-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="e8b54-149">這個範例會使用自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="e8b54-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="e8b54-150">建構 <xref:System.ServiceModel.ServiceHost> 時，會檢查服務型別定義中使用的屬性，並將可用的行為加入至服務描述的行為集合。</span><span class="sxs-lookup"><span data-stu-id="e8b54-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="e8b54-151"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` 介面有`,`三個方法： <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>和。<xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> <xref:System.ServiceModel.Description.IServiceBehavior></span><span class="sxs-lookup"><span data-stu-id="e8b54-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="e8b54-152">當初始化時<xref:System.ServiceModel.ServiceHost> ，WCF 會呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="e8b54-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="e8b54-153">首先會呼叫 <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>，這個方法允許檢查服務有無不一致之處。</span><span class="sxs-lookup"><span data-stu-id="e8b54-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="e8b54-154">接著會呼叫 <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>，這個方法只有在非常進階的狀況中才需要使用。</span><span class="sxs-lookup"><span data-stu-id="e8b54-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="e8b54-155">最後會呼叫 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>，這個方法負責設定執行階段。</span><span class="sxs-lookup"><span data-stu-id="e8b54-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="e8b54-156">下列參數會傳遞至 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>：</span><span class="sxs-lookup"><span data-stu-id="e8b54-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="e8b54-157">`Description`：這個參數會提供整個服務的服務描述。</span><span class="sxs-lookup"><span data-stu-id="e8b54-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="e8b54-158">可以用來檢查有關服務端點、合約、繫結程序以及與服務相關聯之其他資料的描述資料。</span><span class="sxs-lookup"><span data-stu-id="e8b54-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="e8b54-159">`ServiceHostBase`：這個參數會提供<xref:System.ServiceModel.ServiceHostBase>目前正在初始化的。</span><span class="sxs-lookup"><span data-stu-id="e8b54-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="e8b54-160">在自訂 <xref:System.ServiceModel.Description.IServiceBehavior> 實作中，會為 `ObjectPoolInstanceProvider` 產生新的執行個體，並將新執行個體指派至附加到 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 之每個 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 中的 <xref:System.ServiceModel.ServiceHostBase> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e8b54-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp  
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 <span data-ttu-id="e8b54-161">除了 <xref:System.ServiceModel.Description.IServiceBehavior> 實作之外，`ObjectPoolingAttribute` 類別還有數個可以使用屬性引數來自訂物件集區的成員。</span><span class="sxs-lookup"><span data-stu-id="e8b54-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="e8b54-162">這些成員包括 `MaxSize`、`MinSize`、`Enabled` 和 `CreationTimeout`，可用來比對 .NET Enterprise Services 提供的物件共用功能集。</span><span class="sxs-lookup"><span data-stu-id="e8b54-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="e8b54-163">藉由使用新建立的自訂`ObjectPooling`屬性來標注服務執行，現在可以將物件共用行為新增至 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="e8b54-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="e8b54-164">攔截啟動與停用</span><span class="sxs-lookup"><span data-stu-id="e8b54-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="e8b54-165">物件共用的主要目標是，最佳化存留較短且建立和初始化時較會耗費資源的物件。</span><span class="sxs-lookup"><span data-stu-id="e8b54-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="e8b54-166">因此，好好利用的話，可以大幅提高應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="e8b54-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="e8b54-167">由於物件是從集區傳回，因此只能呼叫建構函式一次。</span><span class="sxs-lookup"><span data-stu-id="e8b54-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="e8b54-168">不過，有些應用程式會需要某些層級的控制權，以便初始化及清除單一內容期間使用的資源。</span><span class="sxs-lookup"><span data-stu-id="e8b54-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="e8b54-169">例如，用於一組計算的物件可以在處理下個計算之前，先重設私用欄位。</span><span class="sxs-lookup"><span data-stu-id="e8b54-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="e8b54-170">Enterprise Services 藉由讓物件開發人員覆寫來自 `Activate` 基底類別的 `Deactivate` 和 <xref:System.EnterpriseServices.ServicedComponent> 方法，啟用了這種特定內容的初始化。</span><span class="sxs-lookup"><span data-stu-id="e8b54-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="e8b54-171">物件集區會在從集區傳回物件之前，呼叫 `Activate` 方法。</span><span class="sxs-lookup"><span data-stu-id="e8b54-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="e8b54-172">當物件傳回集區時，會呼叫 `Deactivate`。</span><span class="sxs-lookup"><span data-stu-id="e8b54-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="e8b54-173"><xref:System.EnterpriseServices.ServicedComponent> 基底類別也有名為 `boolean` 的 `CanBePooled` 屬性，可以用來通知集區是否能進一步共用物件。</span><span class="sxs-lookup"><span data-stu-id="e8b54-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="e8b54-174">為了模擬此功能，範例會宣告具有上述成員的公用介面 (`IObjectControl`)。</span><span class="sxs-lookup"><span data-stu-id="e8b54-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="e8b54-175">接著，服務類別會實作這個介面，以提供內容特定的初始化。</span><span class="sxs-lookup"><span data-stu-id="e8b54-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="e8b54-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider> 實作必須經過修改，才能符合這些需求。</span><span class="sxs-lookup"><span data-stu-id="e8b54-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="e8b54-177">現在，每次您藉由呼叫`GetInstance`方法來取得物件時，您必須檢查`IObjectControl.`物件是否執行`Activate` ，如果有的話，您必須適當地呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e8b54-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="e8b54-178">將物件傳回集區時，必須先檢查 `CanBePooled` 屬性，才能將物件新增回集區。</span><span class="sxs-lookup"><span data-stu-id="e8b54-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="e8b54-179">由於服務開發人員可以決定是否可以共用物件，在特定時間內，集區中的物件計數可能會低於大小下限。</span><span class="sxs-lookup"><span data-stu-id="e8b54-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="e8b54-180">因此，您必須檢查物件計數是否曾經低於最低層級，並且在清除程序中執行必要的初始化。</span><span class="sxs-lookup"><span data-stu-id="e8b54-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="e8b54-181">當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="e8b54-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="e8b54-182">在每個主控台視窗中按下 Enter 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="e8b54-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e8b54-183">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="e8b54-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e8b54-184">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e8b54-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e8b54-185">若要建立方案，請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="e8b54-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e8b54-186">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="e8b54-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e8b54-187">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e8b54-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e8b54-188">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e8b54-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="e8b54-189">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="e8b54-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8b54-190">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e8b54-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
