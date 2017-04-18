---
title: "HOW TO：啟用資料服務的存取 (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 設定"
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：啟用資料服務的存取 (WCF Data Services)
在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中，您必須明確授與資料服務所公開之資源的存取權。  這表示當您建立新的資料服務之後，您仍然必須明確提供個別資源的存取權當做實體集。  本主題示範如何在完成[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時所建立的 Northwind 資料服務中，針對其中 5 個實體集啟用讀取和寫入存取權。由於 <xref:System.Data.Services.EntitySetRights> 列舉是使用 <xref:System.FlagsAttribute> 所定義，因此您可以使用邏輯 OR 運算子，為單一實體集指定多個權限。  
  
> [!NOTE]
>  任何可以存取 ASP.NET 應用程式的用戶端也可以存取資料服務公開的資源。  在實際執行的資料服務中，若要避免未經授權存取資源，您也應該要保護應用程式本身的安全。  如需詳細資訊，請參閱[NIB: ASP.NET Security](http://msdn.microsoft.com/zh-tw/04b37532-18d9-40b4-8e5f-ee09a70b311d)。  
  
### 啟用存取資料服務  
  
-   在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     如此可讓用戶端具有 `Orders` 和 `Order_Details` 實體集的讀取和寫入存取權，並擁有 `Customers` 實體集的唯讀存取權。  
  
## 請參閱  
 [HOW TO：開發在 IIS 上執行的 WCF Data Service](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)   
 [設定資料服務](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)