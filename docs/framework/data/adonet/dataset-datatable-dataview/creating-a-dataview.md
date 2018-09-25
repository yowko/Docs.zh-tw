---
title: 建立 DataView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: b88df66ef2e065d1db8d4033eb1fb0e47ebdd189
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108711"
---
# <a name="creating-a-dataview"></a>建立 DataView
建立 <xref:System.Data.DataView> 的方法有兩種。 您可以使用**DataView**建構函式，或者您可以建立參考<xref:System.Data.DataTable.DefaultView%2A>屬性<xref:System.Data.DataTable>。 **DataView**建構函式可以是空的或者也可採用任一**DataTable**做為單一引數，或有**DataTable**篩選準則、 排序條件及一個資料列狀態篩選器。 如需有關其他引數可用以搭配**DataView**，請參閱[排序及篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)。  
  
 因為索引**DataView**會**DataView**建立時，以及當任一**排序**， **RowFilter**，或**RowStateFilter**屬性會經過修改，即可藉由提供任何初始排序順序或篩選準則做為建構函式引數，當您建立時達到最佳效能**DataView**。 建立**DataView**而不指定排序或篩選準則，然後設定**排序**， **RowFilter**，或**RowStateFilter**屬性稍後會導致至少兩次建立索引： 一旦時**DataView**建立時，並一次的任何排序或篩選屬性修改時。  
  
 請注意，如果您建立**DataView**使用未採用任何引數的建構函式，您將無法再使用**DataView**除非您已設定**表格**屬性.  
  
 下列程式碼範例示範如何建立**DataView**使用**DataView**建構函式。 A **RowFilter**，**排序**資料行，並**DataViewRowState**提供**DataTable**。  
  
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
  
 下列程式碼範例示範如何取得預設值的參考**DataView**的**DataTable**使用**DefaultView**資料表屬性。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [排序和篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
