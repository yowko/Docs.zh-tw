---
title: "HOW TO：在 IIS 中裝載 WCF 服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# HOW TO：在 IIS 中裝載 WCF 服務
本主題概要說明建立裝載在網際網路資訊服務 (IIS) 中的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時所需的基本步驟。 本主題假設您熟悉 IIS，而且了解如何使用 IIS 管理工具建立與管理 IIS 應用程式。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]請參閱 IIS[網際網路資訊服務](http://go.microsoft.com/fwlink/?LinkId=132449)A[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]在 IIS 環境中執行的服務會充分善用 IIS 功能，例如處理序回收、 閒置關機、 處理序健康狀態監控，以及訊息啟動。 這個裝載選項要求必須正確設定 IIS，但不要求您將任何裝載程式碼撰寫為應用程式的一部分。 IIS 裝載只能和 HTTP 傳輸一起使用。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]和[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]互動，請參閱[WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]設定安全性，請參閱[安全性](../../../../docs/framework/wcf/feature-details/security.md)。  
  
 此範例的來源複本，請參閱[IIS 裝載使用內嵌程式碼](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)。  
  
### <a name="to-create-a-service-hosted-by-iis"></a>若要建立 IIS 裝載的服務  
  
1.  確認您的電腦上已安裝 IIS 且正在執行中。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]請參閱安裝與設定 IIS[安裝與設定 IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=132128)  
  
2.  為您的應用程式檔案建立稱為 "IISHostedCalcService" 新的資料夾，確保 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 能夠存取資料夾內容，然後使用 IIS 管理工具來建立實際位於此應用程式目錄中的新 IIS 應用程式。 建立應用程式目錄的別名時，請使用 "IISHostedCalc"。  
  
3.  在應用程式目錄中建立名為 "service.svc" 的新檔案。 將下列程式碼來編輯此檔案@ServiceHost項目。  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>  
    ```  
  
4.  在應用程式目錄中建立 App_Code 子目錄。  
  
5.  在 App_Code 子目錄中建立名為 Service.cs 的程式碼檔案。  
  
6.  使用陳述式將以下加入至 Service.cs 檔案的最上方。  
  
    ```  
    using System;  
    using System.ServiceModel;  
    ```  
  
7.  使用陳述式之後，加入下列命名空間宣告。  
  
    ```  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8.  在命名空間宣告內定義服務合約，如下列程式碼所示。  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. 在符合合約定義之後實作服務合約，如下列程式碼所示。  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. 在應用程式目錄中建立名為 "Web.config" 的檔案，並將下列組態程式碼加入至該檔案中。 在執行階段，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構會使用這項資訊以建構用戶端應用程式可通訊的端點。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <!-- This section is optional with the default configuration  
            model introduced in .NET Framework 4 -->  
          <service name="Microsoft.ServiceModel.Samples.CalculatorService">  
  
            <!-- This endpoint is exposed at the base address provided by host:                                        http://localhost/servicemodelsamples/service.svc  -->  
            <endpoint address=""  
                      binding="wsHttpBinding"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  
            <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
      </system.serviceModel>  
  
    </configuration>  
  
    ```  
  
     此範例會在組態檔中明確地指定端點。 如果您沒有將任何端點加入至服務中，執行階段會為您加入預設端點。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]預設端點、 繫結和行為，請參閱[簡化的組態](../../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
11. 若要確認服務裝載正確，請開啟 Internet Explorer 的執行個體，然後瀏覽到服務的 URL：`http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>範例  
 以下是裝載於 IIS 之計算機服務的完整程式碼清單。  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]  
  
 <!-- TODO: review snippet reference [!code[c_HowTo_HostInIIS#100](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  -->  
  
## <a name="see-also"></a>另請參閱  
 [在 網際網路資訊服務中裝載](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)   
 [裝載服務](../../../../docs/framework/wcf/hosting-services.md)   
 [WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)   
 [安全性](../../../../docs/framework/wcf/feature-details/security.md)   
 [Windows Server App Fabric 裝載功能](http://go.microsoft.com/fwlink/?LinkId=201276)