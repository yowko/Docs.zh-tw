---
title: 執行個體初始化
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 651029783f4632fc0b404bea8df8bd3790622bfd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388257"
---
# <a name="instancing-initialization"></a>執行個體初始化
這個範例會延續[Pooling](../../../../docs/framework/wcf/samples/pooling.md)範例藉由定義介面， `IObjectControl`，其中藉由啟動和停用自訂物件的初始化。 用戶端會叫用將物件傳回集區的方法，以及不將物件傳回集區的方法。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
## <a name="extensibility-points"></a>擴充點  
 建立 Windows Communication Foundation (WCF) 擴充功能的第一個步驟是決定要使用的擴充性點。 在 WCF 中，詞彙*EndpointDispatcher*指負責將傳入訊息轉換成使用者的服務上的方法引動過程，以及將來自該方法的傳回值轉換為傳出訊息的執行階段元件. WCF 服務會建立每個端點 EndpointDispatcher。  
  
 EndpointDispatcher 會使用 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 類別，為端點範圍 (針對服務已接收或傳送的所有訊息) 提供擴充性。 這個類別可讓您自訂各種屬性，以控制 EndpointDispatcher 的行為。 此範例著重於 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 屬性，這個屬性會指向提供服務類別之執行個體的物件。  
  
## <a name="iinstanceprovider"></a>IInstanceProvider  
 在 WCF 中，EndpointDispatcher 會建立服務類別的執行個體所使用的執行個體提供者可實作<xref:System.ServiceModel.Dispatcher.IInstanceProvider>介面。 這個介面只有兩個方法：  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>：訊息送達時，發送器會呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法來建立服務類別的執行個體，以便處理訊息。 呼叫此方法的頻率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性決定。 例如，如果 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性設定為 <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>，則會建立服務類別的執行個體來處理送達的每個訊息，這表示只要訊息一送達就會呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>。  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>：當服務執行個體完成處理訊息時，EndpointDispatcher 就會呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。 如同 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法，呼叫此方法的頻率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性決定。  
  
## <a name="the-object-pool"></a>物件集區  
 `ObjectPoolInstanceProvider` 類別包含物件集區 (Object Pool) 的實作。 這個類別會實作 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 介面，以便與服務模型層互動。 當 EndpointDispatcher 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> 方法而不是建立新執行個體時，自訂實作會在記憶體中集區尋找現有的物件。 如果找到了，就會將物件傳回。 否則，`ObjectPoolInstanceProvider` 會檢查 `ActiveObjectsCount` 屬性 (從集區傳回的物件數目) 是否已達到集區的大小上限。 如果未達到，則會建立新執行個體並傳回至呼叫者，接著 `ActiveObjectsCount` 就會遞增。 否則，物件建立要求會在預先設定的期間內加入佇列。 下列範例程式碼會示範 `GetObjectFromThePool` 實作。  
  
```  
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
  
 自訂 `ReleaseInstance` 實作會將釋放的執行個體新增回集區，並遞減 `ActiveObjectsCount` 值。 EndpointDispatcher 可以從不同的執行緒來呼叫這些方法，因此便需要在 `ObjectPoolInstanceProvider` 類別中同步存取類別層級的成員。  
  
```  
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
  
 `ReleaseInstance`方法會提供*清除初始化*功能。 集區通常會在集區的存留期中保留最低限度數目的物件。 不過，可能有些時段會出現過度使用的情形，因而需要在集區中建立其他物件以達到組態中指定的上限。 最後當集區的活動變少時，這些多餘的物件可能會變成額外的負荷。 因此，當 `activeObjectsCount` 成為零時，閒置計時器就會啟動，以觸發並執行清除循環。  
  
