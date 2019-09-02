---
title: DataTable 條件約束
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
ms.openlocfilehash: 68b99e834428261d59c5fb27277b24eb0f6e77e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205059"
---
# <a name="datatable-constraints"></a>DataTable 條件約束
您可以使用條件約束，強制使用 <xref:System.Data.DataTable> 中的資料限制，以維持資料的完整性。 條件約束是指套用到資料行或相關資料行的自動規則，當資料列的值變更時，條件約束可決定採取的動作。 當的`System.Data.DataSet.EnforceConstraints`屬性<xref:System.Data.DataSet>為**true**時, 就會強制執行條件約束。 如需示範如何設定 `EnforceConstraints` 屬性的程式碼範例，請參閱 <xref:System.Data.DataSet.EnforceConstraints%2A> 參考主題。  
  
 ADO.NET 有兩種條件約束：<xref:System.Data.ForeignKeyConstraint> 與 <xref:System.Data.UniqueConstraint>。 根據預設, 當您藉由將加入<xref:System.Data.DataRelation>至**資料集**, 建立兩個或多個資料表之間的關聯性時, 會自動建立這兩個條件約束。 不過, 您可以在建立關聯性時指定**createConstraints**  =  **false**來停用此行為。  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 **ForeignKeyConstraint**會強制執行有關如何傳播更新和刪除相關資料表的規則。 例如, 如果一個資料表的資料列中的值已更新或刪除, 而且相同的值也用於一個或多個相關的資料表中, 則**ForeignKeyConstraint**會決定相關資料表中發生的情況。  
  
 ForeignKeyConstraint <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>的<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>和屬性會定義當使用者嘗試刪除或更新相關資料表中的資料列時, 所要採取的動作。 下表說明**ForeignKeyConstraint**的**DeleteRule**和**UpdateRule**屬性可用的不同設定。  
  
|規則設定|描述|  
|------------------|-----------------|  
|**Cascade**|刪除或更新關聯資料列。|  
|**SetNull**|將相關資料列中的值設定為**DBNull**。|  
|**SetDefault**|將關聯資料列中的值設為預設值。|  
|**無**|不對關聯資料列採取任何動作。 這是預設值。|  
  
 **ForeignKeyConstraint**可以限制及傳播相關資料行的變更。 視資料行的**ForeignKeyConstraint**所設定的屬性而定, 如果 DataSet 的**EnforceConstraints**屬性為**True**, 則在父**資料**列上執行某些作業將會導致例外狀況。 例如, 如果**ForeignKeyConstraint**的**DeleteRule**屬性為**None**, 則父資料列若有任何子資料列, 就無法刪除。  
  
 您可以使用**ForeignKeyConstraint**的函式, 在單一資料行之間或資料行陣列之間建立外鍵條件約束。 將產生的**ForeignKeyConstraint**物件傳遞給資料表的**條件約束**屬性的**Add**方法, 也就是**ConstraintCollection**。 您也可以將函式引數傳遞給**ConstraintCollection**的**Add**方法的數個多載, 以建立**ForeignKeyConstraint**。  
  
 建立**ForeignKeyConstraint**時, 您可以將**DeleteRule**和**UpdateRule**值當做引數傳遞至函式, 也可以將它們設定為屬性, 如下列範例所示 (其中**DeleteRule**值設定為**無**)。  
  
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
 您可以使用**AcceptChanges**方法來接受**資料**列的變更, 或使用 DataSet、 **DataTable**或**DataRow**的**RejectChanges**方法來取消。 當**資料集**包含**ForeignKeyConstraints**時, 叫**用 AcceptChanges**或**RejectChanges**方法會強制執行**AcceptRejectRule**。 **ForeignKeyConstraint**的**AcceptRejectRule**屬性會決定在父資料列上呼叫**AcceptChanges**或**RejectChanges**時, 將對子資料列採取的動作。  
  
 下表列出**AcceptRejectRule**的可用設定。  
  
|規則設定|描述|  
|------------------|-----------------|  
|**Cascade**|接受或拒絕子資料列的變更。|  
|**無**|不對子資料列採取任何動作。 這是預設值。|  
  
### <a name="example"></a>範例  
 下列範例會建立 <xref:System.Data.ForeignKeyConstraint>、設定其某些屬性 (包括 <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>)，並將它加入 <xref:System.Data.ConstraintCollection> 物件的 <xref:System.Data.DataTable>。  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint**物件, 可以指派至單一資料行或**DataTable**中的資料行陣列, 以確保指定之資料行中的所有資料在每一列中都是唯一的。 您可以使用**UniqueConstraint**的函式, 為數據行或資料行陣列建立唯一的條件約束。 將產生的**UniqueConstraint**物件傳遞給資料表的**條件約束**屬性的**Add**方法, 也就是**ConstraintCollection**。 您也可以將函式引數傳遞給**ConstraintCollection**的**Add**方法的數個多載, 以建立**UniqueConstraint**。 建立一或多個資料行的**UniqueConstraint**時, 您可以選擇性地指定資料行是否為主鍵。  
  
 您也可以將資料行的**unique**屬性設定為**true**, 以建立資料行的唯一條件約束。 或者, 將單一資料行的**unique**屬性設定為**false** , 會移除可能存在的任何 Unique 條件約束。 如果將一個或多個資料行定義為資料表的主索引鍵，將會自動為指定的一個或多個資料行建立唯一的條件約束。 如果您從**DataTable**的**PrimaryKey**屬性中移除資料行, 則會移除**UniqueConstraint** 。  
  
 下列範例會針對**DataTable**的兩個數據行建立**UniqueConstraint** 。  
  
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
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
