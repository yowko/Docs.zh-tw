---
title: "在 Visual Basic 中撰寫查詢 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: 70
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3e946ad09c36e94758ce13b4a37a6bf6ae54f947
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="7bf36-102">逐步解說：在 Visual Basic 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="7bf36-102">Walkthrough: Writing Queries in Visual Basic</span></span>
<span data-ttu-id="7bf36-103">本逐步解說會示範如何使用 Visual Basic 語言功能，撰寫[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="7bf36-103">This walkthrough demonstrates how you can use Visual Basic language features to write [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] query expressions.</span></span> <span data-ttu-id="7bf36-104">逐步解說將示範如何建立查詢清單中的學生物件、 如何執行查詢，以及如何修改它們。</span><span class="sxs-lookup"><span data-stu-id="7bf36-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="7bf36-105">查詢會將數個功能，包括物件初始設定式、 區域型別推斷和匿名型別。</span><span class="sxs-lookup"><span data-stu-id="7bf36-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>  
  
 <span data-ttu-id="7bf36-106">完成本逐步解說之後, 您就可以移到特定的文件與範例[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]您感興趣的提供者。</span><span class="sxs-lookup"><span data-stu-id="7bf36-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provider you are interested in.</span></span> [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]<span data-ttu-id="7bf36-107">提供者包括[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]， [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]，和[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7bf36-107"> providers include [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], and [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span>  
  
## <a name="create-a-project"></a><span data-ttu-id="7bf36-108">建立專案</span><span class="sxs-lookup"><span data-stu-id="7bf36-108">Create a Project</span></span>  
  
#### <a name="to-create-a-console-application-project"></a><span data-ttu-id="7bf36-109">若要建立主控台應用程式專案</span><span class="sxs-lookup"><span data-stu-id="7bf36-109">To create a console application project</span></span>  
  
1.  <span data-ttu-id="7bf36-110">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7bf36-110">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7bf36-111">在 [檔案] **** 功能表中，指向 [新增] ****，然後按一下 [專案] ****。</span><span class="sxs-lookup"><span data-stu-id="7bf36-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="7bf36-112">在**已安裝的範本**清單中，按一下**Visual Basic**。</span><span class="sxs-lookup"><span data-stu-id="7bf36-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>  
  
4.  <span data-ttu-id="7bf36-113">在專案類型清單中，按一下 **主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7bf36-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="7bf36-114">在**名稱**方塊內輸入專案的名稱，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="7bf36-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7bf36-115">建立專案。</span><span class="sxs-lookup"><span data-stu-id="7bf36-115">A project is created.</span></span> <span data-ttu-id="7bf36-116">根據預設，它包含 system.core.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="7bf36-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="7bf36-117">此外，**匯入命名空間**清單[專案設計工具 (Visual Basic)、 參考頁](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)包含<xref:System.Linq?displayProperty=fullName>命名空間。</xref:System.Linq?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="7bf36-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=fullName> namespace.</span></span>  
  
5.  <span data-ttu-id="7bf36-118">在[編譯的頁面上，專案設計工具 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，請確認**Option infer**設為**上**。</span><span class="sxs-lookup"><span data-stu-id="7bf36-118">On the [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>  
  
## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="7bf36-119">將記憶體中的資料來源</span><span class="sxs-lookup"><span data-stu-id="7bf36-119">Add an In-Memory Data Source</span></span>  
 <span data-ttu-id="7bf36-120">在此逐步解說中查詢的資料來源是一份`Student`物件。</span><span class="sxs-lookup"><span data-stu-id="7bf36-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="7bf36-121">每個`Student`物件包含名字、 姓氏、 類別年和學術學生主體中的陣序規範。</span><span class="sxs-lookup"><span data-stu-id="7bf36-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="7bf36-122">若要新增資料來源</span><span class="sxs-lookup"><span data-stu-id="7bf36-122">To add the data source</span></span>  
  
-   <span data-ttu-id="7bf36-123">定義`Student`類別，並建立一份類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7bf36-123">Define a `Student` class, and create a list of instances of the class.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7bf36-124">定義所需的程式碼`Student`類別使用的清單，並在這個逐步解說中提供範例[How to︰ 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。</span><span class="sxs-lookup"><span data-stu-id="7bf36-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="7bf36-125">您可以從該處複製它，並將它貼到您的專案。</span><span class="sxs-lookup"><span data-stu-id="7bf36-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="7bf36-126">新的程式碼會取代您在建立專案時出現的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7bf36-126">The new code replaces the code that appeared when you created the project.</span></span>  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="7bf36-127">若要新增新的學生學生清單</span><span class="sxs-lookup"><span data-stu-id="7bf36-127">To add a new student to the students list</span></span>  
  
-   <span data-ttu-id="7bf36-128">請依照下列中的模式`getStudents`方法，加入另一個執行個體`Student`類別清單。</span><span class="sxs-lookup"><span data-stu-id="7bf36-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="7bf36-129">加入學生將為您介紹物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="7bf36-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="7bf36-130">如需詳細資訊，請參閱[物件初始設定式︰ 具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7bf36-130">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="create-a-query"></a><span data-ttu-id="7bf36-131">建立查詢</span><span class="sxs-lookup"><span data-stu-id="7bf36-131">Create a Query</span></span>  
 <span data-ttu-id="7bf36-132">執行時，加入本節中的查詢會產生一份學術排名將它們放入前十名的學生。</span><span class="sxs-lookup"><span data-stu-id="7bf36-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="7bf36-133">因為此查詢會選取完整`Student`物件每次都查詢結果的型別是`IEnumerable(Of Student)`。</span><span class="sxs-lookup"><span data-stu-id="7bf36-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="7bf36-134">不過，查詢的型別通常未指定在查詢定義中。</span><span class="sxs-lookup"><span data-stu-id="7bf36-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="7bf36-135">相反地，編譯器會使用區域型別推斷來判斷型別。</span><span class="sxs-lookup"><span data-stu-id="7bf36-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="7bf36-136">如需詳細資訊，請參閱[本機的型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="7bf36-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="7bf36-137">查詢的範圍變數， `currentStudent`，做為每個參考`Student`來源中的執行個體`students`，在每個物件的屬性來存取`students`。</span><span class="sxs-lookup"><span data-stu-id="7bf36-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="7bf36-138">建立簡單查詢</span><span class="sxs-lookup"><span data-stu-id="7bf36-138">To create a simple query</span></span>  
  
1.  <span data-ttu-id="7bf36-139">尋找中`Main`方法之專案的標記，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="7bf36-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>  
  
     <span data-ttu-id="7bf36-140">[!code-vb[VbLINQWalkthrough #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7bf36-140">[!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]</span></span>  
  
     <span data-ttu-id="7bf36-141">下列程式碼複製並貼上。</span><span class="sxs-lookup"><span data-stu-id="7bf36-141">Copy the following code and paste it in.</span></span>  
  
     <span data-ttu-id="7bf36-142">[!code-vb[VbLINQWalkthrough #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7bf36-142">[!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]</span></span>  
  
2.  <span data-ttu-id="7bf36-143">將滑鼠指標停留`studentQuery`在您的程式碼，以驗證的編譯器指派型`IEnumerable(Of Student)`。</span><span class="sxs-lookup"><span data-stu-id="7bf36-143">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>  
  
## <a name="run-the-query"></a><span data-ttu-id="7bf36-144">執行查詢</span><span class="sxs-lookup"><span data-stu-id="7bf36-144">Run the Query</span></span>  
 <span data-ttu-id="7bf36-145">變數`studentQuery`包含定義的查詢，而不執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="7bf36-145">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="7bf36-146">執行查詢的一般機制是`For Each`迴圈。</span><span class="sxs-lookup"><span data-stu-id="7bf36-146">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="7bf36-147">傳回序列中的每個項目被經由迴圈反覆運算變數。</span><span class="sxs-lookup"><span data-stu-id="7bf36-147">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="7bf36-148">如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="7bf36-148">For more information about query execution, see [Writing Your First LINQ Query](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
#### <a name="to-run-the-query"></a><span data-ttu-id="7bf36-149">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="7bf36-149">To run the query</span></span>  
  
1.  <span data-ttu-id="7bf36-150">新增下列`For Each`迴圈低於您的專案中的查詢。</span><span class="sxs-lookup"><span data-stu-id="7bf36-150">Add the following `For Each` loop below the query in your project.</span></span>  
  
     <span data-ttu-id="7bf36-151">[!code-vb[VbLINQWalkthrough #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7bf36-151">[!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]</span></span>  
  
2.  <span data-ttu-id="7bf36-152">將滑鼠指標停留在迴圈控制變數`studentRecord`以查看其資料型別。</span><span class="sxs-lookup"><span data-stu-id="7bf36-152">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="7bf36-153">型別`studentRecord`就會推斷`Student`，因為`studentQuery`傳回的集合`Student`執行個體。</span><span class="sxs-lookup"><span data-stu-id="7bf36-153">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>  
  
3.  <span data-ttu-id="7bf36-154">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7bf36-154">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7bf36-155">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="7bf36-155">Note the results in the console window.</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="7bf36-156">修改查詢</span><span class="sxs-lookup"><span data-stu-id="7bf36-156">Modify the Query</span></span>  
 <span data-ttu-id="7bf36-157">就很容易掃描查詢結果，如果它們是在指定的順序。</span><span class="sxs-lookup"><span data-stu-id="7bf36-157">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="7bf36-158">您可以排序傳回的序列，根據任何可用的欄位。</span><span class="sxs-lookup"><span data-stu-id="7bf36-158">You can sort the returned sequence based on any available field.</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="7bf36-159">若要排序結果</span><span class="sxs-lookup"><span data-stu-id="7bf36-159">To order the results</span></span>  
  
1.  <span data-ttu-id="7bf36-160">新增下列`Order By`子句之間`Where`陳述式和`Select`查詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="7bf36-160">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="7bf36-161">`Order By`子句會排序結果依字母順序從 A 到 Z，到最後一個根據每個學生的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bf36-161">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  <span data-ttu-id="7bf36-162">若要排序姓氏和名字，這兩個欄位加入查詢︰</span><span class="sxs-lookup"><span data-stu-id="7bf36-162">To order by last name and then first name, add both fields to the query:</span></span>  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     <span data-ttu-id="7bf36-163">您也可以指定`Descending`順序從 Z 到 a。</span><span class="sxs-lookup"><span data-stu-id="7bf36-163">You can also specify `Descending` to order from Z to A.</span></span>  
  
3.  <span data-ttu-id="7bf36-164">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7bf36-164">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7bf36-165">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="7bf36-165">Note the results in the console window.</span></span>  
  
#### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="7bf36-166">導入區域識別項</span><span class="sxs-lookup"><span data-stu-id="7bf36-166">To introduce a local identifier</span></span>  
  
1.  <span data-ttu-id="7bf36-167">本節介紹區域識別項在查詢運算式中的加入程式碼。</span><span class="sxs-lookup"><span data-stu-id="7bf36-167">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="7bf36-168">區域識別項會保留中繼結果。</span><span class="sxs-lookup"><span data-stu-id="7bf36-168">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="7bf36-169">在下列範例中，`name`是識別項會保留串連名學生的名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="7bf36-169">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="7bf36-170">為了方便起見，可用的本機識別碼或它可以儲存結果的運算式，否則會計算多次，以提高效能。</span><span class="sxs-lookup"><span data-stu-id="7bf36-170">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>  
  
     <span data-ttu-id="7bf36-171">[!code-vb[VbLINQWalkthrough #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="7bf36-171">[!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]</span></span>  
  
2.  <span data-ttu-id="7bf36-172">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7bf36-172">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7bf36-173">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="7bf36-173">Note the results in the console window.</span></span>  
  
#### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="7bf36-174">專案 Select 子句中的一個欄位</span><span class="sxs-lookup"><span data-stu-id="7bf36-174">To project one field in the Select clause</span></span>  
  
1.  <span data-ttu-id="7bf36-175">將查詢加入和`For Each`迴圈，從這個區段來建立查詢，以產生的序列，其項目會與不同來源中的項目。</span><span class="sxs-lookup"><span data-stu-id="7bf36-175">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="7bf36-176">在下列範例中，來源是一系列`Student`傳回物件，而每個物件只能有一個成員︰ 姓氏是 Garcia 學生的名字。</span><span class="sxs-lookup"><span data-stu-id="7bf36-176">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="7bf36-177">因為`currentStudent.First`為字串時，所傳回的序列的資料型別`studentQuery3`是`IEnumerable(Of String)`，字串序列。</span><span class="sxs-lookup"><span data-stu-id="7bf36-177">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="7bf36-178">如先前的範例所示輸入的資料指派`studentQuery3`使用區域型別推斷來判斷編譯器會保留。</span><span class="sxs-lookup"><span data-stu-id="7bf36-178">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>  
  
     <span data-ttu-id="7bf36-179">[!code-vb[VbLINQWalkthrough #&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="7bf36-179">[!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]</span></span>  
  
2.  <span data-ttu-id="7bf36-180">將滑鼠指標停留`studentQuery3`在您的程式碼，以確認是否已指派的型別`IEnumerable(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="7bf36-180">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>  
  
3.  <span data-ttu-id="7bf36-181">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7bf36-181">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7bf36-182">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="7bf36-182">Note the results in the console window.</span></span>  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="7bf36-183">在 Select 子句中建立匿名型別</span><span class="sxs-lookup"><span data-stu-id="7bf36-183">To create an anonymous type in the Select clause</span></span>  
  
1.  <span data-ttu-id="7bf36-184">加入此區段可查看如何匿名型別中的程式碼會在查詢中使用。</span><span class="sxs-lookup"><span data-stu-id="7bf36-184">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="7bf36-185">您它們在查詢中使用當您想要從資料來源，而不是完整記錄傳回多個欄位 (`currentStudent`先前範例中的記錄) 或單一欄位 (`First`前一節)。</span><span class="sxs-lookup"><span data-stu-id="7bf36-185">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="7bf36-186">而不是定義新的具名型別，其中包含您想要包含在結果中的欄位，您指定的欄位`Select`子句和編譯器會使用這些欄位做為其屬性建立匿名型別。</span><span class="sxs-lookup"><span data-stu-id="7bf36-186">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="7bf36-187">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7bf36-187">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="7bf36-188">下列範例會建立查詢，傳回的名稱和前輩學術排名是介於 1 到 10 的學術排名順序的陣序規範。</span><span class="sxs-lookup"><span data-stu-id="7bf36-188">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="7bf36-189">在此範例中的型別`studentQuery4`必須推斷，因為`Select`子句會傳回匿名型別執行個體和匿名型別已經沒有可用的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bf36-189">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>  
  
     <span data-ttu-id="7bf36-190">[!code-vb[VbLINQWalkthrough #&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="7bf36-190">[!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]</span></span>  
  
2.  <span data-ttu-id="7bf36-191">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7bf36-191">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="7bf36-192">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="7bf36-192">Note the results in the console window.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="7bf36-193">其他範例</span><span class="sxs-lookup"><span data-stu-id="7bf36-193">Additional Examples</span></span>  
 <span data-ttu-id="7bf36-194">現在您已了解基本概念，以下是列出其他範例來說明彈性和能力[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="7bf36-194">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries.</span></span> <span data-ttu-id="7bf36-195">每個範例被前面有何用途的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="7bf36-195">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="7bf36-196">將滑鼠指標停留在查詢結果變數的每個查詢來查看推斷的型別。</span><span class="sxs-lookup"><span data-stu-id="7bf36-196">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="7bf36-197">使用`For Each`迴圈，產生的結果。</span><span class="sxs-lookup"><span data-stu-id="7bf36-197">Use a `For Each` loop to produce the results.</span></span>  
  
 <span data-ttu-id="7bf36-198">[!code-vb[VbLINQWalkthrough #&7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="7bf36-198">[!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]</span></span>  
  
## <a name="additional-information"></a><span data-ttu-id="7bf36-199">其他資訊</span><span class="sxs-lookup"><span data-stu-id="7bf36-199">Additional Information</span></span>  
 <span data-ttu-id="7bf36-200">您已熟悉使用查詢的基本概念之後，您就準備好要讀取的特定類型的文件和範例[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]您感興趣的提供者︰</span><span class="sxs-lookup"><span data-stu-id="7bf36-200">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provider that you are interested in:</span></span>  
  
 [<span data-ttu-id="7bf36-201">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="7bf36-201">LINQ to Objects</span></span>](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [<span data-ttu-id="7bf36-202">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7bf36-202">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
  
 [<span data-ttu-id="7bf36-203">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="7bf36-203">LINQ to XML</span></span>](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [<span data-ttu-id="7bf36-204">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7bf36-204">LINQ to DataSet</span></span>](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)  
  
## <a name="see-also"></a><span data-ttu-id="7bf36-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bf36-205">See Also</span></span>  
 <span data-ttu-id="7bf36-206">[語言整合查詢 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="7bf36-206">[Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md) </span></span>  
<span data-ttu-id="7bf36-207"> [在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="7bf36-207"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="7bf36-208"> [區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="7bf36-208"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="7bf36-209"> [物件初始設定式︰ 具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="7bf36-209"> [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="7bf36-210"> [匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="7bf36-210"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="7bf36-211"> [在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="7bf36-211"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="7bf36-212"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="7bf36-212"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="7bf36-213"> [查詢](../../../../visual-basic/language-reference/queries/queries.md)</span><span class="sxs-lookup"><span data-stu-id="7bf36-213"> [Queries](../../../../visual-basic/language-reference/queries/queries.md)</span></span>
