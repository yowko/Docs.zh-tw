---
title: 建立 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 539e9763c8aa4affdb6f3bd219a99dbca50cee01
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202339"
---
# <a name="creating-a-dataview"></a>建立 DataView

建立 <xref:System.Data.DataView> 的方法有兩種。 您可以使用 **DataView** 的函式，也可以建立的 <xref:System.Data.DataTable.DefaultView%2A> 屬性參考 <xref:System.Data.DataTable> 。 **DataView**函式可以是空的，也可以採用**datatable**做為單一引數，或採用**datatable**以及篩選準則、排序準則和資料列狀態篩選。 如需可搭配 **DataView**使用之額外引數的詳細資訊，請參閱 [排序和篩選資料](sorting-and-filtering-data.md)。  
  
 由於 dataview 建立時， **會建立** **dataview 的** 索引，而且在修改任何 **Sort**、 **RowFilter**或 **RowStateFilter** 屬性時，您可以在建立 **dataview**時提供任何初始排序次序或篩選準則做為函式引數，以達到最佳效能。 如果建立 **dataview** 而不指定排序或篩選準則，然後設定 **sort**、 **RowFilter**或 **RowStateFilter** 屬性，則會導致至少建立索引兩次：一次建立 **dataview** 時，以及在修改任何排序或篩選屬性時。  
  
 請注意，如果您使用不採用任何引數的函式來建立 **DataView** ，您將無法使用 **DataView** ，除非您已設定 **Table** 屬性。  
  
 下列程式碼範例示範如何使用**dataview**函式來建立**dataview** 。 **RowFilter**、 **Sort**資料行和**DataViewRowState**會隨著**DataTable**提供。  
  
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
  
 下列程式碼範例示範如何使用資料表的**DefaultView**屬性，取得**DataTable**預設**DataView**的參考。  
  
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
- [排序及篩選資料](sorting-and-filtering-data.md)
- [DataTables](datatables.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
