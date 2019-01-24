---
title: HOW TO：以 LINQ 合併資料使用聯結 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], joins
- joins [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- Group Join clause [Visual Basic]
- joining [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
ms.openlocfilehash: fd1025d056dfb11d2253a39defb384c1d05efa32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553694"
---
# <a name="how-to-combine-data-with-linq-by-using-joins-visual-basic"></a><span data-ttu-id="fcb7b-102">HOW TO：以 LINQ 合併資料使用聯結 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcb7b-102">How to: Combine Data with LINQ by Using Joins (Visual Basic)</span></span>
<span data-ttu-id="fcb7b-103">Visual Basic 提供`Join`和`Group Join`查詢子句可讓您結合多個集合之間的一般值為基礎的集合的內容。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-103">Visual Basic provides the `Join` and `Group Join` query clauses to enable you to combine the contents of multiple collections based on common values between the collections.</span></span> <span data-ttu-id="fcb7b-104">這些值稱為*金鑰*值。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-104">These values are known as *key* values.</span></span> <span data-ttu-id="fcb7b-105">開發人員熟悉關聯式資料庫概念會辨識`Join`INNER JOIN 子句和`Group Join`做為有效，LEFT OUTER JOIN 子句。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-105">Developers familiar with relational database concepts will recognize the `Join` clause as an INNER JOIN and the `Group Join` clause as, effectively, a LEFT OUTER JOIN.</span></span>  
  
 <span data-ttu-id="fcb7b-106">本主題中的範例將示範幾種方式使用合併資料`Join`和`Group Join`查詢子句。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-106">The examples in this topic demonstrate a few ways to combine data by using the `Join` and `Group Join` query clauses.</span></span>  
  
## <a name="create-a-project-and-add-sample-data"></a><span data-ttu-id="fcb7b-107">建立專案，並將範例資料</span><span class="sxs-lookup"><span data-stu-id="fcb7b-107">Create a Project and Add Sample Data</span></span>  
  
#### <a name="to-create-a-project-that-contains-sample-data-and-types"></a><span data-ttu-id="fcb7b-108">若要建立包含範例資料和類型的專案</span><span class="sxs-lookup"><span data-stu-id="fcb7b-108">To create a project that contains sample data and types</span></span>  
  
1.  <span data-ttu-id="fcb7b-109">若要執行本主題中的範例，請開啟 Visual Studio，並加入新的 Visual Basic 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-109">To run the samples in this topic, open Visual Studio and add a new Visual Basic Console Application project.</span></span> <span data-ttu-id="fcb7b-110">按兩下建立 Visual basic 的 Module1.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-110">Double-click the Module1.vb file created by Visual Basic.</span></span>  
  
2.  <span data-ttu-id="fcb7b-111">在本主題使用範例`Person`和`Pet`類型和下列程式碼範例中的資料。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-111">The samples in this topic use the `Person` and `Pet` types and data from the following code example.</span></span> <span data-ttu-id="fcb7b-112">此程式碼複製到預設`Module1`Visual Basic 所建立的模組。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-112">Copy this code into the default `Module1` module created by Visual Basic.</span></span>  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_1.vb)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_2.vb)]  
  
## <a name="perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="fcb7b-113">使用 Join 子句執行內部聯結</span><span class="sxs-lookup"><span data-stu-id="fcb7b-113">Perform an Inner Join by Using the Join Clause</span></span>  
 <span data-ttu-id="fcb7b-114">INNER JOIN 結合來自兩個集合的資料。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-114">An INNER JOIN combines data from two collections.</span></span> <span data-ttu-id="fcb7b-115">會包含符合指定的索引鍵值的項目。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-115">Items for which the specified key values match are included.</span></span> <span data-ttu-id="fcb7b-116">會排除任何兩個集合的項目，在另一個集合中沒有相符的項目。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-116">Any items from either collection that do not have a matching item in the other collection are excluded.</span></span>  
  
 <span data-ttu-id="fcb7b-117">在 Visual Basic 中的 LINQ 提供執行內部聯結的兩個選項： 隱含聯結和明確聯結。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-117">In Visual Basic, LINQ provides two options for performing an INNER JOIN: an implicit join and an explicit join.</span></span>  
  
 <span data-ttu-id="fcb7b-118">隱含聯結指定的集合加入`From`子句，並指出在比對的索引鍵欄位`Where`子句。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-118">An implicit join specifies the collections to be joined in a `From` clause and identifies the matching key fields in a `Where` clause.</span></span> <span data-ttu-id="fcb7b-119">Visual Basic 隱含聯結兩個集合根據指定的索引鍵欄位。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-119">Visual Basic implicitly joins the two collections based on the specified key fields.</span></span>  
  
 <span data-ttu-id="fcb7b-120">您可以使用，以指定明確的聯結`Join`子句，當您想要特定的對哪一個索引鍵欄位在聯結中使用。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-120">You can specify an explicit join by using the `Join` clause when you want to be specific about which key fields to use in the join.</span></span> <span data-ttu-id="fcb7b-121">在此情況下，`Where`子句仍可用來篩選查詢結果。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-121">In this case, a `Where` clause can still be used to filter the query results.</span></span>  
  
