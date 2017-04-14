---
title: "HOW TO：藉由保留資料庫值來解決並行衝突 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：藉由保留資料庫值來解決並行衝突
若要先協調預期和實際資料庫值之間的差異再重新送出變更，可以使用 <xref:System.Data.Linq.RefreshMode> 將找到的值保留在資料庫中。  這樣會覆寫物件模型 \(Object Model\) 中的目前值。  如需詳細資訊，請參閱[開放式並行存取概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。  
  
> [!NOTE]
>  在所有情況下，擷取資料庫中更新過的資料會先重新整理用戶端上的資料錄。  這個動作可確保下一次嘗試更新時，不會在相同的並行存取檢查時失敗。  
  
## 範例  
 在這個案例下，當 User1 嘗試送出變更時，因為 User2 同時變更了 Assistant 和 Department 資料行，所以會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況。  下表顯示這個情況。  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|User1 和 User2 查詢時的原始資料庫狀態。|Alfreds|Maria|Sales|  
|User1 準備送出這些變更。|Alfred||Marketing|  
|User2 已送出這些變更。||Mary|服務|  
  
 User1 決定讓較新的資料庫值覆寫物件模型中的目前值，來解決這個衝突。  
  
 User1 使用 <xref:System.Data.Linq.RefreshMode> 解決衝突時，資料庫中的結果會如同下表：  
  
||Manager|Assistant|Department|  
|------|-------------|---------------|----------------|  
|解決衝突後的新狀態。|Alfreds<br /><br /> \(原始\)|Mary<br /><br /> \(來自 User2\)|服務<br /><br /> \(來自 User2\)|  
  
 下列範例程式碼顯示如何使用資料庫值來覆寫物件模型中的目前值   \(但不會對個別成員衝突進行任何檢查或自訂處理\)。  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## 請參閱  
 [HOW TO：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)