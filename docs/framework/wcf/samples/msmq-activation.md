---
title: MSMQ 啟用
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: a03f5783e732c4a0f3f13cf6abd7ec4803c07c8f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559578"
---
# <a name="msmq-activation"></a>MSMQ 啟用
這個範例示範如何在 Windows Process Activation Service (WAS) 中裝載可從訊息佇列讀取的應用程式。 這個範例會使用`netMsmqBinding`且根據[雙向通訊](../../../../docs/framework/wcf/samples/two-way-communication.md)範例。 本例中的服務是 Web 裝載的應用程式，而用戶端則會自我裝載並輸出至主控台，以便觀察所送出採購單的狀態。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!NOTE]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  \<InstallDrive>:\WF_WCF_Samples  
>   
>  如果此目錄不存在，請移至 Windows Communication Foundation (WCF) 的超連結"https://go.microsoft.com/fwlink/?LinkId=150780"\t"_blank"和 Windows Workflow Foundation (WF) 範例[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]以下載所有 WCF 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  \<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.  
  
 Windows Process Activation Service (WAS) 是 [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上全新的處理序啟用機制，可以為使用非 HTTP 通訊協定的應用程式提供類似 IIS 的功能，而這些功能原先只有 HTTP 應用程式才能使用。 Windows Communication Foundation (WCF) 會使用接聽程式配接器介面進行通訊所支援的 WCF，例如 TCP、 具名管道和 MSMQ 的非 HTTP 通訊協定接收啟用要求。 SMSvcHost.exe 中執行的 Managed Windows 服務會裝載可透過非 HTTP 通訊協定接收要求的功能。  
  
 Net.Msmq 接聽程式配接器服務 (NetMsmqActivator) 會根據佇列中的訊息啟動佇列應用程式。  
  
 用戶端會將採購單從交易範圍內傳送至服務。 服務則在交易中接收訂單，然後加以處理。 服務以訂單的狀態來回呼用戶端。 為了促進雙向通訊，用戶端與服務都會使用佇列將採購單和訂單狀態加入佇列。  
  
 服務合約 `IOrderProcessor` 會定義適合與佇列一起使用的單向服務作業。 服務作業使用回覆端點，將訂單狀態傳送至用戶端。 回覆端點的位址是用來將訂單狀態傳回用戶端的佇列 URI。 訂單處理應用程式會實作這個合約。  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true)]  
    void SubmitPurchaseOrder(PurchaseOrder po,   
                                           string reportOrderStatusTo);  
}  
```  
  
 用戶端會指定要將訂單狀態傳送到其中的回覆合約。 用戶端會實作訂單狀態合約。 服務則使用這個合約產生的用戶端將訂單狀態傳回用戶端。  
  
```csharp  
[ServiceContract]  
public interface IOrderStatus  
{  
    [OperationContract(IsOneWay = true)]  
    void OrderStatus(string poNumber, string status);  
}  
```  
  
 服務作業會處理已送出的採購單。 <xref:System.ServiceModel.OperationBehaviorAttribute> 會套用至服務作業以便在用來從佇列接收訊息的交易中指定自動進行登記，以及在服務作業完成時自動完成交易。 `Orders` 類別會封裝訂單處理功能。 在本例中，這個類別會將採購單新增至字典。 `Orders` 類別中的作業可以使用服務作業所登記的交易。  
  
 服務作業除了處理已送出的採購單外，也會將訂單狀態回覆至用戶端。  
  
```csharp  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
        Console.WriteLine("Sending back order status information");  
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();  
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;  
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));  
        // please note that the same transaction that is used to dequeue purchase order is used  
        // to send back order status  
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
        {  
            client.OrderStatus(po.PONumber, po.Status);  
            scope.Complete();  
        }  
    }  
