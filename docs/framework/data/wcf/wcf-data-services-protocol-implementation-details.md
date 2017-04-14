---
title: "WCF Data Services 通訊協定實作詳細資訊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# WCF Data Services 通訊協定實作詳細資訊
## OData 通訊協定實作詳細資訊  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 要求實作通訊協定的資料服務提供一組最低限度的特定功能。  這些功能在通訊協定文件中是以「應該」和「必須」描述。其他選擇性功能則是以「可能」描述。本主題描述 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 目前尚未實作的選擇性功能。  如需詳細資訊，請參閱 [OData 通訊協定文件](http://go.microsoft.com/fwlink/?LinkID=184554)。  
  
### 支援 $format 查詢選項  
 The [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定同時支援 JavaScript 標記法 \(JSON\) 和 Atom 摘要，而且 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 提供 `$format` 系統查詢選項，讓用戶端要求回應摘要的格式。  此系統查詢選項 \(如果資料服務支援\) 必須覆寫要求之 Accept 標頭的值。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 支援同時傳回 JSON 和 Atom 摘要。  不過，預設實作不支援 `$format` 查詢選項，而且僅使用 Accept 標頭的值決定回應的格式。  在某些情況下，您的資料服務可能需要支援 `$format` 查詢選項，例如，用戶端無法設定 Accept 標頭時。  為支援這些案例，您必須擴充資料服務來處理 URI 中的這個選項。  您可以將此功能加入資料服務，方法是從 MSDN Code Gallery 網站下載[適用於 ADO.NET Data Services 之 JSONP 和 URL 控制的格式支援](http://go.microsoft.com/fwlink/?LinkId=208228)範例專案，然後將其加入您的資料服務專案。  此範例會移除 `$format` 查詢選項，並將 Accept 標頭變更為 `application/json`。  當您加入範例專案時，將 `JSONPSupportBehaviorAttribute` 加入至您的資料服務類別中可讓服務處理 `$format` 查詢選項 `$format=json`。  如果也要處理 `$format=atom` 或其他自訂格式，則需要進一步自訂這個範例專案。  
  
## WCF Data Services 行為  
 下列 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 行為未透過 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定明確定義：  
  
### 預設排序行為  
 當傳送至資料服務的查詢要求包含 `$top` 或 `$skip` 系統查詢選項，但不包含 `$orderby` 系統查詢選項時，傳回的摘要會依索引鍵屬性，以遞增順序排序。  這是因為您需要排序，才能確保結果分頁正確。  若要這樣做，資料服務要將排序運算式加入至查詢中。  在資料服務中啟用伺服器驅動型分頁時，也會發生這個行為。  如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。若要控制傳回之摘要的排序，您應該在查詢 RUI 中加入 `$orderby`。  
  
## 請參閱  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)