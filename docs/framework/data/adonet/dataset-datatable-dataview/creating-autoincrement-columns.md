---
title: 建立自動遞增資料行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 9a979f39003e60c70c03206bd886bdd6827c82e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203718"
---
# <a name="creating-autoincrement-columns"></a>建立自動遞增資料行

若要確保資料行的值是唯一的，您可以在將新資料列加入至資料表時，將資料行值設為自動累加。 若要建立自動遞增 <xref:System.Data.DataColumn> ，請將資料 <xref:System.Data.DataColumn.AutoIncrement%2A> 行的屬性設為 **true**。 <xref:System.Data.DataColumn>接著會以屬性中定義的值開始 <xref:System.Data.DataColumn.AutoIncrementSeed%2A> ，並在每個資料列新增**自動遞增**資料行的值，並以資料行屬性中定義的值增加 <xref:System.Data.DataColumn.AutoIncrementStep%2A> 。  
  
 針對 **自動遞增** 資料行，我們建議將 <xref:System.Data.DataColumn.ReadOnly%2A> **DataColumn** 的屬性設定為 **true**。  
  
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

- <xref:System.Data.DataColumn>
- [DataTable 結構描述定義](datatable-schema-definition.md)
- [DataTables](datatables.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
