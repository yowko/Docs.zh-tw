---
title: 將現有條件約束加入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 39b1e9945a1cf6cd847fbe82c0b29e50f23bf785
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714145"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>將現有條件約束加入至資料集
**填滿**方法**DataAdapter**填滿<xref:System.Data.DataSet>只使用資料表資料行和資料列從資料來源; 不過條件約束通常由設定資料來源，**填滿**方法不會加入到此結構描述資訊**資料集**預設。 若要填入**資料集**從資料來源的現有主索引鍵條件約束資訊，您可以呼叫**FillSchema**方法**DataAdapter**，或設定**MissingSchemaAction**屬性**DataAdapter**來**AddWithKey**呼叫之前，先**填滿**。 這可確保該主索引鍵中的條件約束**資料集**反映出資料來源。 外部索引鍵條件約束資訊就不會包含，而且必須明確地中所示建立[DataTable 條件約束](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)。  
  
 新增結構描述資訊**資料集**primary key 條件約束所包含的資料填入可確保先<xref:System.Data.DataTable>中的物件**DataSet**。 如此一來，當其他呼叫，以填滿**資料集**會變成主要索引鍵資料行的資訊用來比對新的資料列從資料來源的目前資料列中每個**DataTable**，以及在目前的資料從資料來源的資料會覆寫資料表。 如果沒有結構描述資訊中，從資料來源的新資料列會附加至**資料集**，產生的重複的資料列。  
  
> [!NOTE]
>  如果資料來源中的資料行識別為自動遞增**FillSchema**方法，或有**填滿**方法**MissingSchemaAction**的**Missingschemaaction**，建立**DataColumn**具有**AutoIncrement**屬性設定為`true`。 不過，您必須設定**AutoIncrementStep**並**AutoIncrementSeed**值。 如需有關自動遞增資料行的詳細資訊，請參閱[建立自動遞增資料行](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)。  
  
 使用**FillSchema**或 設定**MissingSchemaAction**來**AddWithKey**需要進行額外處理，在資料來源來判斷主索引鍵資料行資訊。 這些其他作業可能會降低效能。 如果您在設計階段就已知道主索引鍵資訊，建議您明確地指定主索引鍵資料行，以達到最佳效能。 如需明確設定為資料表的主索引鍵資訊的詳細資訊，請參閱[定義主索引鍵](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
 下列程式碼範例示範如何將結構描述資訊加入**資料集**使用**FillSchema**。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 下列程式碼範例示範如何將結構描述資訊加入**資料集**使用**MissingSchemaAction.AddWithKey**屬性**填滿**方法。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>處理多重結果集  
 如果**DataAdapter**遇到多個結果集傳回**SelectCommand**，它會建立多個資料表中的**資料集**。 以零為起始的遞增預設名稱會給予資料表**表格** *N*，從**資料表**而非"Table0"。 如果資料表名稱會傳遞做為引數**FillSchema**方法，會給予資料表的以零為起始的增量名稱**TableName** *N*，從**TableName**而非"TableName0"。  
  
> [!NOTE]
>  如果**FillSchema**方法**OleDbDataAdapter**物件針對傳回多個結果集的命令呼叫，會傳回只從第一個結果集的結構描述資訊。 傳回多個結果的結構描述資訊時設定使用**OleDbDataAdapter**，則建議您指定**MissingSchemaAction**的**AddWithKey**並取得結構描述資訊時呼叫**填滿**方法。  
  
## <a name="see-also"></a>另請參閱
- [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DataSet、DataTable 和 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
