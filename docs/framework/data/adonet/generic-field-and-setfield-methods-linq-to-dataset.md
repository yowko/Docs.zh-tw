---
title: 泛型 Field 和 SetField 方法 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1883365f-9d6c-4ccb-9187-df309f47706d
ms.openlocfilehash: 1b2c7434543bb2574c59eaec126a621121dd7cef
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504793"
---
# <a name="generic-field-and-setfield-methods-linq-to-dataset"></a>泛型 Field 和 SetField 方法 (LINQ to DataSet)
LINQ to DataSet 提供擴充方法<xref:System.Data.DataRow>類別可用於存取資料行的值：<xref:System.Data.DataRowExtensions.Field%2A>方法和<xref:System.Data.DataRowExtensions.SetField%2A>方法。 這些方法可讓開發人員更容易存取資料行值，尤其是與 Null 值相關的情況。 <xref:System.Data.DataSet>會使用<xref:System.DBNull.Value?displayProperty=nameWithType>來代表 null 值，而[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]會使用<xref:System.Nullable>和<xref:System.Nullable%601>型別。 使用預先存在的資料行存取子中<xref:System.Data.DataRow>需要轉型成適當的類型傳回的物件。 如果中的特定欄位<xref:System.Data.DataRow>可為 null，您必須明確檢查是否有 null 值傳回，因為<xref:System.DBNull.Value?displayProperty=nameWithType>並隱含地將它轉型為另一個型別會擲回<xref:System.InvalidCastException>。 在下列範例中，如果<xref:System.Data.DataRow.IsNull%2A?displayProperty=nameWithType>方法沒有用來檢查是否有 null 值，會擲回例外狀況，是否索引子傳回<xref:System.DBNull.Value?displayProperty=nameWithType>，並嘗試將它轉換成<xref:System.String>。  
  
 [!code-csharp[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#whereisnull)]
 [!code-vb[DP LINQ to DataSet Examples#WhereIsNull](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#whereisnull)]  
  
 <xref:System.Data.DataRowExtensions.Field%2A> 方法可讓您存取 <xref:System.Data.DataRow> 的資料行值而 <xref:System.Data.DataRowExtensions.SetField%2A> 會設定 <xref:System.Data.DataRow> 中的資料行值。 由於 <xref:System.Data.DataRowExtensions.Field%2A> 方法和 <xref:System.Data.DataRowExtensions.SetField%2A> 方法都會處理可為 Null 的型別，因此您不需要明確檢查是否有 Null 值 (如同上一個範例)。 此外，這兩種方法都是泛型方法，所以您不需要轉型傳回型別。  
  
 下列範例使用 <xref:System.Data.DataRowExtensions.Field%2A> 方法。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]  
  
 請注意，`T` 方法和 <xref:System.Data.DataRowExtensions.Field%2A> 方法之泛型參數 <xref:System.Data.DataRowExtensions.SetField%2A> 中指定的資料型別必須與基礎值的型別相符。 否則，系統將擲回 <xref:System.InvalidCastException> 例外狀況。 此外，指定的資料行名稱也必須與 <xref:System.Data.DataSet> 中的資料行名稱相符，否則系統將擲回 <xref:System.ArgumentException>。 在這兩種情況中，其例外狀況是在執行查詢的資料列舉執行階段中擲回。  
  
 <xref:System.Data.DataRowExtensions.SetField%2A> 方法本身不會執行任何型別轉換。 不過，這並不表示不會進行型別轉換。 <xref:System.Data.DataRowExtensions.SetField%2A>方法公開 （expose) 的 ADO.NET 行為<xref:System.Data.DataRow>類別。 無法藉由執行類型轉換<xref:System.Data.DataRow>物件和轉換的值則會儲存到<xref:System.Data.DataRow>物件。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataRowExtensions>
