---
title: "HOW TO：設定自訂 WS-Metadata Exchange 繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WS-Metadata Exchange [WCF]"
  - "WS-Metadata Exchange [WCF], 設定自訂繫結"
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# HOW TO：設定自訂 WS-Metadata Exchange 繫結
本主題說明如何設定自訂的 WS\-Metadata Exchange 繫結。  [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 包括四個系統定義的中繼資料繫結，但您可以使用想要的任何繫結來發行中繼資料。  這個主題會告訴您如何使用 `wsHttpBinding` 發行中繼資料。  這個繫結會提供讓您以安全的方法公開中繼資料的選項。  本文的程式碼是根據[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)。  
  
### 使用組態檔  
  
1.  在服務組態檔中，新增包含 `serviceMetadata` 標記的服務行為：  
  
    ```  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  將 `behaviorConfiguration` 屬性新增至參照這個新行為的服務標記：  
  
    ```  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  新增指定 MEX 為位址、指定 `wsHttpBinding` 為繫結，並指定 <xref:System.ServiceModel.Description.IMetadataExchange> 為合約的中繼資料端點：  
  
    ```  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  若要驗證中繼資料交換端點是否正常運作，請在用戶端組態檔中新增端點標記：  
  
    ```  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  在用戶端的 Main\(\) 方法中，建立新的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 執行個體、將其 <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> 屬性設為 `true`、呼叫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>，然後逐一查看傳回的中繼資料集合：  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### 以程式碼設定  
  
1.  建立 <xref:System.ServiceModel.WsHttpBinding> 繫結執行個體：  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  建立 <xref:System.ServiceModel.ServiceHost> 執行個體：  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  新增服務端點，並新增 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 執行個體：  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  新增中繼資料交換端點，指定稍早建立的 <xref:System.ServiceModel.WSHttpBinding>：  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  若要驗證中繼資料交換端點是否正常運作，請在用戶端組態檔中新增端點標記：  
  
    ```  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  在用戶端的 Main\(\) 方法中，建立新的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 執行個體、將 <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> 屬性設為 `true`、呼叫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>，然後逐一查看傳回的中繼資料集合：  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
  
    ```  
  
## 請參閱  
 [中繼資料發行行為](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)   
 [擷取中繼資料](../../../../docs/framework/wcf/samples/retrieve-metadata.md)   
 [中繼資料](../../../../docs/framework/wcf/feature-details/metadata.md)   
 [發行中繼資料](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)   
 [發行中繼資料端點](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)