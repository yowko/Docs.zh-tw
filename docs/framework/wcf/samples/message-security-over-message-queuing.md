---
title: "訊息佇列上的訊息安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
caps.latest.revision: 22
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 22
---
# 訊息佇列上的訊息安全性
這個範例示範如何實作應用程式，該應用程式會針對用戶端使用具有 X.509v3 憑證驗證的 WS\-Security，並透過 MSMQ 使用伺服器的 X.509v3 憑證來要求伺服器驗證。有時候，為了確保 MSMQ 存放區中的訊息持續加密，並且讓應用程式可以執行其本身的訊息驗證，使用訊息安全性所產生的效果更為理想。  
  
 這個範例是以[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)範例為基礎。訊息會經過加密和簽署。  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  如果服務優先執行，它就會檢查以確定佇列存在。如果佇列不存在，服務將建立一個佇列。您可以先執行服務來建立佇列，也可以透過 MSMQ 佇列管理員建立佇列。請依照下列步驟，在 Windows 2008 中建立佇列。  
  
    1.  在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟伺服器管理員。  
  
    2.  展開 \[**功能**\] 索引標籤。  
  
    3.  以滑鼠右鍵按一下 \[**私用訊息佇列**\]，然後依序選取 \[**新增**\] 和 \[**私用佇列**\]。  
  
    4.  核取 \[**可交易**\] 方塊。  
  
    5.  輸入 `ServiceModelSamplesTransacted` 做為新佇列的名稱。  
  
3.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
### 若要在同一部電腦上執行範例  
  
1.  確認路徑中包含 Makecert.exe 和 FindPrivateKey.exe 所在的資料夾。  
  
2.  從範例安裝資料夾執行 Setup.bat。這會安裝執行範例所需的所有憑證。  
  
    > [!NOTE]
    >  當您完成範例時，請務必執行 Cleanup.bat 以移除憑證。其他安全性範例使用相同的憑證。  
  
3.  從 \\service\\bin 啟動 Service.exe。  
  
4.  從 \\client\\bin 啟動 Client.exe。用戶端活動會顯示在用戶端主控台應用程式上。  
  
5.  如果用戶端和服務無法通訊，請參閱[Troubleshooting Tips](http://msdn.microsoft.com/zh-tw/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
### 若要跨電腦執行範例  
  
1.  將 Setup.bat、Cleanup.bat 和 ImportClientCert.bat 檔案複製到服務電腦。  
  
2.  在用戶端電腦上為用戶端二進位碼檔案建立一個目錄。  
  
3.  將用戶端程式檔複製到用戶端電腦上的用戶端目錄。同時，將 Setup.bat、Cleanup.bat 和 ImportServiceCert.bat 檔案複製到用戶端。  
  
4.  在伺服器上執行 `setup.bat service`。使用 `service` 引數執行 `setup.bat`  就會建立具有電腦完整網域名稱的服務憑證，並且將服務憑證匯出為名為 Service.cer 的檔案。  
  
5.  編輯服務的 Service.exe.config 以反映新的憑證名稱 \(在 [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)的 `findValue` 屬性中\)，這個名稱與電腦的完整網域名稱相同。  
  
6.  從服務目錄中將 Service.cer 檔案複製至用戶端電腦上的用戶端目錄。  
  
7.  在用戶端上執行 `setup.bat client`。使用 `client` 引數執行 `setup.bat` 就會建立名為 client.com 的用戶端憑證，並且會將用戶端憑證匯出為名為 Client.cer 的檔案。  
  
8.  在用戶端電腦上的 Client.exe.config 檔案中，變更端點的位址值以符合服務的新位址。若要這麼做，請使用伺服器的完整網域名稱取代 localhost。您也必須變更服務的憑證名稱，讓它和服務電腦的完整網域名稱相同 \(在 `clientCredentials` 下 `defaultCertificate` 項目的 `findValue` 屬性中 `serviceCertificate`\)。  
  
9. 從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。  
  
10. 在用戶端上執行 `ImportServiceCert.bat`。這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser \- TrustedPeople 存放區中。  
  
11. 在伺服器上執行 `ImportClientCert.bat`，這樣會從 Client.cer 檔案中將用戶端憑證匯入至 LocalMachine \- TrustedPeople 存放區中。  
  
12. 在服務電腦上，從命令提示字元啟動 Service.exe。  
  
13. 在用戶端電腦上，從命令提示字元啟動 Client.exe。如果用戶端和服務無法通訊，請參閱[Troubleshooting Tips](http://msdn.microsoft.com/zh-tw/8787c877-5e96-42da-8214-fa737a38f10b)。  
  
### 若要在使用範例之後進行清除  
  
-   當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
    > [!NOTE]
    >  跨電腦執行此範例時，這個指令碼不會移除用戶端上的服務憑證。如果您已執行跨電腦使用憑證的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 範例，請確定清除安裝在 CurrentUser \- TrustedPeople 存放區中的服務憑證。若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`，例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。  
  
## 需求  
 這個範例需要安裝並執行 MSMQ。  
  
## 示範  
 用戶端會使用服務的公開金鑰對訊息加密，再使用它自己的憑證來簽署訊息。從佇列讀取訊息的服務會使用其受信任人存放區中的憑證來驗證用戶端憑證，然後解密訊息，並將它分派至服務作業。  
  
 由於 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 訊息會在 MSMQ 訊息的本文中當做承載傳送，所以 MSMQ 存放區中的本文仍然是經過加密的。這可以保護訊息，避免不該發生的洩漏風險。請注意，MSMQ 本身並不知道它所攜帶的訊息是否有加密。  
  
 此範例示範如何將訊息層級上的相互驗證與 MSMQ 搭配使用。憑證是透過超出範圍之外的方式進行交換。對佇列應用程式而言，一定都會採用這種方式，因為服務和用戶端並不需要同時啟動和執行。  
  
## 描述  
 本範例用戶端和服務程式碼與[交易 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)範例相同，但還是有一個差異。作業合約附有保護層級的註解，這表示訊息必須經過簽署並加密。  
  
```  
// Define a service contract.   
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
    void SubmitPurchaseOrder(PurchaseOrder po);  
}  
```  
  
 為了確定是使用識別服務和用戶端所需的權杖來保護訊息安全，App.config 會包含認證資訊。  
  
 用戶端組態會指定服務憑證來驗證服務。它使用 LocalMachine 存放區做為可信賴之服務有效性的受信任存放區。它也會指定用戶端憑證，其中附有用戶端之服務驗證的訊息。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"   
                binding="netMsmqBinding"   
                bindingConfiguration="messageSecurityBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"  
                behaviorConfiguration="ClientCertificateBehavior" />  
    </client>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate"/>  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
</configuration>  
```  
  
 請注意，安全性模式是設定為 Message，而 ClientCredentialType 則設定為 Certificate。  
  
 服務組態會包含服務行為，以指定用戶端驗證服務時所使用的服務認證。在 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)的 `findValue` 屬性中會指定伺服器憑證主體名稱。  
  
