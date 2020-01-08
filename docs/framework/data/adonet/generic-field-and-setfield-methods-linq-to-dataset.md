---
title: 泛型 Field 和 SetField 方法 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 310eb3ccecc3159234ed362ed044be7ad704dde4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634829"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>泛型 Field 和 SetField 方法 (LINQ to DataSet)
LINQ to DataSet 提供 <xref:System.Data.DataRow> 類別的擴充方法來存取資料行值： <xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法。 這些方法可讓開發人員更容易存取資料行值，尤其是與 Null 值相關的情況。 <xref:System.Data.DataSet> 使用 <xref:System.DBNull.Value?displayProperty=nameWithType> 來代表 null 值，而 LINQ 則使用 <xref:System.Nullable> 和 <xref:System.Nullable%601> 類型。 在 <xref:System.Data.DataRow> 中使用既有的資料行存取子，您必須將傳回物件轉換成適當的類型。 如果 <xref:System.Data.DataRow> 中的特定欄位可以是 null，您就必須明確檢查是否有 null 值，因為傳回 <xref:System.DBNull.Value?displayProperty=nameWithType>，並將它隱含地轉換成另一個類型，會擲回 <xref:System.InvalidCastException>。 在下列範例中，如果未使用 <xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType> 方法來檢查是否有 null 值，當索引子傳回 <xref:System.DBNull.Value?displayProperty=nameWithType> 並嘗試將它轉換成 <xref:System.String>時，就會擲回例外狀況（exception）。  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> 方法可讓您存取 <xref:System.Data.DataRow> 的資料行值而 <xref:System.Data.DataRowExtensions.SetField%2A> 會設定 <xref:System.Data.DataRow> 中的資料行值。 由於 <xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法都會處理可為 Null 的型別，因此您不需要明確檢查是否有 Null 值 (如同上一個範例)。 此外，這兩種方法都是泛型方法，所以您不需要轉型傳回型別。  
  
 下列範例使用 <xref:System.Data.DataRowExtensions.Field%2A> 方法。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 請注意，`T` 方法和 <xref:System.Data.DataRowExtensions.Field%2A> 方法之泛型參數 <xref:System.Data.DataRowExtensions.SetField%2A> 中指定的資料型別必須與基礎值的型別相符。 否則，系統將擲回 <xref:System.InvalidCastException> 例外狀況。 此外，指定的資料行名稱也必須與 <xref:System.Data.DataSet> 中的資料行名稱相符，否則系統將擲回 <xref:System.ArgumentException>。 在這兩種情況中，其例外狀況是在執行查詢的資料列舉執行階段中擲回。  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> 方法本身不會執行任何型別轉換。 不過，這並不表示不會進行型別轉換。 <xref:System.Data.DataRowExtensions.SetField%2A> 方法會公開 <xref:System.Data.DataRow> 類別的 ADO.NET 行為。 <xref:System.Data.DataRow> 物件可以執行類型轉換，然後轉換後的值會儲存到 <xref:System.Data.DataRow> 物件中。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Data.DataRowExtensions>
