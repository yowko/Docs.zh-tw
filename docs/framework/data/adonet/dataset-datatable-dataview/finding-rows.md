---
title: 尋找資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: ad10557a55b498fe004bff6ce89801e975e7138b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786325"
---
# <a name="finding-rows"></a><span data-ttu-id="8a0e1-102">尋找資料列</span><span class="sxs-lookup"><span data-stu-id="8a0e1-102">Finding Rows</span></span>
<span data-ttu-id="8a0e1-103">您可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法，依照資料列的排序索引鍵值來搜尋資料列。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="8a0e1-104">**Find**和**FindRows**方法中搜尋值的區分大小寫，是由基礎<xref:System.Data.DataTable>的**CaseSensitive**屬性所決定。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="8a0e1-105">搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="8a0e1-106">**Find**方法會傳回一個整數，其中包含符合搜尋<xref:System.Data.DataRowView>條件之的索引。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="8a0e1-107">如果有多個資料列符合搜尋準則，則只會傳回第一個相符**DataRowView**的索引。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="8a0e1-108">如果找不到相符專案，則**Find**會傳回-1。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="8a0e1-109">若要傳回符合多個資料列的搜尋結果，請使用**FindRows**方法。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="8a0e1-110">**FindRows**的運作方式就像**Find**方法，不同之處在于它會傳回參考**DataView**中所有相符資料列的**DataRowView**陣列。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="8a0e1-111">如果找不到相符專案， **DataRowView**陣列將會是空的。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="8a0e1-112">若要使用**Find**或**FindRows**方法，您必須指定排序次序，方法是將**ApplyDefaultSort**設定為**true** ，或使用**sort**屬性。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="8a0e1-113">如果沒有指定任何順序，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="8a0e1-114">**Find**和**FindRows**方法會將值的陣列當做輸入，其長度符合排序次序中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="8a0e1-115">排序單一資料行時，您可傳遞單一值。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="8a0e1-116">如果排序順序包含多個資料行，則您傳遞的是物件陣列。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="8a0e1-117">請注意，針對多個資料行進行排序時，物件陣列中的值必須符合**DataView**的**sort**屬性中所指定的資料行順序。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="8a0e1-118">下列程式碼範例示範如何針對具有單一資料行排序次序的**DataView**呼叫**Find**方法。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 <span data-ttu-id="8a0e1-119">如果您的**Sort**屬性指定多個資料行，您必須以**Sort**屬性所指定的順序，以每個資料行的搜尋值傳遞物件陣列，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="8a0e1-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a0e1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a0e1-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="8a0e1-121">DataView</span><span class="sxs-lookup"><span data-stu-id="8a0e1-121">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="8a0e1-122">ADO.NET 概觀</span><span class="sxs-lookup"><span data-stu-id="8a0e1-122">ADO.NET Overview</span></span>](../ado-net-overview.md)
