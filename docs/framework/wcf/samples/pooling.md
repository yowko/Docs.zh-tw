---
title: Pooling
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 91fdb34a82446aab1528835132efd31e2858191c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832433"
---
# <a name="pooling"></a>Pooling
此範例示範如何擴充 Windows Communication Foundation (WCF) 支援物件共用。 此範例會示範如何建立語法上及語意上與 Enterprise Services 的 `ObjectPoolingAttribute` 屬性功能相似的屬性。 物件共用可以大幅提升應用程式的效能。 不過，如果不當使用，可能會產生反效果。 物件共用有助於避免重複建立常用物件的煩瑣工作，這些物件往往需要大量的初始設定。 不過，如果呼叫共用物件上的方法要花費相當長的時間才能完成，而一旦到達集區的大小上限，物件共用就得將多出的要求加入佇列中。 它可能因此無法受理某個建立物件的要求，而擲回逾時例外狀況。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 建立 WCF 延伸模組的第一個步驟是決定要使用的擴充性點。  
  
 在 WCF 中的字詞*發送器*指的執行階段元件負責將傳入訊息轉換成使用者的服務上的方法引動過程，以及將來自該方法的傳回值轉換為傳出訊息。 WCF 服務會建立每個端點發送器。 如果該用戶端相關聯的合約是雙工合約，WCF 用戶端必須使用發送器。  
  
 通道和端點發送器可以公開各種控制發送器行為的屬性，提供適用於整個通道及合約範圍的擴充性。 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> 屬性同時可讓您檢查、修改或自訂分派程序。 此範例著重於 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 屬性，這個屬性會指向提供服務類別之執行個體的物件。  
  
## <a name="the-iinstanceprovider"></a>IInstanceProvider  
 在 WCF 中，發送器會建立使用服務類別的執行個體<xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>，它會實作<xref:System.ServiceModel.Dispatcher.IInstanceProvider>介面。 這個介面有三個方法：  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>：當訊息抵達發送器會呼叫<xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>方法用來建立服務類別，來處理訊息的執行個體。 呼叫此方法的頻率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性決定。 例如，如果 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性設定為 <xref:System.ServiceModel.InstanceContextMode.PerCall>，則會建立服務類別的執行個體來處理送達的每個訊息，所以只要訊息一送達就會呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>。  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>：這等同於前一個的方法，但這在沒有 Message 引數時叫用。  
  
-   <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>：當服務執行個體的存留期已過，發送器會呼叫<xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>方法。 就和 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> 方法一樣，呼叫這個方法的頻率是由 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性決定。  
  
## <a name="the-object-pool"></a>物件集區  
 自訂的 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 實作會為服務提供必要的物件共用語意 (Semantics)。 因此，這個範例具有 `ObjectPoolingInstanceProvider` 型別，可以提供進行共用所需之 <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 的自訂實作。 當 `Dispatcher` 呼叫 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> 方法，而不是建立新執行個體時，自訂實作會在記憶體中集區尋找現有物件。 如果找到了，就會將物件傳回。 否則，會建立新的物件。 下列範例程式碼會示範 `GetInstance` 實作。  
  
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
  
 自訂 `ReleaseInstance` 實作會將釋放的執行個體新增回集區，並遞減 `ActiveObjectsCount` 值。 `Dispatcher` 可以從不同執行緒中呼叫這些方法，因此需要可在 `ObjectPoolingInstanceProvider` 類別中同步存取類別層級成員的權限。  
  
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
  
 `ReleaseInstance`方法提供 「 清除初始設定 」 功能。 集區通常會在集區的存留期中保留最低限度數目的物件。 不過，可能有些時段會出現過度使用的情形，因而需要在集區中建立其他物件以達到組態中指定的上限。 最後當集區的活動變少時，這些多餘的物件可能會變成額外的負荷。 因此，當 `activeObjectsCount` 成為零時，閒置計時器就會啟動，以觸發並執行清除循環。  
  
## <a name="adding-the-behavior"></a>新增行為  
 您可以使用下列行為來連結發送器層延伸：  
  
-   服務行為。 這些行為允許自訂整個服務執行階段。  
  
-   端點行為。 這些行為允許自訂服務端點，也就是通道和端點發送器。  
  
-   合約行為。 這些行為允許分別在用戶端和服務上自訂 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 和 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別。  
  
 若要做為物件共用延伸之用，您必須建立服務行為。 服務行為是藉由實作 <xref:System.ServiceModel.Description.IServiceBehavior> 介面來建立。 有一些方法可以讓服務模型察覺自訂行為：  
  
-   使用自訂屬性。  
  
-   以命令方式將它加入至服務描述的行為集合。  
  
-   延伸組態檔。  
  
 這個範例會使用自訂屬性。 建構 <xref:System.ServiceModel.ServiceHost> 時，它會檢查服務型別定義中使用的屬性，然後將可用的行為加入至服務描述的行為集合。  
  
 <xref:System.ServiceModel.Description.IServiceBehavior> 介面中有三個方法：<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>、<xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> 和 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>。 <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> 方法是用來確保行為可以套用至服務。 在這個範例中，此實作會確認服務不是透過 <xref:System.ServiceModel.InstanceContextMode.Single> 所設定。 <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> 方法是用來設定服務的繫結。 這在本案例中不是必要項。 <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> 是用來設定服務的發送器。 WCF 會呼叫此方法時<xref:System.ServiceModel.ServiceHost>正在初始化。 傳遞至這個方法中的參數如下：  
  
-   `Description`：此引數會提供整個服務的服務描述。 這可以用來檢查有關服務之端點、合約、繫結程序及其他資料的描述資料。  
  
-   `ServiceHostBase`：這個引數提供<xref:System.ServiceModel.ServiceHostBase>，目前正在初始化。  
  
 在自訂 <xref:System.ServiceModel.Description.IServiceBehavior> 實作中，會產生 `ObjectPoolingInstanceProvider` 的新執行個體，然後將它指派給 ServiceHostBase 中每個 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 的 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 屬性。  
  
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
  
 除了 <xref:System.ServiceModel.Description.IServiceBehavior> 實作之外，<xref:System.EnterpriseServices.ObjectPoolingAttribute> 類別還有數個可以使用屬性引數來自訂物件集區的成員。 這些成員包括 <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>、<xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A> 和 <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>，可以用來配合 .NET Enterprise Services 提供的物件共用功能集。  
  
 將物件共用行為現在可以新增至 WCF 服務使用新建立的自訂服務實作加上附註`ObjectPooling`屬性。  
  
```  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a>執行範例  
 此範例會示範可在特定案例中藉由使用物件共用取得的效能優勢。  
  
 服務應用程式會實作兩個服務：`WorkService` 和 `ObjectPooledWorkService`。 這兩個服務會共用相同的實作；它們都必須進行昂貴的初始設定，然後再公開相對低廉的 `DoWork()` 方法。 唯一的差異在於 `ObjectPooledWorkService` 設定了物件共用：  
  
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
  
 當您執行用戶端時，它會計算呼叫 `WorkService` 5 次的時間， 接著計算呼叫 `ObjectPooledWorkService` 5 次的時間， 然後顯示時間的差距：  
  
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
>  第一次執行用戶端時，兩個服務似乎都花費了相同的時間。 如果您重新執行範例，就可以看出 `ObjectPooledWorkService` 的回傳速度快多了，這是因為此物件的執行個體已經存在於集區中。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!NOTE]
>  如果您使用 Svcutil.exe 重新產生這個範例的組態，請務必修改用戶端組態中的端點名稱，以符合用戶端程式碼。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
  
