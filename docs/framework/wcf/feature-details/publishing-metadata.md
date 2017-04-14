---
title: "發行中繼資料 | Microsoft Docs"
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
  - "中繼資料 [WCF], 發行"
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 發行中繼資料
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務會藉由發行一或多個中繼資料端點以發行中繼資料。發行服務中繼資料會使用標準化的通訊協定 \(例如 WS\-MetadataExchange \(MEX\) 和 HTTP\/GET 要求\) 來提供中繼資料。中繼資料端點與其他服務端點相似的地方，在於兩者都有位址、繫結和合約，並且能夠透過組態或命令式程式碼新增至服務主機。  
  
## 發行中繼資料端點  
 若要發行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的中繼資料端點，您必須先將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 服務行為加入至服務。加入 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 執行個體可讓您的服務公開中繼資料端點。一旦您加入 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 服務行為之後，就可以接著公開支援 MEX 通訊協定或回應 HTTP\/GET 要求的中繼資料端點。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 會使用 <xref:System.ServiceModel.Description.WsdlExporter> 匯出服務中所有服務端點的中繼資料。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]從服務匯出中繼資料的詳細資訊，請參閱[匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)。  
  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 會加入 <xref:System.ServiceModel.Description.ServiceMetadataExtension> 執行個體做為服務主機的延伸。<xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=fullName> 為中繼資料發行通訊協定提供實作。您也可以藉由存取 <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=fullName> 屬性，使用 <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=fullName> 在執行階段取得服務的中繼資料。  
  
### MEX 中繼資料端點  
 若要加入使用 MEX 通訊協定的中繼資料端點，請將服務端點加入至使用 `IMetadataExchange` 服務合約的服務主機。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 包含使用此服務合約名稱的 <xref:System.ServiceModel.Description.IMetadataExchange> 介面，您可以用來做為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 程式設計模型的一部分。WS\-MetadataExchange 端點或 MEX 端點可以使用靜態處理站方法在 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 類別上所公開的四個預設繫結中的其中一個，以比對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 工具 \(例如 Svcutil.exe\) 使用的預設繫結。您也可以使用自己的自訂繫結設定 MEX 中繼資料端點。  
  
### HTTP GET 中繼資料端點  
 若要將中繼資料端點加入至回應 HTTP\/GET 要求的服務，請將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 上的 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 屬性設為 `true`。您也可以將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 上的 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 屬性設為 `true`，以設定使用 HTTPS 的中繼資料端點。  
  
## 本章節內容  
 [HOW TO：使用組態檔發行服務的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 示範如何設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務來發行中繼資料，以便讓用戶端能夠使用 `?wsdl` 查詢字串透過 WS\-MetadataExchange 或 HTTP\/GET 要求擷取中繼資料。  
  
 [HOW TO：使用程式碼發行服務的中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 示範如何在程式碼中啟用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的中繼資料發行，以便讓用戶端能夠使用 `?wsdl` 查詢字串透過 WS\-MetadataExchange 或 HTTP\/GET 要求擷取中繼資料。  
  
## 參考  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## 請參閱  
 [匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)