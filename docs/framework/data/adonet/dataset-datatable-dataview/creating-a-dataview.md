---
title: "建立 DataView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1a8529c317025dbabd9c7467557b244b2f452a77
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="creating-a-dataview"></a>建立 DataView
建立 <xref:System.Data.DataView> 的方法有兩種。 您可以使用**DataView**建構函式，或者您可以建立參考<xref:System.Data.DataTable.DefaultView%2A>屬性<xref:System.Data.DataTable>。 **DataView**建構函式可以是空的或者也可採用任一**DataTable**做為單一引數，或**DataTable**配合篩選準則、 排序準則和資料列狀態篩選器。 如需有關其他引數可用於**DataView**，請參閱[排序及篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)。  
  
 因為索引**DataView**會**DataView**建立時，以及當任一**排序**， **RowFilter**，或**RowStateFilter**修改屬性、 您達到最佳效能提供任何初始排序順序或篩選準則做為建構函式引數，當您建立**DataView**。 建立**DataView**而不指定排序或篩選準則，然後設定**排序**， **RowFilter**，或**RowStateFilter**屬性稍後會導致索引建立至少兩次： 一旦時**DataView**建立時，以及重新排序或篩選屬性的任何會修改。  
  
 請注意，如果您建立**DataView**使用不接受任何引數的建構函式，您將無法使用**DataView**除非您已設定**資料表**屬性.  
  
 下列程式碼範例示範如何建立**DataView**使用**DataView**建構函式。 A **RowFilter**，**排序**資料行，和**DataViewRowState**一併提供**DataTable**。  
  
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
  
 下列程式碼範例示範如何取得預設的參考**DataView**的**DataTable**使用**DefaultView**資料表屬性。  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [排序和篩選資料](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
