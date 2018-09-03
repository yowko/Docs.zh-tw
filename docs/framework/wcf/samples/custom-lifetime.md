---
title: 自訂存留期
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 1946608c69401fb08f6eb458a8adabea24563963
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467742"
---
# <a name="custom-lifetime"></a><span data-ttu-id="c83ec-102">自訂存留期</span><span class="sxs-lookup"><span data-stu-id="c83ec-102">Custom lifetime</span></span>

<span data-ttu-id="c83ec-103">此範例示範如何撰寫 Windows Communication Foundation (WCF) 擴充程式以提供自訂存留時間服務共用的 WCF 服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="c83ec-103">This sample demonstrates how to write a Windows Communication Foundation (WCF) extension to provide custom lifetime services for shared WCF service instances.</span></span>

> [!NOTE]
> <span data-ttu-id="c83ec-104">此範例的安裝程序與建置指示位於本文的結尾。</span><span class="sxs-lookup"><span data-stu-id="c83ec-104">The setup procedure and build instructions for this sample are located at the end of this article.</span></span>

## <a name="shared-instancing"></a><span data-ttu-id="c83ec-105">共用執行個體</span><span class="sxs-lookup"><span data-stu-id="c83ec-105">Shared instancing</span></span>

<span data-ttu-id="c83ec-106">WCF 提供數個執行個體的模式，您的服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="c83ec-106">WCF offers several instancing modes for your service instances.</span></span> <span data-ttu-id="c83ec-107">本文章涵蓋的共用執行個體模式提供共用服務執行個體之間多個通道的方式。</span><span class="sxs-lookup"><span data-stu-id="c83ec-107">The shared instancing mode covered in this article provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="c83ec-108">用戶端可以連絡服務中的 factory 方法，並建立新的通道，以開始進行通訊。</span><span class="sxs-lookup"><span data-stu-id="c83ec-108">Clients can contact a factory method in the service and create a new channel to start communication.</span></span> <span data-ttu-id="c83ec-109">下列程式碼片段會示範如何用戶端應用程式會建立新的通道，與現有的服務執行個體：</span><span class="sxs-lookup"><span data-stu-id="c83ec-109">The following code snippet shows how a client application creates a new channel to an existing service instance:</span></span>

```csharp
// Create a header for the shared instance id
MessageHeader shareableInstanceContextHeader = MessageHeader.CreateHeader(
        CustomHeader.HeaderName,
        CustomHeader.HeaderNamespace,
        Guid.NewGuid().ToString());

// Create the channel factory
ChannelFactory<IEchoService> channelFactory =
    new ChannelFactory<IEchoService>("echoservice");

// Create the first channel
IEchoService proxy = channelFactory.CreateChannel();

// Call an operation to create shared service instance
using (new OperationContextScope((IClientChannel)proxy))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy.Echo("Apple"));
}

((IChannel)proxy).Close();

// Create the second channel
IEchoService proxy2 = channelFactory.CreateChannel();

// Call an operation using the same header that will reuse the shared service instance
using (new OperationContextScope((IClientChannel)proxy2))
{
    OperationContext.Current.OutgoingMessageHeaders.Add(shareableInstanceContextHeader);
    Console.WriteLine("Service returned: " + proxy2.Echo("Apple"));
}
```

<span data-ttu-id="c83ec-110">共用執行個體模式不像其他執行個體模式，前者擁有釋出服務執行個體的唯一方式。</span><span class="sxs-lookup"><span data-stu-id="c83ec-110">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="c83ec-111">根據預設，當所有通道則會都封閉<xref:System.ServiceModel.InstanceContext>，WCF 服務執行階段會檢查是否要服務<xref:System.ServiceModel.InstanceContextMode>設定為<xref:System.ServiceModel.InstanceContextMode.PerCall>或<xref:System.ServiceModel.InstanceContextMode.PerSession>，而且如果因此釋放執行個體，並宣告資源。</span><span class="sxs-lookup"><span data-stu-id="c83ec-111">By default, when all the channels are closed for an <xref:System.ServiceModel.InstanceContext>, the WCF service runtime checks to see if the service <xref:System.ServiceModel.InstanceContextMode> is configured to <xref:System.ServiceModel.InstanceContextMode.PerCall> or <xref:System.ServiceModel.InstanceContextMode.PerSession>, and if so releases the instance and claims the resources.</span></span> <span data-ttu-id="c83ec-112">如果自訂<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>是正在使用中，WCF 會叫用<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>之前釋放執行個體的提供者實作的方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-112">If a custom <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is being used, WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the provider implementation before releasing the instance.</span></span> <span data-ttu-id="c83ec-113">如果<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>會傳回`true`釋放的執行個體，否則為<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>實作都負責通知`Dispatcher`閒置狀態使用的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-113">If <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> returns `true` the instance is released, otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span> <span data-ttu-id="c83ec-114">這是藉由呼叫<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>的提供者的方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-114">This is done by calling the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method of the provider.</span></span>

