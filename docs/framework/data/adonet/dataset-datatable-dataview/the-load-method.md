---
title: Load 方法
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: e22e5812-89c6-41f0-9302-bb899a46dbff
ms.openlocfilehash: 82f840ab7dd26a4888ebf024d696f2c70701eb18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607228"
---
# <a name="the-load-method"></a><span data-ttu-id="57bf5-102">Load 方法</span><span class="sxs-lookup"><span data-stu-id="57bf5-102">The Load Method</span></span>
<span data-ttu-id="57bf5-103">您可以使用 <xref:System.Data.DataTable.Load%2A> 方法，載入具有資料來源之資料列的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="57bf5-103">You can use the <xref:System.Data.DataTable.Load%2A> method to load a <xref:System.Data.DataTable> with rows from a data source.</span></span> <span data-ttu-id="57bf5-104">這是多載的方法，在最簡單的形式，會接受單一參數， **DataReader**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-104">This is an overloaded method which, in its simplest form, accepts a single parameter, a **DataReader**.</span></span> <span data-ttu-id="57bf5-105">在此表單中，它只會載入**DataTable**與資料列。</span><span class="sxs-lookup"><span data-stu-id="57bf5-105">In this form, it simply loads the **DataTable** with rows.</span></span> <span data-ttu-id="57bf5-106">您可以選擇性地指定**LoadOption**參數來控制如何將資料加入至**DataTable**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-106">Optionally, you can specify the **LoadOption** parameter to control how data is added to the **DataTable**.</span></span>  
  
 <span data-ttu-id="57bf5-107">**LoadOption**參數就特別有用，萬一其中**DataTable**已經包含資料列，因為它會說明如何傳入的資料，從資料來源會結合資料已在資料表中。</span><span class="sxs-lookup"><span data-stu-id="57bf5-107">The **LoadOption** parameter is particularly useful in cases where the **DataTable** already contains rows of data, because it describes how incoming data from the data source will be combined with the data already in the table.</span></span> <span data-ttu-id="57bf5-108">例如， **PreserveCurrentValues** （預設值） 指定在資料列會標示為的情況下**Added**中**DataTable**，**原始**值或每個資料行設定為相符的資料列的內容從資料來源。</span><span class="sxs-lookup"><span data-stu-id="57bf5-108">For example, **PreserveCurrentValues** (the default) specifies that in cases where a row is marked as **Added** in the **DataTable**, the **Original** value or each column is set to the contents of the matching row from the data source.</span></span> <span data-ttu-id="57bf5-109">**目前**值會保留資料列已新增時，所指派的值並**RowState**的資料列將會設定為**Changed**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-109">The **Current** value will retain the values assigned when the row was added, and the **RowState** of the row will be set to **Changed**.</span></span>  
  
 <span data-ttu-id="57bf5-110">下列表格簡短說明 <xref:System.Data.LoadOption> 列舉值。</span><span class="sxs-lookup"><span data-stu-id="57bf5-110">The following table gives a short description of the <xref:System.Data.LoadOption> enumeration values.</span></span>  
  
