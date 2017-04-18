---
title: "Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "憑證 [WCF], 服務憑證的驗證"
  - "服務憑證的驗證 [WCF]"
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Internet Explorer 與 WCF 執行之服務憑證驗證之間的差異
因為 Internet Explorer 與 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 使用 HTTPS 時，驗證服務憑證的方法不同，所以即使 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端可成功傳送訊息至服務端點，Internet Explorer 還是有可能無法存取說明網頁或服務的 Web 服務描述語言 \(WSDL\)。這是因為 Internet Explorer 檢查服務憑證在增強用途旗標中是否擁有 `ServerAuthentication` 物件識別項 \(OID\)，而 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 並未強制執行這種限制。若 Internet Explorer 無法存取服務說明網頁或服務的 WSDL，請使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 存取服務中繼資料。  
  
## 請參閱  
 [透過 TCP 與 SOAP 安全性的 HTTPS 與 SSL 之間的憑證驗證差異](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)   
 [HOW TO：擷取中繼資料並實作相容性服務](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)