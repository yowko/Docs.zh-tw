---
title: "DataTable 條件約束"
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
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3767467024d6c0d0dfbf1be8829d77ba3f7fa439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-constraints"></a>DataTable 條件約束
您可以使用條件約束，強制使用 <xref:System.Data.DataTable> 中的資料限制，以維持資料的完整性。 條件約束是指套用到資料行或相關資料行的自動規則，當資料列的值變更時，條件約束可決定採取的動作。 強制使用條件約束時`System.Data.DataSet.EnforceConstraints`屬性<xref:System.Data.DataSet>是**true**。 如需示範如何設定 `EnforceConstraints` 屬性的程式碼範例，請參閱 <xref:System.Data.DataSet.EnforceConstraints%2A> 參考主題。  
  
 ADO.NET 有兩種條件約束：<xref:System.Data.ForeignKeyConstraint> 與 <xref:System.Data.UniqueConstraint>。 根據預設，兩個條件約束會建立時自動建立您所新增的兩個或多個資料表之間的關聯性<xref:System.Data.DataRelation>至**資料集**。 不過，您可以停用此行為藉由指定**createConstraints** = **false**時建立關聯。  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 A **ForeignKeyConstraint**會強制執行規則的相關更新與刪除導引到相關資料表的傳播方式。 例如，如果更新或刪除，一個資料表的資料列中的值和相同的值也會在一或多個關聯資料表， **ForeignKeyConstraint**決定相關的資料表中的動作。  
  
 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A>和<xref:System.Data.ForeignKeyConstraint.UpdateRule%2A>屬性**ForeignKeyConstraint**定義使用者嘗試刪除或更新相關資料表中的資料列時，要採取的動作。 下表描述可用的不同設定**DeleteRule**和**UpdateRule**屬性**ForeignKeyConstraint**。  
  
|規則設定|描述|  
|------------------|-----------------|  
|**重疊顯示**|刪除或更新關聯資料列。|  
|**SetNull**|在相關資料列中設定值**DBNull**。|  
|**SetDefault**|將關聯資料列中的值設為預設值。|  
|**無**|不對關聯資料列採取任何動作。 這是預設值。|  
  
 A **ForeignKeyConstraint**可以限制，以及傳播，變更到關聯資料行。 根據設定的屬性**ForeignKeyConstraint**資料行，如果**EnforceConstraints**屬性**資料集**是**true**，父資料列上執行特定作業時，會導致例外狀況。 例如，如果**DeleteRule**屬性**ForeignKeyConstraint**是**無**，無法刪除父資料列，如果有任何子資料列。  
  
 您可以建立的外部索引鍵的條件約束使用的資料行的陣列之間或單一資料行之間**ForeignKeyConstraint**建構函式。 傳遞所產生的**ForeignKeyConstraint**物件**新增**方法資料表的**條件約束**屬性，這是**ConstraintCollection**. 您也可以傳遞給建構函式引數的數個多載**新增**方法**ConstraintCollection**建立**ForeignKeyConstraint**。  
  
 建立時**ForeignKeyConstraint**，您可以傳遞**DeleteRule**和**UpdateRule**值建構函式做為引數，或者您可以將它們設定為做為中的屬性下列範例 (其中**DeleteRule**值設定為**無**)。  
  
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
 資料列的變更可以使用接受**AcceptChanges**方法，或已取消使用**RejectChanges**方法**資料集**， **DataTable**，或**DataRow**。 當**資料集**包含**ForeignKeyConstraints**、 叫用**AcceptChanges**或**RejectChanges**方法會強制**AcceptRejectRule**。 **AcceptRejectRule**屬性**ForeignKeyConstraint**判斷應採取哪些動作的子系上的資料列時**AcceptChanges**或**RejectChanges**父資料列上呼叫。  
  
 下表列出可用的設定**AcceptRejectRule**。  
  
|規則設定|描述|  
|------------------|-----------------|  
|**重疊顯示**|接受或拒絕子資料列的變更。|  
|**無**|不對子資料列採取任何動作。 這是預設值。|  
  
### <a name="example"></a>範例  
 下列範例會建立 <xref:System.Data.ForeignKeyConstraint>、設定其某些屬性 (包括 <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>)，並將它加入 <xref:System.Data.ConstraintCollection> 物件的 <xref:System.Data.DataTable>。  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 **UniqueConstraint**物件，可以對單一資料行或陣列中的資料行指派**DataTable**，確保指定的資料行或資料行中的所有資料都是唯一的每個資料列。 您可以使用，以建立唯一的條件約束的資料行或資料行陣列**UniqueConstraint**建構函式。 傳遞所產生的**UniqueConstraint**物件**新增**方法資料表的**條件約束**屬性，這是**ConstraintCollection**. 您也可以傳遞給建構函式引數的數個多載**新增**方法**ConstraintCollection**建立**UniqueConstraint**。 建立時**UniqueConstraint**資料行或資料行，您可以選擇性地指定資料行或資料行是主索引鍵。  
  
 您也可以建立 unique 條件約束資料行，藉由設定**Unique**屬性的資料行**true**。 或者，設定**Unique**屬性的單一資料行**false**移除可能存在的任何唯一條件約束。 如果將一個或多個資料行定義為資料表的主索引鍵，將會自動為指定的一個或多個資料行建立唯一的條件約束。 如果您移除的資料行**PrimaryKey**屬性**DataTable**、 **UniqueConstraint**已移除。  
  
 下列範例會建立**UniqueConstraint**兩個資料行的**DataTable**。  
  
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataSet、DataTable 和 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
