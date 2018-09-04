---
title: 建立自動遞增資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 9c6b5393e1928828bca001ba1d2336f09e64c22c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536611"
---
# <a name="creating-autoincrement-columns"></a>建立自動遞增資料行
若要確保資料行的值是唯一的，您可以在將新資料列加入至資料表時，將資料行值設為自動累加。 若要建立自動遞增<xref:System.Data.DataColumn>，將<xref:System.Data.DataColumn.AutoIncrement%2A>屬性的資料行 **，則為 true**。 <xref:System.Data.DataColumn>開頭中定義的值，然後<xref:System.Data.DataColumn.AutoIncrementSeed%2A>屬性，加入每個資料列的值**AutoIncrement**資料行中定義的值會增加<xref:System.Data.DataColumn.AutoIncrementStep%2A>資料行屬性。  
  
 針對**AutoIncrement**資料行，我們建議<xref:System.Data.DataColumn.ReadOnly%2A>屬性**DataColumn**設為**true**。  
  
 下列範例示範如何建立以 200 值做為開頭的資料行，並以增量 3 累加。  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Data.DataColumn>  
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
