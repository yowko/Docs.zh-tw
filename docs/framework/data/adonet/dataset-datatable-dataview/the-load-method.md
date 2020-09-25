---
title: Load 方法
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: ea437d1f8ed567934acafbd8db1f8dba8eb22bcc
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177536"
---
# <a name="the-load-method"></a><span data-ttu-id="e403b-102">Load 方法</span><span class="sxs-lookup"><span data-stu-id="e403b-102">The Load Method</span></span>

<span data-ttu-id="e403b-103">您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="e403b-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="e403b-104">這是一種多載方法，其最簡單的形式是接受單一參數，也就是 **DataReader**。</span><span class="sxs-lookup"><span data-stu-id="e403b-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="e403b-105">在這種形式中，它只會載入具有資料列的 **DataTable** 。</span><span class="sxs-lookup"><span data-stu-id="e403b-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="e403b-106">您可以選擇性地指定 **LoadOption** 參數，以控制如何將資料加入 **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="e403b-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="e403b-107">當**DataTable**已經包含資料列時， **LoadOption**參數特別有用，因為它會說明資料來源中的傳入資料如何與已經存在於資料表中的資料結合。</span><span class="sxs-lookup"><span data-stu-id="e403b-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="e403b-108">例如， **PreserveCurrentValues** (預設) 指定在**資料表**中標記為**已加入**的資料列，**原始**值或每個資料行會設定為數據源中相符資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="e403b-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="e403b-109">**目前**的值會保留加入資料列時指派的值，而且資料列的**RowState**會設定為 [**已變更**]。</span><span class="sxs-lookup"><span data-stu-id="e403b-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="e403b-110">下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="e403b-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="e403b-111">LoadOption 值</span><span class="sxs-lookup"><span data-stu-id="e403b-111">LoadOption value</span></span>|<span data-ttu-id="e403b-112">描述</span><span class="sxs-lookup"><span data-stu-id="e403b-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="e403b-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="e403b-113">**OverwriteRow**</span></span>|<span data-ttu-id="e403b-114">如果內送資料列的 **PrimaryKey** 值與 **DataTable**中既有的資料列相同，則會將每個資料行的 **原始** 值和 **目前** 值取代為內送資料列中的值，並將 **RowState** 屬性設定為 **未**變更。</span><span class="sxs-lookup"><span data-stu-id="e403b-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="e403b-115">資料來源中尚未存在 **DataTable** 中的資料列會加入，且 **RowState** 值為 [ **未**變更]。</span><span class="sxs-lookup"><span data-stu-id="e403b-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="e403b-116">此選項實際上會重新整理 **DataTable** 的內容，使其與資料來源的內容相符。</span><span class="sxs-lookup"><span data-stu-id="e403b-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="e403b-117">**PreserveCurrentValues (預設值)**</span><span class="sxs-lookup"><span data-stu-id="e403b-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="e403b-118">如果內送資料列的 **PrimaryKey** 值與 **DataTable**中的資料列相同，則會將 **原始** 值設定為內送資料列的內容，而且 **目前** 的值不會變更。</span><span class="sxs-lookup"><span data-stu-id="e403b-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="e403b-119">如果**新增**或**修改** **RowState** ，它會設定為 [**已修改**]。</span><span class="sxs-lookup"><span data-stu-id="e403b-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="e403b-120">如果 **RowState** 已 **刪除**，則會保持 **刪除**。</span><span class="sxs-lookup"><span data-stu-id="e403b-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="e403b-121">資料來源中尚未存在 **DataTable** 中的資料列會加入，且 **RowState** 會設定為 **未**變更。</span><span class="sxs-lookup"><span data-stu-id="e403b-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="e403b-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="e403b-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="e403b-123">如果內送資料列的 **PrimaryKey** 值與 **DataTable**中的資料列相同，則會將 **目前** 的值複製到 **原始** 值，然後將 **目前** 的值設定為內送資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="e403b-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="e403b-124">如果已**加入** **DataTable**中的**RowState** ，則**RowState**會保持**新增**。</span><span class="sxs-lookup"><span data-stu-id="e403b-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="e403b-125">針對標示為**修改**或**刪除**的資料列，會**修改** **RowState** 。</span><span class="sxs-lookup"><span data-stu-id="e403b-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="e403b-126">資料來源中尚未存在 **DataTable** 中的資料列會加入，且 **RowState** 會設定為 [ **已加入**]。</span><span class="sxs-lookup"><span data-stu-id="e403b-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="e403b-127">下列範例會使用 **Load** 方法來顯示 **Northwind** 資料庫中員工的生日清單。</span><span class="sxs-lookup"><span data-stu-id="e403b-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e403b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e403b-128">See also</span></span>

- [<span data-ttu-id="e403b-129">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="e403b-129">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- <span data-ttu-id="e403b-130">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="e403b-130">[ADO.NET Overview](../ado-net-overview.md)</span></span>
