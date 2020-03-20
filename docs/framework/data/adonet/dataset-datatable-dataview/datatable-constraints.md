---
title: DataTable 條件約束
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 4b7972c281786a4e36d0e9c1e455776a293423ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151282"
---
# <a name="datatable-constraints"></a>DataTable 條件約束
您可以使用條件約束，強制使用 <xref:System.Data.DataTable> 中的資料限制，以維持資料的完整性。 條件約束是指套用到資料行或相關資料行的自動規則，當資料列的值變更時，條件約束可決定採取的動作。 當 的屬性`System.Data.DataSet.EnforceConstraints`<xref:System.Data.DataSet>**為 true**時，將強制執行約束。 如需示範如何設定 `EnforceConstraints` 屬性的程式碼範例，請參閱 <xref:System.Data.DataSet.EnforceConstraints%2A> 參考主題。  
  
 ADO.NET 有兩種條件約束：<xref:System.Data.ForeignKeyConstraint> 與 <xref:System.Data.UniqueConstraint>。 預設情況下，當您通過向<xref:System.Data.DataRelation>**DataSet**添加 創建 兩個或多個表之間的關係時，將自動創建這兩個約束。 但是，您可以通過在創建關係時指定**創建約束** = **為 false**來禁用此行為。  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 **外鍵約束**強制實施有關如何傳播相關表的更新和刪除的規則。 例如，如果更新或刪除一個表行中的值，並且同一值也用於一個或多個相關表，**則外鍵約束**將確定相關表中發生的情況。  
  
 **外鍵約束**的<xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>和<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>屬性定義使用者嘗試刪除或更新相關表中的行時要執行的操作。 下表描述了**外鍵約束**的**DeleteRule**和**UpdateRule**屬性可用的不同設置。  
  
|規則設定|描述|  
|------------------|-----------------|  
|**級 聯**|刪除或更新關聯資料列。|  
|**SetNull**|將相關行中的值設置為**DBNull**。|  
|**設置預設值**|將關聯資料列中的值設為預設值。|  
|**無**|不對關聯資料列採取任何動作。 這是預設值。|  
  
 **外鍵約束**可以限制並傳播對相關列的更改。 根據為列的**外鍵約束**設置的屬性，如果**DataSet**的**強制約束**屬性**為 true，** 則對父行執行某些操作將導致異常。 例如，如果**外鍵約束**的**DeleteRule**屬性為 **"無**"，則如果父行具有任何子行，則無法刪除該行。  
  
 可以使用**外鍵約束**建構函式在單個列之間或列陣列之間創建外鍵約束。 將生成的**外鍵約束**物件傳遞給**表的約束屬性**的**Add**方法，該方法是**約束集合**。 還可以將建構函式參數傳遞給**約束集合**的**Add**方法的幾個重載，以創建**外鍵約束**。  
  
 創建**外鍵約束**時，可以將**DeleteRule**和**UpdateRule**值作為參數傳遞給建構函式，也可以將它們設置為屬性，如以下示例（其中**DeleteRule**值設置為 **"無**" ）。  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  
 可以使用 **"接受更改**"方法接受對行的更改，或使用**資料集**、**資料表**或 DataRow 的**拒絕更改**方法取消對行**的更改**。 當**資料集**包含**外鍵約束**時，調用 **"接受更改**"或 **"拒絕更改"** 方法將強制執行 **"接受拒絕規則**"。 **外鍵約束**的 **"接受拒絕規則"** 屬性確定在父行上調用 **"接受更改**"或 **"拒絕更改**"時將對子行執行哪些操作。  
  
 下表列出了 **"接受拒絕規則**"的可用設置。  
  
|規則設定|描述|  
|------------------|-----------------|  
|**級 聯**|接受或拒絕子資料列的變更。|  
|**無**|不對子資料列採取任何動作。 這是預設值。|  
  
### <a name="example"></a>範例  
 下列範例會建立 <xref:System.Data.ForeignKeyConstraint>、設定其某些屬性 (包括 <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>)，並將它加入 <xref:System.Data.ConstraintCollection> 物件的 <xref:System.Data.DataTable>。  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **唯一約束**物件可以分配給單個列或**DataTable**中的列陣列，可確保指定列或列中的所有資料每行都是唯一的。 可以使用**唯一約束**建構函式為列或列陣列創建唯一約束。 將生成的**唯一約束**物件傳遞給**表的約束屬性**的**Add**方法，該方法是**約束集合**。 還可以將建構函式參數傳遞給**約束集合**的**Add**方法的幾個重載，以創建**唯一約束**。 為列或列創建**唯一約束**時，可以選擇指定列或列是主鍵。  
  
 還可以通過將列**的唯一**屬性設置為**true，** 為列創建唯一約束。 或者，將單個列**的唯一**屬性設置為**false**將刪除可能存在的任何唯一約束。 如果將一個或多個資料行定義為資料表的主索引鍵，將會自動為指定的一個或多個資料行建立唯一的條件約束。 如果從**DataTable****的主鍵**屬性中刪除列，則將刪除**唯一約束**。  
  
 下面的示例為**DataTable**的兩列創建**唯一約束**。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]
    {custTable.Columns["CustomerID"],
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataRelation>
- <xref:System.Data.DataTable>
- <xref:System.Data.ForeignKeyConstraint>
- <xref:System.Data.UniqueConstraint>
- [DataTable 結構描述定義](datatable-schema-definition.md)
- [DataSet、DataTable 和 DataView](index.md)
- [ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)
