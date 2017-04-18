---
title: "擷取中繼資料 | Microsoft Docs"
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
  - "中繼資料 [WCF], 擷取"
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 擷取中繼資料
中繼資料擷取程序會要求和擷取中繼資料端點內的中繼資料，這些端點包括像是 WS\-MetadataExchange \(MEX\) 中繼資料端點或 HTTP\/GET 中繼資料端點。  
  
## 使用 Svcutil.exe 來從命令列擷取中繼資料  
 您可以使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具並將 `/target:metadata` 參數傳遞至某個位址，以使用 WS\-MetadataExchange 或 HTTP\/GET 要求來擷取服務中繼資料。Svcutil.exe 會在指定的位址下載中繼資料，並將檔案儲存到磁碟中。Svcutil.exe 會在內部使用 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 執行個體 \(Instance\)，而且會從 <xref:System.ServiceModel.Description.IMetadataExchange> 端點組態 \(其名稱與傳遞至 Svcutil.exe 做為輸入的位址配置相同\) 載入。  
  
## 使用 MetadataExchangeClient 來以程式設計方式擷取中繼資料  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 可以使用標準化的通訊協定來擷取服務中繼資料，這些通訊協定包括像是 WS\-MetadataExchange 和 HTTP\/GET 要求。<xref:System.ServiceModel.Description.MetadataExchangeClient> 型別支援上述兩種通訊協定。您可以藉由提供中繼資料端點的位址及選擇性繫結，來擷取使用 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 型別的服務中繼資料。<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 執行個體使用的繫結，可以是 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 靜態類別的其中一個預設繫結、使用者提供的繫結，或是從 `IMetadataExchange` 合約之端點組態載入的繫結。<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 也可以使用 <xref:System.Net.HttpWebRequest> 型別將 HTTP URL 參照解析為中繼資料。  
  
 根據預設，<xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 執行個體與單一的 <xref:System.ServiceModel.ChannelFactory> 執行個體有密切的關係。您可以透過覆寫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> 虛擬方法，以變更或取代 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 所使用的 <xref:System.ServiceModel.ChannelFactory?displayProperty=fullName> 執行個體。同樣地，您可以覆寫 <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=fullName> 虛擬方法，以變更或取代 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 所使用的 <xref:System.Net.HttpWebRequest> 執行個體。  
  
## 本章節內容  
 [HOW TO：使用 Svcutil.exe 來下載中繼資料文件](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 判斷如何使用 Svcutil.exe 來下載中繼資料文件。  
  
 [HOW TO：使用 MetadataResolver 來動態取得繫結中繼資料](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 示範如何使用 <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=fullName> 在執行階段動態地取得中繼資料。  
  
 [HOW TO：使用 MetadataExchangeClient 來擷取中繼資料](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 示範如何使用 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=fullName> 類別將中繼資料檔案下載到包含 <xref:System.ServiceModel.Description.MetadataSection?displayProperty=fullName> 物件的 <xref:System.ServiceModel.Description.MetadataSet?displayProperty=fullName> 物件，以供寫入至檔案或其他用途。  
  
## 請參閱  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>