---
title: DataAdapter DataTable 和 DataColumn 對應
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151555"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable 和 DataColumn 對應
**DataAdapter**在其**表映射**屬性中包含零個或多個<xref:System.Data.Common.DataTableMapping>物件的集合。 **DataTableMapping**在從針對資料來源的查詢返回的資料和 之間提供主映射<xref:System.Data.DataTable>。 **資料表映射**名稱可以代替**資料表**名稱傳遞給**資料配接器**的**填充**方法。 下面的示例為 **"作者"** 表創建名為 **"作者映射"****的資料表映射**。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTable 映射**使您能夠在**DataTable**中使用與資料庫中不同的列名稱。 **資料配接器**在更新表時使用映射與列匹配。  
  
 如果在調用**DataAdapter**的**填充**或**更新**方法時未指定**表名**或**DataTable 映射**名稱，**則資料配接器**將查找名為"表"**的資料表映射**。 如果**資料表映射**不存在，**則資料表**的**表名稱**為"表"。 您可以通過創建名稱為"表"**的資料表映射**來指定預設**資料表映射**。  
  
 以下代碼示例創建**DataTable 映射**（從<xref:System.Data.Common>命名空間），並通過將其命名為"表"使其成為指定**DataAdapter**的預設映射。 然後，該示例將查詢結果中的第一個表（**北風**資料庫**的客戶**表）中的列映射到<xref:System.Data.DataSet>中的**北風客戶**表中的一組更方便使用的名稱。 未被對應的資料行會使用來自資料來源的資料行名稱。  
  
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
  
 在更高級的情況下，您可以決定希望相同的**DataAdapter**支援使用不同的映射載入不同的表。 為此，只需添加其他**DataTable 映射**物件即可。  
  
 當**填充**方法傳遞**DataSet**實例和**DataTable 映射**名稱時，如果存在具有該名稱的映射，則使用該映射;如果使用填充方法。否則，將使用具有該名稱**的資料表**。  
  
 以下示例創建一個**資料表映射**，其名稱為**客戶**，資料**表**名稱為**BizTalkSchema**。 然後，該示例將 SELECT 語句返回的行映射到**BizTalkSchema** **資料表**。  
  
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
> 若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。 如果未為列映射提供源列，則為列映射指定一個增量預設名稱**SourceColumn** *N，* 從**SourceColumn1**開始。 如果表映射未提供源表名稱，則表映射將給出**源表** *N*的增量預設名稱，從**SourceTable1**開始。  
  
> [!NOTE]
> 我們建議您避免為列映射而避免**SourceColumn** *N*的命名約定，或者為表映射保留**SourceTable** *N，* 因為提供的名稱可能與**DataTableMapping 集合**中的**列映射集合**或表映射名稱中的現有預設列映射名稱衝突。 如果提供的名稱已經存在，便會擲回例外狀況。  
  
## <a name="handling-multiple-result-sets"></a>處理多重結果集  
 如果**SelectCommand**返回多個表，**則填充**將自動生成具有**DataSet**中表的增量值的表名稱，從指定的表名稱開始，並在表**Name** *N*表單中繼續，從**表Name1**開始。 可以使用表映射將自動生成的表名稱映射到您希望在**DataSet**中為表指定的名稱。 例如，對於返回兩個表"**客戶**和**訂單**"的**SelectCommand，** 發出以下調用**Fill**。  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 在**DataSet**中創建了兩個表：**客戶**和**客戶1**。 可以使用表映射來確保第二個表名為 **"訂單"** 而不是 **"客戶1"。** 為此，將**客戶 1**的源表映射到**DataSet**表**訂單**，如以下示例所示。  
  
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
- [在 ADO.NET 中擷取和修改資料](retrieving-and-modifying-data.md)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
