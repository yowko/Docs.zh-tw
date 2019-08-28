---
title: 自訂安全中繼資料端點
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 072d2551acaae87904bb12c5e8edafa788674322
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045129"
---
# <a name="custom-secure-metadata-endpoint"></a>自訂安全中繼資料端點
這個範例會示範如何使用使用其中一個非中繼資料交換系結的安全中繼資料端點來執行服務, 以及如何設定[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)或用戶端, 以從這類的取得中繼資料中繼資料端點。 有兩個系統提供的繫結可用來公開中繼資料端點：mexHttpBinding 和 mexHttpsBinding。 mexHttpBinding 可用來以不安全的方式，透過 HTTP 公開中繼資料端點。 mexHttpsBinding 可用來以安全的方式，透過 HTTPS 公開中繼資料端點。 此範例說明如何使用 <xref:System.ServiceModel.WSHttpBinding> 公開安全的中繼資料端點。 當您要變更繫結上的安全性設定時，您會想要這麼做，但是您不想使用 HTTPS。 如果使用 mexHttpsBinding，您的中繼資料端點將是安全的，但是沒有方法可以修改繫結設定。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
## <a name="service"></a>服務  
 這個範例中的服務有兩個端點。 應用程式端點可用於 `ICalculator` 上的 `WSHttpBinding` 合約 (已啟用 `ReliableSession`)，並可用於使用憑證的 `Message` 安全性。 中繼資料端點也會使用 `WSHttpBinding`，它具有相同的安全性設定，但沒有 `ReliableSession`。 此處為相關的組態：  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 在許多其他範例中，中繼資料端點會使用不安全的預設 `mexHttpBinding`。 在此處會使用 `WSHttpBinding` 搭配 `Message` 安全性來確認中繼資料的安全。 為了讓中繼資料用戶端擷取此中繼資料，必須以相符的繫結來進行設定。 這個範例會示範兩個這類的用戶端。  
  
 第一個用戶端使用 Svcutil.exe 來擷取中繼資料，並在設計階段時產生用戶端程式碼和組態。 由於服務會對中繼資料使用非預設繫結，您就必須明確地設定 Svcutil.exe 工具，讓它可使用該繫結從服務中取得中繼資料。  
  
 第二個用戶端會使用 `MetadataResolver` 以動態擷取已知合約的中繼資料，然後在動態產生的用戶端上叫用作業。  
  
## <a name="svcutil-client"></a>Svcutil 用戶端  
 使用預設繫結裝載 `IMetadataExchange` 端點時，可以使用該端點的位址來執行 Svcutil.exe：  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 而這樣做確實有作用。 但在此範例中，伺服器會使用非預設端點來裝載中繼資料。 因此，必須指示 Svcutil.exe 使用正確的繫結。 可以使用 Svcutil.exe.config 檔做到這點。  
  
 Svcutil.exe.config 檔看起來就像一般的用戶端組態檔。 唯一不尋常的方面為用戶端端點名稱和合約：  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 端點名稱必須是在此裝載中繼資料之位址配置的名稱，而端點合約必須為 `IMetadataExchange`。 因此，使用命令列以下列方式執行 Svcutil.exe 時：  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 就會尋找名稱為 "http" 的端點和 `IMetadataExchange` 合約，以設定中繼資料端點通訊交換的繫結和行為。 範例中的其他 Svcutil.exe.config 檔會指定繫結組態和行為認證，以比對中繼資料端點的伺服器組態。  
  
 為了讓 Svcutil.exe 挑選 Svcutil.exe.config 中的組態，Svcutil.exe 的所在目錄必須和組態檔的目錄一樣。 因此，您必須將 Svcutil.exe 從其安裝位置複製至包含 Svcutil.exe.config 檔的目錄。 然後從該目錄執行下列命令：  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 前置的「。\\「確定會執行此目錄中的 Svcutil 複本 (具有對應的 Svcutil 的副本)。  
  
