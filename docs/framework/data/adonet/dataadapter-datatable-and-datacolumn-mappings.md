---
title: DataAdapter DataTable 和 DataColumn 對應
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 1b426dbcdc78ecfddeac003616993849ce60b89c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable 和 DataColumn 對應
A **DataAdapter**包含零或多個集合<xref:System.Data.Common.DataTableMapping>物件在其**TableMappings**屬性。 A **DataTableMapping**提供對資料來源，查詢傳回的資料之間的主要對應和<xref:System.Data.DataTable>。 **DataTableMapping**名稱可以傳遞取代**DataTable**名稱**填滿**方法**DataAdapter**。 下列範例會建立**DataTableMapping**名為**AuthorsMapping**如**作者**資料表。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping**可讓您使用的資料行名稱**DataTable**不同的資料庫。 **DataAdapter**使用對應來更新資料表時，符合的資料行。  
  
 如果您未指定**TableName**或**DataTableMapping**名稱就呼叫**填滿**或**更新**方法**DataAdapter**、 **DataAdapter**尋找**DataTableMapping**名為"Table"。 如果該**DataTableMapping**不存在， **TableName**的**DataTable**是 「 資料表 」。 您可以指定預設值**DataTableMapping**藉由建立**DataTableMapping** 「 資料表 」 的名稱。  
  
 下列程式碼範例會建立**DataTableMapping** (從<xref:System.Data.Common>命名空間)，並讓指定的預設對應**DataAdapter**由其命名為"Table"。 此範例接著將對應從查詢結果中的第一個資料表的資料行 (**客戶**資料表**Northwind**資料庫) 中更加易懂易記名稱的一組**Northwind Customers**資料表中<xref:System.Data.DataSet>。 未被對應的資料行會使用來自資料來源的資料行名稱。  
  
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
  
 在更進階的情況下，您可能決定要相同**DataAdapter**載入具有不同對應的不同資料表。 若要這樣做，只要加入其他**DataTableMapping**物件。  
  
 當**填滿**傳遞給方法的執行個體**資料集**和**DataTableMapping** ，具有該名稱的對應已存在，則會使用; 否則**DataTable**使用具有該名稱。  
  
 下列範例會建立**DataTableMapping**名稱為**客戶**和**DataTable**名稱**BizTalkSchema**。 此範例則會對應到 SELECT 陳述式所傳回的資料列**BizTalkSchema** **DataTable**。  
  
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
>  若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。 如果沒有來源資料行提供給資料行對應時，資料行對應指定的遞增預設名稱**SourceColumn** *N*開頭**SourceColumn1**。 如果沒有來源資料表名稱提供給資料表對應，該資料表對應指定的遞增預設名稱**SourceTable** *N*開始， **SourceTable1**。  
  
> [!NOTE]
>  我們建議您避免命名慣例的**SourceColumn** *N*給資料行對應，或**SourceTable** *N*資料表對應，因為您提供的名稱可能與現有預設資料行對應中的名稱衝突**ColumnMappingCollection**或資料表中的對應名稱**DataTableMappingCollection**. 如果提供的名稱已經存在，便會擲回例外狀況。  
  
## <a name="handling-multiple-result-sets"></a>處理多重結果集  
 如果您**SelectCommand**傳回多個資料表，**填滿**遞增的值中的資料表的資料表名稱會自動產生**資料集**開始，在表單上指定資料表名稱，並繼續**TableName** *N*開始， **TableName1**。 您可以使用資料表對應至自動產生的資料表名稱對應到您要指定給中的資料表名稱**資料集**。 例如，對於**SelectCommand**傳回兩個資料表**客戶**和**訂單**，發出下列呼叫**填滿**。  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 兩個資料表會建立在**資料集**:**客戶**和**Customers1**。 您可以使用資料表對應，以確保第二個資料表名為**訂單**而不是**Customers1**。 若要這樣做，請將對應的來源資料表**Customers1**至**資料集**資料表**訂單**，如下列範例所示。  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>另請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
