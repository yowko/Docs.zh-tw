---
title: "HOW TO：載入相關實體 (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 延後內容"
  - "WCF Data Services, 載入資料"
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：載入相關實體 (WCF Data Services)
當您需要在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中載入相關的實體時，可以在 <xref:System.Data.Services.Client.DataServiceContext> 類別上使用 <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> 方法。  您也可以在 <xref:System.Data.Services.Client.DataServiceQuery%601> 使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法，要求立即將相關實體載入至同一個查詢回應中。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
## 範例  
 下列範例示範如何明確地載入與所傳回之每個 `Orders` 執行個體相關的 `Customer`。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## 範例  
 下列範例示範如何使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法傳回屬於查詢所傳回之 `Orders` 的 `Order Details` 方法。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## 請參閱  
 [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)