```  
  
 您可以使用組態檔來指定要使用的用戶端繫結。  
  
 MSMQ 佇列名稱是指定在組態檔的 appSettings 區段中。 服務端點會定義在組態檔的 System.serviceModel 區段中。  
  
> [!NOTE]
>  MSMQ 佇列名稱與端點位址會使用稍微不同的定址慣例。 MSMQ 佇列名稱會使用點 (.) 來代表本機電腦，並在其路徑中使用反斜線分隔符號。 WCF 端點位址會指定 net.msmq： 配置中，使用"localhost"代表本機電腦，並在其路徑中使用正斜線。 若要讀取裝載於遠端電腦的佇列，請將 "." 和 "localhost" 取代成遠端電腦名稱。  
  
 帶有類別名稱的 .svc 檔案會用來裝載 WAS 中的服務程式碼。  
  
 Service.svc 檔案本身含有要建立 `OrderProcessorService` 的指示詞。  
  
```xml  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>  
```  
  
 Service.svc 檔案還包含組件指示詞，可確保載入 System.Transactions.dll。  
  
```xml  
<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>  
```  
  
 用戶端會建立一個交易範圍。 與服務的通訊會在交易範圍內進行，形成不可部分完成的原子單位 (Atomic Unit)，其中的訊息若不是全部成功，就是全部失敗。 呼叫交易範圍上的 `Complete`，即可認可交易。  
  
```csharp  
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))  
{  
    // Open the ServiceHostBase to create listeners and start listening   
    // for order status messages.  
    serviceHost.Open();  
  
    // Create a proxy with given client endpoint configuration  
    OrderProcessorClient client = new OrderProcessorClient();  
  
    // Create the purchase order  
    PurchaseOrder po = new PurchaseOrder();  
    po.CustomerId = "somecustomer.com";  
    po.PONumber = Guid.NewGuid().ToString();  
  
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
    lineItem1.ProductId = "Blue Widget";  
    lineItem1.Quantity = 54;  
    lineItem1.UnitCost = 29.99F;  
  
    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
    lineItem2.ProductId = "Red Widget";  
    lineItem2.Quantity = 890;  
    lineItem2.UnitCost = 45.89F;  
  
    po.orderLineItems = new PurchaseOrderLineItem[2];  
    po.orderLineItems[0] = lineItem1;  
    po.orderLineItems[1] = lineItem2;  
  
    //Create a transaction scope.  
    using (TransactionScope scope = new   
        TransactionScope(TransactionScopeOption.Required))  
    {  
        // Make a queued call to submit the purchase order  
        client.SubmitPurchaseOrder(po,   
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");  
        // Complete the transaction.  
        scope.Complete();  
    }  
  
    //Closing the client gracefully closes the connection and cleans up   
    //resources  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
  
    // Close the ServiceHostBase to shutdown the service.  
    serviceHost.Close();  
    }  
```  
  
 用戶端程式碼會實作 `IOrderStatus` 合約以接收服務的訂單狀態。 在此範例中，它會印出訂單狀態。  
  
```csharp  
[ServiceBehavior]  
public class OrderStatusService : IOrderStatus  
{  
    [OperationBehavior(TransactionAutoComplete = true,   
                        TransactionScopeRequired = true)]  
    public void OrderStatus(string poNumber, string status)  
    {  
        Console.WriteLine("Status of order {0}:{1} ",   
                                         poNumber , status);  
    }  
}  
```  
  
 訂單狀態佇列會建立在 `Main` 方法中。 用戶端組態會包含訂單狀態服務組態來裝載訂單狀態服務，如下列範例組態所示。  
  
```csharp  
<appSettings>  
    <!-- use appSetting to configure MSMQ queue name -->  
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />  
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />  
  </appSettings>  
  
<system.serviceModel>  
  
    <services>  
      <service   
         name="Microsoft.ServiceModel.Samples.OrderStatusService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"  
                  binding="netMsmqBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />  
      </service>  
    </services>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"   
                binding="netMsmqBinding"   
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
    </client>  
  
  </system.serviceModel>  
```  
  
 當您執行範例時，用戶端與服務活動都會顯示在伺服器與用戶端主控台視窗中。 您可以看到伺服器從用戶端接收訊息。 在每一個主控台視窗中按 ENTER 鍵，即可關閉伺服器與用戶端。  
  
 用戶端會顯示伺服器傳送的訂單狀態資訊。  
  
```Output  
Press <ENTER> to terminate client.  
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定已安裝 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]，因為 WAS 啟動時需要它。  
  
2.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。 此外，您必須安裝 WCF 非 HTTP 啟動元件：  
  
    1.  從**開始**功能表上，選擇**控制台**。  
  
    2.  選取 **程式和功能**。  
  
    3.  按一下 **開啟或關閉 Windows 功能**。  
  
    4.  底下**功能摘要**，按一下**新增功能**。  
  
    5.  依序展開**Microsoft.NET Framework 3.0**節點，並檢查**Windows Communication Foundation 非 HTTP 啟動**功能。  
  
3.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
4.  從命令視窗執行 client.exe，以執行用戶端。 這會建立佇列，並將訊息傳送給它。 讓用戶端繼續執行，以便查看服務讀取訊息的結果。  
  
5.  根據預設，MSMQ 啟動服務會以網路服務的身分執行。 因此，用來啟動應用程式的佇列必須讓「網路服務」擁有接收和查看其中訊息的權限。 您可以使用訊息佇列 MMC 來新增此權限：  
  
    1.  從**開始**功能表上，按一下**執行**，然後輸入`Compmgmt.msc`按 ENTER 鍵。  
  
    2.  底下**服務和應用程式**，展開**Message Queuing**。  
  
    3.  按一下 **私用佇列**。  
  
    4.  以滑鼠右鍵按一下佇列 (servicemodelsamples/Service.svc)，然後選擇 **屬性**。  
  
    5.  在 **安全性**索引標籤上，按一下**新增**將查看和接收的網路服務的權限。  
  
