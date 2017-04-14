---
title: "在程式碼中設定 WCF 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 在程式碼中設定 WCF 服務
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 可讓開發人員使用組態檔或程式碼來設定服務。當服務需要在部署後進行設定時，組態檔非常有用。使用組態檔時，IT 專業人員只需更新組態檔，不必重新編譯。但是組態檔可能會很複雜而難以維護。由於不支援組態檔偵錯，而且組態項目是以名稱來參考，這使得製作組態檔容易出錯且難度增加。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 也允許您以程式碼來設定服務。在舊版 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(4.0 及更早版本\) 中，使用程式碼設定服務很容易在自我裝載情節中達成，有 <xref:System.ServiceModel.ServiceHost> 類別可讓您在呼叫 ServiceHost.Open 之前設定端點和行為。但是在 Web 裝載情節中，您無法直接存取 <xref:System.ServiceModel.ServiceHost> 類別。為了設定 Web 裝載服務，您需要建立會建立 <xref:System.ServiceModel.ServiceHost> 的 <xref:System.ServiceModel.ServiceHostFactory>，並執行任何所需的設定。從 .NET 4.5 開始，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 提供了更簡單的方法，以程式碼來設定自我裝載和 Web 裝載服務。  
  
## Configure 方法  
 只需定義名為 `Configure` 的公用靜態方法，並在您的服務實作類別中包含下列簽章：  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Configure 方法接受可讓開發人員加入端點和行為的 <xref:System.ServiceModel.ServiceConfiguration> 執行個體。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 會在服務主機開啟之前呼叫這個方法。一旦定義之後，將會忽略 app.config 或 web.config 檔案中指定的任何服務組態設定。  
  
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
  
 若要為服務啟用通訊協定 \(例如 https\)，您可以明確加入使用該通訊協定的端點，或是呼叫 ServiceConfiguration.EnableProtocol\(Binding\) 以自動加入端點，也就是自動為每個與通訊協定相容的基底位址 \(Base Address\) 及所定義的每份服務合約加入端點。下列程式碼示範如何使用 ServiceConfiguration.EnableProtocol 方法：  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable “Add Service Reference” support   
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
  
 \<`protocolMappings`\> 區段中的設定只有在未以程式設計方式將任何應用程式端點加入至 <xref:System.ServiceModel.ServiceConfiguration> 時才會使用。您可以選擇呼叫 <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> 從預設應用程式組態檔載入服務組態，然後變更設定。<xref:System.ServiceModel.ServiceConfiguration> 類別也允許您從集中式組態載入設定。下列程式碼說明如何實作這個做法：  
  
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
>  請注意，<xref:System.ServiceModel.LoadFromConfiguration%2A> 會忽略 \<`system.serviceModel`\> 之 \<`service`\> 標記內的 \<`host`\> 設定。在概念上，與 \<`host`\> 有關的是主機組態而不是服務組態，前者會在 Configure 方法執行之前載入。  
  
## 請參閱  
 [使用組態檔設定服務](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)   
 [設定用戶端行為](../../../docs/framework/wcf/configuring-client-behaviors.md)   
 [簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)   
 [以組態為基礎的啟用](../../../docs/framework/wcf/samples/configuration-based-activation.md)   
 [組態](../../../docs/framework/wcf/samples/configuration-sample.md)   
 [在 IIS 與 WAS 中以組態為基礎的啟用](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)   
 [組態與中繼資料支援](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)   
 [組態](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)   
 [HOW TO：指定組態中的服務繫結](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)   
 [HOW TO：在組態中建立服務端點](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)   
 [HOW TO：使用組態檔發行服務的中繼資料](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)   
 [HOW TO：指定組態中的用戶端繫結](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)