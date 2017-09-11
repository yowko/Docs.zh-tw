---
title: "投影作業 (Visual Basic) |Microsoft 文件"
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
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
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
ms.openlocfilehash: aac5cf69e6c3f4041a4302e8d606ca8dfddbc8a2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="bac37-102">投影作業 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bac37-102">Projection Operations (Visual Basic)</span></span>
<span data-ttu-id="bac37-103">投影指的是指將物件轉換成新的表單通常僅包含後續即將使用這些屬性的作業。</span><span class="sxs-lookup"><span data-stu-id="bac37-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="bac37-104">透過使用投影，您可以建構根據每個物件所建立的新型別。</span><span class="sxs-lookup"><span data-stu-id="bac37-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="bac37-105">您可以投影屬性並針對它執行數學函式。</span><span class="sxs-lookup"><span data-stu-id="bac37-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="bac37-106">您也可以投影原始物件，而不變更它。</span><span class="sxs-lookup"><span data-stu-id="bac37-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="bac37-107">執行投影的標準查詢運算子方法詳列於下一節。</span><span class="sxs-lookup"><span data-stu-id="bac37-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bac37-108">方法</span><span class="sxs-lookup"><span data-stu-id="bac37-108">Methods</span></span>  
  
|<span data-ttu-id="bac37-109">方法名稱</span><span class="sxs-lookup"><span data-stu-id="bac37-109">Method Name</span></span>|<span data-ttu-id="bac37-110">描述</span><span class="sxs-lookup"><span data-stu-id="bac37-110">Description</span></span>|<span data-ttu-id="bac37-111">Visual Basic 查詢運算式語法</span><span class="sxs-lookup"><span data-stu-id="bac37-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="bac37-112">更多資訊</span><span class="sxs-lookup"><span data-stu-id="bac37-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="bac37-113">選取</span><span class="sxs-lookup"><span data-stu-id="bac37-113">Select</span></span>|<span data-ttu-id="bac37-114">轉換函式為基礎的專案值。</span><span class="sxs-lookup"><span data-stu-id="bac37-114">Projects values that are based on a transform function.</span></span>|`Select`|<span data-ttu-id="bac37-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bac37-115"><xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="bac37-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bac37-116"><xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="bac37-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="bac37-117">SelectMany</span></span>|<span data-ttu-id="bac37-118">專案的值為基礎的轉換函式，然後將它們簡化成單一序列的順序。</span><span class="sxs-lookup"><span data-stu-id="bac37-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="bac37-119">使用多個`From`子句</span><span class="sxs-lookup"><span data-stu-id="bac37-119">Use multiple `From` clauses</span></span>|<span data-ttu-id="bac37-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bac37-120"><xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="bac37-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="bac37-121"><xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="bac37-122">查詢運算式語法範例</span><span class="sxs-lookup"><span data-stu-id="bac37-122">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="bac37-123">選取</span><span class="sxs-lookup"><span data-stu-id="bac37-123">Select</span></span>  
 <span data-ttu-id="bac37-124">下列範例會使用`Select`子句，以專案從每個字串的字串清單中的第一個字母。</span><span class="sxs-lookup"><span data-stu-id="bac37-124">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a><span data-ttu-id="bac37-125">SelectMany</span><span class="sxs-lookup"><span data-stu-id="bac37-125">SelectMany</span></span>  
 <span data-ttu-id="bac37-126">下列範例會使用多個`From`專案從每個字串的字串清單中的每個單字的子句。</span><span class="sxs-lookup"><span data-stu-id="bac37-126">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="bac37-127">選取與 SelectMany</span><span class="sxs-lookup"><span data-stu-id="bac37-127">Select versus SelectMany</span></span>  
 <span data-ttu-id="bac37-128">這兩者的工作`Select()`和`SelectMany()`取自來源值來產生結果值 （或值）。</span><span class="sxs-lookup"><span data-stu-id="bac37-128">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="bac37-129">`Select()`會產生一個結果值的每個來源值。</span><span class="sxs-lookup"><span data-stu-id="bac37-129">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="bac37-130">整體的結果，因此是具有相同數目的元素與來源集合的集合。</span><span class="sxs-lookup"><span data-stu-id="bac37-130">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="bac37-131">相反地，`SelectMany()`會產生單一的整體結果，其中包含從每個來源值串連的子集合。</span><span class="sxs-lookup"><span data-stu-id="bac37-131">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="bac37-132">轉換函式的引數傳遞之`SelectMany()`必須傳回可列舉序列的每個來源值的值。</span><span class="sxs-lookup"><span data-stu-id="bac37-132">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="bac37-133">這些可列舉序列然後串連`SelectMany()`建立一個大型的順序。</span><span class="sxs-lookup"><span data-stu-id="bac37-133">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="bac37-134">下列兩張圖顯示這兩種方法在動作之間的概念差異。</span><span class="sxs-lookup"><span data-stu-id="bac37-134">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="bac37-135">在每個案例中，假設選取器 （轉換） 函式會從每個來源值選取花卉陣列。</span><span class="sxs-lookup"><span data-stu-id="bac37-135">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="bac37-136">下圖說明如何`Select()`傳回具有相同數目的元素與來源集合的集合。</span><span class="sxs-lookup"><span data-stu-id="bac37-136">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 <span data-ttu-id="bac37-137">![Select （） 動作的概念圖例](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span><span class="sxs-lookup"><span data-stu-id="bac37-137">![Conceptual illustration of the action of Select&#40;&#41;](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")</span></span>  
  
 <span data-ttu-id="bac37-138">下圖說明如何`SelectMany()`串連成一個最後的結果值，其中包含每個中繼陣列中的每個值的陣列中繼序列。</span><span class="sxs-lookup"><span data-stu-id="bac37-138">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 <span data-ttu-id="bac37-139">![顯示 selectmany （） 的動作圖形。] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span><span class="sxs-lookup"><span data-stu-id="bac37-139">![Graphic showing the action of SelectMany&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")</span></span>  
  
### <a name="code-example"></a><span data-ttu-id="bac37-140">程式碼範例</span><span class="sxs-lookup"><span data-stu-id="bac37-140">Code Example</span></span>  
 <span data-ttu-id="bac37-141">下列範例會比較的行為`Select()`和`SelectMany()`。</span><span class="sxs-lookup"><span data-stu-id="bac37-141">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="bac37-142">程式碼會建立 「 花束 」 的 「 花 」 的名稱的每個清單中的前兩個項目來源集合中。</span><span class="sxs-lookup"><span data-stu-id="bac37-142">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="bac37-143">在此範例中，「 單值 」 的轉換函式<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>使用本身就是值的集合。</xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29></span><span class="sxs-lookup"><span data-stu-id="bac37-143">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="bac37-144">這需要額外`For Each`迴圈來列舉每一個子序列中的每個字串。</span><span class="sxs-lookup"><span data-stu-id="bac37-144">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="bac37-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bac37-145">See Also</span></span>  
 <span data-ttu-id="bac37-146"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="bac37-146"><xref:System.Linq></span></span>   
<span data-ttu-id="bac37-147"> [標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="bac37-147"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="bac37-148"> [Select 子句](../../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="bac37-148"> [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="bac37-149"> [如何︰ 使用 Joins 合併資料](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) </span><span class="sxs-lookup"><span data-stu-id="bac37-149"> [How to: Combine Data with Joins](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md) </span></span>  
<span data-ttu-id="bac37-150"> [如何︰ 填入物件集合，從多個來源 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span><span class="sxs-lookup"><span data-stu-id="bac37-150"> [How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md) </span></span>  
<span data-ttu-id="bac37-151"> [如何︰ 將 LINQ 查詢結果，當做特定類型傳回](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md) </span><span class="sxs-lookup"><span data-stu-id="bac37-151"> [How to: Return a LINQ Query Result as a Specific Type](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md) </span></span>  
<span data-ttu-id="bac37-152"> [如何︰ 使用群組 (LINQ) (Visual Basic)，將檔案分割成許多檔案](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span><span class="sxs-lookup"><span data-stu-id="bac37-152"> [How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)</span></span>
