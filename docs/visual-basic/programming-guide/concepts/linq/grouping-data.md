---
title: "群組資料 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ce4e8f924f91eed451d3b1a02cd0bcff75589537
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="8d235-102">群組資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d235-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="8d235-103">群組指的是將資料分成群組，讓每個群組中的項目共用相同屬性的作業。</span><span class="sxs-lookup"><span data-stu-id="8d235-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="8d235-104">下圖顯示的字元序列的分組結果。</span><span class="sxs-lookup"><span data-stu-id="8d235-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="8d235-105">每個群組的索引鍵是字元。</span><span class="sxs-lookup"><span data-stu-id="8d235-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="8d235-106">![LINQ 群組作業](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="8d235-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="8d235-107">群組資料元素的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="8d235-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d235-108">方法</span><span class="sxs-lookup"><span data-stu-id="8d235-108">Methods</span></span>  
  
|<span data-ttu-id="8d235-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="8d235-109">Method Name</span></span>|<span data-ttu-id="8d235-110">描述</span><span class="sxs-lookup"><span data-stu-id="8d235-110">Description</span></span>|<span data-ttu-id="8d235-111">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="8d235-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8d235-112">更多資訊</span><span class="sxs-lookup"><span data-stu-id="8d235-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="8d235-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="8d235-113">GroupBy</span></span>|<span data-ttu-id="8d235-114">群組項目會共用共同的屬性。</span><span class="sxs-lookup"><span data-stu-id="8d235-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="8d235-115">每個群組由<xref:System.Linq.IGrouping%602>物件。</xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="8d235-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<span data-ttu-id="8d235-116"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8d235-116"><xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="8d235-117"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8d235-117"><xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="8d235-118">ToLookup</span><span class="sxs-lookup"><span data-stu-id="8d235-118">ToLookup</span></span>|<span data-ttu-id="8d235-119">插入項目到<xref:System.Linq.Lookup%602>（一對多字典） 會根據索引鍵選取器函式。</xref:System.Linq.Lookup%602></span><span class="sxs-lookup"><span data-stu-id="8d235-119">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="8d235-120">不適用。</span><span class="sxs-lookup"><span data-stu-id="8d235-120">Not applicable.</span></span>|<span data-ttu-id="8d235-121"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="8d235-121"><xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="8d235-122">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="8d235-122">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="8d235-123">下列程式碼範例使用`Group By`子句群組清單，以根據是否為偶數或奇數的整數。</span><span class="sxs-lookup"><span data-stu-id="8d235-123">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d235-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d235-124">See Also</span></span>  
 <span data-ttu-id="8d235-125"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="8d235-125"><xref:System.Linq></span></span>   
<span data-ttu-id="8d235-126"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="8d235-126"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="8d235-127"> [Group By 子句](../../../../visual-basic/language-reference/queries/group-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="8d235-127"> [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md) </span></span>  
<span data-ttu-id="8d235-128"> [如何︰ 依副檔名 (LINQ) (Visual Basic) 的檔案群組](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span><span class="sxs-lookup"><span data-stu-id="8d235-128"> [How to: Group Files by Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md) </span></span>  
<span data-ttu-id="8d235-129"> [如何︰ 使用群組 (LINQ) (Visual Basic)，將檔案分割成許多檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="8d235-129"> [How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
