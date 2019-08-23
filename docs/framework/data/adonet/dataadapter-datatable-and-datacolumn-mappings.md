---
title: DataAdapter DataTable 和 DataColumn 對應
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: eb6841dd24c4c7587cc2424cc1e606194da34585
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944067"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="f99f0-102">DataAdapter DataTable 和 DataColumn 對應</span><span class="sxs-lookup"><span data-stu-id="f99f0-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="f99f0-103">**DataAdapter**在其 TableMappings 屬性中包含零個<xref:System.Data.Common.DataTableMapping>或多個物件的集合。</span><span class="sxs-lookup"><span data-stu-id="f99f0-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="f99f0-104">**DataTableMapping**會在從查詢傳回的資料與資料來源之間提供主要對應, 以及<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="f99f0-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="f99f0-105">**DataTableMapping**名稱可以代替**DataTable**名稱傳遞到**DataAdapter**的**Fill**方法。</span><span class="sxs-lookup"><span data-stu-id="f99f0-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="f99f0-106">下列範例會為**作者**資料表建立名為**AuthorsMapping**的**DataTableMapping** 。</span><span class="sxs-lookup"><span data-stu-id="f99f0-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="f99f0-107">**DataTableMapping**可讓您在**DataTable**中使用與資料庫中不同的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="f99f0-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="f99f0-108">當更新資料表時, **DataAdapter**會使用對應來比對資料行。</span><span class="sxs-lookup"><span data-stu-id="f99f0-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="f99f0-109">如果您在呼叫**DataAdapter**的**Fill**或**Update**方法時未指定**TableName**或**DataTableMapping**名稱, **dataadapter**會尋找名為 "Table" 的**DataTableMapping** 。</span><span class="sxs-lookup"><span data-stu-id="f99f0-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="f99f0-110">如果該**DataTableMapping**不存在, **DataTable**的**TableName**就是 "Table"。</span><span class="sxs-lookup"><span data-stu-id="f99f0-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="f99f0-111">您可以藉由建立名為 "Table" 的**DataTableMapping**來指定預設**DataTableMapping** 。</span><span class="sxs-lookup"><span data-stu-id="f99f0-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="f99f0-112">下列程式碼範例會建立**DataTableMapping** (從<xref:System.Data.Common>命名空間), 並將它命名為 "Table", 使其成為指定**DataAdapter**的預設對應。</span><span class="sxs-lookup"><span data-stu-id="f99f0-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="f99f0-113">然後, 此範例會將查詢結果 ( **northwind**資料庫的**Customers**資料表) 中第一個資料表的資料行對應至中**Northwind** <xref:System.Data.DataSet>Customers 資料表內的一組更好的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="f99f0-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f99f0-114">未被對應的資料行會使用來自資料來源的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="f99f0-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="f99f0-115">在更先進的情況下, 您可能會決定您想要讓相同的**DataAdapter**支援使用不同的對應來載入不同的資料表。</span><span class="sxs-lookup"><span data-stu-id="f99f0-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="f99f0-116">若要這樣做, 只需新增額外的**DataTableMapping**物件即可。</span><span class="sxs-lookup"><span data-stu-id="f99f0-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="f99f0-117">將**資料集**的實例和**DataTableMapping**名稱傳遞給**Fill**方法時, 如果使用該名稱的對應存在, 則會使用它;否則, 會使用具有該名稱的**DataTable** 。</span><span class="sxs-lookup"><span data-stu-id="f99f0-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="f99f0-118">下列範例會建立**DataTableMapping** , 其名稱為**Customers** , 而**DataTable**名稱為**BizTalkSchema**。</span><span class="sxs-lookup"><span data-stu-id="f99f0-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="f99f0-119">然後, 此範例會將 SELECT 語句所傳回的資料列對應至**BizTalkSchema** **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="f99f0-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
> <span data-ttu-id="f99f0-120">若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。</span><span class="sxs-lookup"><span data-stu-id="f99f0-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="f99f0-121">如果未提供資料行對應的來源資料行, 則會從**SourceColumn1**開始, 資料行對應會提供一個增量預設名稱**SourceColumn** *N* 。</span><span class="sxs-lookup"><span data-stu-id="f99f0-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="f99f0-122">如果沒有為資料表對應提供來源資料表名稱, 則會為數據表對應提供**SourceTable** *N*的累加預設名稱, 從**SourceTable1**開始。</span><span class="sxs-lookup"><span data-stu-id="f99f0-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f99f0-123">我們建議您避免資料行對應使用**SourceColumn** *N*的命名慣例, 或針對資料表對應來**SourceTable** *N* , 因為您所提供的名稱可能會與中**現有的預設資料行對應名稱衝突。** **衝突**中的 ColumnMappingCollection 或資料表對應名稱。</span><span class="sxs-lookup"><span data-stu-id="f99f0-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="f99f0-124">如果提供的名稱已經存在，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f99f0-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="f99f0-125">處理多重結果集</span><span class="sxs-lookup"><span data-stu-id="f99f0-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="f99f0-126">如果您的**SelectCommand**傳回多個資料表, **Fill**會自動針對**資料集**內的資料表產生具有累加值的資料表名稱, 並以指定的資料表名稱作為開頭, 並在表單**TableName**中繼續進行。*N*, 從**TableName1**開始。</span><span class="sxs-lookup"><span data-stu-id="f99f0-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="f99f0-127">您可以使用資料表對應, 將自動產生的資料表名稱對應至您想要在**資料集中**為數據表指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="f99f0-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="f99f0-128">例如, 針對傳回兩個數據表 ( **Customers**和**Orders**) 的**SelectCommand** , 請發出下列呼叫以進行**填滿**。</span><span class="sxs-lookup"><span data-stu-id="f99f0-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="f99f0-129">**資料集**內會建立兩個數據表:**客戶**和**Customers1**。</span><span class="sxs-lookup"><span data-stu-id="f99f0-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="f99f0-130">您可以使用資料表對應來確保第二個數據表的名稱是**Orders** , 而不是**Customers1**。</span><span class="sxs-lookup"><span data-stu-id="f99f0-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="f99f0-131">若要這樣做, 請將**Customers1**的來源資料表對應至**資料集**資料表**訂單**, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="f99f0-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="f99f0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f99f0-132">See also</span></span>

- [<span data-ttu-id="f99f0-133">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="f99f0-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="f99f0-134">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="f99f0-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="f99f0-135">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="f99f0-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
