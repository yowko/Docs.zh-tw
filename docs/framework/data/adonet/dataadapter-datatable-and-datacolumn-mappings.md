---
title: DataAdapter DataTable 和 DataColumn 對應
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: b979431836b55b23ac9ba6ec4535f33765dce555
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91177731"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable 和 DataColumn 對應

**DataAdapter** <xref:System.Data.Common.DataTableMapping> 在其 **TableMappings** 屬性中包含零或多個物件的集合。 **DataTableMapping** 會在針對資料來源的查詢所傳回的資料和之間提供主要對應 <xref:System.Data.DataTable> 。 您可以將 **DataTableMapping** 名稱取代為 **DataAdapter** 的 **Fill** 方法的 **DataTable** 名稱。 下列範例會為 **作者** 資料表建立名為 **AuthorsMapping** 的 **DataTableMapping** 。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTableMapping** 可讓您在 **DataTable** 中使用與資料庫中的資料行名稱不同的資料行名稱。 當更新資料表時， **DataAdapter** 會使用對應來比對資料行。  
  
 如果您在呼叫 **DataAdapter** 的 **Fill** 或 **Update** 方法時未指定 **TableName** 或 **DataTableMapping** 名稱，則 **DataAdapter** 會尋找名為 "Table" 的 **DataTableMapping** 。 如果該 **DataTableMapping** 不存在，則 **DataTable** 的 **TableName** 為 "Table"。 您可以建立名稱為 "Table" 的 **DataTableMapping** ，以指定預設的 **DataTableMapping** 。  
  
 下列程式碼範例會建立 **DataTableMapping** <xref:System.Data.Common> 命名空間) 的 DataTableMapping (，並將其命名為 "Table"，使其成為指定之 **DataAdapter** 的預設對應。 然後，此範例會將查詢結果中第一個資料表的資料行， (**northwind** 資料庫的 **Customers** 資料表，) 到中的 **northwind customers** 資料表中的一組更易記的名稱 <xref:System.Data.DataSet> 。 未被對應的資料行會使用來自資料來源的資料行名稱。  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 在更先進的情況下，您可能會決定要使用相同的 **DataAdapter** 來支援載入具有不同對應的不同資料表。 若要這樣做，只需新增其他 **DataTableMapping** 物件。  
  
 當將 **資料集** 的實例和 **DataTableMapping** 名稱傳遞給 **Fill** 方法時，如果使用具有該名稱的對應，就會使用它。否則，就會使用具有該名稱的 **DataTable** 。  
  
 下列範例會建立名稱為 **Customers** 的 **DataTableMapping** 和 **DataTable** name of **biztalkschemadatatable**。 然後，此範例會將 SELECT 語句傳回的資料列對應至 **biztalkschemadatatable** **DataTable**。  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> 若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。 如果沒有為資料行對應提供來源資料行，則會將資料行對應的增量預設名稱指定為 **SourceColumn** *N，* 從 **SourceColumn1** 開始。 如果未提供資料表對應的來源資料表名稱，則會為數據表對應指定 **SourceTable** *N* 的增量預設名稱，從 **SourceTable1** 開始。  
  
> [!NOTE]
> 建議您避免在資料行對應中使用 **SourceColumn** *N* 的命名慣例，或針對資料表對應來 **SourceTable** *N* ，因為您所提供的名稱可能會與 **衝突** 中 **datatablemappingcollection** 或資料表對應名稱中現有的預設資料行對應名稱相衝突。 如果提供的名稱已經存在，便會擲回例外狀況。  
  
## <a name="handling-multiple-result-sets"></a>處理多重結果集  

 如果您的 **SelectCommand** 傳回多個資料表，則 **填滿** 會自動產生 **資料集中** 資料表的累加值的資料表名稱，以指定的資料表名稱為開頭，並 **TableName** 以資料表名稱（從 **TableName1***開始）繼續* 進行。 您可以使用資料表對應，將自動產生的資料表名稱對應到您想要在 **資料集中** 為數據表指定的名稱。 例如，針對傳回兩個數據表、**客戶** 和 **訂單** 的 **SelectCommand** ，發出下列要 **填滿** 的呼叫。  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 **資料集** 內會建立兩個數據表：**客戶** 和 **Customers1**。 您可以使用資料表對應，以確保第二個數據表的名稱為 **Orders** ，而不是 **Customers1**。 若要這樣做，請將 **Customers1** 的來源資料表對應至 **資料集** 資料表 **訂單**，如下列範例所示。  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a>另請參閱

- [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)
- [在 ADO.NET 中傳送和修改資料](retrieving-and-modifying-data.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
