---
title: 自訂存留期
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 8625877d9b4d05d5cf06af2c9f8ef10f701e98db
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715471"
---
# <a name="custom-lifetime"></a>自訂存留期

這個範例會示範如何撰寫 Windows Communication Foundation （WCF）延伸模組，為共用的 WCF 服務實例提供自訂的存留期服務。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本文的結尾。

## <a name="shared-instancing"></a>共用的實例

WCF 為您的服務實例提供了數種實例模式。 本文涵蓋的共用實例模式可讓您在多個通道之間共用服務實例。 用戶端可以與服務中的 factory 方法連線，並建立新的通道來開始通訊。 下列程式碼片段顯示用戶端應用程式如何為現有的服務實例建立新的通道：

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

共用執行個體模式不像其他執行個體模式，前者擁有釋出服務執行個體的唯一方式。 根據預設，當 <xref:System.ServiceModel.InstanceContext>關閉所有通道時，WCF 服務執行時間會檢查服務 <xref:System.ServiceModel.InstanceContextMode> 是否已設定為 <xref:System.ServiceModel.InstanceContextMode.PerCall> 或 <xref:System.ServiceModel.InstanceContextMode.PerSession>，如果是，則會釋放實例並宣告資源。 如果正在使用自訂 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>，WCF 會在發行實例之前，先叫用提供者的 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法。 如果 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 會傳回 `true` 實例會釋出，否則 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 的執行會負責使用回呼方法來通知閒置狀態的 `Dispatcher`。 這是藉由呼叫提供者的 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法來完成。

這個範例會示範如何延遲釋放具有20秒閒置超時的 <xref:System.ServiceModel.InstanceContext>。

## <a name="extending-the-instancecontext"></a>擴充 InstanceContext

在 WCF 中，<xref:System.ServiceModel.InstanceContext> 是服務實例和 `Dispatcher`之間的連結。 WCF 可讓您使用其可延伸物件模式加入新狀態或行為，以擴充這個執行時間元件。 可延伸物件模式用於 WCF 中，以新功能來擴充現有執行時間類別，或將新的狀態功能加入至物件。 在可延伸物件模式中有三種介面：<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601> 和 <xref:System.ServiceModel.IExtensionCollection%601>。

<xref:System.ServiceModel.IExtensibleObject%601> 介面會由物件執行，以允許自訂其功能的延伸模組。

<xref:System.ServiceModel.IExtension%601> 介面是由可以是型別 `T` 之類別延伸模組的物件所實作。

最後，<xref:System.ServiceModel.IExtensionCollection%601> 介面是 <xref:System.ServiceModel.IExtension%601> 的實作為集合，可讓您依其型別來抓取 <xref:System.ServiceModel.IExtension%601> 的執行。

因此，為了擴充 <xref:System.ServiceModel.InstanceContext>，您必須執行 <xref:System.ServiceModel.IExtension%601> 介面。 在此範例專案中，`CustomLeaseExtension` 類別包含此實作為。

```csharp
class CustomLeaseExtension : IExtension<InstanceContext>
{
}
```

<xref:System.ServiceModel.IExtension%601> 介面擁有兩種方法：<xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A>。 顧名思義，當執行階段將延伸模組連接到 <xref:System.ServiceModel.InstanceContext> 類別的執行個體以及從其中斷時，會呼叫這兩個方法。 在此範例中，`Attach` 方法用於追蹤屬於目前延伸模組執行個體的 <xref:System.ServiceModel.InstanceContext> 物件。

```csharp
InstanceContext owner;

public void Attach(InstanceContext owner)
{
    this.owner = owner;
}
```

此外，您必須將必要的實作加入至延伸模組，以提供延伸的存留時間支援。 因此，`ICustomLease` 介面會以所需的方法進行宣告，並在 `CustomLeaseExtension` 類別中執行。

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

當 WCF 在 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 執行中叫用 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法時，這個呼叫會路由傳送至 `CustomLeaseExtension`的 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法。 然後，`CustomLeaseExtension` 會檢查其私用狀態，以查看 <xref:System.ServiceModel.InstanceContext> 是否閒置。 如果閒置，則會傳回 `true`。 否則，它會啟動計時器一段指定的延伸存留時間。

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

在計時器的 `Elapsed` 事件中，會呼叫發送器中的回呼函式，以便啟動另一個清除迴圈。

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

當要移動到閒置狀態的實例有新訊息送達時，就無法更新執行中的計時器。

此範例會實作 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 以攔截對 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的呼叫，並將其路由至 `CustomLeaseExtension`。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作包含在 `CustomLifetimeLease` 類別中。 當 WCF 即將釋放服務實例時，就會叫用 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法。 不過，在 ServiceBehavior 的 `ISharedSessionInstance` 集合中，只有一個特定 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作的執行個體。 這表示在 WCF 檢查 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法時，不會知道 <xref:System.ServiceModel.InstanceContext> 是否已關閉。 因此，此範例會使用執行緒鎖定，將要求序列化為 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法。

> [!IMPORTANT]
> 使用執行緒封鎖並不是建議的方法，因為序列化可能會嚴重影響應用程式的效能。

[私用成員] 欄位會在 `CustomLifetimeLease` 類別中用來追蹤閒置狀態，而且是由 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法所傳回。 每次呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法時，就會傳回 `isIdle` 欄位，並將其重設為 `false`。  請務必將此值設定為 `false`，才能確保 Dispatcher 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法。

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

如果 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType> 方法傳回 `false`，發送器會使用 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法來註冊回呼函式。 此方法會接收要釋出之 <xref:System.ServiceModel.InstanceContext> 的參考。 因此，範例程式碼可以查詢 `ICustomLease` 類型延伸模組，並檢查擴充狀態下的 `ICustomLease.IsIdle` 屬性。

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

在核取 [`ICustomLease.IsIdle`] 屬性之前，必須設定回呼屬性，因為這對於 `CustomLeaseExtension` 會在它閒置時通知發送器是必要的。 如果 `ICustomLease.IsIdle` 傳回 `true`，`isIdle` 私用成員只會在 `CustomLifetimeLease` 中設定為 `true`，並呼叫回呼方法。 因為程式碼持有鎖定，所以其他執行緒無法變更此私用成員的值。 下次發送器呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>時，它會傳回 `true` 並讓發送器釋放實例。

既然自訂延伸模組的基礎已完成，現在必須將其連結至服務模型。 為了將 `CustomLeaseExtension` 的執行連結到 <xref:System.ServiceModel.InstanceContext>，WCF 提供 <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> 介面來執行 <xref:System.ServiceModel.InstanceContext>的啟動載入。 在此範例中，`CustomLeaseInitializer` 類別會實作此介面，並將 `CustomLeaseExtension` 的執行個體從唯一的方法初始化加入至 <xref:System.ServiceModel.InstanceContext.Extensions%2A> 集合。 初始化 <xref:System.ServiceModel.InstanceContext> 時，Dispatcher 會呼叫這個方法。

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 最後，<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 的執行會使用 <xref:System.ServiceModel.Description.IServiceBehavior> 的實連結至服務模型。 此實作放在 `CustomLeaseTimeAttribute` 類別中，而且它也衍生自 <xref:System.Attribute> 基底類別，以便當做屬性公開此行為。

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

您可以使用 `CustomLeaseTime` 屬性加上註解，以便將此行為加入至範例服務類別。

```csharp
[CustomLeaseTime(Timeout = 20000)]
public class EchoService : IEchoService
{
  //…
}
```

當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。

### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例

1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。

2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。

3. 若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](running-the-samples.md)中的指示。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
