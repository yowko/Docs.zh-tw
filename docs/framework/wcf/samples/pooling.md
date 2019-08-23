---
title: Pooling
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: a01b7897031bb379dd8aaa30e32454c08b14cc08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965543"
---
# <a name="pooling"></a><span data-ttu-id="be996-102">Pooling</span><span class="sxs-lookup"><span data-stu-id="be996-102">Pooling</span></span>
<span data-ttu-id="be996-103">這個範例會示範如何擴充 Windows Communication Foundation (WCF) 以支持對象共用。</span><span class="sxs-lookup"><span data-stu-id="be996-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="be996-104">此範例會示範如何建立語法上及語意上與 Enterprise Services 的 `ObjectPoolingAttribute` 屬性功能相似的屬性。</span><span class="sxs-lookup"><span data-stu-id="be996-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="be996-105">物件共用可以大幅提升應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="be996-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="be996-106">不過，如果不當使用，可能會產生反效果。</span><span class="sxs-lookup"><span data-stu-id="be996-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="be996-107">物件共用有助於避免重複建立常用物件的煩瑣工作，這些物件往往需要大量的初始設定。</span><span class="sxs-lookup"><span data-stu-id="be996-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="be996-108">不過，如果呼叫共用物件上的方法要花費相當長的時間才能完成，而一旦到達集區的大小上限，物件共用就得將多出的要求加入佇列中。</span><span class="sxs-lookup"><span data-stu-id="be996-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="be996-109">它可能因此無法受理某個建立物件的要求，而擲回逾時例外狀況。</span><span class="sxs-lookup"><span data-stu-id="be996-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be996-110">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="be996-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="be996-111">建立 WCF 延伸模組的第一個步驟是決定要使用的擴充點。</span><span class="sxs-lookup"><span data-stu-id="be996-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="be996-112">在 WCF 中, 「*發送器*」一詞指的是執行時間元件, 負責將傳入訊息轉換成使用者服務上的方法調用, 以及將該方法的傳回值轉換成外寄訊息。</span><span class="sxs-lookup"><span data-stu-id="be996-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="be996-113">WCF 服務會為每個端點建立發送器。</span><span class="sxs-lookup"><span data-stu-id="be996-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="be996-114">如果與該用戶端相關聯的合約是雙工合約, WCF 用戶端就必須使用發送器。</span><span class="sxs-lookup"><span data-stu-id="be996-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="be996-115">通道和端點發送器可以公開各種控制發送器行為的屬性，提供適用於整個通道及合約範圍的擴充性。</span><span class="sxs-lookup"><span data-stu-id="be996-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="be996-116"><xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> 屬性同時可讓您檢查、修改或自訂分派程序。</span><span class="sxs-lookup"><span data-stu-id="be996-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="be996-117">此範例著重於 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 屬性，這個屬性會指向提供服務類別之執行個體的物件。</span><span class="sxs-lookup"><span data-stu-id="be996-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="be996-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="be996-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="be996-119">在 WCF 中, 發送器會使用執行<xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> <xref:System.ServiceModel.Dispatcher.IInstanceProvider>介面的來建立服務類別的實例。</span><span class="sxs-lookup"><span data-stu-id="be996-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="be996-120">這個介面有三個方法：</span><span class="sxs-lookup"><span data-stu-id="be996-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="be996-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>：當訊息抵達時, 發送器會呼叫<xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>方法來建立服務類別的實例來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="be996-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="be996-122">呼叫此方法的頻率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性決定。</span><span class="sxs-lookup"><span data-stu-id="be996-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="be996-123">例如，如果 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性設定為 <xref:System.ServiceModel.InstanceContextMode.PerCall>，則會建立服務類別的執行個體來處理送達的每個訊息，所以只要訊息一送達就會呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>。</span><span class="sxs-lookup"><span data-stu-id="be996-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="be996-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>：這與先前的方法相同, 不同之處在于沒有訊息引數時叫用。</span><span class="sxs-lookup"><span data-stu-id="be996-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="be996-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>：當服務實例的存留期已過時, 發送器會呼叫<xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>方法。</span><span class="sxs-lookup"><span data-stu-id="be996-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="be996-126">就和 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> 方法一樣，呼叫這個方法的頻率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性決定。</span><span class="sxs-lookup"><span data-stu-id="be996-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="be996-127">物件集區</span><span class="sxs-lookup"><span data-stu-id="be996-127">The Object Pool</span></span>  
 <span data-ttu-id="be996-128">自訂的 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 實作會為服務提供必要的物件共用語意 (Semantics)。</span><span class="sxs-lookup"><span data-stu-id="be996-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="be996-129">因此，這個範例具有 `ObjectPoolingInstanceProvider` 型別，可以提供進行共用所需之 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 的自訂實作。</span><span class="sxs-lookup"><span data-stu-id="be996-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="be996-130">當 `Dispatcher` 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> 方法，而不是建立新執行個體時，自訂實作會在記憶體中集區尋找現有物件。</span><span class="sxs-lookup"><span data-stu-id="be996-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="be996-131">如果找到了，就會將物件傳回。</span><span class="sxs-lookup"><span data-stu-id="be996-131">If one is available, it is returned.</span></span> <span data-ttu-id="be996-132">否則，會建立新的物件。</span><span class="sxs-lookup"><span data-stu-id="be996-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="be996-133">下列範例程式碼會示範 `GetInstance` 實作。</span><span class="sxs-lookup"><span data-stu-id="be996-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;            
}  
```  
  
 <span data-ttu-id="be996-134">自訂 `ReleaseInstance` 實作會將釋放的執行個體新增回集區，並遞減 `ActiveObjectsCount` 值。</span><span class="sxs-lookup"><span data-stu-id="be996-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="be996-135">`Dispatcher` 可以從不同執行緒中呼叫這些方法，因此需要可在 `ObjectPoolingInstanceProvider` 類別中同步存取類別層級成員的權限。</span><span class="sxs-lookup"><span data-stu-id="be996-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests   
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();                       
    }  
}  
```  
  
 <span data-ttu-id="be996-136">`ReleaseInstance`方法提供「清除初始化」功能。</span><span class="sxs-lookup"><span data-stu-id="be996-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="be996-137">集區通常會在集區的存留期中保留最低限度數目的物件。</span><span class="sxs-lookup"><span data-stu-id="be996-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="be996-138">不過，可能有些時段會出現過度使用的情形，因而需要在集區中建立其他物件以達到組態中指定的上限。</span><span class="sxs-lookup"><span data-stu-id="be996-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="be996-139">最後當集區的活動變少時，這些多餘的物件可能會變成額外的負荷。</span><span class="sxs-lookup"><span data-stu-id="be996-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="be996-140">因此，當 `activeObjectsCount` 成為零時，閒置計時器就會啟動，以觸發並執行清除循環。</span><span class="sxs-lookup"><span data-stu-id="be996-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="be996-141">新增行為</span><span class="sxs-lookup"><span data-stu-id="be996-141">Adding the Behavior</span></span>  
 <span data-ttu-id="be996-142">您可以使用下列行為來連結發送器層延伸：</span><span class="sxs-lookup"><span data-stu-id="be996-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="be996-143">服務行為。</span><span class="sxs-lookup"><span data-stu-id="be996-143">Service Behaviors.</span></span> <span data-ttu-id="be996-144">這些行為允許自訂整個服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="be996-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="be996-145">端點行為。</span><span class="sxs-lookup"><span data-stu-id="be996-145">Endpoint Behaviors.</span></span> <span data-ttu-id="be996-146">這些行為允許自訂服務端點，也就是通道和端點發送器。</span><span class="sxs-lookup"><span data-stu-id="be996-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="be996-147">合約行為。</span><span class="sxs-lookup"><span data-stu-id="be996-147">Contract Behaviors.</span></span> <span data-ttu-id="be996-148">這些行為允許分別在用戶端和服務上自訂 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 和 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別。</span><span class="sxs-lookup"><span data-stu-id="be996-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="be996-149">若要做為物件共用延伸之用，您必須建立服務行為。</span><span class="sxs-lookup"><span data-stu-id="be996-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="be996-150">服務行為是藉由實作 <xref:System.ServiceModel.Description.IServiceBehavior> 介面來建立。</span><span class="sxs-lookup"><span data-stu-id="be996-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="be996-151">有一些方法可以讓服務模型察覺自訂行為：</span><span class="sxs-lookup"><span data-stu-id="be996-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="be996-152">使用自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="be996-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="be996-153">以命令方式將它加入至服務描述的行為集合。</span><span class="sxs-lookup"><span data-stu-id="be996-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="be996-154">延伸組態檔。</span><span class="sxs-lookup"><span data-stu-id="be996-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="be996-155">這個範例會使用自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="be996-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="be996-156">建構 <xref:System.ServiceModel.ServiceHost> 時，它會檢查服務型別定義中使用的屬性，然後將可用的行為加入至服務描述的行為集合。</span><span class="sxs-lookup"><span data-stu-id="be996-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="be996-157"><xref:System.ServiceModel.Description.IServiceBehavior> 介面中有三個方法：<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>、<xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> 和 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>。</span><span class="sxs-lookup"><span data-stu-id="be996-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="be996-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> 方法是用來確保行為可以套用至服務。</span><span class="sxs-lookup"><span data-stu-id="be996-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="be996-159">在這個範例中，此實作會確認服務不是透過 <xref:System.ServiceModel.InstanceContextMode.Single> 所設定。</span><span class="sxs-lookup"><span data-stu-id="be996-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="be996-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> 方法是用來設定服務的繫結。</span><span class="sxs-lookup"><span data-stu-id="be996-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="be996-161">這在本案例中不是必要項。</span><span class="sxs-lookup"><span data-stu-id="be996-161">It is not required in this scenario.</span></span> <span data-ttu-id="be996-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> 是用來設定服務的發送器。</span><span class="sxs-lookup"><span data-stu-id="be996-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="be996-163">當初始化時<xref:System.ServiceModel.ServiceHost> , WCF 會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="be996-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="be996-164">傳遞至這個方法中的參數如下：</span><span class="sxs-lookup"><span data-stu-id="be996-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="be996-165">`Description`：這個引數會提供整個服務的服務描述。</span><span class="sxs-lookup"><span data-stu-id="be996-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="be996-166">這可以用來檢查有關服務之端點、合約、繫結程序及其他資料的描述資料。</span><span class="sxs-lookup"><span data-stu-id="be996-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="be996-167">`ServiceHostBase`：這個引數會<xref:System.ServiceModel.ServiceHostBase>提供目前正在初始化的。</span><span class="sxs-lookup"><span data-stu-id="be996-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="be996-168">在自訂 <xref:System.ServiceModel.Description.IServiceBehavior> 實作中，會產生 `ObjectPoolingInstanceProvider` 的新執行個體，然後將它指派給 ServiceHostBase 中每個 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 的 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 屬性。</span><span class="sxs-lookup"><span data-stu-id="be996-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,   
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior   
    // (this.throttlingBehavior==null), it should have initialized   
    // a single ServiceThrottle on all ChannelDispatchers.    
    // As we loop through the ChannelDispatchers, we verify that   
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in   
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all   
            // endpoints. If there were others, we could not enforce   
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&   
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                if (throttle == null)  
                {  
                    throttle = cd.ServiceThrottle;  
                }  
                if (cd.ServiceThrottle == null)  
                {  
                    throw new   
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =   
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items   
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >   
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="be996-169">除了 <xref:System.ServiceModel.Description.IServiceBehavior> 實作之外，<xref:System.EnterpriseServices.ObjectPoolingAttribute> 類別還有數個可以使用屬性引數來自訂物件集區的成員。</span><span class="sxs-lookup"><span data-stu-id="be996-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="be996-170">這些成員包括 <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>、<xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> 和 <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>，可以用來配合 .NET Enterprise Services 提供的物件共用功能集。</span><span class="sxs-lookup"><span data-stu-id="be996-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="be996-171">藉由使用新建立的自訂`ObjectPooling`屬性來標注服務執行, 現在可以將物件共用行為新增至 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="be996-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="be996-172">執行範例</span><span class="sxs-lookup"><span data-stu-id="be996-172">Running the Sample</span></span>  
 <span data-ttu-id="be996-173">此範例會示範可在特定案例中藉由使用物件共用取得的效能優勢。</span><span class="sxs-lookup"><span data-stu-id="be996-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="be996-174">服務應用程式會實作兩個服務：`WorkService` 和 `ObjectPooledWorkService`。</span><span class="sxs-lookup"><span data-stu-id="be996-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="be996-175">這兩個服務會共用相同的實作；它們都必須進行昂貴的初始設定，然後再公開相對低廉的 `DoWork()` 方法。</span><span class="sxs-lookup"><span data-stu-id="be996-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="be996-176">唯一的差異在於 `ObjectPooledWorkService` 設定了物件共用：</span><span class="sxs-lookup"><span data-stu-id="be996-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }          
}  
```  
  
 <span data-ttu-id="be996-177">當您執行用戶端時，它會計算呼叫 `WorkService` 5 次的時間，</span><span class="sxs-lookup"><span data-stu-id="be996-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="be996-178">接著計算呼叫 `ObjectPooledWorkService` 5 次的時間，</span><span class="sxs-lookup"><span data-stu-id="be996-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="be996-179">然後顯示時間的差距：</span><span class="sxs-lookup"><span data-stu-id="be996-179">The difference in time is then displayed:</span></span>  
  
```  
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> <span data-ttu-id="be996-180">第一次執行用戶端時，兩個服務似乎都花費了相同的時間。</span><span class="sxs-lookup"><span data-stu-id="be996-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="be996-181">如果您重新執行範例，就可以看出 `ObjectPooledWorkService` 的回傳速度快多了，這是因為此物件的執行個體已經存在於集區中。</span><span class="sxs-lookup"><span data-stu-id="be996-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="be996-182">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="be996-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="be996-183">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="be996-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="be996-184">若要建立方案, 請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="be996-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="be996-185">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="be996-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be996-186">如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="be996-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="be996-187">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="be996-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="be996-188">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="be996-188">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="be996-189">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="be996-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="be996-190">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="be996-190">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
