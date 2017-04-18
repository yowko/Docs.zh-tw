---
title: "HOW TO：攔截資料服務訊息 (WCF Data Services) | Microsoft Docs"
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
  - "查詢攔截器 [WCF Data Services]"
  - "WCF Data Services, 自訂"
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：攔截資料服務訊息 (WCF Data Services)
使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，您可以攔截要求訊息，因此您可以將自訂邏輯加入至作業。  若要攔截訊息，您可以特別使用資料服務中的屬性化方法。  如需詳細資訊，請參閱[攔截器](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務。  此服務會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
### 定義 Orders 實體集的查詢攔截器  
  
1.  在 Northwind 資料服務專案中，開啟 Northwind.svc 檔案。  
  
2.  在 `Northwind` 類別的字碼頁中，加入下列 `using` 陳述式 \(在 Visual Basic 中是 `Imports`\)。  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  在 `Northwind` 類別中，定義名為 `OnQueryOrders` 的服務作業方法，如下所示：  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### 定義 Products 實體集的變更攔截器  
  
1.  在 Northwind 資料服務專案中，開啟 Northwind.svc 檔案。  
  
2.  在 `Northwind` 類別中，定義名為 `OnChangeProducts` 的服務作業方法，如下所示：  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## 範例  
 這個範例定義 `Orders` 實體集的查詢攔截器方法，傳回 Lambda 運算式。  這個運算式包含的委派，可根據具有特定連絡人名稱的相關 `Customers`，篩選要求的 `Orders`。  名稱會根據要求的使用者依序判斷。  這個範例假設資料服務裝載於使用 WCF，並已啟用驗證的 ASP.NET Web 應用程式內。  <xref:System.Web.HttpContext> 類別會用來擷取目前要求的原則。  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## 範例  
 這個範例定義 `Products` 實體集的變更攔截器方法。  這個方法會驗證 <xref:System.Data.Services.UpdateOperations> 或 <xref:System.Data.Services.UpdateOperations> 作業服務的輸入，如果停售的產品進行變更，將會引發例外狀況。  同時產品的刪除動作也會遭到封鎖而成為不支援的作業。  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## 請參閱  
 [HOW TO：定義服務作業](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)   
 [定義 WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)