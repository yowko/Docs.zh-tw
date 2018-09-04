---
title: 在 Visual Basic 中撰寫查詢
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 2f641d04b53d2e80985defcd6bd9a4882004fd97
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533218"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="26b2c-102">逐步解說：在 Visual Basic 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="26b2c-102">Walkthrough: Writing Queries in Visual Basic</span></span>
<span data-ttu-id="26b2c-103">本逐步解說示範如何使用 Visual Basic 語言功能，以及在寫入[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="26b2c-103">This walkthrough demonstrates how you can use Visual Basic language features to write [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query expressions.</span></span> <span data-ttu-id="26b2c-104">逐步解說示範如何建立一份學生物件上的查詢、 如何執行查詢，以及如何修改它們。</span><span class="sxs-lookup"><span data-stu-id="26b2c-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="26b2c-105">查詢會將數個功能，包括物件初始設定式、 區域類型推斷和匿名型別。</span><span class="sxs-lookup"><span data-stu-id="26b2c-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>  
  
 <span data-ttu-id="26b2c-106">完成本逐步解說之後, 您就可以移至特定的文件與範例[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]您感興趣的提供者。</span><span class="sxs-lookup"><span data-stu-id="26b2c-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider you are interested in.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="26b2c-107"> 提供者包括[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]， [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]，和[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="26b2c-107"> providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
## <a name="create-a-project"></a><span data-ttu-id="26b2c-108">建立專案</span><span class="sxs-lookup"><span data-stu-id="26b2c-108">Create a Project</span></span>  
  
#### <a name="to-create-a-console-application-project"></a><span data-ttu-id="26b2c-109">若要建立主控台應用程式專案</span><span class="sxs-lookup"><span data-stu-id="26b2c-109">To create a console application project</span></span>  
  
1.  <span data-ttu-id="26b2c-110">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="26b2c-110">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="26b2c-111">在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。</span><span class="sxs-lookup"><span data-stu-id="26b2c-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="26b2c-112">在 **已安裝的範本**清單中，按一下**Visual Basic**。</span><span class="sxs-lookup"><span data-stu-id="26b2c-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>  
  
4.  <span data-ttu-id="26b2c-113">在專案類型清單中，按一下**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="26b2c-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="26b2c-114">在 **名稱**方塊中，輸入專案的名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="26b2c-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>  
  
     <span data-ttu-id="26b2c-115">建立專案。</span><span class="sxs-lookup"><span data-stu-id="26b2c-115">A project is created.</span></span> <span data-ttu-id="26b2c-116">根據預設，它包含對 System.Core.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="26b2c-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="26b2c-117">此外，**匯入命名空間**上列出[專案設計工具 (Visual Basic)、 參考頁](/visualstudio/ide/reference/references-page-project-designer-visual-basic)包含<xref:System.Linq?displayProperty=nameWithType>命名空間。</span><span class="sxs-lookup"><span data-stu-id="26b2c-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
5.  <span data-ttu-id="26b2c-118">在上[編譯的 Page，Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，請確認**Option infer**設定為**上**。</span><span class="sxs-lookup"><span data-stu-id="26b2c-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>  
  
## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="26b2c-119">加入記憶體中的資料來源</span><span class="sxs-lookup"><span data-stu-id="26b2c-119">Add an In-Memory Data Source</span></span>  
 <span data-ttu-id="26b2c-120">本逐步解說中的查詢的資料來源是一份`Student`物件。</span><span class="sxs-lookup"><span data-stu-id="26b2c-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="26b2c-121">每個`Student`物件包含名字、 姓氏、 一類別，以及 academic 學生主體中的陣序規範。</span><span class="sxs-lookup"><span data-stu-id="26b2c-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="26b2c-122">若要新增資料來源</span><span class="sxs-lookup"><span data-stu-id="26b2c-122">To add the data source</span></span>  
  
-   <span data-ttu-id="26b2c-123">定義`Student`類別，並建立一份類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="26b2c-123">Define a `Student` class, and create a list of instances of the class.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="26b2c-124">定義所需的程式碼`Student`類別，並建立使用的清單中的逐步解說中提供範例[如何： 建立項目的清單](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)。</span><span class="sxs-lookup"><span data-stu-id="26b2c-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="26b2c-125">您可以從該處複製，並將它貼到您的專案。</span><span class="sxs-lookup"><span data-stu-id="26b2c-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="26b2c-126">新的程式碼取代您在建立專案時出現的程式碼。</span><span class="sxs-lookup"><span data-stu-id="26b2c-126">The new code replaces the code that appeared when you created the project.</span></span>  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="26b2c-127">若要將新的學生新增至學生清單</span><span class="sxs-lookup"><span data-stu-id="26b2c-127">To add a new student to the students list</span></span>  
  
-   <span data-ttu-id="26b2c-128">請依照下列中的模式`getStudents`方法，以新增另一個執行個體`Student`類別清單。</span><span class="sxs-lookup"><span data-stu-id="26b2c-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="26b2c-129">加入學生將為您介紹物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="26b2c-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="26b2c-130">如需詳細資訊，請參閱 <<c0> [ 物件初始設定式： 具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="26b2c-130">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="create-a-query"></a><span data-ttu-id="26b2c-131">建立查詢</span><span class="sxs-lookup"><span data-stu-id="26b2c-131">Create a Query</span></span>  
 <span data-ttu-id="26b2c-132">在執行時，在這一節中新增此查詢會產生學術排名將它們放入前十名學生的清單。</span><span class="sxs-lookup"><span data-stu-id="26b2c-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="26b2c-133">因為此查詢會選取完整`Student`物件每次查詢結果的型別是`IEnumerable(Of Student)`。</span><span class="sxs-lookup"><span data-stu-id="26b2c-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="26b2c-134">不過，查詢類型通常是未指定查詢定義中。</span><span class="sxs-lookup"><span data-stu-id="26b2c-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="26b2c-135">相反地，編譯器會使用區域類型推斷來判斷型別。</span><span class="sxs-lookup"><span data-stu-id="26b2c-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="26b2c-136">如需詳細資訊，請參閱 <<c0> [ 區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="26b2c-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="26b2c-137">查詢的範圍變數`currentStudent`，做為每個參考`Student`在來源中，執行個體`students`，提供存取權的每個物件在屬性`students`。</span><span class="sxs-lookup"><span data-stu-id="26b2c-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="26b2c-138">建立簡單查詢</span><span class="sxs-lookup"><span data-stu-id="26b2c-138">To create a simple query</span></span>  
  
1.  <span data-ttu-id="26b2c-139">尋找在處`Main`方法之專案的標記，如下所示：</span><span class="sxs-lookup"><span data-stu-id="26b2c-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     <span data-ttu-id="26b2c-140">下列程式碼複製並貼入。</span><span class="sxs-lookup"><span data-stu-id="26b2c-140">Copy the following code and paste it in.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  <span data-ttu-id="26b2c-141">將滑鼠指標停留`studentQuery`在您的程式碼，若要確認編譯器指派的類型為`IEnumerable(Of Student)`。</span><span class="sxs-lookup"><span data-stu-id="26b2c-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>  
  
## <a name="run-the-query"></a><span data-ttu-id="26b2c-142">執行查詢</span><span class="sxs-lookup"><span data-stu-id="26b2c-142">Run the Query</span></span>  
 <span data-ttu-id="26b2c-143">變數`studentQuery`包含定義的查詢，而不執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="26b2c-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="26b2c-144">執行查詢的一般機制是`For Each`迴圈。</span><span class="sxs-lookup"><span data-stu-id="26b2c-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="26b2c-145">透過迴圈反覆項目變數來存取傳回序列中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="26b2c-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="26b2c-146">如需有關查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="26b2c-146">For more information about query execution, see [Writing Your First LINQ Query](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
#### <a name="to-run-the-query"></a><span data-ttu-id="26b2c-147">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="26b2c-147">To run the query</span></span>  
  
1.  <span data-ttu-id="26b2c-148">新增下列`For Each`迴圈下您的專案中的查詢。</span><span class="sxs-lookup"><span data-stu-id="26b2c-148">Add the following `For Each` loop below the query in your project.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  <span data-ttu-id="26b2c-149">將滑鼠指標停留在迴圈控制變數`studentRecord`以查看其資料類型。</span><span class="sxs-lookup"><span data-stu-id="26b2c-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="26b2c-150">型別`studentRecord`就會推斷`Student`，因為`studentQuery`傳回的集合`Student`執行個體。</span><span class="sxs-lookup"><span data-stu-id="26b2c-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>  
  
3.  <span data-ttu-id="26b2c-151">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="26b2c-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="26b2c-152">請注意 [主控台] 視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="26b2c-152">Note the results in the console window.</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="26b2c-153">修改查詢</span><span class="sxs-lookup"><span data-stu-id="26b2c-153">Modify the Query</span></span>  
 <span data-ttu-id="26b2c-154">很容易就能掃描查詢結果，如果它們是在指定的順序。</span><span class="sxs-lookup"><span data-stu-id="26b2c-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="26b2c-155">您可以排序所傳回的序列，根據任何可用的欄位。</span><span class="sxs-lookup"><span data-stu-id="26b2c-155">You can sort the returned sequence based on any available field.</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="26b2c-156">若要排序結果</span><span class="sxs-lookup"><span data-stu-id="26b2c-156">To order the results</span></span>  
  
1.  <span data-ttu-id="26b2c-157">新增下列`Order By`子句之間`Where`陳述式和`Select`查詢陳述式。</span><span class="sxs-lookup"><span data-stu-id="26b2c-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="26b2c-158">`Order By`子句會排序結果依字母順序從 A 到 Z，到最後一個根據每個學生的名稱。</span><span class="sxs-lookup"><span data-stu-id="26b2c-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  <span data-ttu-id="26b2c-159">若要排序姓氏及名字，加入查詢中的兩個欄位：</span><span class="sxs-lookup"><span data-stu-id="26b2c-159">To order by last name and then first name, add both fields to the query:</span></span>  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     <span data-ttu-id="26b2c-160">您也可以指定`Descending`從 Z 到 a。 的順序</span><span class="sxs-lookup"><span data-stu-id="26b2c-160">You can also specify `Descending` to order from Z to A.</span></span>  
  
3.  <span data-ttu-id="26b2c-161">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="26b2c-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="26b2c-162">請注意 [主控台] 視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="26b2c-162">Note the results in the console window.</span></span>  
  
#### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="26b2c-163">若要導入的本機識別碼</span><span class="sxs-lookup"><span data-stu-id="26b2c-163">To introduce a local identifier</span></span>  
  
1.  <span data-ttu-id="26b2c-164">在本節中導入了查詢運算式中的本機識別碼加入程式碼。</span><span class="sxs-lookup"><span data-stu-id="26b2c-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="26b2c-165">本機識別碼會保留中繼結果。</span><span class="sxs-lookup"><span data-stu-id="26b2c-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="26b2c-166">在下列範例中，`name`是保存的學生串連的識別項的名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="26b2c-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="26b2c-167">為了方便起見，可用的本機識別碼或透過儲存運算式，否則會計算數次的結果，它可以提升效能。</span><span class="sxs-lookup"><span data-stu-id="26b2c-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  <span data-ttu-id="26b2c-168">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="26b2c-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="26b2c-169">請注意 [主控台] 視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="26b2c-169">Note the results in the console window.</span></span>  
  
#### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="26b2c-170">Project Select 子句中的一個欄位</span><span class="sxs-lookup"><span data-stu-id="26b2c-170">To project one field in the Select clause</span></span>  
  
1.  <span data-ttu-id="26b2c-171">加入查詢和`For Each`此區段來建立可產生的一連串的項目不同於來源中的項目查詢中的迴圈。</span><span class="sxs-lookup"><span data-stu-id="26b2c-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="26b2c-172">在下列範例中，來源是一堆`Student`物件，而每個物件的成員只有一個會傳回： 姓氏是牙哥加西亞島的學生的名字。</span><span class="sxs-lookup"><span data-stu-id="26b2c-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="26b2c-173">因為`currentStudent.First`是一個字串，所傳回的序列的資料型別`studentQuery3`是`IEnumerable(Of String)`，一系列的字串。</span><span class="sxs-lookup"><span data-stu-id="26b2c-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="26b2c-174">如先前範例所示的資料指派輸入`studentQuery3`留給編譯器使用區域型別推斷來判斷。</span><span class="sxs-lookup"><span data-stu-id="26b2c-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  <span data-ttu-id="26b2c-175">將滑鼠指標停留`studentQuery3`在您的程式碼，以確認指派的類型為`IEnumerable(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="26b2c-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>  
  
3.  <span data-ttu-id="26b2c-176">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="26b2c-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="26b2c-177">請注意 [主控台] 視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="26b2c-177">Note the results in the console window.</span></span>  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="26b2c-178">若要建立 Select 子句中的匿名型別</span><span class="sxs-lookup"><span data-stu-id="26b2c-178">To create an anonymous type in the Select clause</span></span>  
  
1.  <span data-ttu-id="26b2c-179">加入此區段可查看如何匿名型別中的程式碼會在查詢中使用。</span><span class="sxs-lookup"><span data-stu-id="26b2c-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="26b2c-180">您它們在查詢中使用當您想要傳回的數個欄位從資料來源，而不是完整記錄 (`currentStudent`先前範例中的記錄) 或單一欄位 (`First`上一節)。</span><span class="sxs-lookup"><span data-stu-id="26b2c-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="26b2c-181">而不是定義新的具名型別，其中包含您想要包含在結果中的欄位，您可以指定中的欄位`Select`子句和編譯器建立匿名型別為其屬性的這些欄位。</span><span class="sxs-lookup"><span data-stu-id="26b2c-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="26b2c-182">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="26b2c-182">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="26b2c-183">下列範例會建立查詢，傳回的名稱和陣序規範的前輩學術排名是介於 1 到 10，學術排名的順序。</span><span class="sxs-lookup"><span data-stu-id="26b2c-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="26b2c-184">在此範例中的型別`studentQuery4`必須推斷，因為`Select`子句會傳回匿名類型的執行個體和匿名型別已經沒有可用的名稱。</span><span class="sxs-lookup"><span data-stu-id="26b2c-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  <span data-ttu-id="26b2c-185">建置並按下 CTRL + F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="26b2c-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="26b2c-186">請注意 [主控台] 視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="26b2c-186">Note the results in the console window.</span></span>  
  
## <a name="additional-examples"></a><span data-ttu-id="26b2c-187">其他範例</span><span class="sxs-lookup"><span data-stu-id="26b2c-187">Additional Examples</span></span>  
 <span data-ttu-id="26b2c-188">既然您了解基本概念，以下是清單中的其他範例，以說明彈性和能力[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]查詢。</span><span class="sxs-lookup"><span data-stu-id="26b2c-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries.</span></span> <span data-ttu-id="26b2c-189">每個範例會加上其用途的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="26b2c-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="26b2c-190">將滑鼠指標停留在查詢結果變數的每個查詢都看到 推斷的型別。</span><span class="sxs-lookup"><span data-stu-id="26b2c-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="26b2c-191">使用`For Each`迴圈來產生結果。</span><span class="sxs-lookup"><span data-stu-id="26b2c-191">Use a `For Each` loop to produce the results.</span></span>  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a><span data-ttu-id="26b2c-192">其他資訊</span><span class="sxs-lookup"><span data-stu-id="26b2c-192">Additional Information</span></span>  
 <span data-ttu-id="26b2c-193">您已熟悉使用查詢的基本概念之後，您就可以讀取的特定類型的文件和範例[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]您感興趣的提供者：</span><span class="sxs-lookup"><span data-stu-id="26b2c-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provider that you are interested in:</span></span>  
  
 [<span data-ttu-id="26b2c-194">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="26b2c-194">LINQ to Objects</span></span>](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [<span data-ttu-id="26b2c-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="26b2c-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="26b2c-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="26b2c-196">LINQ to XML</span></span>](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [<span data-ttu-id="26b2c-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="26b2c-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a><span data-ttu-id="26b2c-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26b2c-198">See Also</span></span>  
 [<span data-ttu-id="26b2c-199">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26b2c-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="26b2c-200">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="26b2c-200">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="26b2c-201">區域類型推斷</span><span class="sxs-lookup"><span data-stu-id="26b2c-201">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="26b2c-202">物件初始設定式：具名和匿名類型</span><span class="sxs-lookup"><span data-stu-id="26b2c-202">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="26b2c-203">匿名類型</span><span class="sxs-lookup"><span data-stu-id="26b2c-203">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="26b2c-204">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="26b2c-204">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="26b2c-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="26b2c-205">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="26b2c-206">查詢</span><span class="sxs-lookup"><span data-stu-id="26b2c-206">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
