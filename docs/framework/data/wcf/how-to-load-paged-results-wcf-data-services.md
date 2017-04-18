---
title: "HOW TO：載入分頁結果 (WCF Data Services) | Microsoft Docs"
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
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：載入分頁結果 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓資料服務限制單一回應摘要中傳回的實體數量。  執行此功能時，摘要中的最後一個項目會包含下一頁資料的連結。  您可以呼叫執行 <xref:System.Data.Services.Client.DataServiceQuery%601> 時所傳回之 <xref:System.Data.Services.Client.QueryOperationResponse%601> 的 <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> 方法，來取得下一頁資料的 URI。  如需詳細資訊，請參閱[載入延後的內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
## 範例  
 本範例使用 `do…while` 迴圈，從資料服務的分頁結果載入 `Customers` 實體。  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## 範例  
 本範例會隨每個 `Customers` 實體傳回相關的 `Orders` 實體，並使用 `do…while` 迴圈載入 `Customers` 實體頁，同時使用巢狀的 `while` 迴圈從資料服務載入相關 `Orders` 實體的頁面。  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## 請參閱  
 [載入延後的內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)   
 [HOW TO：載入相關實體](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)