#### <a name="to-perform-an-inner-join-by-using-the-join-clause"></a><span data-ttu-id="fcb7b-122">若要執行使用 Join 子句的 Inner Join</span><span class="sxs-lookup"><span data-stu-id="fcb7b-122">To perform an Inner Join by using the Join clause</span></span>  
  
1.  <span data-ttu-id="fcb7b-123">將下列程式碼加入`Module1`若要查看這兩個隱含和明確內部聯結的範例專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-123">Add the following code to the `Module1` module in your project to see examples of both an implicit and explicit inner join.</span></span>  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_3.vb)]  
  
## <a name="perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="fcb7b-124">使用 Group Join 子句來執行左方外部聯結</span><span class="sxs-lookup"><span data-stu-id="fcb7b-124">Perform a Left Outer Join by Using the Group Join Clause</span></span>  
 <span data-ttu-id="fcb7b-125">左外部聯結中包含的所有項目左側集合的聯結，以及僅比對從聯結的右方集合的值。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-125">A LEFT OUTER JOIN includes all the items from the left-side collection of the join and only matching values from the right-side collection of the join.</span></span> <span data-ttu-id="fcb7b-126">從查詢結果會排除任何從聯結的右方集合的項目左邊的集合中沒有相符的項目。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-126">Any items from the right-side collection of the join that do not have a matching item in the left-side collection are excluded from the query result.</span></span>  
  
 <span data-ttu-id="fcb7b-127">`Group Join`子句執行時，實際上，LEFT OUTER JOIN。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-127">The `Group Join` clause performs, in effect, a LEFT OUTER JOIN.</span></span> <span data-ttu-id="fcb7b-128">通常稱左外部聯結和之間的差異`Group Join`是的子句會傳回`Group Join`右側集合中的每個項目左邊的集合中的聯結子句群組結果。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-128">The difference between what is typically known as a LEFT OUTER JOIN and what the `Group Join` clause returns is that the `Group Join` clause groups results from the right-side collection of the join for each item in the left-side collection.</span></span> <span data-ttu-id="fcb7b-129">在關聯式資料庫中，左外部聯結會傳回已取消群組的結果，在查詢中的每個項目會造成在其中包含符合的項目，從這兩個聯結的集合。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-129">In a relational database, a LEFT OUTER JOIN returns an ungrouped result in which each item in the query result contains matching items from both collections in the join.</span></span> <span data-ttu-id="fcb7b-130">在此情況下，從聯結的左側集合的項目會重複的每個相符的項目，從右邊的集合。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-130">In this case, the items from the left-side collection of the join are repeated for each matching item from the right-side collection.</span></span> <span data-ttu-id="fcb7b-131">您會看到看起來像這樣當您完成下一個程序。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-131">You will see what this looks like when you complete the next procedure.</span></span>  
  
 <span data-ttu-id="fcb7b-132">您可以擷取的結果`Group Join`做為已取消群組的結果，藉由擴充您的查詢傳回的項目，針對每個群組的查詢結果的查詢。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-132">You can retrieve the results of a `Group Join` query as an ungrouped result by extending your query to return an item for each grouped query result.</span></span> <span data-ttu-id="fcb7b-133">若要這麼做，您必須確定您查詢上`DefaultIfEmpty`的群組集合的方法。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-133">To accomplish this, you have to ensure that you query on the `DefaultIfEmpty` method of the grouped collection.</span></span> <span data-ttu-id="fcb7b-134">這可確保，從聯結的左側集合的項目仍然包含在查詢結果即使它們有沒有符合的結果，從右邊的集合。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-134">This ensures that items from the left-side collection of the join are still included in the query result even if they have no matching results from the right-side collection.</span></span> <span data-ttu-id="fcb7b-135">您可以將程式碼加入您的查詢，以從聯結的右方集合沒有相符的值時提供預設的結果值。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-135">You can add code to your query to provide a default result value when there is no matching value from the right-side collection of the join.</span></span>  
  
