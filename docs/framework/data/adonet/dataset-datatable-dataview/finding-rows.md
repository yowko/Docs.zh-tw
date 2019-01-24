---
title: 尋找資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: e5a48c5caf9239e0e7b7f2e7a3ad8ab5df168ba1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684186"
---
# <a name="finding-rows"></a><span data-ttu-id="299ff-102">尋找資料列</span><span class="sxs-lookup"><span data-stu-id="299ff-102">Finding Rows</span></span>
<span data-ttu-id="299ff-103">您可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法，依照資料列的排序索引鍵值來搜尋資料列。</span><span class="sxs-lookup"><span data-stu-id="299ff-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="299ff-104">中值的搜尋區分大小寫**尋找**並**FindRows**取決於方法**CaseSensitive**基礎屬性<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="299ff-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="299ff-105">搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。</span><span class="sxs-lookup"><span data-stu-id="299ff-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="299ff-106">**尋找**方法會傳回索引的整數<xref:System.Data.DataRowView>符合搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="299ff-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="299ff-107">如果多個資料列符合搜尋準則，只有第一個相符的索引**DataRowView**會傳回。</span><span class="sxs-lookup"><span data-stu-id="299ff-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="299ff-108">如果找不到任何相符項目，**尋找**會傳回-1。</span><span class="sxs-lookup"><span data-stu-id="299ff-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="299ff-109">若要傳回符合多個資料列的搜尋結果，請使用**FindRows**方法。</span><span class="sxs-lookup"><span data-stu-id="299ff-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="299ff-110">**FindRows**運作方式就像**尋找**方法，但是它會傳回**DataRowView**參考中的所有相符資料列的陣列**DataView**。</span><span class="sxs-lookup"><span data-stu-id="299ff-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="299ff-111">如果找不到任何相符項目， **DataRowView**陣列會是空的。</span><span class="sxs-lookup"><span data-stu-id="299ff-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="299ff-112">若要使用**尋找**或**FindRows**方法，您必須指定排序順序： **ApplyDefaultSort**至**true**或使用**排序**屬性。</span><span class="sxs-lookup"><span data-stu-id="299ff-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="299ff-113">如果沒有指定任何順序，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="299ff-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="299ff-114">**尋找**並**FindRows**方法會採用值的陣列做為輸入的長度符合排序次序中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="299ff-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="299ff-115">排序單一資料行時，您可傳遞單一值。</span><span class="sxs-lookup"><span data-stu-id="299ff-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="299ff-116">如果排序順序包含多個資料行，則您傳遞的是物件陣列。</span><span class="sxs-lookup"><span data-stu-id="299ff-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="299ff-117">請注意，針對多個資料行排序，物件陣列中的值必須符合指定之資料行的順序**排序**屬性**DataView**。</span><span class="sxs-lookup"><span data-stu-id="299ff-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="299ff-118">下列程式碼範例所示**尋找**針對正在呼叫的方法**DataView**具有單一資料行排序次序。</span><span class="sxs-lookup"><span data-stu-id="299ff-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="299ff-119">如果您**排序**屬性會指定多個資料行，您都必須通過每個資料行搜尋值的物件陣列中所指定的順序**排序**屬性，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="299ff-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="299ff-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="299ff-120">See also</span></span>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="299ff-121">DataView</span><span class="sxs-lookup"><span data-stu-id="299ff-121">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [<span data-ttu-id="299ff-122">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="299ff-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
