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
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="09575-102">DataAdapter DataTable 和 DataColumn 對應</span><span class="sxs-lookup"><span data-stu-id="09575-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="09575-103">**DataAdapter**在其**表映射**屬性中包含零個或多個<xref:System.Data.Common.DataTableMapping>物件的集合。</span><span class="sxs-lookup"><span data-stu-id="09575-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="09575-104">**DataTableMapping**在從針對資料來源的查詢返回的資料和 之間提供主映射<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="09575-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="09575-105">**資料表映射**名稱可以代替**資料表**名稱傳遞給**資料配接器**的**填充**方法。</span><span class="sxs-lookup"><span data-stu-id="09575-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="09575-106">下面的示例為 **"作者"** 表創建名為 **"作者映射"\*\*\*\*的資料表映射**。</span><span class="sxs-lookup"><span data-stu-id="09575-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="09575-107">**DataTable 映射**使您能夠在**DataTable**中使用與資料庫中不同的列名稱。</span><span class="sxs-lookup"><span data-stu-id="09575-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="09575-108">**資料配接器**在更新表時使用映射與列匹配。</span><span class="sxs-lookup"><span data-stu-id="09575-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="09575-109">如果在調用**DataAdapter**的**填充**或**更新**方法時未指定**表名**或**DataTable 映射**名稱，**則資料配接器**將查找名為"表"**的資料表映射**。</span><span class="sxs-lookup"><span data-stu-id="09575-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="09575-110">如果**資料表映射**不存在，**則資料表**的**表名稱**為"表"。</span><span class="sxs-lookup"><span data-stu-id="09575-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="09575-111">您可以通過創建名稱為"表"**的資料表映射**來指定預設**資料表映射**。</span><span class="sxs-lookup"><span data-stu-id="09575-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="09575-112">以下代碼示例創建**DataTable 映射**（從<xref:System.Data.Common>命名空間），並通過將其命名為"表"使其成為指定**DataAdapter**的預設映射。</span><span class="sxs-lookup"><span data-stu-id="09575-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="09575-113">然後，該示例將查詢結果中的第一個表（**北風**資料庫**的客戶**表）中的列映射到<xref:System.Data.DataSet>中的**北風客戶**表中的一組更方便使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="09575-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="09575-114">未被對應的資料行會使用來自資料來源的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="09575-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="09575-115">在更高級的情況下，您可以決定希望相同的**DataAdapter**支援使用不同的映射載入不同的表。</span><span class="sxs-lookup"><span data-stu-id="09575-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="09575-116">為此，只需添加其他**DataTable 映射**物件即可。</span><span class="sxs-lookup"><span data-stu-id="09575-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="09575-117">當**填充**方法傳遞**DataSet**實例和**DataTable 映射**名稱時，如果存在具有該名稱的映射，則使用該映射;如果使用填充方法。否則，將使用具有該名稱**的資料表**。</span><span class="sxs-lookup"><span data-stu-id="09575-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="09575-118">以下示例創建一個**資料表映射**，其名稱為**客戶**，資料**表**名稱為**BizTalkSchema**。</span><span class="sxs-lookup"><span data-stu-id="09575-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="09575-119">然後，該示例將 SELECT 語句返回的行映射到**BizTalkSchema** **資料表**。</span><span class="sxs-lookup"><span data-stu-id="09575-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
> <span data-ttu-id="09575-120">若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。</span><span class="sxs-lookup"><span data-stu-id="09575-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="09575-121">如果未為列映射提供源列，則為列映射指定一個增量預設名稱**SourceColumn** *N，* 從**SourceColumn1**開始。</span><span class="sxs-lookup"><span data-stu-id="09575-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="09575-122">如果表映射未提供源表名稱，則表映射將給出**源表** *N*的增量預設名稱，從**SourceTable1**開始。</span><span class="sxs-lookup"><span data-stu-id="09575-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09575-123">我們建議您避免為列映射而避免**SourceColumn** *N*的命名約定，或者為表映射保留**SourceTable** *N，* 因為提供的名稱可能與**DataTableMapping 集合**中的**列映射集合**或表映射名稱中的現有預設列映射名稱衝突。</span><span class="sxs-lookup"><span data-stu-id="09575-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="09575-124">如果提供的名稱已經存在，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="09575-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="09575-125">處理多重結果集</span><span class="sxs-lookup"><span data-stu-id="09575-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="09575-126">如果**SelectCommand**返回多個表，**則填充**將自動生成具有**DataSet**中表的增量值的表名稱，從指定的表名稱開始，並在表**Name** *N*表單中繼續，從**表Name1**開始。</span><span class="sxs-lookup"><span data-stu-id="09575-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="09575-127">可以使用表映射將自動生成的表名稱映射到您希望在**DataSet**中為表指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="09575-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="09575-128">例如，對於返回兩個表"**客戶**和**訂單**"的**SelectCommand，** 發出以下調用**Fill**。</span><span class="sxs-lookup"><span data-stu-id="09575-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="09575-129">在**DataSet**中創建了兩個表：**客戶**和**客戶1**。</span><span class="sxs-lookup"><span data-stu-id="09575-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="09575-130">可以使用表映射來確保第二個表名為 **"訂單"** 而不是 **"客戶1"。**</span><span class="sxs-lookup"><span data-stu-id="09575-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="09575-131">為此，將**客戶 1**的源表映射到**DataSet**表**訂單**，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="09575-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="09575-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09575-132">See also</span></span>

- [<span data-ttu-id="09575-133">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="09575-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="09575-134">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="09575-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="09575-135">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="09575-135">[ADO.NET Overview](ado-net-overview.md)</span></span>
