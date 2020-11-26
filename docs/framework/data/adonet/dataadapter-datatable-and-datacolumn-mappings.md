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
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="83ef7-102">DataAdapter DataTable 和 DataColumn 對應</span><span class="sxs-lookup"><span data-stu-id="83ef7-102">DataAdapter DataTable and DataColumn Mappings</span></span>

<span data-ttu-id="83ef7-103">**DataAdapter** <xref:System.Data.Common.DataTableMapping> 在其 **TableMappings** 屬性中包含零或多個物件的集合。</span><span class="sxs-lookup"><span data-stu-id="83ef7-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="83ef7-104">**DataTableMapping** 會在針對資料來源的查詢所傳回的資料和之間提供主要對應 <xref:System.Data.DataTable> 。</span><span class="sxs-lookup"><span data-stu-id="83ef7-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="83ef7-105">您可以將 **DataTableMapping** 名稱取代為 **DataAdapter** 的 **Fill** 方法的 **DataTable** 名稱。</span><span class="sxs-lookup"><span data-stu-id="83ef7-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="83ef7-106">下列範例會為 **作者** 資料表建立名為 **AuthorsMapping** 的 **DataTableMapping** 。</span><span class="sxs-lookup"><span data-stu-id="83ef7-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="83ef7-107">**DataTableMapping** 可讓您在 **DataTable** 中使用與資料庫中的資料行名稱不同的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="83ef7-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="83ef7-108">當更新資料表時， **DataAdapter** 會使用對應來比對資料行。</span><span class="sxs-lookup"><span data-stu-id="83ef7-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="83ef7-109">如果您在呼叫 **DataAdapter** 的 **Fill** 或 **Update** 方法時未指定 **TableName** 或 **DataTableMapping** 名稱，則 **DataAdapter** 會尋找名為 "Table" 的 **DataTableMapping** 。</span><span class="sxs-lookup"><span data-stu-id="83ef7-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="83ef7-110">如果該 **DataTableMapping** 不存在，則 **DataTable** 的 **TableName** 為 "Table"。</span><span class="sxs-lookup"><span data-stu-id="83ef7-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="83ef7-111">您可以建立名稱為 "Table" 的 **DataTableMapping** ，以指定預設的 **DataTableMapping** 。</span><span class="sxs-lookup"><span data-stu-id="83ef7-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="83ef7-112">下列程式碼範例會建立 **DataTableMapping** <xref:System.Data.Common> 命名空間) 的 DataTableMapping (，並將其命名為 "Table"，使其成為指定之 **DataAdapter** 的預設對應。</span><span class="sxs-lookup"><span data-stu-id="83ef7-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="83ef7-113">然後，此範例會將查詢結果中第一個資料表的資料行， (**northwind** 資料庫的 **Customers** 資料表，) 到中的 **northwind customers** 資料表中的一組更易記的名稱 <xref:System.Data.DataSet> 。</span><span class="sxs-lookup"><span data-stu-id="83ef7-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="83ef7-114">未被對應的資料行會使用來自資料來源的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="83ef7-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="83ef7-115">在更先進的情況下，您可能會決定要使用相同的 **DataAdapter** 來支援載入具有不同對應的不同資料表。</span><span class="sxs-lookup"><span data-stu-id="83ef7-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="83ef7-116">若要這樣做，只需新增其他 **DataTableMapping** 物件。</span><span class="sxs-lookup"><span data-stu-id="83ef7-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="83ef7-117">當將 **資料集** 的實例和 **DataTableMapping** 名稱傳遞給 **Fill** 方法時，如果使用具有該名稱的對應，就會使用它。否則，就會使用具有該名稱的 **DataTable** 。</span><span class="sxs-lookup"><span data-stu-id="83ef7-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="83ef7-118">下列範例會建立名稱為 **Customers** 的 **DataTableMapping** 和 **DataTable** name of **biztalkschemadatatable**。</span><span class="sxs-lookup"><span data-stu-id="83ef7-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="83ef7-119">然後，此範例會將 SELECT 語句傳回的資料列對應至 **biztalkschemadatatable** **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="83ef7-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
> <span data-ttu-id="83ef7-120">若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。</span><span class="sxs-lookup"><span data-stu-id="83ef7-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="83ef7-121">如果沒有為資料行對應提供來源資料行，則會將資料行對應的增量預設名稱指定為 **SourceColumn** *N，* 從 **SourceColumn1** 開始。</span><span class="sxs-lookup"><span data-stu-id="83ef7-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="83ef7-122">如果未提供資料表對應的來源資料表名稱，則會為數據表對應指定 **SourceTable** *N* 的增量預設名稱，從 **SourceTable1** 開始。</span><span class="sxs-lookup"><span data-stu-id="83ef7-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83ef7-123">建議您避免在資料行對應中使用 **SourceColumn** *N* 的命名慣例，或針對資料表對應來 **SourceTable** *N* ，因為您所提供的名稱可能會與 **衝突** 中 **datatablemappingcollection** 或資料表對應名稱中現有的預設資料行對應名稱相衝突。</span><span class="sxs-lookup"><span data-stu-id="83ef7-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="83ef7-124">如果提供的名稱已經存在，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="83ef7-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="83ef7-125">處理多重結果集</span><span class="sxs-lookup"><span data-stu-id="83ef7-125">Handling Multiple Result Sets</span></span>  

 <span data-ttu-id="83ef7-126">如果您的 **SelectCommand** 傳回多個資料表，則 **填滿** 會自動產生 **資料集中** 資料表的累加值的資料表名稱，以指定的資料表名稱為開頭，並 **TableName** 以資料表名稱（從 \**TableName1\*\*\*開始）繼續* 進行。</span><span class="sxs-lookup"><span data-stu-id="83ef7-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="83ef7-127">您可以使用資料表對應，將自動產生的資料表名稱對應到您想要在 **資料集中** 為數據表指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="83ef7-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="83ef7-128">例如，針對傳回兩個數據表、**客戶** 和 **訂單** 的 **SelectCommand** ，發出下列要 **填滿** 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="83ef7-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="83ef7-129">**資料集** 內會建立兩個數據表：**客戶** 和 **Customers1**。</span><span class="sxs-lookup"><span data-stu-id="83ef7-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="83ef7-130">您可以使用資料表對應，以確保第二個數據表的名稱為 **Orders** ，而不是 **Customers1**。</span><span class="sxs-lookup"><span data-stu-id="83ef7-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="83ef7-131">若要這樣做，請將 **Customers1** 的來源資料表對應至 **資料集** 資料表 **訂單**，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="83ef7-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="83ef7-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83ef7-132">See also</span></span>

- [<span data-ttu-id="83ef7-133">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="83ef7-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="83ef7-134">在 ADO.NET 中傳送和修改資料</span><span class="sxs-lookup"><span data-stu-id="83ef7-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- <span data-ttu-id="83ef7-135">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="83ef7-135">[ADO.NET Overview](ado-net-overview.md)</span></span>