<span data-ttu-id="c83ec-115">這個範例會示範如何延遲釋放<xref:System.ServiceModel.InstanceContext>與 20 秒的閒置逾時。</span><span class="sxs-lookup"><span data-stu-id="c83ec-115">This sample demonstrates how you can delay releasing the <xref:System.ServiceModel.InstanceContext> with an idle timeout of 20 seconds.</span></span>

## <a name="extending-the-instancecontext"></a><span data-ttu-id="c83ec-116">擴充 InstanceContext</span><span class="sxs-lookup"><span data-stu-id="c83ec-116">Extending the InstanceContext</span></span>

<span data-ttu-id="c83ec-117">在 WCF 中，<xref:System.ServiceModel.InstanceContext>是服務執行個體之間的連結和`Dispatcher`。</span><span class="sxs-lookup"><span data-stu-id="c83ec-117">In WCF, <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> <span data-ttu-id="c83ec-118">WCF 可讓您擴充這個執行階段元件使用其可擴充物件模式加入新的狀態或行為。</span><span class="sxs-lookup"><span data-stu-id="c83ec-118">WCF allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="c83ec-119">可擴充物件模式可在 WCF 中，搭配來擴充現有的執行階段類別的新功能，或新增狀態功能到物件。</span><span class="sxs-lookup"><span data-stu-id="c83ec-119">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="c83ec-120">在可延伸物件模式中有三種介面：<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601> 和 <xref:System.ServiceModel.IExtensionCollection%601>。</span><span class="sxs-lookup"><span data-stu-id="c83ec-120">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>

<span data-ttu-id="c83ec-121"><xref:System.ServiceModel.IExtensibleObject%601>介面藉由允許自訂其功能的延伸模組的物件。</span><span class="sxs-lookup"><span data-stu-id="c83ec-121">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by objects to allow extensions that customize their functionality.</span></span>

<span data-ttu-id="c83ec-122"><xref:System.ServiceModel.IExtension%601> 介面是由可以是型別 `T` 之類別延伸模組的物件所實作。</span><span class="sxs-lookup"><span data-stu-id="c83ec-122">The <xref:System.ServiceModel.IExtension%601> interface is implemented by objects that can be extensions of classes of type `T`.</span></span>

<span data-ttu-id="c83ec-123">最後<xref:System.ServiceModel.IExtensionCollection%601>介面是一堆<xref:System.ServiceModel.IExtension%601>是用來擷取的實作的實作<xref:System.ServiceModel.IExtension%601>依其類型。</span><span class="sxs-lookup"><span data-stu-id="c83ec-123">And finally, the <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of <xref:System.ServiceModel.IExtension%601> implementations that allows for retrieving an implementation of <xref:System.ServiceModel.IExtension%601> by their type.</span></span>

<span data-ttu-id="c83ec-124">因此，若要擴充<xref:System.ServiceModel.InstanceContext>，您必須實作<xref:System.ServiceModel.IExtension%601>介面。</span><span class="sxs-lookup"><span data-stu-id="c83ec-124">Therefore, in order to extend the <xref:System.ServiceModel.InstanceContext>, you must implement the <xref:System.ServiceModel.IExtension%601> interface.</span></span> <span data-ttu-id="c83ec-125">在此範例專案中，`CustomLeaseExtension`類別包含這項實作。</span><span class="sxs-lookup"><span data-stu-id="c83ec-125">In this sample project, the `CustomLeaseExtension` class contains this implementation.</span></span>

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<span data-ttu-id="c83ec-126"><xref:System.ServiceModel.IExtension%601> 介面擁有兩種方法：<xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A>。</span><span class="sxs-lookup"><span data-stu-id="c83ec-126">The <xref:System.ServiceModel.IExtension%601> interface has two methods <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span> <span data-ttu-id="c83ec-127">顧名思義，當執行階段將延伸模組連接到 <xref:System.ServiceModel.InstanceContext> 類別的執行個體以及從其中斷時，會呼叫這兩個方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-127">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="c83ec-128">在此範例中，`Attach` 方法用於追蹤屬於目前延伸模組執行個體的 <xref:System.ServiceModel.InstanceContext> 物件。</span><span class="sxs-lookup"><span data-stu-id="c83ec-128">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

