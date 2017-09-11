---
title: "分組資料 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 86d7ef5f6b8978b9ef14a1c7274c231d81f20994
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="grouping-data-c"></a><span data-ttu-id="4fd37-102">分組資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="4fd37-102">Grouping Data (C#)</span></span>
<span data-ttu-id="4fd37-103">分組指的是將資料放在群組中，好讓每一個群組中的項目共用共同的屬性。</span><span class="sxs-lookup"><span data-stu-id="4fd37-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="4fd37-104">下圖顯示一系列字元的分組結果。</span><span class="sxs-lookup"><span data-stu-id="4fd37-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="4fd37-105">每個群組的索引鍵是字元。</span><span class="sxs-lookup"><span data-stu-id="4fd37-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="4fd37-106">![LINQ 群組作業](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="4fd37-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="4fd37-107">分組資料項目的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="4fd37-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fd37-108">方法</span><span class="sxs-lookup"><span data-stu-id="4fd37-108">Methods</span></span>  
  
|<span data-ttu-id="4fd37-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="4fd37-109">Method Name</span></span>|<span data-ttu-id="4fd37-110">描述</span><span class="sxs-lookup"><span data-stu-id="4fd37-110">Description</span></span>|<span data-ttu-id="4fd37-111">C# 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="4fd37-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="4fd37-112">更多資訊</span><span class="sxs-lookup"><span data-stu-id="4fd37-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="4fd37-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="4fd37-113">GroupBy</span></span>|<span data-ttu-id="4fd37-114">共用共同屬性的群組項目。</span><span class="sxs-lookup"><span data-stu-id="4fd37-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="4fd37-115">每個群組由 <xref:System.Linq.IGrouping%602> 物件表示。</span><span class="sxs-lookup"><span data-stu-id="4fd37-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="4fd37-116">-或-</span><span class="sxs-lookup"><span data-stu-id="4fd37-116">-or-</span></span><br /><br /> `group … by … into …`|<span data-ttu-id="4fd37-117"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4fd37-117"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="4fd37-118"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4fd37-118"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="4fd37-119">ToLookup</span><span class="sxs-lookup"><span data-stu-id="4fd37-119">ToLookup</span></span>|<span data-ttu-id="4fd37-120">將項目根據索引鍵選取器函式插入到 <xref:System.Linq.Lookup%602> (一對多字典) 中。</span><span class="sxs-lookup"><span data-stu-id="4fd37-120">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="4fd37-121">不適用。</span><span class="sxs-lookup"><span data-stu-id="4fd37-121">Not applicable.</span></span>|<span data-ttu-id="4fd37-122"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4fd37-122"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="4fd37-123">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="4fd37-123">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="4fd37-124">下列程式碼範例使用 `group by` 子句，將整數依奇偶數分組至清單。</span><span class="sxs-lookup"><span data-stu-id="4fd37-124">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4fd37-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fd37-125">See Also</span></span>  
 <span data-ttu-id="4fd37-126"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="4fd37-126"><xref:System.Linq></span></span>   
<span data-ttu-id="4fd37-127"> [標準查詢運算子概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="4fd37-127"> [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="4fd37-128"> [group 子句](../../../../csharp/language-reference/keywords/group-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4fd37-128"> [group clause](../../../../csharp/language-reference/keywords/group-clause.md) </span></span>  
<span data-ttu-id="4fd37-129"> [如何：建立巢狀群組](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md) </span><span class="sxs-lookup"><span data-stu-id="4fd37-129"> [How to: Create a Nested Group](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md) </span></span>  
<span data-ttu-id="4fd37-130"> [如何：依副檔名分組檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span><span class="sxs-lookup"><span data-stu-id="4fd37-130"> [How to: Group Files by Extension (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span></span>  
<span data-ttu-id="4fd37-131"> [如何：分組查詢結果](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md) </span><span class="sxs-lookup"><span data-stu-id="4fd37-131"> [How to: Group Query Results](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md) </span></span>  
<span data-ttu-id="4fd37-132"> [如何：在分組作業上執行子查詢](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md) </span><span class="sxs-lookup"><span data-stu-id="4fd37-132"> [How to: Perform a Subquery on a Grouping Operation](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md) </span></span>  
<span data-ttu-id="4fd37-133"> [如何：使用群組將檔案分割成許多檔案 (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="4fd37-133"> [How to: Split a File Into Many Files by Using Groups (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
