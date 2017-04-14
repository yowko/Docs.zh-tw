---
title: "HOW TO：新增、修改及刪除實體 (WCF Data Services) | Microsoft Docs"
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
ms.assetid: a00f8933-b232-4445-95ba-adc634f055d8
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：新增、修改及刪除實體 (WCF Data Services)
使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫時，您可以建立、更新及刪除資料服務中的實體，只要藉由對 <xref:System.Data.Services.Client.DataServiceContext> 中的物件執行相同的動作即可。  如需詳細資訊，請參閱[更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
## 範例  
 下列範例會建立新的物件執行個體，然後呼叫 <xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> 方法，在內容中建立項目。  呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP POST 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#AddProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addproduct)]
 [!code-vb[Astoria Northwind Client#AddProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addproduct)]  
  
## 範例  
 下列範例會擷取並修改現有的物件，然後呼叫 <xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 方法，將內容中的項目標記為已更新。  呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP MERGE 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#modifycustomer)]
 [!code-vb[Astoria Northwind Client#ModifyCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#modifycustomer)]  
  
## 範例  
 下列範例會在 <xref:System.Data.Services.Client.DataServiceContext> 呼叫 <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> 方法，將內容中的項目標記為已刪除。  呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP DELETE 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#deleteproduct)]
 [!code-vb[Astoria Northwind Client#DeleteProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#deleteproduct)]  
  
## 範例  
 下列範例會建立一個新的物件執行個體，然後呼叫 <xref:System.Data.Services.Client.DataServiceContext> 的 <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> 方法，在內容中建立項目與相關訂單的連結。  呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將 HTTP POST 訊息傳送至資料服務。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addorderdetailtoorderauto)]  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)   
 [HOW TO：將現有的實體附加至 DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)   
 [HOW TO：定義實體關聯性](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)   
 [批次作業](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)