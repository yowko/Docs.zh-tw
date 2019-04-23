---
title: 將資料行加入至 DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
ms.openlocfilehash: 2e7008f6693d7d76520a7ff6ae9172e28e4990c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207002"
---
# <a name="adding-columns-to-a-datatable"></a>將資料行加入至 DataTable
A<xref:System.Data.DataTable>包含的集合<xref:System.Data.DataColumn>所參考的物件**資料行**資料表屬性。 這個資料行集合 (可搭配任何條件約束) 可定義資料表的結構描述 (或結構)。  
  
 您建立**DataColumn**使用資料表中的物件**DataColumn**建構函式，或藉由呼叫**新增**方法**資料行**資料表，也就是屬性<xref:System.Data.DataColumnCollection>。 **新增**方法會接受選擇性**ColumnName**， **DataType**，並**運算式**引數，並建立新**DataColumn**為集合的成員。 它也會接受現有**DataColumn**物件，並將它加入至集合中，並傳回的參考加入**DataColumn**如果要求。 因為**DataTable**物件並非特定用於任何資料來源、 指定的資料類型時，會使用.NET Framework 型別**DataColumn**。  
  
 下列範例會將四個資料行**DataTable**。  
  
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
  
 在範例中，請注意，屬性**CustID**資料行設定為不允許**DBNull**值並限制為唯一的值。 不過，如果您定義**CustID**資料行做為資料表的主索引鍵資料行**AllowDBNull**屬性會自動設為**false**和**Unique**屬性會自動設為 **，則為 true**。 如需詳細資訊，請參閱 <<c0> [ 定義主索引鍵](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
> [!CAUTION]
>  如果資料行名稱未提供資料行中，指定資料行的資料行的遞增預設名稱*N* "Column1"從開始，當它加入**DataColumnCollection**。 我們建議您避免命名慣例 」 資料行*N*「 當您提供的資料行名稱，因為您提供的名稱可能會與在現有的預設資料行名稱衝突**DataColumnCollection**。 如果提供的名稱已經存在，便會發生例外狀況。  
  
 如果您要使用 <xref:System.Xml.Linq.XElement> 當做 <xref:System.Data.DataColumn.DataType%2A> 中 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataTable>，當您讀入資料時，XML 序列化將無法運作。 例如，如果您使用 <xref:System.Xml.XmlDocument> 方法來寫出 `DataTable.WriteXml`，在序列化至 XML 時，<xref:System.Xml.Linq.XElement> 就會存在額外的父節點。 若要解決此問題，請使用 <xref:System.Data.SqlTypes.SqlXml> 型別而非 <xref:System.Xml.Linq.XElement>。 `ReadXml` 和 `WriteXml` 會搭配 <xref:System.Data.SqlTypes.SqlXml> 正確運作。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataColumn>
- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataTable>
- [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)
- [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