<span data-ttu-id="c83ec-129">此外，您必須將必要的實作加入至延伸模組，以提供延伸的存留時間支援。</span><span class="sxs-lookup"><span data-stu-id="c83ec-129">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="c83ec-130">因此，`ICustomLease`介面以所需的方法進行宣告和實作中`CustomLeaseExtension`類別。</span><span class="sxs-lookup"><span data-stu-id="c83ec-130">Therefore, the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>

```csharp
interface ICustomLease
{
    bool IsIdle { get; }
    InstanceContextIdleCallback Callback { get; set; }
}

class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease
{
}
```

<span data-ttu-id="c83ec-131">當叫用 WCF<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法中的<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>實作，這個呼叫會路由傳送至<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法`CustomLeaseExtension`。</span><span class="sxs-lookup"><span data-stu-id="c83ec-131">When WCF invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation, this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="c83ec-132">然後，`CustomLeaseExtension`檢查其私用的狀態，以查看是否<xref:System.ServiceModel.InstanceContext>處於閒置狀態。</span><span class="sxs-lookup"><span data-stu-id="c83ec-132">Then, the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="c83ec-133">如果它處於閒置狀態，它會傳回`true`。</span><span class="sxs-lookup"><span data-stu-id="c83ec-133">If it is idle, it returns `true`.</span></span> <span data-ttu-id="c83ec-134">否則，它會啟動計時器一段指定的延伸存留時間。</span><span class="sxs-lookup"><span data-stu-id="c83ec-134">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>

```csharp
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

<span data-ttu-id="c83ec-135">在計時器的`Elapsed`事件發送器的回呼函式呼叫才能啟動另一個清除循環。</span><span class="sxs-lookup"><span data-stu-id="c83ec-135">In the timer’s `Elapsed` event, the callback function in the Dispatcher is called in order to start another clean-up cycle.</span></span>

```csharp
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)
{
    lock (thisLock)
    {
        StopTimer();
        isIdle = true;
        Utility.WriteMessageToConsole(
            ResourceHelper.GetString("MsgLeaseExpired"));
        callback(owner);
    }
}
```

<span data-ttu-id="c83ec-136">沒有任何新訊息送達執行個體移到閒置狀態時，更新執行中的計時器的方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-136">There's no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>

<span data-ttu-id="c83ec-137">此範例會實作 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 以攔截對 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的呼叫，並將其路由至 `CustomLeaseExtension`。</span><span class="sxs-lookup"><span data-stu-id="c83ec-137">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="c83ec-138"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作包含在 `CustomLifetimeLease` 類別中。</span><span class="sxs-lookup"><span data-stu-id="c83ec-138">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="c83ec-139"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF 即將要釋放服務執行個體時，會叫用方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-139">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when WCF is about to release the service instance.</span></span> <span data-ttu-id="c83ec-140">不過，在 ServiceBehavior 的 `ISharedSessionInstance` 集合中，只有一個特定 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c83ec-140">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="c83ec-141">這表示沒有任何方法的了解如果<xref:System.ServiceModel.InstanceContext>已關閉時，WCF 會檢查<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-141">This means there's no way of knowing if the <xref:System.ServiceModel.InstanceContext> is closed at the time WCF checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="c83ec-142">因此，此範例會使用執行緒封鎖來序列化要求<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-142">Therefore, this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c83ec-143">使用執行緒封鎖並不是建議的方法，因為序列化可能會嚴重影響應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="c83ec-143">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>

<span data-ttu-id="c83ec-144">私用成員欄位使用於`CustomLifetimeLease`類別來追蹤閒置狀態，並傳回<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-144">A private member field is used in the `CustomLifetimeLease` class to track the idle state and is returned by the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="c83ec-145">每次<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>呼叫方法時，`isIdle`欄位是傳回，而且重設為`false`。</span><span class="sxs-lookup"><span data-stu-id="c83ec-145">Each time the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is called, the `isIdle` field is returned and reset to `false`.</span></span>  <span data-ttu-id="c83ec-146">請務必將此值設定為 `false`，才能確保 Dispatcher 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-146">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>

```csharp
public bool IsIdle(InstanceContext instanceContext)
{
    get
    {
        lock (thisLock)
        {
            //...
            bool idleCopy = isIdle;
            isIdle = false;
            return idleCopy;
        }
    }
}
```

<span data-ttu-id="c83ec-147">如果<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>方法會傳回`false`，發送器藉由註冊回呼函式<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-147">If the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> method returns `false`, the Dispatcher registers a callback function by using the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span> <span data-ttu-id="c83ec-148">此方法會接收要釋出之 <xref:System.ServiceModel.InstanceContext> 的參考。</span><span class="sxs-lookup"><span data-stu-id="c83ec-148">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="c83ec-149">因此，範例程式碼可以查詢`ICustomLease`輸入副檔名，並檢查`ICustomLease.IsIdle`屬性在擴充的狀態。</span><span class="sxs-lookup"><span data-stu-id="c83ec-149">Therefore, the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>

```csharp
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

