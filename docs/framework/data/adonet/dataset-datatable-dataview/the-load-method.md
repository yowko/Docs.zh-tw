---
title: Load 方法
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: da0695aff9447355b1fc44a033c1b4a1cc224435
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785877"
---
# <a name="the-load-method"></a><span data-ttu-id="12b90-102">Load 方法</span><span class="sxs-lookup"><span data-stu-id="12b90-102">The Load Method</span></span>
<span data-ttu-id="12b90-103">您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="12b90-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="12b90-104">這是一種多載方法，其最簡單的形式是接受單一參數，也就是**DataReader**。</span><span class="sxs-lookup"><span data-stu-id="12b90-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="12b90-105">在此表單中，它只會載入具有資料列的**DataTable** 。</span><span class="sxs-lookup"><span data-stu-id="12b90-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="12b90-106">（選擇性）您可以指定**LoadOption**參數來控制資料加入至**DataTable**的方式。</span><span class="sxs-lookup"><span data-stu-id="12b90-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="12b90-107">在**DataTable**已經包含資料列的情況下， **LoadOption**參數特別有用，因為它會描述資料來源的傳入資料如何與已經在資料表中的資料結合。</span><span class="sxs-lookup"><span data-stu-id="12b90-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="12b90-108">例如， **PreserveCurrentValues** （預設值）指定在**DataTable**中將資料列標示為**已加入**時，會將**原始**值或每個資料行設定為數據源中相符的資料列內容。</span><span class="sxs-lookup"><span data-stu-id="12b90-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="12b90-109">當加入資料列時，**目前**的值會保留指派的值，而資料列的**RowState**會設定為**已變更**。</span><span class="sxs-lookup"><span data-stu-id="12b90-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="12b90-110">下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="12b90-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="12b90-111">LoadOption 值</span><span class="sxs-lookup"><span data-stu-id="12b90-111">LoadOption value</span></span>|<span data-ttu-id="12b90-112">說明</span><span class="sxs-lookup"><span data-stu-id="12b90-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="12b90-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="12b90-113">**OverwriteRow**</span></span>|<span data-ttu-id="12b90-114">如果內送資料列的**PrimaryKey**值與**DataTable**中已經存在的資料列相同，則會將每個資料行的**原始**值和**目前**值取代為內送資料列中的值，並將**RowState**屬性設定為**未**變更。</span><span class="sxs-lookup"><span data-stu-id="12b90-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="12b90-115">資料來源中不存在於**DataTable**中的資料列會以 [**未**變更] 的**RowState**值來加入。</span><span class="sxs-lookup"><span data-stu-id="12b90-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="12b90-116">此選項實際上會重新整理**DataTable**的內容，使其符合資料來源的內容。</span><span class="sxs-lookup"><span data-stu-id="12b90-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="12b90-117">**PreserveCurrentValues （預設值）**</span><span class="sxs-lookup"><span data-stu-id="12b90-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="12b90-118">如果內送資料列的**PrimaryKey**值與**DataTable**中已經存在的資料列相同，則**原始**值會設為傳入資料列的內容，而**目前**的值不會變更。</span><span class="sxs-lookup"><span data-stu-id="12b90-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="12b90-119">如果**RowState**已**新增**或**修改**，則會設定為 [**已修改**]。</span><span class="sxs-lookup"><span data-stu-id="12b90-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="12b90-120">如果**RowState**已**刪除**，它會保持**刪除**。</span><span class="sxs-lookup"><span data-stu-id="12b90-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="12b90-121">不存在於**DataTable**中的資料來源中的資料列會加入，而且**RowState**會設定為**未**變更。</span><span class="sxs-lookup"><span data-stu-id="12b90-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="12b90-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="12b90-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="12b90-123">如果內送資料列的**PrimaryKey**值與**DataTable**中已經存在的資料列相同，則**目前**的值會複製到**原始**值，而**目前**的值會設定為內送資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="12b90-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="12b90-124">如果**加入** **DataTable**中的**RowState** ，則**RowState**會保持**新增**。</span><span class="sxs-lookup"><span data-stu-id="12b90-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="12b90-125">針對標示為**已修改**或**已刪除**的資料列，會**修改** **RowState** 。</span><span class="sxs-lookup"><span data-stu-id="12b90-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="12b90-126">系統會新增資料來源中不存在於**DataTable**中的資料列，並將**RowState**設定為 [**已加入**]。</span><span class="sxs-lookup"><span data-stu-id="12b90-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="12b90-127">下列範例會使用**Load**方法，針對**Northwind**資料庫中的員工顯示生日清單。</span><span class="sxs-lookup"><span data-stu-id="12b90-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
```vb  
Private Sub LoadBirthdays(ByVal connectionString As String)  
    ' Assumes that connectionString is a valid connection string  
    ' to the Northwind database on SQL Server.  
    Dim queryString As String = _  
    "SELECT LastName, FirstName, BirthDate " & _  
      " FROM dbo.Employees " & _  
      "ORDER BY BirthDate, LastName, FirstName"  
  
    ' Open and fill a DataSet.   
    Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
        queryString, connectionString)  
    Dim employees As New DataSet  
    adapter.Fill(employees, "Employees")  
  
    ' Create a SqlDataReader for use with the Load Method.  
    Dim reader As DataTableReader = employees.GetDataReader()  
  
    ' Create an instance of DataTable and assign the first  
    ' DataTable in the DataSet.Tables collection to it.  
    Dim dataTableEmp As DataTable = employees.Tables(0)  
  
    ' Fill the DataTable with data by calling Load and  
    ' passing the SqlDataReader.  
    dataTableEmp.Load(reader, LoadOption.OverwriteRow)  
  
    ' Loop through the rows collection and display the values  
    ' in the console window.  
    Dim employeeRow As DataRow  
    For Each employeeRow In dataTableEmp.Rows  
        Console.WriteLine("{0:MM\\dd\\yyyy}" & ControlChars.Tab & _  
          "{1}, {2}", _  
          employeeRow("BirthDate"), _  
          employeeRow("LastName"), _  
          employeeRow("FirstName"))  
    Next employeeRow  
  
    ' Keep the window opened to view the contents.  
    Console.ReadLine()  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="12b90-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12b90-128">See also</span></span>

- [<span data-ttu-id="12b90-129">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="12b90-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="12b90-130">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="12b90-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
