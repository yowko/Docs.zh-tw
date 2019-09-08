---
title: 將現有條件約束加入至資料集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: db072692eba4044e854f25ff2c7f8c9960714018
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785120"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="213c8-102">將現有條件約束加入至資料集</span><span class="sxs-lookup"><span data-stu-id="213c8-102">Adding Existing Constraints to a DataSet</span></span>
<span data-ttu-id="213c8-103">**DataAdapter**的<xref:System.Data.DataSet> **Fill**方法只會將資料來源中的資料表資料行和資料列填滿。雖然條件約束通常是由資料來源所設定，但**Fill**方法並不會將此架構資訊新增至**預設為資料集**。</span><span class="sxs-lookup"><span data-stu-id="213c8-103">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="213c8-104">若要使用資料來源中現有的 primary key 條件約束資訊來填入**資料集**，您可以呼叫**dataadapter**的**FillSchema**方法，或設定**dataadapter**的**MissingSchemaAction**屬性在呼叫**Fill**之前**missingschemaaction.addwithkey** 。</span><span class="sxs-lookup"><span data-stu-id="213c8-104">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="213c8-105">這可確保資料**集中**的 primary key 條件約束反映在資料來源中。</span><span class="sxs-lookup"><span data-stu-id="213c8-105">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="213c8-106">外鍵條件約束資訊不會包含在內，而且必須明確建立，如[DataTable 條件約束](./dataset-datatable-dataview/datatable-constraints.md)中所示。</span><span class="sxs-lookup"><span data-stu-id="213c8-106">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](./dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="213c8-107">在將架構資訊填入資料之前，將其加入**dataset** ，可確保<xref:System.Data.DataTable> **資料集**內的物件會包含 primary key 條件約束。</span><span class="sxs-lookup"><span data-stu-id="213c8-107">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="213c8-108">如此一來，當進行額外的填入資料**集**的呼叫時，就會使用主鍵資料行資訊來比對資料來源中的新資料列與每個**DataTable**中的目前資料列，並使用來自的資料來覆寫資料表中的目前資料。資料來源。</span><span class="sxs-lookup"><span data-stu-id="213c8-108">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="213c8-109">如果沒有架構資訊，資料來源中的新資料列就會附加至資料**集**，因而產生重複的資料列。</span><span class="sxs-lookup"><span data-stu-id="213c8-109">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="213c8-110">如果資料來源中的資料行識別為自動遞增、 **FillSchema**方法或**MissingSchemaAction**為**missingschemaaction.addwithkey**的**Fill**方法，會建立具有**自動**累加屬性的**DataColumn**將設定`true`為。</span><span class="sxs-lookup"><span data-stu-id="213c8-110">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="213c8-111">不過，您將需要自行設定**AutoIncrementStep**和**AutoIncrementSeed**值。</span><span class="sxs-lookup"><span data-stu-id="213c8-111">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="213c8-112">如需自動遞增資料行的詳細資訊，請參閱[建立自動](./dataset-datatable-dataview/creating-autoincrement-columns.md)調整資料行。</span><span class="sxs-lookup"><span data-stu-id="213c8-112">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
 <span data-ttu-id="213c8-113">使用**FillSchema**或將**MissingSchemaAction**設定為**missingschemaaction.addwithkey**時，需要在資料來源進行額外的處理，以判斷主鍵資料行資訊。</span><span class="sxs-lookup"><span data-stu-id="213c8-113">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="213c8-114">這些其他作業可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="213c8-114">This additional processing can hinder performance.</span></span> <span data-ttu-id="213c8-115">如果您在設計階段就已知道主索引鍵資訊，建議您明確地指定主索引鍵資料行，以達到最佳效能。</span><span class="sxs-lookup"><span data-stu-id="213c8-115">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="213c8-116">如需明確設定資料表主鍵資訊的相關資訊，請參閱[定義主鍵](./dataset-datatable-dataview/defining-primary-keys.md)。</span><span class="sxs-lookup"><span data-stu-id="213c8-116">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="213c8-117">下列程式碼範例示範如何使用**FillSchema**將架構資訊新增至**資料集**。</span><span class="sxs-lookup"><span data-stu-id="213c8-117">The following code example shows how to add schema information to a **DataSet** using **FillSchema**.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 <span data-ttu-id="213c8-118">下列程式碼範例示範如何使用**Fill**方法的**MissingSchemaAction. missingschemaaction.addwithkey**屬性，將架構資訊新增至**資料集**。</span><span class="sxs-lookup"><span data-stu-id="213c8-118">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method.</span></span>  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="213c8-119">處理多重結果集</span><span class="sxs-lookup"><span data-stu-id="213c8-119">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="213c8-120">如果**DataAdapter**遇到從**SelectCommand**傳回的多個結果集，它會在**資料集中**建立多個資料表。</span><span class="sxs-lookup"><span data-stu-id="213c8-120">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="213c8-121">資料表會提供以零為基底的增量預設名稱**table** *N*，開頭為**table** ，而不是 "Table0"。</span><span class="sxs-lookup"><span data-stu-id="213c8-121">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="213c8-122">如果將資料表名稱當做引數傳遞至**FillSchema**方法，則會為數據表指定以零為基底的**tablename** *N*增量名稱，從**Tablename**開始，而不是 "TableName0"。</span><span class="sxs-lookup"><span data-stu-id="213c8-122">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="213c8-123">如果針對傳回多個結果集的命令呼叫**OleDbDataAdapter**物件的**FillSchema**方法，則只會傳回第一個結果集的架構資訊。</span><span class="sxs-lookup"><span data-stu-id="213c8-123">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="213c8-124">使用**OleDbDataAdapter**傳回多個結果集的架構資訊時，建議您指定**missingschemaaction.addwithkey**的**MissingSchemaAction** ，並在呼叫**Fill**時取得架構資訊。方法.</span><span class="sxs-lookup"><span data-stu-id="213c8-124">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="213c8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="213c8-125">See also</span></span>

- [<span data-ttu-id="213c8-126">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="213c8-126">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="213c8-127">DataSet、DataTable 和 DataView</span><span class="sxs-lookup"><span data-stu-id="213c8-127">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="213c8-128">在 ADO.NET 中擷取和修改資料</span><span class="sxs-lookup"><span data-stu-id="213c8-128">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="213c8-129">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="213c8-129">ADO.NET Overview</span></span>](ado-net-overview.md)
