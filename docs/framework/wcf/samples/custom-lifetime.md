---
title: 自訂存留期
ms.date: 03/30/2017
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
ms.openlocfilehash: 1d9baa2d6eab476d5c8428208576f341e71fef2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="custom-lifetime"></a>自訂存留期
這個範例會示範如何撰寫 Windows Communication Foundation (WCF) 擴充程式以提供自訂存留時間服務共用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務執行個體。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
## <a name="shared-instancing"></a>共用執行個體  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 針對您的服務執行個體提供數種執行個體模式。 本主題中涵蓋的「共用執行個體」模式提供一種方式，可以在多個通道間共用服務執行個體。 用戶端可以在本機解析執行個體的端點位址，或連絡服務中的 Factory 方法，以取得執行中執行個體的端點位址。 一旦擁有端點位址之後，它就可以建立新的通道並開始通訊。 下列程式碼片段示範用戶端應用程式如何針對現有的服務執行個體建立新的通道。  
  
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
  
 共用執行個體模式不像其他執行個體模式，前者擁有釋出服務執行個體的唯一方式。 當系統為某個執行個體關閉所有通道時，服務 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 執行階段會啟動計時器。 如果在逾時到期前沒有人建立連線，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會釋出執行個體並宣告資源。 在清場過程中，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會先叫用所有 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 實作的 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 方法，然後才釋出執行個體。 如果它們全部傳回 `true`，則會釋出執行個體。 否則，<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作會負責使用回呼方法，通知 `Dispatcher` 閒置狀態。  
  
 根據預設，<xref:System.ServiceModel.InstanceContext> 的閒置逾時值為一分鐘。 不過，此範例示範您可以如何使用自訂延伸模組擴充這個時間。  
  
## <a name="extending-the-instancecontext"></a>擴充 InstanceContext  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，<xref:System.ServiceModel.InstanceContext> 是服務執行個體與 `Dispatcher` 之間的連結。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可讓您使用其可延伸物件模式加入新狀態或行為，以擴充這個執行階段元件。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中使用可擴充物件模式，可以搭配新功能來擴充現有執行階段類別，或新增狀態功能到物件。 在可延伸物件模式中有三種介面：`IExtensibleObject<T>`、`IExtension<T>` 和 `IExtensionCollection<T>`。  
  
 `IExtensibleObject<T>` 介面是由允許自訂其功能的延伸模組所實作的。  
  
 `IExtension<T>` 介面是由可以是型別 `T` 之類別延伸模組的物件所實作。  
  
 最後，`IExtensionCollection<T>` 介面則是 `IExtensions` 的集合，可允許依其型別擷取 `IExtensions`。  
  
 因此，若要擴充 <xref:System.ServiceModel.InstanceContext>，您必須實作 `IExtension` 介面。 在此範例專案中，`CustomLeaseExtension` 類別包含這個實作。  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 `IExtension` 介面擁有兩種方法：`Attach` 和 `Detach`。 顧名思義，當執行階段將延伸模組連接到 <xref:System.ServiceModel.InstanceContext> 類別的執行個體以及從其中斷時，會呼叫這兩個方法。 在此範例中，`Attach` 方法用於追蹤屬於目前延伸模組執行個體的 <xref:System.ServiceModel.InstanceContext> 物件。  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 此外，您必須將必要的實作加入至延伸模組，以提供延伸的存留時間支援。 因此，系統會使用所需的方法宣告 `ICustomLease` 介面，並在 `CustomLeaseExtension` 類別中實作。  
  
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
  
 當 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 在 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 實作中叫用 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 方法時，這個呼叫會路由至 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 的 `CustomLeaseExtension` 方法。 然後，`CustomLeaseExtension` 會檢查其私用狀態以查看 <xref:System.ServiceModel.InstanceContext> 是否閒置。 如果閒置，則會傳回 `true`。 否則，它會啟動計時器一段指定的延伸存留時間。  
  
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
  
 在計時器的 `Elapsed` 事件中，系統會呼叫 Dispatcher 中的回呼函式，以啟動另一個清除循環。  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 當移到閒置狀態的執行個體有新訊息時，無法更新執行中的計時器。  
  
 此範例會實作 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 以攔截對 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的呼叫，並將其路由至 `CustomLeaseExtension`。 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作包含在 `CustomLifetimeLease` 類別中。 當 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 即將釋出服務執行個體時，會叫用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 方法。 不過，在 ServiceBehavior 的 `ISharedSessionInstance` 集合中，只有一個特定 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 實作的執行個體。 也就是說，在 <xref:System.ServiceModel.InstanceContext> 檢查 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 方法時，沒有任何方式可以知道 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 即將關閉。 因此，此範例使用執行緒封鎖來序列化 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 方法的要求。  
  
> [!IMPORTANT]
>  使用執行緒封鎖並不是建議的方法，因為序列化可能會嚴重影響應用程式的效能。  
  
 在 `CustomLeaseExtension` 類別中會使用一個私用成員變數來追蹤 `IsIdle` 值。 每次系統擷取 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 的值時，就會傳回 `IsIdle` 私用成員，並重設為 `false`。 請務必將此值設定為 `false`，才能確保 Dispatcher 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> 方法。  
  
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
  
 如果 `ISharedSessionLifetime.IsIdle` 屬性傳回 `false`，Dispatcher 會使用 `NotifyIdle` 方法登錄一個回呼函式。 此方法會接收要釋出之 <xref:System.ServiceModel.InstanceContext> 的參考。 因此，範例程式碼可以查詢 `ICustomLease` 型別擴充，然後在擴充的狀態下檢查 `ICustomLease.IsIdle` 屬性。  
  
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
  
 在 `ICustomLease.IsIdle` 屬性進行檢查之前，必須設定回呼屬性，因為這在 `CustomLeaseExtension` 通知 Dispatcher 它變成閒置時相當重要。 如果 `ICustomLease.IsIdle` 傳回 `true`，`isIdle` 私用成員只會在 `CustomLifetimeLease` 中設定為 `true`，並呼叫回呼方法。 由於程式碼保留鎖定，因此其他執行緒無法變更此私用成員的值。 此外，在 Dispatcher 下次檢查 `ISharedSessionLifetime.IsIdle` 時，它會傳回 `true`，然後讓 Dispatcher 釋出執行個體。  
  
 既然自訂延伸模組的基礎已完成，現在必須將其連結至服務模型。 為將 `CustomLeaseExtension` 實作連結到 <xref:System.ServiceModel.InstanceContext>，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會提供 <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> 介面來執行 <xref:System.ServiceModel.InstanceContext> 的啟動載入。 在此範例中，`CustomLeaseInitializer` 類別會實作此介面，並將 `CustomLeaseExtension` 的執行個體從唯一的方法初始化加入至 <xref:System.ServiceModel.InstanceContext.Extensions%2A> 集合。 初始化 <xref:System.ServiceModel.InstanceContext> 時，Dispatcher 會呼叫這個方法。  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 最後`System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime`和<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>實作是最多使用服務模型塊狀<xref:System.ServiceModel.Description.IServiceBehavior>實作。 此實作放在 `CustomLeaseTimeAttribute` 類別中，而且它也衍生自 `Attribute` 基底類別，以便當做屬性公開此行為。 在 `IServiceBehavior.ApplyBehavior` 方法中，<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> 和 `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` 實作的執行個體會分別加入至 `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` 的 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> 和 <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> 集合中。  
  
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
  
 您可以使用 `CustomLeaseTime` 屬性加上註解，以便將此行為加入至範例服務類別。  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a>另請參閱
