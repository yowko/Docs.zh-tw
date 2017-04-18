---
title: "HOW TO：啟用資料服務結果的分頁 (WCF Data Services) | Microsoft Docs"
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
  - "分頁輸出 [WCF Data Services]"
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：啟用資料服務結果的分頁 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可讓您限制資料服務查詢所傳回的實體數目。  當服務已初始化且可針對每個實體集分別設定服務時，分頁限制會定義於所呼叫的方法中。  
  
 啟用分頁時，摘要中的最後一個項目會包含下一頁資料的連結。  如需詳細資訊，請參閱[設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。  
  
 本主題顯示如何修改資料服務以啟用傳回之 `Customers` 和 `Orders` 實體集之分頁。  本主題中的範例使用 Northwind 範例資料服務。  此服務會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
### 如何啟用傳回之 Customers 和 Orders 實體集之分頁  
  
-   在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## 請參閱  
 [載入延後的內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)   
 [HOW TO：載入分頁結果](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)