---
title: 將現有條件約束加入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 05f95a9c4f250100ca97e3ab52e4073d027df1b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932188"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>將現有條件約束加入至資料集
**DataAdapter**的<xref:System.Data.DataSet> **Fill**方法只會將資料來源中的資料表資料行和資料列填滿。雖然條件約束通常是由資料來源所設定, 但**Fill**方法並不會將此架構資訊新增至**預設為資料集**。 若要使用資料來源中現有的 primary key 條件約束資訊來填入**資料集**, 您可以呼叫**dataadapter**的**FillSchema**方法, 或設定**dataadapter**的**MissingSchemaAction**屬性在呼叫**Fill**之前**missingschemaaction.addwithkey** 。 這可確保資料**集中**的 primary key 條件約束反映在資料來源中。 外鍵條件約束資訊不會包含在內, 而且必須明確建立, 如[DataTable 條件約束](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)中所示。  
  
 在將架構資訊填入資料之前, 將其加入**dataset** , 可確保<xref:System.Data.DataTable> **資料集**內的物件會包含 primary key 條件約束。 如此一來, 當進行額外的填入資料**集**的呼叫時, 就會使用主鍵資料行資訊來比對資料來源中的新資料列與每個**DataTable**中的目前資料列, 並使用來自的資料來覆寫資料表中的目前資料。資料來源。 如果沒有架構資訊, 資料來源中的新資料列就會附加至資料**集**, 因而產生重複的資料列。  
  
> [!NOTE]
> 如果資料來源中的資料行識別為自動遞增、 **FillSchema**方法或**MissingSchemaAction**為**missingschemaaction.addwithkey**的**Fill**方法, 會建立具有**自動**累加屬性的**DataColumn**將設定`true`為。 不過, 您將需要自行設定**AutoIncrementStep**和**AutoIncrementSeed**值。 如需自動遞增資料行的詳細資訊, 請參閱[建立自動](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)調整資料行。  
  
 使用**FillSchema**或將**MissingSchemaAction**設定為**missingschemaaction.addwithkey**時, 需要在資料來源進行額外的處理, 以判斷主鍵資料行資訊。 這些其他作業可能會降低效能。 如果您在設計階段就已知道主索引鍵資訊，建議您明確地指定主索引鍵資料行，以達到最佳效能。 如需明確設定資料表主鍵資訊的相關資訊, 請參閱[定義主鍵](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)。  
  
 下列程式碼範例示範如何使用**FillSchema**將架構資訊新增至**資料集**。  
  
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
  
 下列程式碼範例示範如何使用**Fill**方法的**MissingSchemaAction. missingschemaaction.addwithkey**屬性, 將架構資訊新增至**資料集**。  
  
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
 如果**DataAdapter**遇到從**SelectCommand**傳回的多個結果集, 它會在**資料集中**建立多個資料表。 資料表會提供以零為基底的增量預設名稱**table** *N*, 開頭為**table** , 而不是 "Table0"。 如果將資料表名稱當做引數傳遞至**FillSchema**方法, 則會為數據表指定以零為基底的**tablename** *N*增量名稱, 從**Tablename**開始, 而不是 "TableName0"。  
  
> [!NOTE]
> 如果針對傳回多個結果集的命令呼叫**OleDbDataAdapter**物件的**FillSchema**方法, 則只會傳回第一個結果集的架構資訊。 使用**OleDbDataAdapter**傳回多個結果集的架構資訊時, 建議您指定**missingschemaaction.addwithkey**的**MissingSchemaAction** , 並在呼叫**Fill**時取得架構資訊。方法.  
  
## <a name="see-also"></a>另請參閱

- [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DataSet、DataTable 和 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
