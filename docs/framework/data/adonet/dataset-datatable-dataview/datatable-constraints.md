---
title: "DataTable 條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# DataTable 條件約束
您可以使用條件約束，強制使用 <xref:System.Data.DataTable> 中的資料限制，以維持資料的完整性。  條件約束是指套用到資料行或相關資料行的自動規則，當資料列的值變更時，條件約束可決定採取的動作。  <xref:System.Data.DataSet> 的  `System.Data.DataSet.EnforceConstraints` 屬性為 **true** 時，便會強制使用條件約束。  如需示範如何設定 `EnforceConstraints` 屬性的程式碼範例，請參閱 <xref:System.Data.DataSet.EnforceConstraints%2A> 參考主題。  
  
 ADO.NET 有兩種條件約束：<xref:System.Data.ForeignKeyConstraint> 與 <xref:System.Data.UniqueConstraint>。  將 <xref:System.Data.DataRelation> 加入 **DataSet** 中，藉而建立兩個或多個資料表之間的關係時，預設會自動建立這兩個條件約束。  但是，您也可以在建立關聯時指定 **createConstraints** \= **false**，即可停用這種行為。  
  
## ForeignKeyConstraint  
 **ForeignKeyConstraint** 對於相關資料表中更新和刪除內容的傳播方式，會強制使用規則。  例如，如果更新或刪除一個資料表的資料列值，而且有一或多個關聯資料表使用相同的值時，**ForeignKeyConstraint** 便會決定關聯資料表中發生的動作。  
  
 **ForeignKeyConstraint** 的 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> 和 <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> 屬性會定義使用者嘗試刪除或更新相關資料表中的資料列時，所要採取的動作。  下列表格說明 **ForeignKeyConstraint** 的 **DeleteRule** 和 **UpdateRule** 屬性可以使用的不同設定。  
  
|規則設定|描述|  
|----------|--------|  
|**Cascade**|刪除或更新關聯資料列。|  
|**SetNull**|將關聯資料列中的值設為 **DBNull**。|  
|**SetDefault**|將關聯資料列中的值設為預設值。|  
|**無**|不對關聯資料列採取任何動作。  這是預設值。|  
  
 **ForeignKeyConstraint** 可以限制 \(和傳播\) 變更到關聯資料行。  如果 **DataSet** 的 **EnforceConstraints** 屬性為 **true**，則當您在父資料列上執行特定作業時，便會視專為資料行的 **ForeignKeyConstraint** 所設定的屬性而定，傳回例外狀況。  例如，如果 **ForeignKeyConstraint** 的 **DeleteRule** 屬性設為 **None**，如果父資料列具有子資料列，該父資料列將無法刪除。  
  
 您可以使用 **ForeignKeyConstraint** 建構函式，在單一資料行之間或是在資料行陣列之間建立外部索引鍵條件約束。  將產生的 **ForeignKeyConstraint** 物件傳遞給資料表的 **Constraints** 屬性的 **Add** 方法，也就是 **ConstraintCollection**。  您也可以將建構函式的引數傳遞給 **ConstraintCollection** 的 **Add** 方法的數個多載，來建立 **ForeignKeyConstraint**。  
  
 當您建立 **ForeignKeyConstraint** 時，可以將 **DeleteRule** 和 **UpdateRule** 值當做引數傳遞給建構函式，也可以將它們設定為屬性，如下列範例所示 \(其中 **DeleteRule** 值設為 **None**\)。  
  
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
  
### AcceptRejectRule  
 您可以使用 **AcceptChanges** 方法來接受資料列的變更，或使用 **DataSet**、**DataTable** 和 **DataRow** 的 **RejectChanges** 方法來取消資料列的變更。  如果 **DataSet** 含有 **ForeignKeyConstraints**，呼叫 **AcceptChanges** 或 **RejectChanges** 方法會強制 **AcceptRejectRule**。  **ForeignKeyConstraint** 的 **AcceptRejectRule** 屬性可決定當在父資料列呼叫 **AcceptChanges** 或 **RejectChanges** 時，子資料列上將採取的動作。  
  
 下列表格列出 **AcceptRejectRule** 的可用設定。  
  
|規則設定|描述|  
|----------|--------|  
|**Cascade**|接受或拒絕子資料列的變更。|  
|**無**|不對子資料列採取任何動作。  這是預設值。|  
  
### 範例  
 下列範例會建立 <xref:System.Data.ForeignKeyConstraint>、設定其某些屬性 \(包括 <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>\)，並將它加入 <xref:System.Data.DataTable> 物件的 <xref:System.Data.ConstraintCollection>。  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## UniqueConstraint  
 **UniqueConstraint** 物件可指定為單一資料行或 **DataTable** 的資料行陣列，它可確保每個資料列的指定資料行的所有資料都是唯一的。  您可以使用 **UniqueConstraint** 建構函式，為資料行或資料行陣列建立唯一的條件約束。  將產生的 **UniqueConstraint** 物件傳遞給資料表的 **Constraints** 屬性的 **Add** 方法，也就是 **ConstraintCollection**。  您也可以將建構函式的引數傳遞給 **ConstraintCollection** 的 **Add** 方法的數個多載，來建立 **UniqueConstraint**。  當您為一個或多個資料行建立 **UniqueConstraint** 時，可以選擇性地指定這些資料行是否為主索引鍵。  
  
 您也可以將資料行的 **Unique** 屬性設定為 **true**，來為資料行建立唯一的條件約束。  另一種可能是，將單一資料行的 **Unique** 屬性設定為 **false**，這麼做會移除可能存在的任何唯一的條件約束。  如果將一個或多個資料行定義為資料表的主索引鍵，將會自動為指定的一個或多個資料行建立唯一的條件約束。  如果您從 **DataTable** 的 **PrimaryKey** 屬性中移除資料行，也會移除 **UniqueConstraint**。  
  
 下列範例為 **DataTable** 的兩個資料行建立 **UniqueConstraint**。  
  
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
  
## 請參閱  
 <xref:System.Data.DataRelation>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.ForeignKeyConstraint>   
 <xref:System.Data.UniqueConstraint>   
 [DataTable 結構描述定義](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [DataSet、DataTable 及 DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)