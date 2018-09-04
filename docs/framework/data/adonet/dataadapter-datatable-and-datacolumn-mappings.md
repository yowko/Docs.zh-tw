---
title: DataAdapter DataTable 和 DataColumn 對應
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 9f33ae085bef2b611d1ce95bed1b26f9101a10b9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505238"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable 和 DataColumn 對應
A **DataAdapter**包含零或多個集合<xref:System.Data.Common.DataTableMapping>中的物件及其**TableMappings**屬性。 A **DataTableMapping**提供對資料來源，查詢所傳回的資料之間的主要對應和<xref:System.Data.DataTable>。 **DataTableMapping**可以傳遞名稱，取代**DataTable**名稱**填滿**方法**DataAdapter**。 下列範例會建立**DataTableMapping**名為**AuthorsMapping** for**作者**資料表。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping**可讓您使用的資料行名稱**DataTable**不同於與資料庫中。 **DataAdapter**使用對應來更新資料表時，符合的資料行。  
  
 如果您未指定**TableName**或**DataTableMapping**名稱就呼叫**填滿**或是**更新**方法**DataAdapter**，則**DataAdapter**會尋找**DataTableMapping**名為"Table"。 如果該**DataTableMapping**不存在， **TableName**的**DataTable**為"Table"。 您可以指定預設值**DataTableMapping**藉由建立**DataTableMapping** "Table"的名稱。  
  
 下列程式碼範例會建立**DataTableMapping** (從<xref:System.Data.Common>命名空間)，並使其指定的預設對應**DataAdapter**藉由將它命名為 「 資料表 」。 範例接著會對應從查詢結果中的第一個資料表的資料行 (**客戶**的資料表**Northwind**資料庫) 的使用者易記的名稱，在一組**Northwind Customers**資料表中<xref:System.Data.DataSet>。 未被對應的資料行會使用來自資料來源的資料行名稱。  
  
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
  
 在更進階的情況下，您可以決定讓相同**DataAdapter**無法支援載入不同的資料表，具有不同的對應。 若要這樣做，只要另外加**DataTableMapping**物件。  
  
 當**填滿**傳遞給方法的執行個體**資料集**並**DataTableMapping**名稱，如果具有該名稱的對應存在，則為， **DataTable**會使用的名稱。  
  
 下列範例會建立**DataTableMapping**名稱取代**客戶**並**DataTable**名稱**BizTalkSchema**。 此範例則會對應到 SELECT 陳述式所傳回的資料列**BizTalkSchema** **DataTable**。  
  
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
>  若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。 如果沒有來源資料行提供資料行對應，該資料行對應會指定的遞增預設名稱**SourceColumn** *N*開頭**SourceColumn1**。 如果沒有來源資料表名稱提供給資料表對應，該資料表對應會指定的遞增預設名稱**SourceTable** *N*，從**SourceTable1**。  
  
> [!NOTE]
>  我們建議您避免命名慣例**SourceColumn** *N*資料行對應，或**SourceTable** *N*資料表對應，因為您提供的名稱可能與在現有的預設資料行對應名稱衝突**ColumnMappingCollection**或 資料表對應名稱**DataTableMappingCollection**. 如果提供的名稱已經存在，便會擲回例外狀況。  
  
## <a name="handling-multiple-result-sets"></a>處理多重結果集  
 如果您**SelectCommand**會傳回多個資料表，**填滿**會自動產生具遞增值的資料表中的資料表名稱**資料集**開始，在表單上指定資料表名稱，並繼續**TableName** *N*，從**TableName1**。 您可以使用 資料表對應至自動產生的資料表名稱對應至您想要指定資料表名稱**資料集**。 例如，對於**SelectCommand**會傳回兩個資料表**客戶**和**訂單**，發出下列呼叫來**填滿**。  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 中會建立兩個資料表**資料集**:**客戶**並**Customers1**。 您可以使用資料表對應，以確保第二個資料表名為**訂單**而不是**Customers1**。 若要這樣做，請將對應的來源資料表**Customers1**要**資料集**表格**訂單**，如下列範例所示。  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>另請參閱  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [在 ADO.NET 中擷取和修改資料](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