|<span data-ttu-id="57bf5-111">LoadOption 值</span><span class="sxs-lookup"><span data-stu-id="57bf5-111">LoadOption value</span></span>|<span data-ttu-id="57bf5-112">描述</span><span class="sxs-lookup"><span data-stu-id="57bf5-112">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="57bf5-113">**OverwriteRow**</span><span class="sxs-lookup"><span data-stu-id="57bf5-113">**OverwriteRow**</span></span>|<span data-ttu-id="57bf5-114">內送資料列都有相同**PrimaryKey**為已在資料列的值**DataTable**，則**原始**並**目前**的每個值資料行所取代的值中的內送的資料列，而**RowState**屬性設定為**Unchanged**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-114">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** and **Current** values of each column are replaced with the values in the incoming row, and the **RowState** property is set to **Unchanged**.</span></span><br /><br /> <span data-ttu-id="57bf5-115">還不存在於資料來源的資料列**DataTable**會加上**RowState**的值**Unchanged**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-115">Rows from the data source that do not already exist in the **DataTable** are added with a **RowState** value of **Unchanged**.</span></span><br /><br /> <span data-ttu-id="57bf5-116">此選項會實際重新整理的內容**DataTable** ，使其符合資料來源的內容。</span><span class="sxs-lookup"><span data-stu-id="57bf5-116">This option in effect refreshes the contents of the **DataTable** so that it matches the contents of the data source.</span></span>|  
|<span data-ttu-id="57bf5-117">**PreserveCurrentValues （預設值）**</span><span class="sxs-lookup"><span data-stu-id="57bf5-117">**PreserveCurrentValues (default)**</span></span>|<span data-ttu-id="57bf5-118">如果內送資料列具有相同**PrimaryKey**為已在資料列的值**DataTable**，則**原始**值設定為內容的內送的資料列，以及**目前**值不會變更。</span><span class="sxs-lookup"><span data-stu-id="57bf5-118">If incoming rows have the same **PrimaryKey** value as a row already in the **DataTable**, the **Original** value is set to the contents of the incoming row, and the **Current** value is not changed.</span></span><br /><br /> <span data-ttu-id="57bf5-119">如果**RowState**是**Added**或**Modified**，它會設定為**Modified**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-119">If the **RowState** is **Added** or **Modified**, it is set to **Modified**.</span></span><br /><br /> <span data-ttu-id="57bf5-120">如果**RowState**已**Deleted**，則仍會保持**Deleted**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-120">If the **RowState** was **Deleted**, it remains **Deleted**.</span></span><br /><br /> <span data-ttu-id="57bf5-121">還不存在於資料來源的資料列**DataTable**加入，而**RowState**設定為**Unchanged**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-121">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Unchanged**.</span></span>|  
|<span data-ttu-id="57bf5-122">**UpdateCurrentValues**</span><span class="sxs-lookup"><span data-stu-id="57bf5-122">**UpdateCurrentValues**</span></span>|<span data-ttu-id="57bf5-123">如果內送資料列具有相同**PrimaryKey**已在資料列的值**DataTable**，則**目前**值複製到**原始**值，而**目前**值會設定內送資料列的內容。</span><span class="sxs-lookup"><span data-stu-id="57bf5-123">If incoming rows have the same **PrimaryKey** value as the row already in the **DataTable**, the **Current** value is copied to the **Original** value, and the **Current** value is then set to the contents of the incoming row.</span></span><br /><br /> <span data-ttu-id="57bf5-124">如果**RowState**中**DataTable**已**Added**，則**RowState**保持**Added**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-124">If the **RowState** in the **DataTable** was **Added**, the **RowState** remains **Added**.</span></span> <span data-ttu-id="57bf5-125">資料列標示為**Modified**或**Deleted**，則**RowState**是**Modified**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-125">For rows marked as **Modified** or **Deleted**, the **RowState** is **Modified**.</span></span><br /><br /> <span data-ttu-id="57bf5-126">還不存在於資料來源的資料列**DataTable**加入，而**RowState**設定為**Added**。</span><span class="sxs-lookup"><span data-stu-id="57bf5-126">Rows from the data source that do not already exist in the **DataTable** are added, and the **RowState** is set to **Added**.</span></span>|  
  
 <span data-ttu-id="57bf5-127">下列範例會使用**負載**方法，以顯示生日清單中的員工**Northwind**資料庫。</span><span class="sxs-lookup"><span data-stu-id="57bf5-127">The following sample uses the **Load** method to display a list of birthdays for the employees in the **Northwind** database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57bf5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57bf5-128">See also</span></span>

- [<span data-ttu-id="57bf5-129">在 DataTable 中操作資料</span><span class="sxs-lookup"><span data-stu-id="57bf5-129">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="57bf5-130">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="57bf5-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
