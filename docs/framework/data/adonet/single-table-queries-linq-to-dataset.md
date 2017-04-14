---
title: "單一資料表查詢 (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 單一資料表查詢 (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 查詢會在實作 <xref:System.Collections.Generic.IEnumerable%601> 介面或 <xref:System.Query.IQueryable%601> 介面的資料來源上運作。  由於 <xref:System.Data.DataTable> 類別 \(Class\) 不會實作任何一種介面，因此如果您想要在 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 查詢的 `From` 子句中使用 <xref:System.Data.DataTable> 當做來源，就必須呼叫 <xref:System.Data.DataTableExtensions.AsEnumerable%2A> 方法。  
  
 下列範例會從 SalesOrderHeader 資料表中取得所有線上訂單，並將訂單識別碼、訂單日期和訂單號碼輸出至主控台。  
  
 [!code-csharp[dp linq to dataset examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]
 [!code-vb[dp linq to dataset examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]  
  
 區域變數查詢是以查詢運算式初始化，而此運算式會透過套用標準查詢運算子或 \(在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 的情況中\) <xref:System.Data.DataSet> 類別專用之運算子中的一個或多個查詢運算子，在一個或多個資訊來源上運作。  上一個範例中的查詢運算式會使用其中兩個標準查詢運算子：`Where` 與 `Select`。  
  
 在 `OnlineOrderFlag` 設定為 `true` 的情況中，`Where` 子句會根據條件來篩選序列 \(Sequence\)。  `Select` 運算子會配置並傳回擷取傳遞給運算子之引數的可列舉物件。  在上述範例中，匿名型別是使用三個屬性建立的：`SalesOrderID`、`OrderDate` 和 `SalesOrderNumber`。  這三個屬性的值分別設定為 `SalesOrderHeader` 資料表中 `SalesOrderID`、`OrderDate` 和 `SalesOrderNumber` 資料行的值。  
  
 然後，`foreach` 迴圈 \(Loop\) 會列舉 `Select` 所傳回的可列舉物件並產生查詢結果。  由於查詢是實作 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Linq.Enumerable> 型別，因此查詢的評估會延後，直到使用 `foreach` 迴圈來反覆查看查詢變數為止。  延後的查詢評估允許將查詢保留成可多次評估的值，而且每次可能會產生不同的結果。  
  
 <xref:System.Data.DataRowExtensions.Field%2A> 方法可讓您存取 <xref:System.Data.DataRow> 的資料行值而 <xref:System.Data.DataRowExtensions.SetField%2A> \(上一個範例中未顯示\) 會設定 <xref:System.Data.DataRow> 中的資料行值。  由於 <xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法都會處理可為 Null 的型別 \(Nullable Type\)，因此您不需要明確檢查是否有 Null 值。  此外，這兩種方法都是泛型方法，表示您不需要轉型傳回型別。  雖然您可以使用 <xref:System.Data.DataRow> 中的現有資料行存取子 \(例如 `o["OrderDate"]`\)，但是這樣做就必須將傳回物件轉型為適當的型別。  如果資料行可為 Null，您就必須使用 <xref:System.Data.DataRow.IsNull%2A> 方法來檢查其值是否為 Null。  如需詳細資訊，請參閱[泛型 Field 和 SetField 方法](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)。  
  
 請注意，<xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法之泛型參數 `T` 中指定的資料型別必須與基礎值的型別相符，否則系統將擲回 <xref:System.InvalidCastException>。  此外，指定的資料行名稱也必須與 <xref:System.Data.DataSet> 中的資料行名稱相符，否則系統將擲回 <xref:System.ArgumentException>。  在這兩種情況中，其例外狀況 \(Exception\) 是在執行查詢的資料列舉執行階段中擲回。  
  
## 請參閱  
 [跨資料表查詢](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)   
 [查詢具型別 DataSet](../../../../docs/framework/data/adonet/querying-typed-datasets.md)   
 [泛型 Field 和 SetField 方法](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)