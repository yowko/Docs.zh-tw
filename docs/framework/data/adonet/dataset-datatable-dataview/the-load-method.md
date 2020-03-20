---
title: Load 方法
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: f1c819333225c22efb85946001a1fc8340d57989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150723"
---
# <a name="the-load-method"></a><span data-ttu-id="8a29f-102">Load 方法</span><span class="sxs-lookup"><span data-stu-id="8a29f-102">The Load Method</span></span>
<span data-ttu-id="8a29f-103">您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="8a29f-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="8a29f-104">這是一個重載方法，其最簡單的形式是接受單個參數 **，即 DataReader**。</span><span class="sxs-lookup"><span data-stu-id="8a29f-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="8a29f-105">在此表單中，它只需使用行載入**DataTable**即可。</span><span class="sxs-lookup"><span data-stu-id="8a29f-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="8a29f-106">或者，您可以指定**LoadOption**參數來控制將資料添加到**DataTable**中的方式。</span><span class="sxs-lookup"><span data-stu-id="8a29f-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="8a29f-107">**LoadOption**參數在**DataTable**已包含資料行的情況下特別有用，因為它描述了資料來源的傳入資料如何與表中已有的資料組合。</span><span class="sxs-lookup"><span data-stu-id="8a29f-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="8a29f-108">例如，**保留當前值**（預設值）指定在**資料表中**將行標記為 **"已添加**"的情況下，**原始**值或每列將設置為數據源中匹配行的內容。</span><span class="sxs-lookup"><span data-stu-id="8a29f-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="8a29f-109">"**當前**"值將保留添加行時分配的值，行的**RowState**將設置為 **"已更改**"。</span><span class="sxs-lookup"><span data-stu-id="8a29f-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="8a29f-110">下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="8a29f-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="8a29f-111">LoadOption 值</span><span class="sxs-lookup"><span data-stu-id="8a29f-111">LoadOption value</span></span>|<span data-ttu-id="8a29f-112">描述</span><span class="sxs-lookup"><span data-stu-id="8a29f-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="8a29f-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="8a29f-113">**OverwriteRow**</span></span>|<span data-ttu-id="8a29f-114">如果傳入行具有與**DataTable**中已有的行相同的**主鍵**值，則每列**的原始**值和**當前**值將替換為傳入行中的值，並且**RowState**屬性設置為 **"未更改**"。</span><span class="sxs-lookup"><span data-stu-id="8a29f-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="8a29f-115">**資料表中**不存在的資料來源中的行添加的**RowState**值**為"未更改**"。</span><span class="sxs-lookup"><span data-stu-id="8a29f-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="8a29f-116">此選項實際上刷新**了 DataTable**的內容，以便它與資料來源的內容匹配。</span><span class="sxs-lookup"><span data-stu-id="8a29f-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="8a29f-117">**PreserveCurrentValues (預設值)**</span><span class="sxs-lookup"><span data-stu-id="8a29f-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="8a29f-118">如果傳入行具有與**DataTable**中已有的行相同的**主鍵**值，則**原始**值將設置為傳入行的內容，並且不會更改 **"當前"** 值。</span><span class="sxs-lookup"><span data-stu-id="8a29f-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="8a29f-119">如果 **"行狀態**已**添加**或**修改**"，則將其設置為 **"已修改**"。</span><span class="sxs-lookup"><span data-stu-id="8a29f-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="8a29f-120">如果**RowState** **已刪除**，則保留**為 "已刪除**"。</span><span class="sxs-lookup"><span data-stu-id="8a29f-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="8a29f-121">將添加**DataTable**中不存在的資料來源中的行，並將**RowState**設置為 **"未更改**"。</span><span class="sxs-lookup"><span data-stu-id="8a29f-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="8a29f-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="8a29f-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="8a29f-123">如果傳入行具有與**DataTable**中已有的行相同的**主鍵**值，則**當前**值將複製到**原始**值，然後將 **"當前**"值設置為傳入行的內容。</span><span class="sxs-lookup"><span data-stu-id="8a29f-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="8a29f-124">如果**已添加** **DataTable**中的**行狀態**，則 **"行狀態**"將保持**已添加**。</span><span class="sxs-lookup"><span data-stu-id="8a29f-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="8a29f-125">對於標記為 **"已修改**或刪除"**的**行，將**修改\*\*\*\*"行狀態**"。</span><span class="sxs-lookup"><span data-stu-id="8a29f-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="8a29f-126">將添加**DataTable**中不存在的資料來源中的行，並將**RowState**設置為 **"已添加**"。</span><span class="sxs-lookup"><span data-stu-id="8a29f-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="8a29f-127">以下示例使用**Load**方法顯示**Northwind**資料庫中員工的生日清單。</span><span class="sxs-lookup"><span data-stu-id="8a29f-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a29f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a29f-128">See also</span></span>

- [<span data-ttu-id="8a29f-129">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="8a29f-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- <span data-ttu-id="8a29f-130">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="8a29f-130">[ADO.NET Overview](../ado-net-overview.md)</span></span>
