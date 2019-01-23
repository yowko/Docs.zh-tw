---
title: 單一資料表查詢 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
ms.openlocfilehash: 3bde9a5f718dcc7bdf31f84369546d530dca38d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637227"
---
# <a name="single-table-queries-linq-to-dataset"></a>單一資料表查詢 (LINQ to DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] 實作的資料來源上的查詢運作<xref:System.Collections.Generic.IEnumerable%601>介面或<xref:System.Linq.IQueryable%601>介面。 <xref:System.Data.DataTable>類別未實作其中一個介面，因此您必須呼叫<xref:System.Data.DataTableExtensions.AsEnumerable%2A>如果您想要使用的方法<xref:System.Data.DataTable>中的來源`From`子句[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]查詢。  
  
 下列範例會從 SalesOrderHeader 資料表中取得所有線上訂單，並將訂單識別碼、訂單日期和訂單號碼輸出至主控台。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 使用查詢運算式中，一或多個資訊來源上套用一或多個查詢運算子，從標準查詢運算子的操作，或在案例中的初始化區域變數查詢[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]，運算子特有<xref:System.Data.DataSet>類別。 上一個範例中的查詢運算式會使用其中兩個標準查詢運算子：`Where` 與 `Select`。  
  
 在 `Where` 設定為 `OnlineOrderFlag` 的情況中，`true` 子句會根據條件來篩選序列 (Sequence)。 `Select` 運算子會配置並傳回擷取傳遞給運算子之引數的可列舉物件。 在上述範例中，匿名型別是使用三個屬性建立的：`SalesOrderID`、`OrderDate` 和 `SalesOrderNumber`。 這三個屬性的值分別設定為 `SalesOrderID` 資料表中 `OrderDate`、`SalesOrderNumber` 和 `SalesOrderHeader` 資料行的值。  
  
 然後，`foreach` 迴圈 (Loop) 會列舉 `Select` 所傳回的可列舉物件並產生查詢結果。 由於查詢是實作 <xref:System.Linq.Enumerable> 的 <xref:System.Collections.Generic.IEnumerable%601> 型別，因此查詢的評估會延後，直到使用 `foreach` 迴圈來反覆查看查詢變數為止。 延後的查詢評估允許將查詢保留成可多次評估的值，而且每次可能會產生不同的結果。  
  
 <xref:System.Data.DataRowExtensions.Field%2A> 方法可讓您存取 <xref:System.Data.DataRow> 的資料行值而 <xref:System.Data.DataRowExtensions.SetField%2A> (上一個範例中未顯示) 會設定 <xref:System.Data.DataRow> 中的資料行值。 由於 <xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法都會處理可為 Null 的型別 (Nullable Type)，因此您不需要明確檢查是否有 Null 值。 此外，這兩種方法都是泛型方法，表示您不需要轉型傳回型別。 雖然您可以使用 <xref:System.Data.DataRow> 中的現有資料行存取子 (例如 `o["OrderDate"]`)，但是這樣做就必須將傳回物件轉型為適當的型別。  如果資料行可為 Null，您就必須使用 <xref:System.Data.DataRow.IsNull%2A> 方法來檢查其值是否為 Null。 如需詳細資訊，請參閱 <<c0> [ 泛型 Field 和 SetField 方法](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)。  
  
 請注意，`T` 方法和 <xref:System.Data.DataRowExtensions.Field%2A> 方法之泛型參數 <xref:System.Data.DataRowExtensions.SetField%2A> 中指定的資料型別必須與基礎值的型別相符，否則系統將擲回 <xref:System.InvalidCastException>。 此外，指定的資料行名稱也必須與 <xref:System.Data.DataSet> 中的資料行名稱相符，否則系統將擲回 <xref:System.ArgumentException>。 在這兩種情況中，其例外狀況 (Exception) 是在執行查詢的資料列舉執行階段中擲回。  
  
## <a name="see-also"></a>另請參閱
- [跨資料表查詢](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [查詢具類型資料集](../../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [泛型 Field 和 SetField 方法](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
