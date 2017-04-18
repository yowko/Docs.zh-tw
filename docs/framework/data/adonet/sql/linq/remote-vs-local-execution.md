---
title: "遠端和本機執行的比較 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 遠端和本機執行的比較
您可以決定執行查詢的方式為遠端 \(也就是，資料庫引擎對資料庫執行查詢\) 或本機 \([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 對本機快取執行查詢\)。  
  
## 遠端執行  
 請考慮下列查詢：  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 如果資料庫有數千列訂單，當您只要處理一小部分的訂單時，您不會想要擷取出所有訂單。  在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，<xref:System.Data.Linq.EntitySet%601> 類別 \(Class\) 會實作 <xref:System.Linq.IQueryable> 介面。  這種方法可以確認這類查詢可以遠端執行。  這項技術的兩個主要優點是：  
  
-   不會擷取不必要的資料。  
  
-   因為利用資料庫索引，所以資料庫引擎執行的查詢通常會較具效率。  
  
## 本機執行的比較  
 在其他情況下，您可能會想要擁有本機快取中的完整一組相關實體 \(Entity\)。  因此，<xref:System.Data.Linq.EntitySet%601> 提供 <xref:System.Data.Linq.EntitySet%601.Load%2A> 方法，可以明確載入 <xref:System.Data.Linq.EntitySet%601> 的所有成員。  
  
 如果已載入 <xref:System.Data.Linq.EntitySet%601>，則會在本機執行後續查詢。  這種方法有兩項優點：  
  
-   如果必須在本機或多次使用完整集合，則可以避免遠端查詢和相關的延遲時間。  
  
-   實體可以序列化為完整實體。  
  
 下列程式碼片段說明如何取得本機執行：  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## 比較  
 這兩個功能可提供強大的選項組合：遠端執行適用於大型集合，而本機執行則適用於小型集合或需要完整集合之處。  您可以透過 <xref:System.Linq.IQueryable> 實作遠端執行，而本機執行則是根據記憶體中 <xref:System.Collections.Generic.IEnumerable%601> 集合來實作。  若要強制使用本機執行 \(即 <xref:System.Collections.Generic.IEnumerable%601>\)，請參閱 [將型別轉換為泛型 IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)。  
  
### 對未排序集合進行查詢  
 請注意下列兩者之間的重要差異：實作 <xref:System.Collections.Generic.List%601> 的本機集合，以及可針對關聯式資料庫中「*未排序集合*」\(Unordered Set\) 執行遠端查詢的集合。  <xref:System.Collections.Generic.List%601> 方法 \(如使用索引值的方法\) 需要清單語意 \(Semantics\)，而這一般無法透過對未排序集合的遠端查詢來取得。  因此，這類方法會隱含地載入 <xref:System.Data.Linq.EntitySet%601>，以允許進行本機執行。  
  
## 請參閱  
 [查詢概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)