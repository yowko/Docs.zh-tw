---
title: 泛型 Field 和 SetField 方法 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: d7ddee775e91c6be6166a091997afd58113cfe6b
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249099"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>泛型 Field 和 SetField 方法 (LINQ to DataSet)
LINQ 到 DataSet 為<xref:System.Data.DataRow>類提供用於訪問列值的擴充方法<xref:System.Data.DataRowExtensions.Field%2A>：方法和方法<xref:System.Data.DataRowExtensions.SetField%2A>。 這些方法可讓開發人員更容易存取資料行值，尤其是與 Null 值相關的情況。 <xref:System.Data.DataSet>用於<xref:System.DBNull.Value?displayProperty=nameWithType>表示空值，而 LINQ 使用<xref:System.Nullable>和<xref:System.Nullable%601>類型。 在 中使用 中<xref:System.Data.DataRow>預先存在的列訪問器需要將返回物件轉換為適當的類型。 如果 中<xref:System.Data.DataRow>的特定欄位可以為空，則必須顯式檢查 null 值，因為返回<xref:System.DBNull.Value?displayProperty=nameWithType>並隱式將其強制轉換到另一個類型將引發<xref:System.InvalidCastException>。 在下面的示例中，<xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType>如果該方法未用於檢查 null 值，則如果索引子返回<xref:System.DBNull.Value?displayProperty=nameWithType>並嘗試將其強制轉換為 ，<xref:System.String>則將引發異常。  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> 方法可讓您存取 <xref:System.Data.DataRow> 的資料行值而 <xref:System.Data.DataRowExtensions.SetField%2A> 會設定 <xref:System.Data.DataRow> 中的資料行值。 <xref:System.Data.DataRowExtensions.Field%2A>該方法和方法<xref:System.Data.DataRowExtensions.SetField%2A>都處理空數值型別，因此不必像前面的示例中那樣顯式檢查空值。 此外，這兩種方法都是泛型方法，所以您不需要轉型傳回型別。  
  
 下列範例使用 <xref:System.Data.DataRowExtensions.Field%2A> 方法。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 請注意，`T` 方法和 <xref:System.Data.DataRowExtensions.Field%2A> 方法之泛型參數 <xref:System.Data.DataRowExtensions.SetField%2A> 中指定的資料型別必須與基礎值的型別相符。 否則，系統將擲回 <xref:System.InvalidCastException> 例外狀況。 此外，指定的資料行名稱也必須與 <xref:System.Data.DataSet> 中的資料行名稱相符，否則系統將擲回 <xref:System.ArgumentException>。 在這兩種情況中，其例外狀況是在執行查詢的資料列舉執行階段中擲回。  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> 方法本身不會執行任何型別轉換。 不過，這並不表示不會進行型別轉換。 該方法<xref:System.Data.DataRowExtensions.SetField%2A>公開類ADO.NET行為<xref:System.Data.DataRow>。 <xref:System.Data.DataRow>類型轉換可以由物件執行，然後轉換的值將保存到<xref:System.Data.DataRow>物件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataRowExtensions>
