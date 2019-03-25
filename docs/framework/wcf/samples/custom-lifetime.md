---
title: 自訂存留期
ms.date: 08/20/2018
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: be6013d568e3625c5eac7e0c145db7df1c6917e3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410377"
---
# <a name="custom-lifetime"></a>自訂存留期

此範例示範如何撰寫 Windows Communication Foundation (WCF) 擴充程式以提供自訂存留時間服務共用的 WCF 服務執行個體。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本文的結尾。

## <a name="shared-instancing"></a>共用執行個體

WCF 提供數個執行個體的模式，您的服務執行個體。 本文章涵蓋的共用執行個體模式提供共用服務執行個體之間多個通道的方式。 用戶端可以連絡服務中的 factory 方法，並建立新的通道，以開始進行通訊。 下列程式碼片段會示範如何用戶端應用程式會建立新的通道，與現有的服務執行個體：

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

共用執行個體模式不像其他執行個體模式，前者擁有釋出服務執行個體的唯一方式。 根據預設，當所有通道則會都封閉<xref:System.ServiceModel.InstanceContext>，WCF 服務執行階段會檢查是否要服務<xref:System.ServiceModel.InstanceContextMode>設定為<xref:System.ServiceModel.InstanceContextMode.PerCall>或<xref:System.ServiceModel.InstanceContextMode.PerSession>，而且如果因此釋放執行個體，並宣告資源。 如果自訂<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>是正在使用中，WCF 會叫用<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>之前釋放執行個體的提供者實作的方法。 如果<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>會傳回`true`釋放的執行個體，否則為<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>實作都負責通知`Dispatcher`閒置狀態使用的回呼方法。 這是藉由呼叫<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>的提供者的方法。

這個範例會示範如何延遲釋放<xref:System.ServiceModel.InstanceContext>與 20 秒的閒置逾時。

## <a name="extending-the-instancecontext"></a>擴充 InstanceContext

在 WCF 中，<xref:System.ServiceModel.InstanceContext>是服務執行個體之間的連結和`Dispatcher`。 WCF 可讓您擴充這個執行階段元件使用其可擴充物件模式加入新的狀態或行為。 可擴充物件模式可在 WCF 中，搭配來擴充現有的執行階段類別的新功能，或新增狀態功能到物件。 在可延伸物件模式中有三種介面：<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601> 和 <xref:System.ServiceModel.IExtensionCollection%601>。

<xref:System.ServiceModel.IExtensibleObject%601>介面藉由允許自訂其功能的延伸模組的物件。


  <xref:System.ServiceModel.IExtension%601> 介面是由可以是型別 `T` 之類別延伸模組的物件所實作。

最後<xref:System.ServiceModel.IExtensionCollection%601>介面是一堆<xref:System.ServiceModel.IExtension%601>是用來擷取的實作的實作<xref:System.ServiceModel.IExtension%601>依其類型。

因此，若要擴充<xref:System.ServiceModel.InstanceContext>，您必須實作<xref:System.ServiceModel.IExtension%601>介面。 在此範例專案中，`CustomLeaseExtension`類別包含這項實作。

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

此外，您必須將必要的實作加入至延伸模組，以提供延伸的存留時間支援。 因此，`ICustomLease`介面以所需的方法進行宣告和實作中`CustomLeaseExtension`類別。

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

當叫用 WCF<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法中的<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>實作，這個呼叫會路由傳送至<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法`CustomLeaseExtension`。 然後，`CustomLeaseExtension`檢查其私用的狀態，以查看是否<xref:System.ServiceModel.InstanceContext>處於閒置狀態。 如果它處於閒置狀態，它會傳回`true`。 否則，它會啟動計時器一段指定的延伸存留時間。

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

在計時器的`Elapsed`事件發送器的回呼函式呼叫才能啟動另一個清除循環。

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

沒有任何新訊息送達執行個體移到閒置狀態時，更新執行中的計時器的方法。

此範例會實作 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 以攔截對 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的呼叫，並將其路由至 `CustomLeaseExtension`。 
  <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作包含在 `CustomLifetimeLease` 類別中。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> WCF 即將要釋放服務執行個體時，會叫用方法。 不過，在 ServiceBehavior 的 `ISharedSessionInstance` 集合中，只有一個特定 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作的執行個體。 這表示沒有任何方法的了解如果<xref:System.ServiceModel.InstanceContext>已關閉時，WCF 會檢查<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。 因此，此範例會使用執行緒封鎖來序列化要求<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。

> [!IMPORTANT]
> 使用執行緒封鎖並不是建議的方法，因為序列化可能會嚴重影響應用程式的效能。

私用成員欄位使用於`CustomLifetimeLease`類別來追蹤閒置狀態，並傳回<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>方法。 每次<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A>呼叫方法時，`isIdle`欄位是傳回，而且重設為`false`。  請務必將此值設定為 `false`，才能確保 Dispatcher 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法。

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

如果<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>方法會傳回`false`，發送器藉由註冊回呼函式<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A>方法。 此方法會接收要釋出之 <xref:System.ServiceModel.InstanceContext> 的參考。 因此，範例程式碼可以查詢`ICustomLease`輸入副檔名，並檢查`ICustomLease.IsIdle`屬性在擴充的狀態。

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

再`ICustomLease.IsIdle`會檢查屬性，回呼屬性必須設定，因為這是不可或缺的`CustomLeaseExtension`通知 Dispatcher 它變成閒置時。 如果 `ICustomLease.IsIdle` 傳回 `true`，`isIdle` 私用成員只會在 `CustomLifetimeLease` 中設定為 `true`，並呼叫回呼方法。 由於程式碼保留鎖定，其他執行緒無法變更此私用成員的值。 與發送器會呼叫在下一次<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A?displayProperty=nameWithType>，它會傳回`true`然後讓 Dispatcher 釋出執行個體。

既然自訂延伸模組的基礎已完成，現在必須將其連結至服務模型。 若要將連結`CustomLeaseExtension`實作，以<xref:System.ServiceModel.InstanceContext>，WCF 會提供<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>介面來執行的啟動程序<xref:System.ServiceModel.InstanceContext>。 在此範例中，`CustomLeaseInitializer` 類別會實作此介面，並將 `CustomLeaseExtension` 的執行個體從唯一的方法初始化加入至 <xref:System.ServiceModel.InstanceContext.Extensions%2A> 集合。 初始化 <xref:System.ServiceModel.InstanceContext> 時，Dispatcher 會呼叫這個方法。

```csharp
public void InitializeInstanceContext(InstanceContext instanceContext,
    System.ServiceModel.Channels.Message message, IContextChannel channel)

    //...

    IExtension<InstanceContext> customLeaseExtension =
        new CustomLeaseExtension(timeout, headerId);
    instanceContext.Extensions.Add(customLeaseExtension);
}
```

 最後<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider>實作會連結至服務模型使用<xref:System.ServiceModel.Description.IServiceBehavior>實作。 此實作放在 `CustomLeaseTimeAttribute` 類別中，而且它也衍生自 <xref:System.Attribute> 基底類別，以便當做屬性公開此行為。

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

1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](one-time-setup-procedure-for-the-wcf-samples.md)。

2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](building-the-samples.md)中的指示。

3. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](running-the-samples.md)。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> 如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`
