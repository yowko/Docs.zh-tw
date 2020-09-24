---
title: 建立運算式資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0af3bd64-92a2-4b47-ae62-f5df35f131a6
ms.openlocfilehash: ad14e4d3d6a1107f994d9536485257f9dc1851f5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166842"
---
# <a name="creating-expression-columns"></a>建立運算式資料行

您可以定義資料行的運算式，使其包含從相同資料列的其他資料行值，或從資料表的多重資料列的資料行值來計算所得的值。 若要定義要評估的運算式，請使用目標資料行的 <xref:System.Data.DataColumn.Expression%2A> 屬性，並使用 <xref:System.Data.DataColumn.ColumnName%2A> 屬性來參照運算式中的其他資料行。 運算式資料行的 <xref:System.Data.DataColumn.DataType%2A> 必須適用於運算式傳回的值。  
  
 下表列出數個資料表的運算式資料行可能使用的方法。  
  
|運算式型別|範例|  
|---------------------|-------------|  
|比較|"Total >= 500"|  
|計算|"UnitPrice * Quantity"|  
|彙總|Sum(Price)|  
  
 您可以在現有的**DataColumn**物件上設定**Expression**屬性，也可以包含屬性做為傳遞給函式的第三個引數 <xref:System.Data.DataColumn> ，如下列範例所示。  
  
```vb  
workTable.Columns.Add("Total",Type.GetType("System.Double"))  
workTable.Columns.Add("SalesTax", Type.GetType("System.Double"), _  
  "Total * 0.086")  
```  
  
```csharp  
workTable.Columns.Add("Total", typeof(Double));  
workTable.Columns.Add("SalesTax", typeof(Double), "Total * 0.086");  
```  
  
 運算式可參考其他運算式資料行；但循環參考 (兩個運算式互相參考) 將產生例外狀況。 如需撰寫運算式的規則，請參閱 <xref:System.Data.DataColumn.Expression%2A> **DataColumn** 類別的屬性。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataTable 結構描述定義](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
