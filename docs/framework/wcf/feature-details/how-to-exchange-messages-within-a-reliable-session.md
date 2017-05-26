---
title: "HOW TO：在可靠的工作階段內交換訊息 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# HOW TO：在可靠的工作階段內交換訊息
本主題概要說明透過其中一個系統提供的繫結啟用可靠工作階段 \(此繫結支援此類工作階段，但非預設\) 所需的步驟。您可以透過命令式程式碼或是宣告式組態檔來啟用可靠工作階段。本程序透過用戶端組態檔與服務組態檔來啟用可靠工作階段，並規定訊息以當初傳送的相同順序依序抵達。  
  
 此程序的重要部分在於端點組態項目包含 `bindingConfiguration` 屬性，而此屬性參考了名為 "Binding1" 的繫結組態。[\<繫結\>](../../../../docs/framework/misc/binding.md) 組態項目可以接著參考此名稱並將 [reliableSession](http://msdn.microsoft.com/zh-tw/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) 項目的 `enabled` 屬性設為 `true` 來啟用可靠工作階段。您可以將 `ordered` 屬性設為 `true`，為可靠工作階段指定依序傳遞保證。  
  
 如需這個範例的原始檔複本，請參閱 [WS 可靠工作階段](../../../../docs/framework/wcf/samples/ws-reliable-session.md)。  
  
### 若要將包含 WSHttpBinding 的服務設為使用可靠工作階段  
  
1.  定義服務類型的服務合約。  
  
     [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]  
  
2.  在服務類別中實作服務合約。請注意，服務的實作內並未指定位址或繫結資訊。同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。  
  
     [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]  
  
3.  建立 Web.config 檔案為 `CalculatorService` 設定端點，這個端點會使用已啟用可靠工作階段並要求訊息依序傳遞的 <xref:System.ServiceModel.WSHttpBinding>。  
  
     <!-- TODO: review snippet reference [!code[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]  -->  
  
4.  建立包含此行的 Service.svc 檔案：  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  將 Service.svc 檔放入您的網際網路資訊服務 \(IIS\) 虛擬目錄中。  
  
### 若要將包含 WSHttpBinding 的用戶端設為使用可靠工作階段  
  
1.  從命令列使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，產生來自服務中繼資料的程式碼：  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  所產生的用戶端會包含 `ICalculator` 介面，其中定義了用戶端實作所必須滿足的服務合約。  
  
     [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]  
  
3.  產生的用戶端應用程式也包含 `ClientCalculator` 的實作。請注意，服務的實作內部並未指定位址和繫結資訊。同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。  
  
     [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]  
  
4.  Svcutil.exe 也會為使用 <xref:System.ServiceModel.WSHttpBinding> 類別的用戶端產生組態。使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 時，此檔案應該命名為 App.config。  
  
     <!-- TODO: review snippet reference [!code[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]  -->  
  
5.  在應用程式中建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。  
  
     [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]  
  
6.  請編譯並執行用戶端。  
  
## 範例  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
 好幾個系統提供的繫結預設都支援可靠工作階段。包括：  
  
-   <xref:System.ServiceModel.WSDualHttpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>  
  
 如需示範如何建立可支援可靠工作階段的自訂繫結，請參閱 [HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)。  
  
## 請參閱  
 [可靠工作階段](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)