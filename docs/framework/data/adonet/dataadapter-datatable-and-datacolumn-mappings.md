---
title: "DataAdapter DataTable 和 DataColumn 對應"
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
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e104ba75026c2ff387eb7c74b11c505e34085f41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="a1a4b-102">DataAdapter DataTable 和 DataColumn 對應</span><span class="sxs-lookup"><span data-stu-id="a1a4b-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="a1a4b-103">A **DataAdapter**包含零或多個集合<xref:System.Data.Common.DataTableMapping>物件在其**TableMappings**屬性。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="a1a4b-104">A **DataTableMapping**提供對資料來源，查詢傳回的資料之間的主要對應和<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a1a4b-105">**DataTableMapping**名稱可以傳遞取代**DataTable**名稱**填滿**方法**DataAdapter**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="a1a4b-106">下列範例會建立**DataTableMapping**名為**AuthorsMapping**如**作者**資料表。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="a1a4b-107">A **DataTableMapping**可讓您使用的資料行名稱**DataTable**不同的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="a1a4b-108">**DataAdapter**使用對應來更新資料表時，符合的資料行。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="a1a4b-109">如果您未指定**TableName**或**DataTableMapping**名稱就呼叫**填滿**或**更新**方法**DataAdapter**、 **DataAdapter**尋找**DataTableMapping**名為"Table"。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="a1a4b-110">如果該**DataTableMapping**不存在， **TableName**的**DataTable**是 「 資料表 」。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="a1a4b-111">您可以指定預設值**DataTableMapping**藉由建立**DataTableMapping** 「 資料表 」 的名稱。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="a1a4b-112">下列程式碼範例會建立**DataTableMapping** (從<xref:System.Data.Common>命名空間)，並讓指定的預設對應**DataAdapter**由其命名為"Table"。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="a1a4b-113">此範例接著將對應從查詢結果中的第一個資料表的資料行 (**客戶**資料表**Northwind**資料庫) 中更加易懂易記名稱的一組**Northwind Customers**資料表中<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="a1a4b-114">未被對應的資料行會使用來自資料來源的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
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
  
 <span data-ttu-id="a1a4b-115">在更進階的情況下，您可能決定要相同**DataAdapter**載入具有不同對應的不同資料表。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="a1a4b-116">若要這樣做，只要加入其他**DataTableMapping**物件。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="a1a4b-117">當**填滿**傳遞給方法的執行個體**資料集**和**DataTableMapping** ，具有該名稱的對應已存在，則會使用; 否則**DataTable**使用具有該名稱。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="a1a4b-118">下列範例會建立**DataTableMapping**名稱為**客戶**和**DataTable**名稱**BizTalkSchema**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="a1a4b-119">此範例則會對應到 SELECT 陳述式所傳回的資料列**BizTalkSchema** **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
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
>  <span data-ttu-id="a1a4b-120">若未提供來源資料行名稱給資料行對應，或是未提供來源資料表名稱給資料表對應，便會自動產生預設名稱。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="a1a4b-121">如果沒有來源資料行提供給資料行對應時，資料行對應指定的遞增預設名稱**SourceColumn** *N*開頭**SourceColumn1**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="a1a4b-122">如果沒有來源資料表名稱提供給資料表對應，該資料表對應指定的遞增預設名稱**SourceTable** *N*開始， **SourceTable1**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1a4b-123">我們建議您避免命名慣例的**SourceColumn** *N*給資料行對應，或**SourceTable** *N*資料表對應，因為您提供的名稱可能與現有預設資料行對應中的名稱衝突**ColumnMappingCollection**或資料表中的對應名稱**DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="a1a4b-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="a1a4b-124">如果提供的名稱已經存在，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="a1a4b-125">處理多重結果集</span><span class="sxs-lookup"><span data-stu-id="a1a4b-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="a1a4b-126">如果您**SelectCommand**傳回多個資料表，**填滿**遞增的值中的資料表的資料表名稱會自動產生**資料集**開始，在表單上指定資料表名稱，並繼續**TableName** *N*開始， **TableName1**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="a1a4b-127">您可以使用資料表對應至自動產生的資料表名稱對應到您要指定給中的資料表名稱**資料集**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="a1a4b-128">例如，對於**SelectCommand**傳回兩個資料表**客戶**和**訂單**，發出下列呼叫**填滿**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="a1a4b-129">兩個資料表會建立在**資料集**:**客戶**和**Customers1**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="a1a4b-130">您可以使用資料表對應，以確保第二個資料表名為**訂單**而不是**Customers1**。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="a1a4b-131">若要這樣做，請將對應的來源資料表**Customers1**至**資料集**資料表**訂單**，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a1a4b-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1a4b-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="a1a4b-132">See Also</span></span>  
 [<span data-ttu-id="a1a4b-133">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="a1a4b-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="a1a4b-134">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="a1a4b-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="a1a4b-135">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="a1a4b-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
