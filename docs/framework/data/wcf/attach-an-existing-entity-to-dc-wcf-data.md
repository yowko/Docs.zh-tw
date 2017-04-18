---
title: "HOW TO：將現有的實體附加至 DataServiceContext (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 變更資料"
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：將現有的實體附加至 DataServiceContext (WCF Data Services)
若實體已經存在資料服務中，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫可讓您將代表該實體的物件直接附加至 <xref:System.Data.Services.Client.DataServiceContext>，且不需先執行查詢。  如需詳細資訊，請參閱[更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
## 範例  
 下列範例示範如何建立現有的 `Customer` 物件，此物件包含要儲存至資料服務的變更。  系統會將物件附加至內容，並呼叫 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 方法，將附加物件標記為 <xref:System.Data.Services.Client.EntityStates>，然後再呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法。  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)