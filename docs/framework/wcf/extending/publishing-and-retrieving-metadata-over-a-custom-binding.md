---
title: "發行與擷取自訂繫結上的中繼資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 發行與擷取自訂繫結上的中繼資料
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 提供新增中繼資料端點到服務的支援。這些中繼資料端點可回應位於具有 `?wsdl`  查詢字串之 URL 的 HTTP GET 要求，並回應依照 WS\-MetadataExchange \(MEX\) 規格中定義的 WS\-Transfer GET 要求。MEX 端點會實作 <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=fullName> 合約。  
  
## 發行自訂繫結上的中繼資料  
 只要將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=fullName> 或 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=fullName> 屬性設定為 `true`，便可啟用 HTTP GET 中繼資料端點和 HTTPS GET 中繼資料端點。這些端點的繫結無法設定。  
  
 不過，<xref:System.ServiceModel.Description.IMetadataExchange> 合約可搭配任何端點使用，包括那些使用自訂繫結的端點，因為 <xref:System.ServiceModel.Description.IMetadataExchange> 端點與任何其他 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務端點相同。如果您知道如何修改系統提供之繫結的組態，或者知道如何設定 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName>，則可設定繫結以搭配 <xref:System.ServiceModel.Description.IMetadataExchange> 端點使用。  
  
## 擷取自訂繫結上的中繼資料  
 您可以使用標準 HTTP 或 HTTPS GET 要求，從 HTTP Get 與 HTTPS Get 中繼資料端點擷取中繼資料。  
  
 若要從 MEX 中繼資料端點擷取中繼資料，一般可使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援的其中一個標準 MEX 繫結。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=fullName>.<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 型別與 Svcutil.exe 工具會根據指定中繼資料端點的位址，自動選取其中一個標準 MEX 繫結。  
  
 如果 MEX 中繼資料端點使用的繫結異於其中一個標準 MEX 繫結，您可以使用程式碼或提供 <xref:System.ServiceModel.Description.IMetadataExchange> 用戶端端點組態，設定 <xref:System.ServiceModel.Description.MetadataExchangeClient> 所使用的繫結。Svcutil.exe 工具會自動從其組態檔載入 <xref:System.ServiceModel.Description.IMetadataExchange> 用戶端端點組態，此組態與中繼資料端點位址之 URI 配置的名稱相同。  
  
## 安全性  
 發行自訂繫結上的中繼資料時，繫結務必要提供您中繼資料所需的安全性支援。例如，若要避免資訊洩漏，並且確定您的用戶端有權限可取得中繼資料，您可將 <xref:System.ServiceModel.Description.IMetadataExchange> 端點設為需要驗證和加密，讓中繼資料和應用程式更安全。[自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)範例將示範此案例。  
  
## 請參閱  
 [保護服務的安全](../../../../docs/framework/wcf/securing-services.md)   
 [WS\-MetadataExchange 繫結](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)   
 [HOW TO：設定自訂 WS\-Metadata Exchange 繫結](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)   
 [HOW TO：透過非 MEX 繫結擷取中繼資料](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)