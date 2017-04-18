---
title: "HOW TO：設定基本 Windows Communication Foundation 用戶端 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "WCF 用戶端 [WCF], 設定"
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: 47
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 47
---
# HOW TO：設定基本 Windows Communication Foundation 用戶端
這是在建立基本 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六項工作中的第五項。  如需這六個工作的概觀，請參閱[快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。  
  
 本主題說明使用 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 之 \[加入服務參考\] 功能或 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 所產生的用戶端組態檔。  設定用戶端包含指定用戶端用來存取服務的端點。  端點內含位址、繫結和合約，每一項都必須在設定用戶端的過程中加以指定。  
  
### 若要設定 Windows Communication Foundation 用戶端  
  
1.  從 GettingStartedClient 專案開啟產生的組態檔 \(App.config\)。  下列範例是產生之組態檔的外觀。  在 [\<system.serviceModel\>](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)[\<endpoint\> 區段下方，尋找](http://msdn.microsoft.com/zh-tw/13aa23b7-2f08-4add-8dbf-a99f8127c017) 項目。  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
          <!-- specifies the version of WCF to use-->  
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <!-- Uses wsHttpBinding-->  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <!-- specifies the endpoint to use when calling the service -->  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration><?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
        <startup>   
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />  
        </startup>  
        <system.serviceModel>  
            <bindings>  
                <wsHttpBinding>  
                    <binding name="WSHttpBinding_ICalculator" />  
                </wsHttpBinding>  
            </bindings>  
            <client>  
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"  
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"  
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">  
                    <identity>  
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />  
                    </identity>  
                </endpoint>  
            </client>  
        </system.serviceModel>  
    </configuration>   
    ```  
  
     此範例會設定用戶端用來存取服務的端點，而該服務則位於下列位址：http:\/\/localhost:8000\/ServiceModelSamples\/Service\/CalculatorService。  
  
     端點元素會指定將 `ServiceReference1.ICalculator` 服務合約用於 WCF 用戶端和服務之間的通訊。  WCF 通道是透過系統提供的 <xref:System.ServiceModel.WsHttpBinding> 進行設定。  這個合約是使用 Visual Studio 中的 \[加入服務參考\] 所產生。  它基本上是 GettingStartedLib 專案中所定義之合約的複本。  <xref:System.ServiceModel.WsHttpBinding> 繫結會指定 HTTP 為傳輸、互通安全性，與其他組態詳細資料。  
  
2.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]如何使用產生的用戶端來搭配此組態的詳細資訊，請參閱 [HOW TO：使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。  
  
## 請參閱  
 [使用繫結來設定服務和用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [HOW TO：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [使用者入門](../../../docs/framework/wcf/samples/getting-started-sample.md)   
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)