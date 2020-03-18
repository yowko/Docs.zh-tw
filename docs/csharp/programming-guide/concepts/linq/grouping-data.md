---
title: 分組資料 (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635739"
---
# <a name="grouping-data-c"></a><span data-ttu-id="9bd4e-102">分組資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="9bd4e-102">Grouping Data (C#)</span></span>
<span data-ttu-id="9bd4e-103">分組指的是將資料放在群組中，好讓每一個群組中的項目共用共同的屬性。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="9bd4e-104">下圖顯示一系列字元的分組結果。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="9bd4e-105">每個群組的索引鍵是字元。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-105">The key for each group is the character.</span></span>  
  
 ![顯示 LINQ 群組作業的圖表。](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="9bd4e-107">分組資料項目的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9bd4e-108">方法</span><span class="sxs-lookup"><span data-stu-id="9bd4e-108">Methods</span></span>  
  
|<span data-ttu-id="9bd4e-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="9bd4e-109">Method Name</span></span>|<span data-ttu-id="9bd4e-110">描述</span><span class="sxs-lookup"><span data-stu-id="9bd4e-110">Description</span></span>|<span data-ttu-id="9bd4e-111">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="9bd4e-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="9bd4e-112">相關資訊</span><span class="sxs-lookup"><span data-stu-id="9bd4e-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="9bd4e-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="9bd4e-113">GroupBy</span></span>|<span data-ttu-id="9bd4e-114">共用共同屬性的群組項目。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="9bd4e-115">每個群組都由一個 <xref:System.Linq.IGrouping%602> 物件代表。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="9bd4e-116">-或-</span><span class="sxs-lookup"><span data-stu-id="9bd4e-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9bd4e-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="9bd4e-117">ToLookup</span></span>|<span data-ttu-id="9bd4e-118">根據索引鍵選取器函式，將元素插入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="9bd4e-119">不適用。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="9bd4e-120">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="9bd4e-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="9bd4e-121">下列程式碼範例使用 `group by` 子句，將整數依奇偶數分組至清單。</span><span class="sxs-lookup"><span data-stu-id="9bd4e-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9bd4e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bd4e-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9bd4e-123">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="9bd4e-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="9bd4e-124">group 子句</span><span class="sxs-lookup"><span data-stu-id="9bd4e-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="9bd4e-125">創建嵌套組</span><span class="sxs-lookup"><span data-stu-id="9bd4e-125">Create a nested group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="9bd4e-126">如何按副檔名 （LINQ） （C#） 對檔進行分組</span><span class="sxs-lookup"><span data-stu-id="9bd4e-126">How to group files by extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="9bd4e-127">組查詢結果</span><span class="sxs-lookup"><span data-stu-id="9bd4e-127">Group query results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="9bd4e-128">對分組操作執行子查詢</span><span class="sxs-lookup"><span data-stu-id="9bd4e-128">Perform a subquery on a grouping operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="9bd4e-129">如何使用組 （LINQ） （C#） 將檔拆分為多個檔</span><span class="sxs-lookup"><span data-stu-id="9bd4e-129">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
