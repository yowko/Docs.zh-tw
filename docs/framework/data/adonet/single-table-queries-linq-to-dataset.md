---
title: 單一資料表查詢 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 17a2fcf54cae64d9443b0cc0e8a37e1002bbd394
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175352"
---
# <a name="single-table-queries-linq-to-dataset"></a>單一資料表查詢 (LINQ to DataSet)

 (LINQ) 查詢的語言整合式查詢適用于執行 <xref:System.Collections.Generic.IEnumerable%601> 介面或介面的資料來源 <xref:System.Linq.IQueryable%601> 。 <xref:System.Data.DataTable>類別不會執行任何一個介面，因此， <xref:System.Data.DataTableExtensions.AsEnumerable%2A> 如果您想要在 <xref:System.Data.DataTable> LINQ 查詢的子句中使用做為來源，則必須呼叫方法 `From` 。  
  
 下列範例會從 SalesOrderHeader 資料表中取得所有線上訂單，並將訂單識別碼、訂單日期和訂單號碼輸出至主控台。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
 區域變數查詢會以查詢運算式初始化，此查詢運算式會套用標準查詢運算子中的一或多個查詢運算子，或在 LINQ to DataSet 的情況下，針對類別專屬的運算子來操作一或多個資訊來源 <xref:System.Data.DataSet> 。 上一個範例中的查詢運算式會使用其中兩個標準查詢運算子：`Where` 與 `Select`。  
  
 在 `Where` 設定為 `OnlineOrderFlag` 的情況中，`true` 子句會根據條件來篩選序列 (Sequence)。 `Select` 運算子會配置並傳回擷取傳遞給運算子之引數的可列舉物件。 在上述範例中，匿名型別是使用三個屬性建立的：`SalesOrderID`、`OrderDate` 和 `SalesOrderNumber`。 這三個屬性的值分別設定為 `SalesOrderID` 資料表中 `OrderDate`、`SalesOrderNumber` 和 `SalesOrderHeader` 資料行的值。  
  
 然後，`foreach` 迴圈 (Loop) 會列舉 `Select` 所傳回的可列舉物件並產生查詢結果。 由於查詢是實作 <xref:System.Linq.Enumerable> 的 <xref:System.Collections.Generic.IEnumerable%601> 型別，因此查詢的評估會延後，直到使用 `foreach` 迴圈來反覆查看查詢變數為止。 延後的查詢評估允許將查詢保留成可多次評估的值，而且每次可能會產生不同的結果。  
  
 <xref:System.Data.DataRowExtensions.Field%2A> 方法可讓您存取 <xref:System.Data.DataRow> 的資料行值而 <xref:System.Data.DataRowExtensions.SetField%2A> (上一個範例中未顯示) 會設定 <xref:System.Data.DataRow> 中的資料行值。 <xref:System.Data.DataRowExtensions.Field%2A>方法和方法都會 <xref:System.Data.DataRowExtensions.SetField%2A> 處理可為 null 的實值型別，因此您不需要明確檢查是否有 null 值。 此外，這兩種方法都是泛型方法，表示您不需要轉型傳回型別。 雖然您可以使用 <xref:System.Data.DataRow> 中的現有資料行存取子 (例如 `o["OrderDate"]`)，但是這樣做就必須將傳回物件轉型為適當的型別。  如果資料行是可為 null 的實值型別，您必須使用方法來檢查值是否為 null <xref:System.Data.DataRow.IsNull%2A> 。 如需詳細資訊，請參閱 [泛型 Field 和 SetField 方法](generic-field-and-setfield-methods-linq-to-dataset.md)。  
  
 請注意，`T` 方法和 <xref:System.Data.DataRowExtensions.Field%2A> 方法之泛型參數 <xref:System.Data.DataRowExtensions.SetField%2A> 中指定的資料型別必須與基礎值的型別相符，否則系統將擲回 <xref:System.InvalidCastException>。 此外，指定的資料行名稱也必須與 <xref:System.Data.DataSet> 中的資料行名稱相符，否則系統將擲回 <xref:System.ArgumentException>。 在這兩種情況中，其例外狀況 (Exception) 是在執行查詢的資料列舉執行階段中擲回。  
  
## <a name="see-also"></a>另請參閱

- [跨資料表查詢](cross-table-queries-linq-to-dataset.md)
- [查詢具類型資料集](querying-typed-datasets.md)
- [泛型 Field 和 SetField 方法](generic-field-and-setfield-methods-linq-to-dataset.md)
