---
title: "HOW TO：偵測和解決衝突提交 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：偵測和解決衝突提交
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供了許多資源，以便偵測和解決多位使用者變更資料庫所造成的衝突。  如需詳細資訊，請參閱[HOW TO：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)。  
  
## 範例  
 下列範例顯示的 `try`\/`catch` 區塊攔截了 <xref:System.Data.Linq.ChangeConflictException> 例外狀況。  主控台視窗中會顯示每個衝突的實體和成員資訊。  
  
> [!NOTE]
>  您必須納入 `using System.Reflection` 指示詞 \(在 Visual Basic 中為 `Imports System.Reflection`\)，才能支援資訊擷取。  如需詳細資訊，請參閱<xref:System.Reflection>。  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## 請參閱  
 [進行和提交資料變更](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)   
 [HOW TO：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)