<span data-ttu-id="c83ec-150">再`ICustomLease.IsIdle`會檢查屬性，回呼屬性必須設定，因為這是不可或缺的`CustomLeaseExtension`通知 Dispatcher 它變成閒置時。</span><span class="sxs-lookup"><span data-stu-id="c83ec-150">Before the `ICustomLease.IsIdle` property is checked, the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="c83ec-151">如果 `ICustomLease.IsIdle` 傳回 `true`，`isIdle` 私用成員只會在 `CustomLifetimeLease` 中設定為 `true`，並呼叫回呼方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-151">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="c83ec-152">由於程式碼保留鎖定，其他執行緒無法變更此私用成員的值。</span><span class="sxs-lookup"><span data-stu-id="c83ec-152">Because the code holds a lock, other threads can't change the value of this private member.</span></span> <span data-ttu-id="c83ec-153">與發送器會呼叫在下一次<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>，它會傳回`true`然後讓 Dispatcher 釋出執行個體。</span><span class="sxs-lookup"><span data-stu-id="c83ec-153">And the next time Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>, it returns `true` and lets Dispatcher release the instance.</span></span>

<span data-ttu-id="c83ec-154">既然自訂延伸模組的基礎已完成，現在必須將其連結至服務模型。</span><span class="sxs-lookup"><span data-stu-id="c83ec-154">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="c83ec-155">若要將連結`CustomLeaseExtension`實作，以<xref:System.ServiceModel.InstanceContext>，WCF 會提供<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>介面來執行的啟動程序<xref:System.ServiceModel.InstanceContext>。</span><span class="sxs-lookup"><span data-stu-id="c83ec-155">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, WCF provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="c83ec-156">在此範例中，`CustomLeaseInitializer` 類別會實作此介面，並將 `CustomLeaseExtension` 的執行個體從唯一的方法初始化加入至 <xref:System.ServiceModel.InstanceContext.Extensions%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="c83ec-156">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="c83ec-157">初始化 <xref:System.ServiceModel.InstanceContext> 時，Dispatcher 會呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="c83ec-157">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 <span data-ttu-id="c83ec-158">最後<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>實作會連結至服務模型使用<xref:System.ServiceModel.Description.IServiceBehavior>實作。</span><span class="sxs-lookup"><span data-stu-id="c83ec-158">Finally the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="c83ec-159">此實作放在 `CustomLeaseTimeAttribute` 類別中，而且它也衍生自 `Attribute` 基底類別，以便當做屬性公開此行為。</span><span class="sxs-lookup"><span data-stu-id="c83ec-159">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span>

```csharp
public void ApplyDispatchBehavior(ServiceDescription description,
           ServiceHostBase serviceHostBase)
{
    CustomLifetimeLease customLease = new CustomLifetimeLease(timeout);

    foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)
    {
        ChannelDispatcher cd = cdb as ChannelDispatcher;

        if (cd != null)
        {
            foreach (EndpointDispatcher ed in cd.Endpoints)
            {
                ed.DispatchRuntime.InstanceContextProvider = customLease;
            }
        }
    }
}
```

<span data-ttu-id="c83ec-160">您可以使用 `CustomLeaseTime` 屬性加上註解，以便將此行為加入至範例服務類別。</span><span class="sxs-lookup"><span data-stu-id="c83ec-160">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

<span data-ttu-id="c83ec-161">當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="c83ec-161">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="c83ec-162">在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="c83ec-162">Press ENTER in each console window to shut down the service and client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c83ec-163">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="c83ec-163">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c83ec-164">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c83ec-164">Ensure that you've performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="c83ec-165">若要建置方案的 C# 或 Visual Basic.NET 版本，請依照下列中的指示[建置 Windows Communication Foundation 範例](building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c83ec-165">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="c83ec-166">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="c83ec-166">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c83ec-167">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="c83ec-167">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c83ec-168">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="c83ec-168">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c83ec-169">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="c83ec-169">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c83ec-170">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="c83ec-170">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
