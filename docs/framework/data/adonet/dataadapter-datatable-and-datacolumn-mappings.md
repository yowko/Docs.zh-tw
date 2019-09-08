---
title: DataAdapter DataTable 和 DataColumn 對應
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 357812aa95ea731fe86fbe49b2cb1b2806e3915a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784860"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable 和 DataColumn 對應
**DataAdapter**在其 TableMappings 屬性中包含零個<xref:System.Data.Common.DataTableMapping>或多個物件的集合。 **DataTableMapping**會在從查詢傳回的資料與資料來源之間提供主要對應，以及<xref:System.Data.DataTable>。 **DataTableMapping**名稱可以代替**DataTable**名稱傳遞到**DataAdapter**的**Fill**方法。 下列範例會為**作者**資料表建立名為**AuthorsMapping**的**DataTableMapping** 。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTableMapping**可讓您在**DataTable**中使用與資料庫中不同的資料行名稱。 當更新資料表時， **DataAdapter**會使用對應來比對資料行。  
  
 如果您在呼叫**DataAdapter**的**Fill**或**Update**方法時未指定**TableName**或**DataTableMapping**名稱， **dataadapter**會尋找名為 "Table" 的**DataTableMapping** 。 如果該**DataTableMapping**不存在， **DataTable**的**TableName**就是 "Table"。 您可以藉由建立名為 "Table" 的**DataTableMapping**來指定預設**DataTableMapping** 。  
  
 下列程式碼範例會建立**DataTableMapping** （從<xref:System.Data.Common>命名空間），並將它命名為 "Table"，使其成為指定**DataAdapter**的預設對應。 然後，此範例會將查詢結果（ **northwind**資料庫的**Customers**資料表）中第一個資料表的資料行對應至中**Northwind** <xref:System.Data.DataSet>Customers 資料表內的一組更好的使用者名稱。 未被對應的資料行會使用來自資料來源的資料行名稱。  
  
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
  
 在更先進的情況下，您可能會決定您想要讓相同的**DataAdapter**支援使用不同的對應來載入不同的資料表。 若要這樣做，只需新增額外的**DataTableMapping**物件即可。  
  
 將**資料集**的實例和**DataTableMapping**名稱傳遞給**Fill**方法時，如果使用該名稱的對應存在，則會使用它;否則，會使用具有該名稱的**DataTable** 。  
  
 下列範例會建立**DataTableMapping** ，其名稱為**Customers** ，而**DataTable**名稱為**BizTalkSchema**。 然後，此範例會將 SELECT 語句所傳回的資料列對應至**BizTalkSchema** **DataTable**。  
  
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
> 若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。 如果未提供資料行對應的來源資料行，則會從**SourceColumn1**開始，資料行對應會提供一個增量預設名稱**SourceColumn** *N* 。 如果沒有為資料表對應提供來源資料表名稱，則會為數據表對應提供**SourceTable** *N*的累加預設名稱，從**SourceTable1**開始。  
  
> [!NOTE]
> 我們建議您避免資料行對應使用**SourceColumn** *N*的命名慣例，或針對資料表對應來**SourceTable** *N* ，因為您所提供的名稱可能會與中**現有的預設資料行對應名稱衝突。** **衝突**中的 ColumnMappingCollection 或資料表對應名稱。 如果提供的名稱已經存在，便會擲回例外狀況。  
  
## <a name="handling-multiple-result-sets"></a>處理多重結果集  
 如果您的**SelectCommand**傳回多個資料表， **Fill**會自動針對**資料集**內的資料表產生具有累加值的資料表名稱，並以指定的資料表名稱作為開頭，並在表單**TableName**中繼續進行。*N*，從**TableName1**開始。 您可以使用資料表對應，將自動產生的資料表名稱對應至您想要在**資料集中**為數據表指定的名稱。 例如，針對傳回兩個數據表（ **Customers**和**Orders**）的**SelectCommand** ，請發出下列呼叫以進行**填滿**。  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 **資料集**內會建立兩個數據表：**客戶**和**Customers1**。 您可以使用資料表對應來確保第二個數據表的名稱是**Orders** ，而不是**Customers1**。 若要這樣做，請將**Customers1**的來源資料表對應至**資料集**資料表**訂單**，如下列範例所示。  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>另請參閱

- [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)
- [在 ADO.NET 中擷取和修改資料](retrieving-and-modifying-data.md)
- [ADO.NET 概觀](ado-net-overview.md)
