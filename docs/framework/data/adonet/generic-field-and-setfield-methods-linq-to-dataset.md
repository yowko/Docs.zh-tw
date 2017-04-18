---
title: "泛型 Field 和 SetField 方法 (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 泛型 Field 和 SetField 方法 (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 會提供擴充方法給 <xref:System.Data.DataRow> 類別 \(Class\)，以便存取資料行值：<xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法。這些方法可讓開發人員更容易存取資料行值，尤其是與 Null 值相關的情況。<xref:System.Data.DataSet> 會使用 <xref:System.DBNull.Value> 來代表 Null 值，而 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 則會使用 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] 中引進的可為 Null 的型別 \(Nullable Type\) 支援。  如果使用 <xref:System.Data.DataRow> 中的現有資料行存取子，您就必須將傳回物件轉型為適當的型別。  如果 <xref:System.Data.DataRow> 中的特定欄位可為 Null，您就必須明確檢查是否有 Null 值，因為傳回 <xref:System.DBNull.Value> 並將它隱含轉型為其他型別會擲回 <xref:System.InvalidCastException>。  在下列範例中，如果 <xref:System.Data.DataRow.IsNull%2A> 方法沒有用來檢查是否有 Null 值，而且索引子 \(Indexer\) 傳回了 <xref:System.DBNull.Value> 並嘗試將它轉型為 <xref:System.String>，系統就會擲回例外狀況 \(Exception\)。  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> 方法可讓您存取 <xref:System.Data.DataRow> 的資料行值而 <xref:System.Data.DataRowExtensions.SetField%2A> 會設定 <xref:System.Data.DataRow> 中的資料行值。  由於 <xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法都會處理可為 Null 的型別，因此您不需要明確檢查是否有 Null 值 \(如同上一個範例\)。  此外，這兩種方法都是泛型方法，所以您不需要轉型傳回型別。  
  
 下列範例使用 <xref:System.Data.DataRowExtensions.Field%2A> 方法。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 請注意，<xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法之泛型參數 `T` 中指定的資料型別必須與基礎值的型別相符。  否則，系統將擲回 <xref:System.InvalidCastException> 例外狀況。  此外，指定的資料行名稱也必須與 <xref:System.Data.DataSet> 中的資料行名稱相符，否則系統將擲回 <xref:System.ArgumentException>。  在這兩種情況中，其例外狀況是在執行查詢的資料列舉執行階段中擲回。  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> 方法本身不會執行任何型別轉換。  不過，這並不表示不會進行型別轉換。  <xref:System.Data.DataRowExtensions.SetField%2A> 方法會公開 \(Expose\) <xref:System.Data.DataRow> 類別的 [!INCLUDE[ado_whidbey_long](../../../../includes/ado-whidbey-long-md.md)] 行為。  <xref:System.Data.DataRow> 物件可以執行型別轉換，然後再將轉換的值儲存至 <xref:System.Data.DataRow> 物件。  
  
## 請參閱  
 <xref:System.Data.DataRowExtensions>