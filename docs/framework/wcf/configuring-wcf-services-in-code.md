---
title: 在程式碼中設定 WCF 服務
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174806"
---
# <a name="configuring-wcf-services-in-code"></a>在程式碼中設定 WCF 服務
Windows 通信基礎 （WCF） 允許開發人員使用設定檔或代碼佈建服務。  當服務需要在部署後進行設定時，組態檔非常有用。 使用組態檔時，IT 專業人員只需更新組態檔，不必重新編譯。 但是組態檔可能會很複雜而難以維護。 由於不支援組態檔偵錯，而且組態項目是以名稱來參考，這使得製作組態檔容易出錯且難度增加。 WCF 還允許您在代碼中佈建服務。 在早期版本的 WCF（4.0 和更早版本）中，在自託管方案中佈建服務很容易，<xref:System.ServiceModel.ServiceHost>該類允許您在調用 ServiceHost.Open 之前配置終結點和行為。 但是在 Web 裝載案例中，您就無法直接存取 <xref:System.ServiceModel.ServiceHost> 類別。 為了設定 Web 裝載服務，您需要建立會建立 `System.ServiceModel.ServiceHostFactory` 的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，並執行任何所需的設定。 從 .NET 4.5 開始，WCF 提供了一種更簡單的方法來在代碼中配置自託管服務和 Web 託管服務。  
  
## <a name="the-configure-method"></a>Configure 方法  
 只需定義名為 `Configure` 的公用靜態方法，並在您的服務實作類別中包含下列簽章：  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Configure 方法接受可讓開發人員加入端點和行為的 <xref:System.ServiceModel.ServiceConfiguration> 執行個體。 在打開服務主機之前，WCF 會調用此方法。 一旦定義之後，將會忽略 app.config 或 web.config 檔案中指定的任何服務組態設定。  
  
 下列程式碼片段說明如何定義 `Configure` 方法，以及加入服務端點、端點行為和服務行為：  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 若要為服務啟用通訊協定 (例如 https)，您可以明確加入使用該通訊協定的端點，或是呼叫 ServiceConfiguration.EnableProtocol(Binding) 以自動加入端點，也就是自動為每個與通訊協定相容的基底位址 (Base Address) 及所定義的每份服務合約加入端點。 下列程式碼示範如何使用 ServiceConfiguration.EnableProtocol 方法：  
  
```csharp  
public class Service1 : IService1
{
    public string GetData(int value);
    public static void Configure(ServiceConfiguration config)
    {
        // Enable "Add Service Reference" support
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });
       // set up support for http, https, net.tcp, net.pipe
       config.EnableProtocol(new BasicHttpBinding());
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 僅當未以程式設計方式`protocolMappings`將應用程式終結點添加到中時，才會使用<>部分中的<xref:System.ServiceModel.ServiceConfiguration>設置。您可以通過調用<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>然後更改設置，從預設應用程式佈建檔中選擇載入服務配置。 <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> 類別也允許您從集中式組態載入組態。 下列程式碼說明如何實作此作業：  
  
```csharp
public class Service1 : IService1
{
    public void DoWork();
    public static void Configure(ServiceConfiguration config)
    {
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));
    }
}  
```  
  
> [!IMPORTANT]
> 請注意，<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>忽略<><>`host``service``system.serviceModel`標記中<>設置。 從概念上講`host`，<>是關於主機配置的，而不是服務配置，並且在"配置"方法執行之前載入它。  
  
## <a name="see-also"></a>另請參閱

- [使用組態檔設定服務](configuring-services-using-configuration-files.md)
- [設定用戶端行為](configuring-client-behaviors.md)
- [簡化設定](simplified-configuration.md)
- [組態](./samples/configuration-sample.md)
- [在 IIS 與 WAS 中以組態為基礎的啟動](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [組態與中繼資料支援](./extending/configuration-and-metadata-support.md)
- [組態](./diagnostics/exceptions-reference/configuration.md)
- [如何：在設定中指定服務繫結](how-to-specify-a-service-binding-in-configuration.md)
- [HOW TO：在組態中建立服務端點](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [HOW TO：使用組態檔發行服務的中繼資料](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [如何：在設定中指定用戶端繫結](how-to-specify-a-client-binding-in-configuration.md)
