---
title: 尋找資料列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: cfd4587f0dde7687ecf88bf6b31c44b90a2287ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151139"
---
# <a name="finding-rows"></a><span data-ttu-id="0bdbc-102">尋找資料列</span><span class="sxs-lookup"><span data-stu-id="0bdbc-102">Finding Rows</span></span>
<span data-ttu-id="0bdbc-103">您可以使用 <xref:System.Data.DataView.Find%2A> 的 <xref:System.Data.DataView.FindRows%2A> 和 <xref:System.Data.DataView> 方法，依照資料列的排序索引鍵值來搜尋資料列。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-103">You can search for rows according to their sort key values by using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="0bdbc-104">**Find**和**FindRows**方法中搜索值的區分度由基礎<xref:System.Data.DataTable>的**Case敏感**屬性確定。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-104">The case sensitivity of search values in the **Find** and **FindRows** methods is determined by the **CaseSensitive** property of the underlying <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="0bdbc-105">搜尋值必須完全符合現有的排序索引鍵值，才能傳回結果。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-105">Search values must match existing sort key values in their entirety in order to return a result.</span></span>  
  
 <span data-ttu-id="0bdbc-106">**Find**方法返回一個整數，該整數與<xref:System.Data.DataRowView>搜尋條件匹配的索引。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-106">The **Find** method returns an integer with the index of the <xref:System.Data.DataRowView> that matches the search criteria.</span></span> <span data-ttu-id="0bdbc-107">如果多行與搜尋條件匹配，則僅返回第一個匹配**DataRowView**的索引。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-107">If more than one row matches the search criteria, only the index of the first matching **DataRowView** is returned.</span></span> <span data-ttu-id="0bdbc-108">如果未找到匹配項，**則查找**返回 -1。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-108">If no matches are found, **Find** returns -1.</span></span>  
  
 <span data-ttu-id="0bdbc-109">要返回與多行匹配的搜尋結果，請使用**FindRows**方法。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-109">To return search results that match multiple rows, use the **FindRows** method.</span></span> <span data-ttu-id="0bdbc-110">**FindRows**的工作方式與**Find**方法類似，只不過它返回一個**資料羅視圖**陣列，該陣列引用**DataView**中的所有匹配行。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-110">**FindRows** works just like the **Find** method, except that it returns a **DataRowView** array that references all matching rows in the **DataView**.</span></span> <span data-ttu-id="0bdbc-111">如果未找到匹配項 **，DataRowView**陣列將為空。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-111">If no matches are found, the **DataRowView** array will be empty.</span></span>  
  
 <span data-ttu-id="0bdbc-112">要使用 **"查找**"**或"查找行"** 方法，必須通過將 **"應用預設排序"** 設置為**true**或使用**排序**屬性來指定排序次序。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-112">To use the **Find** or **FindRows** methods you must specify a sort order either by setting **ApplyDefaultSort** to **true** or by using the **Sort** property.</span></span> <span data-ttu-id="0bdbc-113">如果沒有指定任何順序，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-113">If no sort order is specified, an exception is thrown.</span></span>  
  
 <span data-ttu-id="0bdbc-114">**Find**和**FindRows**方法採用一個值陣列作為輸入，其長度與排序次序中的列數匹配。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-114">The **Find** and **FindRows** methods take an array of values as input whose length matches the number of columns in the sort order.</span></span> <span data-ttu-id="0bdbc-115">排序單一資料行時，您可傳遞單一值。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-115">In the case of a sort on a single column, you can pass a single value.</span></span> <span data-ttu-id="0bdbc-116">如果排序順序包含多個資料行，則您傳遞的是物件陣列。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-116">For sort orders containing multiple columns, you pass an array of objects.</span></span> <span data-ttu-id="0bdbc-117">請注意，對於對多個列的排序，物件陣列中的值必須與**DataView**的**Sort**屬性中指定的列的順序匹配。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-117">Note that for a sort on multiple columns, the values in the object array must match the order of the columns specified in the **Sort** property of the **DataView**.</span></span>  
  
 <span data-ttu-id="0bdbc-118">以下代碼示例顯示針對具有單個列排序次序的**DataView**調用**的 Find**方法。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-118">The following code example shows the **Find** method being called against a **DataView** with a single column sort order.</span></span>  
  
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
  
 <span data-ttu-id="0bdbc-119">如果**Sort**屬性指定了多個列，則必須按照**Sort**屬性指定的順序傳遞具有每列搜索值的物件陣列，如以下代碼示例所示。</span><span class="sxs-lookup"><span data-stu-id="0bdbc-119">If your **Sort** property specifies multiple columns, you must pass an object array with the search values for each column in the order specified by the **Sort** property, as in the following code example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0bdbc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bdbc-120">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="0bdbc-121">DataView</span><span class="sxs-lookup"><span data-stu-id="0bdbc-121">DataViews</span></span>](dataviews.md)
- <span data-ttu-id="0bdbc-122">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="0bdbc-122">[ADO.NET Overview](../ado-net-overview.md)</span></span>
