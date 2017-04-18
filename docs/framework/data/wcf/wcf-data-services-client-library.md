---
title: "WCF Data Services 用戶端程式庫 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "HTML"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DataServiceContext 類別, 關於 DataServiceContext 類別"
  - "DataServiceQuery 類別, 關於 DataServiceQuery 類別"
  - "WCF Data Services, 用戶端程式庫"
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF Data Services 用戶端程式庫
任何可以傳送 HTTP 要求並處理資料服務傳回之 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的應用程式，都可以與 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 型資料服務互動。這個互通性可讓您存取許多 Web 架構應用程式的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 型服務。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 包含用戶端程式庫，在您從 .NET Framework 或 Silverlight 架構應用程式取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要時，可為您提供更豐富的程式設計體驗。  
  
 用戶端程式庫的兩個主要類別是 <xref:System.Data.Services.Client.DataServiceContext> 類別和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別。  <xref:System.Data.Services.Client.DataServiceContext> 類別會封裝針對特定資料服務支援的作業。  雖然 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務沒有狀態，但是內容具有狀態。  因此，您可以使用 <xref:System.Data.Services.Client.DataServiceContext> 類別，在用戶端上維護與資料服務互動之間的狀態，以便支援變更管理之類的功能。  這個類別也可以管理識別及追蹤變更。  <xref:System.Data.Services.Client.DataServiceQuery%601> 類別表示針對特定實體集的查詢。  
  
 本節將描述如何使用用戶端程式庫，存取和變更 .NET Framework 用戶端應用程式的資料。  如需如何搭配 Silverlight 架構應用程式使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫的詳細資訊，請參閱 [WCF Data Services \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=186016)。  有其他用戶端程式庫可讓您在其他種類的應用程式中取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。  如需詳細資訊，請參閱 [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796)。  
  
## 在本節中  
 [產生資料服務用戶端程式庫](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 說明如何產生根據 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的用戶端程式庫和用戶端資料服務類別。  
  
 [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 描述如何使用用戶端程式庫查詢 .NET Framework 架構應用程式的資料服務。  
  
 [載入延後的內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 描述如何載入不包含在初始查詢回應中的額外內容。  
  
 [更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 描述如何使用用戶端程式庫建立、修改，以及刪除實體及關聯性。  
  
 [非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 描述以非同步方式，搭配用戶端程式庫提供的機能與資料服務一起使用。  
  
 [批次作業](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 描述如何使用用戶端程式庫，在單一批次中將多個要求傳送至資料服務。  
  
 [將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 說明如何將控制項繫結至資料服務所傳回的[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要。  
  
 [呼叫服務作業](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 說明如何使用用戶端程式庫呼叫服務作業。  
  
 [管理資料服務內容](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 說明用於管理用戶端程式庫行為的選項。  
  
 [使用二進位資料](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 說明如何存取及變更資料服務當做資料流傳回的二進位資料。  
  
## 請參閱  
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)   
 [使用者入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)