---
title: "將現有條件約束加入至資料集"
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
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2f2f6c60197b1d71feb13ca351ad19298e09ea56
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="adding-existing-constraints-to-a-dataset"></a>將現有條件約束加入至資料集
**填滿**方法**DataAdapter**填滿<xref:System.Data.DataSet>只能搭配資料表資料行和資料列從資料來源; 雖然條件約束通常由設定資料來源，**填滿**方法不會加入此結構描述資訊**資料集**預設。 填入**資料集**與資料來源的現有主索引鍵條件約束資訊，您可以呼叫**FillSchema**方法**DataAdapter**，或設定**MissingSchemaAction**屬性**DataAdapter**至**Missingschemaaction**之前先呼叫**填滿**。 這可確保該主索引鍵中的條件約束**資料集**反映出在資料來源。 外部索引鍵條件約束資訊就不會包含與必須明確地如下所示建立[DataTable 條件約束](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)。  
  
 加入至結構描述資訊**資料集**填入資料可確保 primary key 條件約束隨附於之前<xref:System.Data.DataTable>中的物件**資料集**。 如此一來，當其他呼叫以填入**資料集**所做的主要索引鍵資料行資訊用來比對資料來源的新資料列的目前資料列中每個**DataTable**，以及在目前的資料從資料來源的資料會覆寫資料表。 如果沒有結構描述資訊，從資料來源的新資料列會附加至**資料集**，並產生重複的資料列。  
  
> [!NOTE]
>  如果資料來源中的資料行識別為自動遞增**FillSchema**方法，或**填滿**方法**MissingSchemaAction**的**Missingschemaaction**，建立**DataColumn**與**AutoIncrement**屬性設定為`true`。 不過，您必須設定**AutoIncrementStep**和**AutoIncrementSeed**值。 如需自動遞增資料行的詳細資訊，請參閱[建立自動遞增資料行](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)。  
  
 使用**FillSchema**或設定**MissingSchemaAction**至**Missingschemaaction**需要進行額外處理，在資料來源來判斷主要索引鍵資料行資訊。 這些其他作業可能會降低效能。 如果您在設計階段就已知道主索引鍵資訊，建議您明確地指定主索引鍵資料行，以達到最佳效能。 如需明確設定為資料表的主索引鍵資訊，請參閱[定義主索引鍵](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
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
 如果**DataAdapter**遇到多個結果集傳回**SelectCommand**，它會建立多個資料表中的**資料集**。 以零為起始的遞增預設名稱將會給予資料表**資料表** *N*開始，**資料表**而非"Table0"。 如果資料表名稱會做為引數傳遞**FillSchema**方法，則會給予資料表的以零為起始的增量名稱**TableName** *N*，從**TableName**而非"TableName0"。  
  
> [!NOTE]
>  如果**FillSchema**方法**OleDbDataAdapter**傳回多個結果集的命令呼叫物件時，會傳回只從第一個結果集的結構描述資訊。 傳回多個結果的結構描述資訊。 當設定使用**OleDbDataAdapter**，建議您指定**MissingSchemaAction**的**Missingschemaaction**呼叫時，取得結構描述資訊和**填滿**方法。  
  
## <a name="see-also"></a>請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSet、DataTable 和 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
