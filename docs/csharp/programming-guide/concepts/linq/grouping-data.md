---
title: 分組資料 (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: a85babc43f673711fe1bdfa5cec1836a5073c785
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753924"
---
# <a name="grouping-data-c"></a><span data-ttu-id="96016-102">分組資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="96016-102">Grouping Data (C#)</span></span>
<span data-ttu-id="96016-103">分組指的是將資料放在群組中，好讓每一個群組中的項目共用共同的屬性。</span><span class="sxs-lookup"><span data-stu-id="96016-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="96016-104">下圖顯示一系列字元的分組結果。</span><span class="sxs-lookup"><span data-stu-id="96016-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="96016-105">每個群組的索引鍵是字元。</span><span class="sxs-lookup"><span data-stu-id="96016-105">The key for each group is the character.</span></span>  
  
 ![顯示 LINQ 群組作業的圖表。](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="96016-107">分組資料項目的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="96016-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96016-108">方法</span><span class="sxs-lookup"><span data-stu-id="96016-108">Methods</span></span>  
  
|<span data-ttu-id="96016-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="96016-109">Method Name</span></span>|<span data-ttu-id="96016-110">說明</span><span class="sxs-lookup"><span data-stu-id="96016-110">Description</span></span>|<span data-ttu-id="96016-111">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="96016-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="96016-112">更多資訊</span><span class="sxs-lookup"><span data-stu-id="96016-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="96016-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="96016-113">GroupBy</span></span>|<span data-ttu-id="96016-114">共用共同屬性的群組項目。</span><span class="sxs-lookup"><span data-stu-id="96016-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="96016-115">每個群組都由一個 <xref:System.Linq.IGrouping%602> 物件代表。</span><span class="sxs-lookup"><span data-stu-id="96016-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="96016-116">-或-</span><span class="sxs-lookup"><span data-stu-id="96016-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="96016-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="96016-117">ToLookup</span></span>|<span data-ttu-id="96016-118">根據索引鍵選取器函式，將元素插入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="96016-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="96016-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="96016-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="96016-120">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="96016-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="96016-121">下列程式碼範例使用 `group by` 子句，將整數依奇偶數分組至清單。</span><span class="sxs-lookup"><span data-stu-id="96016-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="96016-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96016-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="96016-123">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="96016-123">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="96016-124">group 子句</span><span class="sxs-lookup"><span data-stu-id="96016-124">group clause</span></span>](../../../../csharp/language-reference/keywords/group-clause.md)
- [<span data-ttu-id="96016-125">如何：建立巢狀群組</span><span class="sxs-lookup"><span data-stu-id="96016-125">How to: Create a Nested Group</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)
- [<span data-ttu-id="96016-126">如何：依副檔名分組檔案 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="96016-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="96016-127">如何：將查詢結果分組</span><span class="sxs-lookup"><span data-stu-id="96016-127">How to: Group Query Results</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)
- [<span data-ttu-id="96016-128">如何：在分組作業上執行子查詢</span><span class="sxs-lookup"><span data-stu-id="96016-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="96016-129">如何：使用群組將檔案分割成多個檔案 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="96016-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
