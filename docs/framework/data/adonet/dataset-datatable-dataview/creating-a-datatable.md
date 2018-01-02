---
title: "建立 DataTable"
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 68f8272aa0f525c04120f129057e6151e42ffee1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datatable"></a>建立 DataTable
<xref:System.Data.DataTable> 表示記憶體中關聯式資料的某個資料表，它可以單獨建立及使用，也可以由其他 .NET Framework 物件所使用，而它最常見用法是做為 <xref:System.Data.DataSet> 的成員。  
  
 您可以建立**DataTable**物件使用適當的**DataTable**建構函式。 您可以將它加入至**資料集**使用**新增**方法將它加入至**DataTable**物件的**資料表**集合。  
  
 您也可以建立**DataTable**物件內**資料集**使用**填滿**或**FillSchema**方法**DataAdapter**物件，或從預先定義或推斷 XML 結構描述使用**ReadXml**， **ReadXmlSchema**，或**InferXmlSchema**方法的**資料集**。 請注意，當您加入**DataTable**成員的身分**資料表**的其中一個集合**資料集**，您無法加入資料表的任何其他集合**資料集**。  
  
 當您第一次建立**DataTable**，它並沒有結構描述 （亦即結構）。 若要定義資料表的結構描述，您必須建立並新增<xref:System.Data.DataColumn>物件加入至**資料行**資料表的集合。 您也可以定義資料表的主索引鍵資料行和建立及新增**條件約束**物件加入至**條件約束**資料表的集合。 您定義的結構描述之後**DataTable**，您可以加入資料列的資料表加入**DataRow**物件加入至**列**資料表的集合。  
  
 您不需要提供的值<xref:System.Data.DataTable.TableName%2A>屬性，當您建立**DataTable**; 您可以在其他時候，指定的屬性，或您可以將它保留空白。 不過，當您加入的資料表沒有**TableName**值設定為**資料集**，資料表會指定資料表的累加預設名稱*N*，從"Table"開始 （table0)。  
  
> [!NOTE]
>  我們建議您避免 「 資料表*N*"命名慣例，當您提供**TableName**值，因為您提供的名稱可能與現有的預設資料表名稱中衝突**資料集**. 如果提供的名稱已經存在，便會發生例外狀況。  
  
 下列範例會建立的執行個體**DataTable**物件，並將其指派的名稱 「 客戶 」。  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 下列範例會建立的執行個體**DataTable**將它加入至**資料表**集合**資料集**。  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [從 DataAdapter 填入 DataSet](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [從 XML 載入資料集](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [從 XML 載入資料集結構描述資訊](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