```  
  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"  
          behaviorConfiguration="PurchaseOrderServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"  
                  binding="netMsmqBinding"  
                  bindingConfiguration="messageSecurityBinding"  
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
        <netMsmqBinding>  
            <binding name="messageSecurityBinding">  
                <security mode="Message">  
                    <message clientCredentialType="Certificate" />  
                </security>  
            </binding>  
        </netMsmqBinding>  
    </bindings>  
  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="PurchaseOrderServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!--   
               The serviceCredentials behavior allows one to define a service certificate.  
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
               This configuration references the "localhost" certificate installed during the setup instructions.  
          -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it is trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
  
```  
  
 這個範例示範如何使用組態控制驗證以及如何從安全性內容取得呼叫者身分識別，如下列範例程式碼所示：  
  
```  
    // Service class which implements the service contract.  
    // Added code to write output to the console window.  
    public class OrderProcessorService : IOrderProcessor  
    {  
        private string GetCallerIdentity()  
        {  
            // The client certificate is not mapped to a Windows identity by default.  
            // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
            // in the certificate that the client used to authenticate itself to the service.  
            return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void SubmitPurchaseOrder(PurchaseOrder po)  
        {  
            Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());  
            Orders.Add(po);  
            Console.WriteLine("Processing {0} ", po);  
        }  
  //…  
}  
```  
  
 執行時，服務程式碼會顯示用戶端識別。下列是服務程式碼的範例輸出：  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C  
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
```  
  
## 註解  
  
-   建立用戶端憑證。  
  
     批次檔中的下列程式行會建立用戶端憑證。在所建立之憑證主體的名稱中，會使用指定的用戶端名稱。憑證會儲存在位於 `CurrentUser` 存放區的 `My` 存放區中。  
  
    ```  
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
  
    ```  
  
-   將用戶端憑證安裝至伺服器的受信任憑證存放區中。  
  
     批次檔中的下列程式行會將用戶端憑證複製到伺服器的 TrustedPeople 存放區，讓伺服器可以做出相關的信任或不信任決定。若要讓安裝在 TrustedPeople 存放區中的憑證能受到 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務信任，用戶端憑證驗證模式必須設為 `PeerOrChainTrust` 或 `PeerTrust` 值。請參閱先前的服務組態範例，以了解如何使用組態檔完成這個工作。  
  
    ```  
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
  
    ```  
  
-   建立伺服器憑證。  
  
     下列 Setup.bat 批次檔中的程式行會建立要使用的伺服器憑證：  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     %SERVER\_NAME% 變數會指定伺服器名稱。憑證是儲存在 LocalMachine 存放區中。如果使用 service 的引數執行安裝批次檔 \(例如，`setup.bat service`\)，%SERVER\_NAME% 就會包含電腦的完整網域名稱。否則，預設為 localhost  
  
-   將伺服器憑證安裝到用戶端的受信任憑證存放區中。  
  
     下列程式行會將伺服器憑證複製到用戶端受信任人的存放區中。這是必要步驟，因為用戶端系統並未隱含信任 Makecert.exe 產生的憑證。如果您已經有一個以用戶端信任的根憑證 \(例如 Microsoft 所發行的憑證\) 為基礎的憑證，就不需要這個將伺服器憑證填入用戶端憑證的步驟。  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
    > [!NOTE]
    >  如果您使用的是非美式英文版的 Microsoft Windows，就必須編輯 Setup.bat 檔案，並以適用您所在地區的對等帳戶來取代 "NT AUTHORITY\\NETWORK SERVICE" 帳戶名稱。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`  
  
## 請參閱