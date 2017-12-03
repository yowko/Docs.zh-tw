---
title: "在程式碼中設定 WCF 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c05cc5947a36bbe8573c5308cdfbbe3f6c990815
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-wcf-services-in-code"></a>在程式碼中設定 WCF 服務
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 可讓開發人員使用組態檔或程式碼來設定服務。  當服務需要在部署後進行設定時，組態檔非常有用。 使用組態檔時，IT 專業人員只需更新組態檔，不必重新編譯。 但是組態檔可能會很複雜而難以維護。 由於不支援組態檔偵錯，而且組態項目是以名稱來參考，這使得製作組態檔容易出錯且難度增加。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 也允許您以程式碼來設定服務。 在舊版 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] (4.0 及更早版本) 的在自我裝載案例中，您可以輕鬆使用程式碼來設定服務，因為 <xref:System.ServiceModel.ServiceHost> 類別可讓您在呼叫 ServiceHost.Open 之前設定端點和行為。 但是在 Web 裝載案例中，您就無法直接存取 <xref:System.ServiceModel.ServiceHost> 類別。 為了設定 Web 裝載服務，您需要建立會建立 `System.ServiceModel.ServiceHostFactory` 的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，並執行任何所需的設定。 從 .NET 4.5 開始，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 提供了更簡單的方法，以程式碼來設定自我裝載和 Web 裝載服務。  
  
## <a name="the-configure-method"></a>Configure 方法  
 只需定義名為 `Configure` 的公用靜態方法，並在您的服務實作類別中包含下列簽章：  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Configure 方法接受可讓開發人員加入端點和行為的 <xref:System.ServiceModel.ServiceConfiguration> 執行個體。 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 會在服務主機開啟之前呼叫這個方法。 一旦定義之後，將會忽略 app.config 或 web.config 檔案中指定的任何服務組態設定。  
  
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
            return string.Format("You entered: {0}", value);  
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
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 在 設定 <`protocolMappings`> 區段只有在任何應用程式端點會加入至<xref:System.ServiceModel.ServiceConfiguration>以程式設計的方式。您可以選擇性地服務組態從載入預設應用程式組態檔藉由呼叫<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>然後變更設定。 <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> 類別也允許您從集中式組態載入組態。 下列程式碼說明如何實作此作業：  
  
```  
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
>  請注意，<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>會忽略 <`host`> 中的設定 <`service`> 標記 <`system.serviceModel`>。 就概念而言，<`host`> 主應用程式組態、 沒有服務組態和它的設定方法執行之前取得已載入。  
  
## <a name="see-also"></a>另請參閱  
 [使用設定檔設定服務](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [設定用戶端行為](../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [簡化設定](../../../docs/framework/wcf/simplified-configuration.md)  
 [以組態為基礎的啟用](../../../docs/framework/wcf/samples/configuration-based-activation.md)  
 [組態](../../../docs/framework/wcf/samples/configuration-sample.md)  
 [在 IIS 和 WAS 組態為基礎的啟用](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)  
 [設定和中繼資料支援](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)  
 [組態](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)  
 [如何：在設定中指定服務繫結](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [如何： 在組態中建立服務端點](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 [如何： 使用組態檔的服務發行中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [如何：在設定中指定用戶端繫結](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
