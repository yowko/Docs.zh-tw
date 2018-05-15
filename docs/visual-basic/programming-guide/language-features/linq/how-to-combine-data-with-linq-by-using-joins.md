---
title: 如何：使用 Joins 以 LINQ 合併資料 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: f0279cc13e938b6f7853ef11fee1ef046f192316
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="b00b9-102">如何：使用 Joins 以 LINQ 合併資料 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b00b9-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="b00b9-103">Visual Basic 提供`Join`和`Group Join`查詢子句可讓您結合多個集合之間的一般值為基礎的集合的內容。</span><span class="sxs-lookup"><span data-stu-id="b00b9-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="b00b9-104">這些值稱為*金鑰*值。</span><span class="sxs-lookup"><span data-stu-id="b00b9-104">These values are known as *key* values.</span></span> <span data-ttu-id="b00b9-105">開發人員熟悉關聯式資料庫概念會辨識`Join`INNER JOIN 子句和`Group Join`做為有效，LEFT OUTER JOIN 子句。</span><span class="sxs-lookup"><span data-stu-id="b00b9-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="b00b9-106">本主題中的範例將示範幾個方法將資料結合使用`Join`和`Group Join`查詢子句。</span><span class="sxs-lookup"><span data-stu-id="b00b9-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="b00b9-107">建立專案並加入範例資料</span><span class="sxs-lookup"><span data-stu-id="b00b9-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="b00b9-108">若要建立專案，其中包含範例資料類型</span><span class="sxs-lookup"><span data-stu-id="b00b9-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="b00b9-109">若要執行本主題中的範例，請開啟 Visual Studio，並加入新的 Visual Basic 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b00b9-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="b00b9-110">按兩下建立 Visual Basic 的 Module1.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="b00b9-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="b00b9-111">在這個主題使用範例`Person`和`Pet`類型和資料從下列程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="b00b9-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="b00b9-112">此程式碼複製到預設`Module1`Visual Basic 所建立的模組。</span><span class="sxs-lookup"><span data-stu-id="b00b9-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="b00b9-113">使用 Join 子句來執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="b00b9-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="b00b9-114">內部聯結結合來自兩個集合資料。</span><span class="sxs-lookup"><span data-stu-id="b00b9-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="b00b9-115">會包含符合指定的索引鍵值的項目。</span><span class="sxs-lookup"><span data-stu-id="b00b9-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="b00b9-116">會排除任何兩個集合的項目，另一個集合中沒有相符的項目。</span><span class="sxs-lookup"><span data-stu-id="b00b9-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="b00b9-117">在 Visual Basic 中的 LINQ 提供執行內部聯結的兩個選項： 隱含聯結和明確聯結。</span><span class="sxs-lookup"><span data-stu-id="b00b9-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="b00b9-118">隱含聯結指定要加入集合`From`子句，並指出在比對的索引鍵欄位`Where`子句。</span><span class="sxs-lookup"><span data-stu-id="b00b9-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="b00b9-119">Visual Basic 隱含聯結兩個指定的索引鍵欄位為基礎的集合。</span><span class="sxs-lookup"><span data-stu-id="b00b9-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="b00b9-120">您可以使用，以指定明確的聯結`Join`子句，當您想要明確的 join 中使用欄位的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b00b9-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="b00b9-121">在此情況下，`Where`子句仍可用來篩選查詢結果。</span><span class="sxs-lookup"><span data-stu-id="b00b9-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="b00b9-122">若要執行 Inner Join 使用 Join 子句</span><span class="sxs-lookup"><span data-stu-id="b00b9-122">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="b00b9-123">將下列程式碼加入`Module1`即可查看這兩個隱含和明確內部聯結的範例專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="b00b9-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="b00b9-124">使用 Group Join 子句來執行左外部聯結</span><span class="sxs-lookup"><span data-stu-id="b00b9-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="b00b9-125">左外部聯結包含的所有項目左邊之集合的結合，並只比對從聯結的右方集合的值。</span><span class="sxs-lookup"><span data-stu-id="b00b9-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="b00b9-126">從查詢結果會排除任何聯結的右方集合中的項目左邊的集合中沒有相符的項目。</span><span class="sxs-lookup"><span data-stu-id="b00b9-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="b00b9-127">`Group Join`子句執行時，作用中，LEFT OUTER JOIN。</span><span class="sxs-lookup"><span data-stu-id="b00b9-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="b00b9-128">通常稱左外部聯結和之間的差異`Group Join`子句會傳回在於`Group Join`右邊集合中的每個項目左邊的集合中的聯結子句群組結果。</span><span class="sxs-lookup"><span data-stu-id="b00b9-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="b00b9-129">在關聯式資料庫中，左外部聯結會傳回查詢中的每個項目發生已取消群組的結果會包含符合的項目，從這兩個聯結中的集合。</span><span class="sxs-lookup"><span data-stu-id="b00b9-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="b00b9-130">在此情況下，聯結的左方集合中的項目會重複每個相符項目從右邊的集合。</span><span class="sxs-lookup"><span data-stu-id="b00b9-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="b00b9-131">您會看到什麼這看起來像當您完成下一個程序。</span><span class="sxs-lookup"><span data-stu-id="b00b9-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="b00b9-132">您可以擷取的結果`Group Join`擴充查詢傳回的每個群組的查詢結果項目已取消群組的結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="b00b9-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="b00b9-133">若要達成此目的，您必須確定針對查詢`DefaultIfEmpty`群組集合的方法。</span><span class="sxs-lookup"><span data-stu-id="b00b9-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="b00b9-134">這可確保聯結左側的集合中的項目會仍包含查詢結果中即使它們沒有符合的結果，從右邊的集合。</span><span class="sxs-lookup"><span data-stu-id="b00b9-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="b00b9-135">您可以將程式碼加入至查詢，以從聯結的右方集合沒有相符的值時提供預設的結果值。</span><span class="sxs-lookup"><span data-stu-id="b00b9-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="b00b9-136">若要執行左方外部聯結使用 Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="b00b9-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="b00b9-137">將下列程式碼加入`Module1`專案，以查看群組左方外部聯結和已取消群組的左方外部聯結的範例中的模組。</span><span class="sxs-lookup"><span data-stu-id="b00b9-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="b00b9-138">使用複合索引鍵執行聯結</span><span class="sxs-lookup"><span data-stu-id="b00b9-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="b00b9-139">您可以使用`And`關鍵字`Join`或`Group Join`中要聯結之集合的子句來識別比對時使用的多個索引鍵欄位值。</span><span class="sxs-lookup"><span data-stu-id="b00b9-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="b00b9-140">`And`關鍵字會指定所有指定的索引鍵欄位必須符合，聯結的項目。</span><span class="sxs-lookup"><span data-stu-id="b00b9-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="b00b9-141">若要使用複合索引鍵執行聯結</span><span class="sxs-lookup"><span data-stu-id="b00b9-141">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="b00b9-142">將下列程式碼加入`Module1`即可查看使用複合索引鍵的聯結的範例專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="b00b9-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a><span data-ttu-id="b00b9-143">執行程式碼</span><span class="sxs-lookup"><span data-stu-id="b00b9-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="b00b9-144">加入程式碼以執行範例</span><span class="sxs-lookup"><span data-stu-id="b00b9-144">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="b00b9-145">取代`Sub Main`中`Module1`執行本主題中的範例為下列程式碼專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="b00b9-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  <span data-ttu-id="b00b9-146">按 F5 執行範例。</span><span class="sxs-lookup"><span data-stu-id="b00b9-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00b9-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b00b9-147">See Also</span></span>  
 [<span data-ttu-id="b00b9-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="b00b9-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="b00b9-149">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="b00b9-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="b00b9-150">Join 子句</span><span class="sxs-lookup"><span data-stu-id="b00b9-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)  
 [<span data-ttu-id="b00b9-151">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="b00b9-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [<span data-ttu-id="b00b9-152">From 子句</span><span class="sxs-lookup"><span data-stu-id="b00b9-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="b00b9-153">Where 子句</span><span class="sxs-lookup"><span data-stu-id="b00b9-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="b00b9-154">查詢</span><span class="sxs-lookup"><span data-stu-id="b00b9-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="b00b9-155">使用 LINQ 轉換資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="b00b9-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
