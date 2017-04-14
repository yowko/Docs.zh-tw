---
title: "HOW TO：關閉延後載入 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：關閉延後載入
您可以將 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 設定為 `false`，以關閉延後載入。  如需詳細資訊，請參閱[延後和立即載入的比較](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)。  
  
> [!NOTE]
>  關閉物件追蹤時，也會隱含地關閉延後載入。  如需詳細資訊，請參閱[HOW TO：將資訊擷取成唯讀資訊](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)。  
  
## 範例  
 下列範例顯示如何將 <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> 設定為 `false`，以關閉延後載入。  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## 請參閱  
 [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)   
 [查詢資料庫](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)