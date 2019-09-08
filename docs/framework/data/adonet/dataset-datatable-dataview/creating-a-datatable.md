---
title: 建立 DataTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: e48359041f92e7b534513aa461a293a822bede19
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786495"
---
# <a name="creating-a-datatable"></a>建立 DataTable
<xref:System.Data.DataTable> 表示記憶體中關聯式資料的某個資料表，它可以單獨建立及使用，也可以由其他 .NET Framework 物件所使用，而它最常見用法是做為 <xref:System.Data.DataSet> 的成員。  
  
 您可以使用適當的**datatable**函數來建立**datatable**物件。 您可以使用**add**方法將它加入至**DataTable**物件的**Tables**集合，將它新增至**資料集**。  
  
 您也可以使用**DataAdapter**物件的**Fill**或**FillSchema**方法，或使用**ReadXml**、ReadXmlSchema 的預先定義或推斷 XML 架構，在**資料集**內建立**DataTable**物件。或**資料集**的**InferXmlSchema**方法。 請注意，在您將**DataTable**加入為某個**資料集**之**tables**集合的成員之後，就無法將它加入至任何其他**資料集**的資料表集合。  
  
 當您第一次建立**DataTable**時，它沒有架構（也就是結構）。 若要定義資料表的架構，您必須建立物件並將<xref:System.Data.DataColumn>其加入至資料表的**Columns**集合。 您也可以定義資料表的主鍵資料行，並建立**條件約束**物件，並將其加入至資料表的**條件約束**集合。 定義**DataTable**的架構之後，您可以將資料列加入資料表中，方法是將**DataRow**物件加入至資料表的**rows**集合中。  
  
 當您建立<xref:System.Data.DataTable.TableName%2A> **DataTable**時，不需要提供屬性的值; 您可以在另一次指定屬性，或將它保留空白。 不過，當您將沒有**TableName**值的資料表加入至**資料集**時，資料表會被授與資料表*N*的累加預設名稱，開頭為 "table" 以進行 Table0。  
  
> [!NOTE]
> 當您提供**TableName**值時，建議您避免使用 "Table*N*" 命名慣例，因為您所提供的名稱可能會與**資料集中**現有的預設資料表名稱衝突。 如果提供的名稱已經存在，便會發生例外狀況。  
  
 下列範例會建立**DataTable**物件的實例，並為其指派「Customers」名稱。  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 下列範例會建立**DataTable**的實例，方法是將它加入至**資料集**的**Tables**集合。  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [DataTable](datatables.md)
- [從 DataAdapter 填入 DataSet](../populating-a-dataset-from-a-dataadapter.md)
- [從 XML 載入資料集](loading-a-dataset-from-xml.md)
- [從 XML 載入資料集結構描述資訊](loading-dataset-schema-information-from-xml.md)
- [ADO.NET 概觀](../ado-net-overview.md)