```  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 您可以使用下列行為來連結 ServiceModel 層的延伸項目：  
  
-   服務行為：允許自訂整個服務執行階段。  
  
-   端點行為：允許自訂特定服務端點，包括 EndpointDispatcher。  
  
-   合約行為：允許分別在用戶端或服務上自訂 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 或 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別。  
  
-   作業行為：允許分別在用戶端或服務上自訂 <xref:System.ServiceModel.Dispatcher.ClientOperation> 或 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別。  
  
 若要做為物件共用延伸項目的用途，可以建立端點行為或服務行為。 這個範例採用服務行為，服務行為可以將物件共用能力套用至服務的每個端點。 服務行為是藉由實作 <xref:System.ServiceModel.Description.IServiceBehavior> 介面來建立。 有一些方法可以讓 ServiceModel 察覺自訂行為：  
  
-   使用自訂屬性。  
  
-   以命令方式將它加入至服務描述的行為集合。  
  
-   延伸組態檔。  
  
 這個範例會使用自訂屬性。 建構 <xref:System.ServiceModel.ServiceHost> 時，會檢查服務型別定義中使用的屬性，並將可用的行為加入至服務描述的行為集合。  
  
 <xref:System.ServiceModel.Description.IServiceBehavior>介面有三個方法： <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> `,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> `,`和<xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>。 WCF 會呼叫這些方法時<xref:System.ServiceModel.ServiceHost>正在初始化。 首先會呼叫 <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType>，這個方法允許檢查服務有無不一致之處。 接著會呼叫 <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType>，這個方法只有在非常進階的狀況中才需要使用。 最後會呼叫 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>，這個方法負責設定執行階段。 下列參數會傳遞至 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>：  
  
-   `Description`：這個參數提供整個服務的服務描述， 可以用來檢查有關服務端點、合約、繫結以及與服務相關聯之其他資料的描述資料。  
  
-   `ServiceHostBase`：這個參數提供目前正在初始化的 <xref:System.ServiceModel.ServiceHostBase>。  
  
 在自訂 <xref:System.ServiceModel.Description.IServiceBehavior> 實作中，會為 `ObjectPoolInstanceProvider` 產生新的執行個體，並將新執行個體指派至附加到 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 之每個 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 中的 <xref:System.ServiceModel.ServiceHostBase> 屬性。  
  
```  
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
  
 除了 <xref:System.ServiceModel.Description.IServiceBehavior> 實作之外，`ObjectPoolingAttribute` 類別還有數個可以使用屬性引數來自訂物件集區的成員。 這些成員包括 `MaxSize`、`MinSize`、`Enabled` 和 `CreationTimeout`，可用來比對 .NET Enterprise Services 提供的物件共用功能集。  
  
 將物件共用行為現在可以新增至 WCF 服務使用新建立的自訂服務實作加上附註`ObjectPooling`屬性。  
  
```  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a>攔截啟動與停用  
 物件共用的主要目標是，最佳化存留較短且建立和初始化時較會耗費資源的物件。 因此，好好利用的話，可以大幅提高應用程式的效能。 由於物件是從集區傳回，因此只能呼叫建構函式一次。 不過，有些應用程式會需要某些層級的控制權，以便初始化及清除單一內容期間使用的資源。 例如，用於一組計算的物件可以在處理下個計算之前，先重設私用欄位。 Enterprise Services 藉由讓物件開發人員覆寫來自 `Activate` 基底類別的 `Deactivate` 和 <xref:System.EnterpriseServices.ServicedComponent> 方法，啟用了這種特定內容的初始化。  
  
 物件集區會在從集區傳回物件之前，呼叫 `Activate` 方法。 當物件傳回集區時，會呼叫 `Deactivate`。 <xref:System.EnterpriseServices.ServicedComponent> 基底類別也有名為 `boolean` 的 `CanBePooled` 屬性，可以用來通知集區是否能進一步共用物件。  
  
 為了模擬此功能，範例會宣告具有上述成員的公用介面 (`IObjectControl`)。 接著，服務類別會實作這個介面，以提供內容特定的初始化。 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 實作必須經過修改，才能符合這些需求。 現在，每當您取得的物件呼叫`GetInstance`方法，您必須檢查物件是否實作`IObjectControl.`若是如此，您必須呼叫`Activate`方法適當地。  
  
```  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 將物件傳回集區時，必須先檢查 `CanBePooled` 屬性，才能將物件新增回集區。  
  
```  
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
  
 由於服務開發人員可以決定是否可以共用物件，在特定時間內，集區中的物件計數可能會低於大小下限。 因此，您必須檢查物件計數是否曾經低於最低層級，並且在清除程序中執行必要的初始化。  
  
```  
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
  
 當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。 在每個主控台視窗中按下 Enter 鍵，即可關閉服務與用戶端。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
  
## <a name="see-also"></a>另請參閱
