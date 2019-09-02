---
title: 建立 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: 391c071f19149e9690c9121b1094aef5bfa605cd
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203835"
---
# <a name="creating-a-dataview"></a>建立 DataView
建立 <xref:System.Data.DataView> 的方法有兩種。 您可以使用**DataView**函式, 也可以建立的<xref:System.Data.DataTable.DefaultView%2A>屬性<xref:System.Data.DataTable>參考。 **DataView**函式可以是空的, 或者可以接受**datatable**做為單一引數, 或將 datatable當做篩選準則、排序準則和資料列狀態篩選。 如需可搭配**DataView**使用之其他引數的詳細資訊, 請參閱[排序和篩選資料](sorting-and-filtering-data.md)。  
  
 由於建立**dataview**時, 會同時建立**dataview**的索引, 而且在修改任何**Sort**、 **RowFilter**或**RowStateFilter**屬性時, 您可以藉由提供任何初始的來達到最佳效能。當您建立**DataView**時, 排序次序或篩選準則做為函式引數。 建立**dataview**而不指定排序或篩選準則, 然後設定**sort**、 **RowFilter**或**RowStateFilter**屬性之後, 會導致索引至少建立兩次: 一次在**DataView**為會在修改任何排序或篩選屬性時再次建立。  
  
 請注意, 如果您使用不接受任何引數的函式來建立**dataview** , 在設定**資料表**屬性之前, 您將無法使用**dataview** 。  
  
 下列程式碼範例示範如何使用**dataview**函式建立**dataview** 。 **RowFilter**、 **Sort**資料行和**DataViewRowState**會連同**DataTable**一起提供。  
  
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
  
 下列程式碼範例示範如何使用資料表的**DefaultView**屬性, 取得**DataTable**之預設**DataView**的參考。  
  
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
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
