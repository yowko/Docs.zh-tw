---
title: "HOW TO：指定要測試哪些成員是否發生並行衝突 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：指定要測試哪些成員是否發生並行衝突
將三個列舉的其中一個套用至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\) 上的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 \(Property\)，指定要併入更新檢查以偵測開放式並行存取 \(Optimistic Concurrency\) 衝突的成員。  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 \(在設計階段對應\) 是與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的執行階段並行存取功能搭配使用。  如需詳細資訊，請參閱[開放式並行存取概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。  
  
> [!NOTE]
>  只要未將成員指定為 `IsVersion=true`，原始成員值就會與目前資料庫狀態進行比較。  如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。  
  
 如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。  
  
### 若一律要使用這個成員來偵測衝突  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 \(Property\) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 \(Property\) 值設定為 `Always`。  
  
### 若永不使用這個成員來偵測衝突  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 \(Property\) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 \(Property\) 值設定為 `Never`。  
  
### 若只有在應用程式已變更成員的值時，才使用這個成員來偵測衝突  
  
1.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 \(Property\) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 \(Attribute\)。  
  
2.  將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 \(Property\) 值設定為 `WhenChanged`。  
  
## 範例  
 下列範例指定 `HomePage` 物件永遠不應該在更新檢查期間進行測試。  如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## 請參閱  
 [HOW TO：管理變更衝突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)   
 [進行和提交資料變更](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)