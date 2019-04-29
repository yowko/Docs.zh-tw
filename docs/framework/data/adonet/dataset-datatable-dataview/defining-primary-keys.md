---
title: 定義主索引鍵
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 84c84cb8fc0ee484b09c69c72571a19c335b58f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607306"
---
# <a name="defining-primary-keys"></a>定義主索引鍵
資料庫資料表通常會有資料行或資料行群組，可唯一識別資料表的每個資料列。 這個識別欄位或資料行群組又稱為主索引鍵。  
  
 當您找出單一<xref:System.Data.DataColumn>做為<xref:System.Data.DataTable.PrimaryKey%2A>如<xref:System.Data.DataTable>，資料表會自動設定<xref:System.Data.DataColumn.AllowDBNull%2A>的資料行的屬性**false**和<xref:System.Data.DataColumn.Unique%2A>屬性設**true**。 針對多個資料行主要金鑰時，只有**AllowDBNull**屬性會自動設為**false**。  
  
 **PrimaryKey**屬性<xref:System.Data.DataTable>做為其值會接收一或多個陣列**DataColumn**物件，如下列範例所示。 第一個範例定義單一資料行為主索引鍵。  
  
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
- [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
