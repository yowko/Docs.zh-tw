---
title: "HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# HOW TO：使用 HTTPS 建立自訂可靠工作階段繫結
本主題示範使用 Secure Sockets Layer \(SSL\) 傳輸安全性來搭配可靠工作階段。  若要透過 HTTPS 使用可靠工作階段，您必須建立使用可靠工作階段與 HTTPS 傳輸的自訂繫結。  您可以透過命令式程式碼或是宣告式組態檔來啟用可靠工作階段。  此程序會使用用戶端與服務的組態檔來啟用可靠工作階段和 [\<httpsTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md) 項目。  
  
 此程序的關鍵在於 `endpoint` 組態項目所包含的 `bindingConfiguration` 屬性可參考名為 "reliableSessionOverHttps" 的自訂繫結組態。  [\<繫結\>](../../../../docs/framework/misc/binding.md) 組態項目可以接著參考此名稱，並加入 `reliableSession` 和 `httpsTransport` 項目以指定使用可靠工作階段和 HTTPS 傳輸。  
  
 如需這個範例的原始檔複本，請參閱[HTTPS 上的自訂繫結可靠工作階段](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md)。  
  
### 若要設定包含 CustomBinding 的服務來使用搭配 HTTPS 的可靠工作階段  
  
1.  定義服務類型的服務合約。  
  
     [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]  
  
2.  在服務類別中實作服務合約。  請注意，服務的實作內並未指定位址或繫結資訊。  同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。  
  
     [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]  
  
3.  建立 Web.config 檔，以便使用名為 "reliableSessionOverHttps" \(使用可靠工作階段和 HTTPS 傳輸\) 的自訂繫結來設定 `CalculatorService` 端點。  
  
     <!-- TODO: review snippet reference [!code[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]  -->  
  
4.  建立包含此行的 Service.svc 檔案：  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  將 Service.svc 檔放入您的網際網路資訊服務 \(IIS\) 虛擬目錄中。  
  
### 若要設定包含 CustomBinding 的用戶端來使用搭配 HTTPS 的可靠工作階段  
  
1.  從命令列使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)，產生來自服務中繼資料的程式碼。  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  所產生的用戶端會包含 `ICalculator` 介面，其中定義了用戶端實作所必須滿足的服務合約。  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]  
  
3.  產生的用戶端應用程式也包含 `ClientCalculator` 的實作。  請注意，服務的實作內部並未指定位址和繫結資訊。  同時，您不需要撰寫可從組態檔擷取該資訊的程式碼。  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]  
  
4.  將名為 "reliableSessionOverHttps" 的自訂繫結設定成使用 HTTPS 傳輸和可靠的工作階段。  
  
     <!-- TODO: review snippet reference [!code[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]  -->  
  
5.  在應用程式中建立 `ClientCalculator` 的執行個體，然後呼叫服務作業。  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]  
  
6.  請編譯並執行用戶端。  
  
## 範例  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## .NET Framework 安全性  
 因為本範例中所使用的憑證是使用 Makecert.exe 所建立的測試憑證，所以當您嘗試從瀏覽器存取 HTTPS 位址時 \(例如 https:\/\/localhost\/servicemodelsamples\/service.svc\)，會顯示安全性警示。  
  
## 請參閱  
 [可靠工作階段](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)