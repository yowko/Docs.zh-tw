---
title: 群組資料 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: e2732c91dfff65ebb86ef45296ba369c3073a8f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644195"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="59c31-102">群組資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59c31-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="59c31-103">分組指的是將資料放在群組中，好讓每一個群組中的項目共用共同的屬性。</span><span class="sxs-lookup"><span data-stu-id="59c31-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="59c31-104">下圖顯示一系列字元的分組結果。</span><span class="sxs-lookup"><span data-stu-id="59c31-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="59c31-105">每個群組的索引鍵是字元。</span><span class="sxs-lookup"><span data-stu-id="59c31-105">The key for each group is the character.</span></span>  
  
 <span data-ttu-id="59c31-106">![LINQ 群組作業](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span><span class="sxs-lookup"><span data-stu-id="59c31-106">![LINQ Grouping Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")</span></span>  
  
 <span data-ttu-id="59c31-107">分組資料項目的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="59c31-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59c31-108">方法</span><span class="sxs-lookup"><span data-stu-id="59c31-108">Methods</span></span>  
  
|<span data-ttu-id="59c31-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="59c31-109">Method Name</span></span>|<span data-ttu-id="59c31-110">描述</span><span class="sxs-lookup"><span data-stu-id="59c31-110">Description</span></span>|<span data-ttu-id="59c31-111">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="59c31-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="59c31-112">更多資訊</span><span class="sxs-lookup"><span data-stu-id="59c31-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="59c31-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="59c31-113">GroupBy</span></span>|<span data-ttu-id="59c31-114">共用共同屬性的群組項目。</span><span class="sxs-lookup"><span data-stu-id="59c31-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="59c31-115">每個群組都由一個 <xref:System.Linq.IGrouping%602> 物件代表。</span><span class="sxs-lookup"><span data-stu-id="59c31-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="59c31-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="59c31-116">ToLookup</span></span>|<span data-ttu-id="59c31-117">根據索引鍵選取器函式，將元素插入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="59c31-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="59c31-118">不適用。</span><span class="sxs-lookup"><span data-stu-id="59c31-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="59c31-119">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="59c31-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="59c31-120">下列程式碼範例使用 `Group By` 子句，將整數依奇偶數分組至清單。</span><span class="sxs-lookup"><span data-stu-id="59c31-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59c31-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59c31-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="59c31-122">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59c31-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="59c31-123">Group By 子句</span><span class="sxs-lookup"><span data-stu-id="59c31-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)  
 [<span data-ttu-id="59c31-124">如何： 依副檔名 (LINQ) (Visual Basic) 的檔案群組</span><span class="sxs-lookup"><span data-stu-id="59c31-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 [<span data-ttu-id="59c31-125">如何： 將檔案分割成許多檔案中，使用群組 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59c31-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
