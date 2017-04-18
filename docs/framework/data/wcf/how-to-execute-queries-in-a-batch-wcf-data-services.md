---
title: "HOW TO：在批次中執行查詢 (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 批次要求"
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：在批次中執行查詢 (WCF Data Services)
透過使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫，您可以在單一批次中，針對資料服務執行一個以上的查詢。  如需詳細資訊，請參閱[批次作業](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
## 範例  
 下列範例顯示如何呼叫 <xref:Microsoft.SqlServer.ReportingServices.ReportingService.ExecuteBatch%2A> 方法，執行 <xref:System.Data.Services.Client.DataServiceRequest%601> 物件的陣列，其中包含從 Northwind 資料服務同時傳回 `Customers` 和 `Products` 物件的查詢。  在傳回的 <xref:System.Data.Services.Client.DataServiceResponse>中，會列舉 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件集合以及包含在每一個 <xref:System.Data.Services.Client.QueryOperationResponse%601> 中的物件集合。  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)