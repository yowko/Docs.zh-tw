---
title: HOW TO：設定基本 Windows Communication Foundation 用戶端
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
caps.latest.revision: 47
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bde13abeac782da1c553afa290943eeff925fa4
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>HOW TO：設定基本 Windows Communication Foundation 用戶端
這是在建立基本 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六項工作中的第五項。 六個工作的概觀，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。  
  
 此主題 disuccess 使用的 [加入服務參考] 功能產生的用戶端組態檔[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]或[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 設定用戶端包含指定用戶端用來存取服務的端點。 端點內含位址、繫結和合約，每一項都必須在設定用戶端的過程中加以指定。  
  
### <a name="to-configure-a-windows-communication-foundation-client"></a>若要設定 Windows Communication Foundation 用戶端  
  
1.  從 GettingStartedClient 專案開啟產生的組態檔 (App.config)。 下列範例是產生之組態檔的外觀。 在下[ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)區段中，尋找[\<端點 >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)項目。  
  
    ```xml  
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
    </configuration>   
    ```  
  
     這個範例會設定用戶端用來存取位於下列位址的服務端點： http://localhost:8000/ServiceModelSamples/Service/CalculatorService  
  
     端點元素會指定將 `ServiceReference1.ICalculator` 服務合約用於 WCF 用戶端和服務之間的通訊。 系統提供設定 WCF 通道 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>。 這個合約是使用 Visual Studio 中的 [加入服務參考] 所產生。 它基本上是 GettingStartedLib 專案中所定義之合約的複本。 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 繫結會指定 HTTP 傳輸、 互通安全性，以及其他組態詳細資料。  
  
2.  如需如何搭配這項設定使用產生的用戶端的詳細資訊，請參閱[How to： 使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用繫結設定服務與用戶端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)
