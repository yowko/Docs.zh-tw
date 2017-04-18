---
title: "HOW TO：指定何時擲回並行例外狀況 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：指定何時擲回並行例外狀況
在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，因為開放式並行存取 \(Optimistic Concurrency\) 衝突而未更新物件時，會擲回 <xref:System.Data.Linq.ChangeConflictException> 例外狀況 \(Exception\)。  如需詳細資訊，請參閱[開放式並行存取概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。  
  
 將變更提交至資料庫之前，您可以指定何時應擲出並行例外狀況：  
  
-   在第一次失敗時擲出例外狀況 \(<xref:System.Data.Linq.ConflictMode>\)。  
  
-   完成所有更新嘗試、累積所有失敗，並且在例外狀況中報告所累積的失敗 \(<xref:System.Data.Linq.ConflictMode>\)。  
  
 擲出後，<xref:System.Data.Linq.ChangeConflictException> 例外狀況會提供 <xref:System.Data.Linq.ChangeConflictCollection> 集合的存取權。  此集合會提供每個衝突的詳細資訊 \(對應至失敗的單一更新嘗試\)，其中包含 <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> 集合的存取權。  每個成員衝突都會對應至未通過並行存取檢查之更新中的單一成員。  
  
## 範例  
 下列程式碼會顯示有兩個值的範例。  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## 請參閱  
 [HOW TO：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)   
 [進行和提交資料變更](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)