## <a name="metadataresolver-client"></a>MetadataResolver 用戶端  
 如果用戶端知道合約以及如何在設計階段與中繼資料互動，用戶端就可以使用 `MetadataResolver`，動態找出繫結和應用程式端點的位址。 這個範例用戶端會示範如何藉由建立和設定 `MetadataResolver`，進而設定 `MetadataExchangeClient` 所使用的繫結和認證。  
  
 您可以在 `MetadataExchangeClient` 上，以命令方式指定出現在 Svcutil.exe.config 中的相同繫結和憑證資訊。  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 設定 `mexClient` 時，可以列舉感興趣的合約，並使用 `MetadataResolver` 來擷取具有這些合約的端點清單：  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 最後，使用來自這些端點的資訊來初始化 `ChannelFactory` 的繫結和位址，您可透過此繫結和位址建立通道以與應用程式端點進行通訊。  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 如果您正在使用 `MetadataResolver`，而且您必須對中繼資料交換通訊指定自訂繫結或行為，則此範例的重點在於示範使用 `MetadataExchangeClient` 來指定這些自訂設定。  
  
#### <a name="to-set-up-and-build-the-sample"></a>若要設定和建置範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建立方案, 請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a>若要在同一部機器上執行範例  
  
1. 從範例安裝資料夾執行 Setup.bat。 這會安裝執行範例所需的所有憑證。 請注意, 安裝程式會使用 FindPrivateKey, 此工具是從[Windows Communication Foundation 範例的一次性安裝程式執行](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)setupCertTool 所安裝。  
  
2. 從 \MetadataResolverClient\bin 或 \SvcutilClient\bin 執行用戶端應用程式。 用戶端活動會顯示在用戶端主控台應用程式上。  
  
3. 如果用戶端和服務無法通訊, 請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
4. 當您完成範例時，請執行 Cleanup.bat 以移除憑證。 其他安全性範例使用相同的憑證。  
  
#### <a name="to-run-the-sample-across-machines"></a>若要跨機器執行範例  
  
1. 在伺服器上執行 `setup.bat service`。 `setup.bat` 使用引數執行時,會建立具有電腦完整功能變數名稱的服務憑證,並將服務憑證匯出至名`service`為 .cer 的檔案。  
  
2. 在伺服器上編輯 Web.config，以反映新的憑證名稱。 也就是, 將`findValue` [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)元素中的屬性變更為電腦的完整功能變數名稱。  
  
3. 從服務目錄中將 Service.cer 檔案複製至用戶端機器上的用戶端目錄。  
  
4. 在用戶端上執行 `setup.bat client`。 `setup.bat` 使用引數執行會建立名為Client.com的用戶端憑證,並將用戶端憑證匯出至名為`client` client .cer 的檔案。  
  
5. 在用戶端機器上之 `MetadataResolverClient` 的 App.config 檔案中，變更 MEX 端點的位址值以符合服務的新位址。 您可以藉由使用伺服器的完整網域名稱取代 localhost，完成這個動作。 也請將 metadataResolverClient.cs 檔案中的其他 "localhost" 變更為新的服務憑證名稱 (伺服器的完整網域名稱)。 對 SvcutilClient 專案的 App.config 執行相同的動作。  
  
6. 從用戶端目錄將 Client.cer 檔案複製到伺服器上的服務目錄中。  
  
7. 在用戶端上執行 `ImportServiceCert.bat`。 這樣會將服務憑證從 Service.cer 檔案匯入至 CurrentUser - TrustedPeople 存放區中。  
  
8. 在伺服器上執行 `ImportClientCert.bat`，這樣會從 Client.cer 檔案中將用戶端憑證匯入至 LocalMachine - TrustedPeople 存放區中。  
  
9. 在服務機器的 Visual Studio 中建置服務專案，並在 Web 瀏覽器中選取說明頁以驗證是否是在執行。  
  
10. 在用戶端機器上，從 VS 執行 MetadataResolverClient 或 SvcutilClient。  
  
    1. 如果用戶端和服務無法通訊, 請參閱[WCF 範例的疑難排解秘訣](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))。  
  
#### <a name="to-clean-up-after-the-sample"></a>若要在使用範例之後進行清除  
  
- 當您完成執行範例後，請執行範例資料夾中的 Cleanup.bat。  
  
    > [!NOTE]
    > 跨機器執行此範例時，這個指令碼不會移除用戶端上的服務憑證。 如果您已在電腦上執行使用憑證的 Windows Communication Foundation (WCF) 範例, 請務必清除已安裝在 CurrentUser-TrustedPeople 存放區中的服務憑證。 若要這麼做，請使用下列命令：`certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`。 例如：`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
