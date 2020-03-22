---
title: 分組資料
ms.date: 07/20/2015
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
ms.openlocfilehash: 9a4011b77f91ff241d23f7aeca95925a1e170483
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266816"
---
# <a name="grouping-data-visual-basic"></a><span data-ttu-id="fb4f5-102">分組資料（可視基礎）</span><span class="sxs-lookup"><span data-stu-id="fb4f5-102">Grouping Data (Visual Basic)</span></span>
<span data-ttu-id="fb4f5-103">分組指的是將資料放在群組中，好讓每一個群組中的項目共用共同的屬性。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="fb4f5-104">下圖顯示一系列字元的分組結果。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="fb4f5-105">每個群組的索引鍵是字元。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-105">The key for each group is the character.</span></span>  
  
 ![顯示 LINQ 群組作業的圖表。](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="fb4f5-107">分組資料項目的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb4f5-108">方法</span><span class="sxs-lookup"><span data-stu-id="fb4f5-108">Methods</span></span>  
  
|<span data-ttu-id="fb4f5-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="fb4f5-109">Method Name</span></span>|<span data-ttu-id="fb4f5-110">描述</span><span class="sxs-lookup"><span data-stu-id="fb4f5-110">Description</span></span>|<span data-ttu-id="fb4f5-111">可視基本查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="fb4f5-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="fb4f5-112">相關資訊</span><span class="sxs-lookup"><span data-stu-id="fb4f5-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="fb4f5-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="fb4f5-113">GroupBy</span></span>|<span data-ttu-id="fb4f5-114">共用共同屬性的群組項目。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="fb4f5-115">每個群組都由一個 <xref:System.Linq.IGrouping%602> 物件代表。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fb4f5-116">ToLookup</span><span class="sxs-lookup"><span data-stu-id="fb4f5-116">ToLookup</span></span>|<span data-ttu-id="fb4f5-117">根據索引鍵選取器函式，將元素插入 <xref:System.Linq.Lookup%602> (一對多字典)。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-117">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="fb4f5-118">不適用。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="fb4f5-119">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="fb4f5-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="fb4f5-120">下列程式碼範例使用 `Group By` 子句，將整數依奇偶數分組至清單。</span><span class="sxs-lookup"><span data-stu-id="fb4f5-120">The following code example uses the `Group By` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb4f5-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb4f5-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fb4f5-122">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb4f5-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="fb4f5-123">按子項分組</span><span class="sxs-lookup"><span data-stu-id="fb4f5-123">Group By Clause</span></span>](../../../../visual-basic/language-reference/queries/group-by-clause.md)
- [<span data-ttu-id="fb4f5-124">如何：按副檔名分組檔 （LINQ） （可視基本）</span><span class="sxs-lookup"><span data-stu-id="fb4f5-124">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="fb4f5-125">如何：通過使用組 （LINQ） 將檔拆分為多個檔（可視基本）</span><span class="sxs-lookup"><span data-stu-id="fb4f5-125">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