6.  設定 Windows Process Activation Service (WAS) 以支援 MSMQ 啟動。  
  
     為了方便起見，下列步驟會以範例目錄中名為 AddMsmqSiteBinding.cmd 的批次檔實作。  
  
    1.  若要支援 net.msmq 啟動，預設的網站必須先繫結至 net.msmq 通訊協定。 使用隨 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 管理工具集安裝的 appcmd.exe 即可完成此操作。 從提高權限的 (系統管理員) 命令提示字元中執行下列命令。  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  這個命令是單行文字。  
  
         此命令會將 net.msmq 網站繫結加入至預設網站。  
  
    2.  雖然網站中的所有應用程式會共用一般 net.msmq 繫結，但是每個應用程式都可以個別啟用 net.msmq 支援。 若要啟用 /servicemodelsamples 應用程式的 net.msmq，請從提高權限的命令提示字元中執行下列命令。  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq  
        ```  
  
        > [!NOTE]
        >  這個命令是單行文字。  
  
         此命令會啟用 /servicemodelsamples 應用程式使用存取 http://localhost/servicemodelsamples和 net.msmq: //localhost/servicemodelsamples。  
  
7.  如果您之前未曾這麼做，請確定 MSMQ 啟動服務已啟用。 從**開始**功能表上，按一下**執行**，然後輸入`Services.msc`。 搜尋的服務清單**Net.Msmq 接聽程式配接器**。 以滑鼠右鍵按一下並選取**屬性**。 設定**啟動類型**要**自動**，按一下 **套用**，按一下 **啟動** 按鈕。 這個步驟只需要在第一次使用 Net.Msmq 接聽程式配接器服務之前執行一次。  
  
8.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。 此外，還要在發送採購單的用戶端上變更程式碼，以便在送出採購單時將電腦名稱反映於佇列的 URI。 請使用下列程式碼：  
  
    ```  
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");  
    ```  
  
9. 移除您為此範例加入的 net.msmq 網站繫結。  
  
     為了方便起見，下列步驟會以範例目錄中名為 RemoveMsmqSiteBinding.cmd 的批次檔實作：  
  
    1.  從提高權限的命令提示字元中執行下列命令，以從啟用的通訊協定清單中移除 net.msmq。  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  這個命令是單行文字。  
  
    2.  從提高權限的命令提示字元中執行下列命令以移除 net.msmq 網站繫結。  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']  
        ```  
  
        > [!NOTE]
        >  這個命令是單行文字。  
  
    > [!WARNING]
    >  執行批次檔會將 DefaultAppPool 重設為使用 .NET Framework 2.0 版執行。  
  
 根據預設，安全性會透過 `netMsmqBinding` 繫結傳輸啟用。 `MsmqAuthenticationMode` 和 `MsmqProtectionLevel` 這兩個屬性會共同決定傳輸安全性的類型。 根據預設，驗證模式會設定為 `Windows`，保護層級則會設定為 `Sign`。 若要 MSMQ 提供驗證和簽署功能，則 MSMQ 必須是網域的一部分。 如果您在不屬於網域的電腦上執行這個範例，就會收到下列錯誤：「使用者的內部訊息佇列憑證不存在」。  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a>若要在加入至工作群組的電腦上執行範例  
  
1.  如果您的電腦不是網域的一部分，請將驗證模式和保護層級設定為 None，以關閉傳輸安全性，如下面的範例組態所示：  
  
    ```xml  
    <bindings>  
        <netMsmqBinding>  
            <binding configurationName="TransactedBinding">  
                <security mode="None"/>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
    ```  
  
2.  請先變更伺服器與用戶端上的組態，再執行範例。  
  
    > [!NOTE]
    >  將 `security mode` 設定為 `None`，相當於將 `MsmqAuthenticationMode`、`MsmqProtectionLevel` 和 `Message` 安全性設定為 `None`。  
  
3.  若要在已加入工作群組的電腦中啟用啟動作業，則啟動服務和背景工作處理序都必須透過特定使用者帳戶 (這兩者的帳戶必須相同) 來執行，而且佇列必須具有特定使用者帳戶的 ACL。  
  
     若要變更背景工作處理序用以執行的身分識別：  
  
    1.  執行 Inetmgr.exe。  
  
    2.  底下**應用程式集區**，以滑鼠右鍵按一下**AppPool** (通常**DefaultAppPool**)，然後選擇 **設定應用程式集區預設值...**.  
  
    3.  變更 Identity 屬性以使用特定的使用者帳戶。  
  
     若要變更啟動服務用以執行的身分識別：  
  
    1.  執行 Services.msc。  
  
    2.  以滑鼠右鍵按一下**Net.MsmqListener 配接器**，然後選擇**屬性**。  
  
4.  變更此帳戶**登入** 索引標籤。  
  
5.  在工作群組中，服務還必須使用不受限制的權杖來執行。 若要這麼做，請在命令視窗中執行下列命令：  
  
    ```  
    sc sidtype netmsmqactivator unrestricted  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 主控與持續性範例](https://go.microsoft.com/fwlink/?LinkId=193961)
