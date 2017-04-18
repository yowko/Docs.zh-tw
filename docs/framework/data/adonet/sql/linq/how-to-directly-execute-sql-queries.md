---
title: "HOW TO：直接執行 SQL 查詢 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：直接執行 SQL 查詢
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您撰寫的查詢轉譯為參數型 SQL 查詢 \(文字格式\)，並將它們傳送給 SQL Server 進行處理。  
  
 SQL 無法執行您應用程式可以在本機使用的各種方法。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會嘗試將這些本機方法轉換為可以在 SQL 環境內進行的對等作業和函式。  [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 內建型別的大部分方法和運算子都可以直接轉譯為 SQL 命令。  而有些方法和運算則可以透過可用的函式產生。  無法產生的部分則會產生執行階段例外狀況。  如需詳細資訊，請參閱[SQL\-CLR 型別對應](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)。  
  
 如果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查詢不足以進行特殊化工作，則可以使用 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法執行 SQL 查詢，然後將查詢結果直接轉換為物件。  
  
## 範例  
 在下列範例中，假設 `Customer` 類別的資料分佈於兩張資料表 \(customer1 和 customer2\)。  這個查詢會傳回 `Customer` 物件的序列。  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 只要表格式結果中的資料行名稱符合實體 \(Entity\) 類別的資料行屬性，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 就會從任何 SQL 查詢建立物件。  
  
## 範例  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> 方法也允許使用參數。  使用下列程式碼，就可以執行參數型查詢。  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 查詢文字中的參數使用與 `Console.WriteLine()` 和 `String.Format()` 所用的相同大括號標記法來表示。  實際上，`String.Format()` 是在提供的查詢字串上進行實際呼叫，但是會將大括號參數取代為所產生的參數名稱 \(如 @p0、@p1 …、@p\(n\)\)。  
  
## 請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)   
 [查詢資料庫](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)