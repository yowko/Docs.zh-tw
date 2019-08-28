---
title: 將資料行加入至 DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 77bf117b8835623d768f8b8b0ec3e4195174cad7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043954"
---
# <a name="adding-columns-to-a-datatable"></a>將資料行加入至 DataTable
包含資料表的 Columns 屬性<xref:System.Data.DataColumn>所參考之物件的集合。 <xref:System.Data.DataTable> 這個資料行集合 (可搭配任何條件約束) 可定義資料表的結構描述 (或結構)。  
  
 您可以使用**datacolumn**的函式, 或呼叫資料表之**Columns**屬性的<xref:System.Data.DataColumnCollection> **Add**方法 (也就是), 在資料表中建立**DataColumn**物件。 **Add**方法會接受選擇性的**ColumnName**、 **DataType**和**Expression**引數, 並建立新的**DataColumn**做為集合的成員。 它也可接受現有的**datacolumn**物件, 並將它新增至集合, 並在要求時, 傳回已新增之**DataColumn**的參考。 因為**DataTable**物件不是任何資料來源特有, 所以在指定**DataColumn**的資料類型時, 會使用 .NET Framework 類型。  
  
 下列範例會將四個數據行加入至**DataTable**。  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 在此範例中, 請注意, **CustID**資料行的屬性會設定為不允許**DBNull**值, 並將值限制為唯一。 不過, 如果您將**CustID**資料行定義為數據表的主鍵資料行, 則**AllowDBNull**屬性會自動設為**false** , 而**Unique**屬性會自動設定為**true**。 如需詳細資訊, 請參閱[定義主要索引鍵](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
> [!CAUTION]
> 如果未提供資料行的資料行名稱, 則在將資料行新增至**DataColumnCollection**時, 會為數據行指定遞增的預設名稱 *(* 從 "Column1" 開始)。 當您提供資料行名稱時, 建議您避免「資料行*N*」的命名慣例, 因為您所提供的名稱可能會與**DataColumnCollection**中現有的預設資料行名稱相衝突。 如果提供的名稱已經存在，便會發生例外狀況。  
  
 如果您要使用 <xref:System.Xml.Linq.XElement> 當做 <xref:System.Data.DataColumn.DataType%2A> 中 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataTable>，當您讀入資料時，XML 序列化將無法運作。 例如，如果您使用 <xref:System.Xml.XmlDocument> 方法來寫出 `DataTable.WriteXml`，在序列化至 XML 時，<xref:System.Xml.Linq.XElement> 就會存在額外的父節點。 若要解決此問題，請使用 <xref:System.Data.SqlTypes.SqlXml> 型別而非 <xref:System.Xml.Linq.XElement>。 `ReadXml` 和 `WriteXml` 會搭配 <xref:System.Data.SqlTypes.SqlXml> 正確運作。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
