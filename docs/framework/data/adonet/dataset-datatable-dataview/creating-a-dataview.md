---
title: 建立 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 9d21b17068ff3ce5b0bd3990144383d7f9ded2f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151334"
---
# <a name="creating-a-dataview"></a>建立 DataView
建立 <xref:System.Data.DataView> 的方法有兩種。 您可以使用**DataView**建構函式，也可以創建對<xref:System.Data.DataTable.DefaultView%2A>屬性<xref:System.Data.DataTable>的引用。 **DataView**建構函式可以是空的，也可以將**DataTable**作為單個參數，也可以將 DataTable 以及篩選器條件、排序條件和行狀態篩選器視為 **"DataTable"。** 有關可用於**DataView**的其他參數的詳細資訊，請參閱[排序和篩選資料](sorting-and-filtering-data.md)。  
  
 由於**DataView**的索引是在創建**DataView**時構建的，並且當修改任何**排序**、**行篩選器**或**RowStateFilter**屬性時，在創建**DataView**時，通過提供任何初始排序次序或篩選準則作為建構函式參數來實現最佳性能。 創建**DataView**而不指定排序或篩選準則，然後設置**排序**、**行篩選器**或**RowStateFilter**屬性，以後會導致索引至少生成兩次：創建**DataView**時生成一次，在修改任何排序或篩選器屬性時再次生成索引。  
  
 請注意，如果使用不採用任何參數的建構函式創建**DataView，** 則在設置**表**屬性之前，您將無法使用**DataView。**  
  
 以下代碼示例演示如何使用**DataView**建構函式創建**DataView。** 隨**資料表**一起提供**行篩選器**、**排序**列和**DataViewRowState。**  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],
    "Country = 'USA'",
    "ContactName",
    DataViewRowState.CurrentRows);  
```  
  
 以下代碼示例演示如何使用表的**DefaultView**屬性獲取對**DataTable**的預設**DataView**的引用。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataView](dataviews.md)
- [排序和篩選資料](sorting-and-filtering-data.md)
- [DataTable](datatables.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