#### <a name="to-perform-a-left-outer-join-by-using-the-group-join-clause"></a><span data-ttu-id="fcb7b-136">若要執行左方外部聯結使用 Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="fcb7b-136">To perform a Left Outer Join by using the Group Join clause</span></span>  
  
1.  <span data-ttu-id="fcb7b-137">將下列程式碼加入`Module1`以查看群組的左方外部聯結和已取消群組的左方外部聯結的範例專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-137">Add the following code to the `Module1` module in your project to see examples of both a grouped left outer join and an ungrouped left outer join.</span></span>  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_4.vb)]  
  
## <a name="perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="fcb7b-138">使用複合索引鍵執行聯結</span><span class="sxs-lookup"><span data-stu-id="fcb7b-138">Perform a Join by Using a Composite Key</span></span>  
 <span data-ttu-id="fcb7b-139">您可以使用`And`中的關鍵字`Join`或`Group Join`子句來識別比對時所要使用的多個索引鍵欄位值所聯結之集合中。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-139">You can use the `And` keyword in a `Join` or `Group Join` clause to identify multiple key fields to use when matching values from the collections being joined.</span></span> <span data-ttu-id="fcb7b-140">`And`關鍵字會指定所有指定的索引鍵欄位必須符合要加入的項目。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-140">The `And` keyword specifies that all specified key fields must match for items to be joined.</span></span>  
  
#### <a name="to-perform-a-join-by-using-a-composite-key"></a><span data-ttu-id="fcb7b-141">若要使用複合索引鍵執行聯結</span><span class="sxs-lookup"><span data-stu-id="fcb7b-141">To perform a Join by using a composite key</span></span>  
  
1.  <span data-ttu-id="fcb7b-142">將下列程式碼加入`Module1`即可查看使用複合索引鍵的聯結的範例專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-142">Add the following code to the `Module1` module in your project to see examples of a join that uses a composite key.</span></span>  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_5.vb)]  
  
## <a name="run-the-code"></a><span data-ttu-id="fcb7b-143">執行程式碼</span><span class="sxs-lookup"><span data-stu-id="fcb7b-143">Run the Code</span></span>  
  
#### <a name="to-add-code-to-run-the-examples"></a><span data-ttu-id="fcb7b-144">加入程式碼以執行範例</span><span class="sxs-lookup"><span data-stu-id="fcb7b-144">To add code to run the examples</span></span>  
  
1.  <span data-ttu-id="fcb7b-145">取代`Sub Main`在`Module1`下列的程式碼，以執行本主題中的範例專案中的模組。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-145">Replace the `Sub Main` in the `Module1` module in your project with the following code to run the examples in this topic.</span></span>  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-combine-data-with-linq-by-using-joins_6.vb)]  
  
2.  <span data-ttu-id="fcb7b-146">按 F5 執行範例。</span><span class="sxs-lookup"><span data-stu-id="fcb7b-146">Press F5 to run the examples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcb7b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcb7b-147">See also</span></span>
- [<span data-ttu-id="fcb7b-148">LINQ</span><span class="sxs-lookup"><span data-stu-id="fcb7b-148">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="fcb7b-149">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="fcb7b-149">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="fcb7b-150">Join 子句</span><span class="sxs-lookup"><span data-stu-id="fcb7b-150">Join Clause</span></span>](../../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="fcb7b-151">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="fcb7b-151">Group Join Clause</span></span>](../../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="fcb7b-152">From 子句</span><span class="sxs-lookup"><span data-stu-id="fcb7b-152">From Clause</span></span>](../../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="fcb7b-153">Where 子句</span><span class="sxs-lookup"><span data-stu-id="fcb7b-153">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="fcb7b-154">查詢</span><span class="sxs-lookup"><span data-stu-id="fcb7b-154">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="fcb7b-155">使用 LINQ 轉換資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="fcb7b-155">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)
