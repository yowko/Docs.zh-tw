---
title: 定義主索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 0f87b1b730eecf0edad75bd87ca8b491b96e1d2b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784716"
---
# <a name="defining-primary-keys"></a>定義主索引鍵
資料庫資料表通常會有資料行或資料行群組，可唯一識別資料表的每個資料列。 這個識別欄位或資料行群組又稱為主索引鍵。  
  
 當您<xref:System.Data.DataColumn>將單一識別<xref:System.Data.DataColumn.AllowDBNull%2A> <xref:System.Data.DataTable> <xref:System.Data.DataTable.PrimaryKey%2A>為的時，資料表會自動將資料行的屬性設為**false** ，並<xref:System.Data.DataColumn.Unique%2A>將屬性設定為**true**。 針對多重資料行的主鍵，只有**AllowDBNull**屬性會自動設為**false**。  
  
 的**PrimaryKey**屬性<xref:System.Data.DataTable>會接收一個或多個**DataColumn**物件的陣列值，如下列範例所示。 第一個範例定義單一資料行為主索引鍵。  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 下列範例定義兩個資料行作為主索引鍵。  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataTable>
- [DataTable 結構描述定義](datatable-schema-definition.md)
- [DataTable](datatables.md)
- [ADO.NET 概觀](../ado-net-overview.md)
