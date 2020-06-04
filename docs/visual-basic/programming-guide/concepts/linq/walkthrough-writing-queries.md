---
title: 撰寫查詢
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 25905d7ac3ca4bb66a22ad1df421b400eaa6b08f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413267"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a><span data-ttu-id="da85f-102">逐步解說：在 Visual Basic 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="da85f-102">Walkthrough: Writing Queries in Visual Basic</span></span>

<span data-ttu-id="da85f-103">本逐步解說會示範如何使用 Visual Basic 語言功能來撰寫語言整合式查詢（LINQ）查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="da85f-103">This walkthrough demonstrates how you can use Visual Basic language features to write Language-Integrated Query (LINQ) query expressions.</span></span> <span data-ttu-id="da85f-104">本逐步解說示範如何在學生物件清單上建立查詢、如何執行查詢，以及如何加以修改。</span><span class="sxs-lookup"><span data-stu-id="da85f-104">The walkthrough demonstrates how to create queries on a list of Student objects, how to run the queries, and how to modify them.</span></span> <span data-ttu-id="da85f-105">這些查詢會併入數個功能，包括物件初始化運算式、區欄位型別推斷和匿名型別。</span><span class="sxs-lookup"><span data-stu-id="da85f-105">The queries incorporate several features including object initializers, local type inference, and anonymous types.</span></span>

<span data-ttu-id="da85f-106">完成本逐步解說之後，您就可以開始移至您感興趣之特定 LINQ 提供者的範例和檔。</span><span class="sxs-lookup"><span data-stu-id="da85f-106">After completing this walkthrough, you will be ready to move on to the samples and documentation for the specific LINQ provider you are interested in.</span></span> <span data-ttu-id="da85f-107">LINQ 提供者包括 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 、LINQ to DataSet 和 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="da85f-107">LINQ providers include [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet, and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>

## <a name="create-a-project"></a><span data-ttu-id="da85f-108">建立專案</span><span class="sxs-lookup"><span data-stu-id="da85f-108">Create a Project</span></span>

### <a name="to-create-a-console-application-project"></a><span data-ttu-id="da85f-109">建立主控台應用程式專案</span><span class="sxs-lookup"><span data-stu-id="da85f-109">To create a console application project</span></span>

1. <span data-ttu-id="da85f-110">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="da85f-110">Start Visual Studio.</span></span>

2. <span data-ttu-id="da85f-111">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="da85f-111">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="da85f-112">在 [**已安裝的範本**] 清單中，按一下 [ **Visual Basic**]。</span><span class="sxs-lookup"><span data-stu-id="da85f-112">In the **Installed Templates** list, click **Visual Basic**.</span></span>

4. <span data-ttu-id="da85f-113">在專案類型清單中，按一下 [**主控台應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="da85f-113">In the list of project types, click **Console Application**.</span></span> <span data-ttu-id="da85f-114">在 [**名稱**] 方塊中，輸入專案的名稱，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="da85f-114">In the **Name** box, type a name for the project, and then click **OK**.</span></span>

    <span data-ttu-id="da85f-115">隨即建立專案。</span><span class="sxs-lookup"><span data-stu-id="da85f-115">A project is created.</span></span> <span data-ttu-id="da85f-116">根據預設，它包含 System.web 的參考。</span><span class="sxs-lookup"><span data-stu-id="da85f-116">By default, it contains a reference to System.Core.dll.</span></span> <span data-ttu-id="da85f-117">此外，[參考] 頁面上的 [匯**入的命名空間**] 清單 [[專案設計工具] （Visual Basic）](/visualstudio/ide/reference/references-page-project-designer-visual-basic)包含 <xref:System.Linq?displayProperty=nameWithType> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="da85f-117">Also, the **Imported namespaces** list on the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) includes the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>

5. <span data-ttu-id="da85f-118">在 [[編譯] 頁面上，[專案設計工具] （Visual Basic）](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)，確定 [**選項推斷**] 已設定為 [**開啟**]。</span><span class="sxs-lookup"><span data-stu-id="da85f-118">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>

## <a name="add-an-in-memory-data-source"></a><span data-ttu-id="da85f-119">新增記憶體中的資料來源</span><span class="sxs-lookup"><span data-stu-id="da85f-119">Add an In-Memory Data Source</span></span>

<span data-ttu-id="da85f-120">本逐步解說中查詢的資料來源是物件的清單 `Student` 。</span><span class="sxs-lookup"><span data-stu-id="da85f-120">The data source for the queries in this walkthrough is a list of `Student` objects.</span></span> <span data-ttu-id="da85f-121">每個 `Student` 物件都包含名字、姓氏、類別年份，以及學生主體中的學術排名。</span><span class="sxs-lookup"><span data-stu-id="da85f-121">Each `Student` object contains a first name, a last name, a class year, and an academic rank in the student body.</span></span>

### <a name="to-add-the-data-source"></a><span data-ttu-id="da85f-122">若要新增資料來源</span><span class="sxs-lookup"><span data-stu-id="da85f-122">To add the data source</span></span>

- <span data-ttu-id="da85f-123">定義 `Student` 類別，並建立類別的實例清單。</span><span class="sxs-lookup"><span data-stu-id="da85f-123">Define a `Student` class, and create a list of instances of the class.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="da85f-124">`Student`[如何：建立專案清單](how-to-create-a-list-of-items.md)中提供定義類別及建立逐步解說範例所使用之清單所需的程式碼。</span><span class="sxs-lookup"><span data-stu-id="da85f-124">The code needed to define the `Student` class and create the list used in the walkthrough examples is provided in [How to: Create a List of Items](how-to-create-a-list-of-items.md).</span></span> <span data-ttu-id="da85f-125">您可以從該處複製該檔案，並將它貼到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="da85f-125">You can copy it from there and paste it into your project.</span></span> <span data-ttu-id="da85f-126">新的程式碼會取代您在建立專案時所出現的程式碼。</span><span class="sxs-lookup"><span data-stu-id="da85f-126">The new code replaces the code that appeared when you created the project.</span></span>

### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="da85f-127">若要將新的學生新增至學生清單</span><span class="sxs-lookup"><span data-stu-id="da85f-127">To add a new student to the students list</span></span>

- <span data-ttu-id="da85f-128">請遵循方法中的模式 `getStudents` ，將類別的另一個實例新增 `Student` 至清單。</span><span class="sxs-lookup"><span data-stu-id="da85f-128">Follow the pattern in the `getStudents` method to add another instance of the `Student` class to the list.</span></span> <span data-ttu-id="da85f-129">新增 student 會向您介紹物件初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="da85f-129">Adding the student will introduce you to object initializers.</span></span> <span data-ttu-id="da85f-130">如需詳細資訊，請參閱[物件初始化運算式：名稱和匿名型別](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="da85f-130">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>

## <a name="create-a-query"></a><span data-ttu-id="da85f-131">建立查詢</span><span class="sxs-lookup"><span data-stu-id="da85f-131">Create a Query</span></span>

<span data-ttu-id="da85f-132">執行時，本節中新增的查詢會產生一份清單，其中的學術排名會將其放在前十名。</span><span class="sxs-lookup"><span data-stu-id="da85f-132">When executed, the query added in this section produces a list of the students whose academic rank puts them in the top ten.</span></span> <span data-ttu-id="da85f-133">因為查詢 `Student` 每次都會選取完整的物件，所以查詢結果的類型為 `IEnumerable(Of Student)` 。</span><span class="sxs-lookup"><span data-stu-id="da85f-133">Because the query selects the complete `Student` object each time, the type of the query result is `IEnumerable(Of Student)`.</span></span> <span data-ttu-id="da85f-134">不過，查詢定義中通常不會指定查詢的類型。</span><span class="sxs-lookup"><span data-stu-id="da85f-134">However, the type of the query typically is not specified in query definitions.</span></span> <span data-ttu-id="da85f-135">相反地，編譯器會使用區域型別推斷來判斷型別。</span><span class="sxs-lookup"><span data-stu-id="da85f-135">Instead, the compiler uses local type inference to determine the type.</span></span> <span data-ttu-id="da85f-136">如需詳細資訊，請參閱[區欄位型別推斷](../../language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="da85f-136">For more information, see [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span> <span data-ttu-id="da85f-137">查詢的範圍變數 `currentStudent` 可作為來源中每個實例的參考，並 `Student` `students` 提供中每個物件屬性的存取權 `students` 。</span><span class="sxs-lookup"><span data-stu-id="da85f-137">The query's range variable, `currentStudent`, serves as a reference to each `Student` instance in the source, `students`, providing access to the properties of each object in `students`.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="da85f-138">建立簡單查詢</span><span class="sxs-lookup"><span data-stu-id="da85f-138">To create a simple query</span></span>

1. <span data-ttu-id="da85f-139">找出專案的方法中標示為的位置，如下所示 `Main` ：</span><span class="sxs-lookup"><span data-stu-id="da85f-139">Find the place in the `Main` method of the project that is marked as follows:</span></span>

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    <span data-ttu-id="da85f-140">複製下列程式碼，並將它貼到中。</span><span class="sxs-lookup"><span data-stu-id="da85f-140">Copy the following code and paste it in.</span></span>

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. <span data-ttu-id="da85f-141">將滑鼠指標停留 `studentQuery` 在您的程式碼中，以確認編譯器指派的類型為 `IEnumerable(Of Student)` 。</span><span class="sxs-lookup"><span data-stu-id="da85f-141">Rest the mouse pointer over `studentQuery` in your code to verify that the compiler-assigned type is `IEnumerable(Of Student)`.</span></span>

## <a name="run-the-query"></a><span data-ttu-id="da85f-142">執行查詢</span><span class="sxs-lookup"><span data-stu-id="da85f-142">Run the Query</span></span>

<span data-ttu-id="da85f-143">變數 `studentQuery` 包含查詢的定義，而不是執行查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-143">The variable `studentQuery` contains the definition of the query, not the results of running the query.</span></span> <span data-ttu-id="da85f-144">執行查詢的一般機制是 `For Each` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="da85f-144">A typical mechanism for running a query is a `For Each` loop.</span></span> <span data-ttu-id="da85f-145">傳回序列中的每個元素都是透過迴圈反覆運算變數來存取。</span><span class="sxs-lookup"><span data-stu-id="da85f-145">Each element in the returned sequence is accessed through the loop iteration variable.</span></span> <span data-ttu-id="da85f-146">如需查詢執行的詳細資訊，請參閱[撰寫您的第一個 LINQ 查詢](writing-your-first-linq-query.md)。</span><span class="sxs-lookup"><span data-stu-id="da85f-146">For more information about query execution, see [Writing Your First LINQ Query](writing-your-first-linq-query.md).</span></span>

### <a name="to-run-the-query"></a><span data-ttu-id="da85f-147">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="da85f-147">To run the query</span></span>

1. <span data-ttu-id="da85f-148">將下列迴圈新增至 `For Each` 專案中的查詢下方。</span><span class="sxs-lookup"><span data-stu-id="da85f-148">Add the following `For Each` loop below the query in your project.</span></span>

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. <span data-ttu-id="da85f-149">將滑鼠指標停留在迴圈控制變數上 `studentRecord` ，以查看其資料類型。</span><span class="sxs-lookup"><span data-stu-id="da85f-149">Rest the mouse pointer over the loop control variable `studentRecord` to see its data type.</span></span> <span data-ttu-id="da85f-150">的類型 `studentRecord` 會推斷為 `Student` ，因為會傳回 `studentQuery` 實例的集合 `Student` 。</span><span class="sxs-lookup"><span data-stu-id="da85f-150">The type of `studentRecord` is inferred to be `Student`, because `studentQuery` returns a collection of `Student` instances.</span></span>

3. <span data-ttu-id="da85f-151">按 CTRL + F5，建立並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="da85f-151">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="da85f-152">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-152">Note the results in the console window.</span></span>

## <a name="modify-the-query"></a><span data-ttu-id="da85f-153">修改查詢</span><span class="sxs-lookup"><span data-stu-id="da85f-153">Modify the Query</span></span>

<span data-ttu-id="da85f-154">如果查詢結果是依指定的順序，則會更容易掃描。</span><span class="sxs-lookup"><span data-stu-id="da85f-154">It is easier to scan query results if they are in a specified order.</span></span> <span data-ttu-id="da85f-155">您可以根據任何可用的欄位來排序傳回的序列。</span><span class="sxs-lookup"><span data-stu-id="da85f-155">You can sort the returned sequence based on any available field.</span></span>

### <a name="to-order-the-results"></a><span data-ttu-id="da85f-156">若要排序結果</span><span class="sxs-lookup"><span data-stu-id="da85f-156">To order the results</span></span>

1. <span data-ttu-id="da85f-157">在 `Order By` `Where` 查詢的語句與語句之間加入下列子句 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="da85f-157">Add the following `Order By` clause between the `Where` statement and the `Select` statement of the query.</span></span> <span data-ttu-id="da85f-158">`Order By`子句會根據每個學生的姓氏，從 A 到 Z 依字母順序排序結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-158">The `Order By` clause will order the results alphabetically from A to Z, according to the last name of each student.</span></span>

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. <span data-ttu-id="da85f-159">若要依姓氏和名字進行排序，請將這兩個欄位加入至查詢：</span><span class="sxs-lookup"><span data-stu-id="da85f-159">To order by last name and then first name, add both fields to the query:</span></span>

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    <span data-ttu-id="da85f-160">您也可以指定 `Descending` 從 Z 到 A 的順序。</span><span class="sxs-lookup"><span data-stu-id="da85f-160">You can also specify `Descending` to order from Z to A.</span></span>

3. <span data-ttu-id="da85f-161">按 CTRL + F5，建立並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="da85f-161">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="da85f-162">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-162">Note the results in the console window.</span></span>

### <a name="to-introduce-a-local-identifier"></a><span data-ttu-id="da85f-163">引進區域識別碼</span><span class="sxs-lookup"><span data-stu-id="da85f-163">To introduce a local identifier</span></span>

1. <span data-ttu-id="da85f-164">加入本節中的程式碼，以在查詢運算式中引進區域識別碼。</span><span class="sxs-lookup"><span data-stu-id="da85f-164">Add the code in this section to introduce a local identifier in the query expression.</span></span> <span data-ttu-id="da85f-165">本機識別碼會保存中繼結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-165">The local identifier will hold an intermediate result.</span></span> <span data-ttu-id="da85f-166">在下列範例中， `name` 是一個識別碼，它會保存學生姓氏和名字的串連。</span><span class="sxs-lookup"><span data-stu-id="da85f-166">In the following example, `name` is an identifier that holds a concatenation of the student's first and last names.</span></span> <span data-ttu-id="da85f-167">本機識別碼可以用來方便使用，也可以藉由儲存運算式的結果來提升效能，而這會計算多次。</span><span class="sxs-lookup"><span data-stu-id="da85f-167">A local identifier can be used for convenience, or it can enhance performance by storing the results of an expression that would otherwise be calculated multiple times.</span></span>

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. <span data-ttu-id="da85f-168">按 CTRL + F5，建立並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="da85f-168">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="da85f-169">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-169">Note the results in the console window.</span></span>

### <a name="to-project-one-field-in-the-select-clause"></a><span data-ttu-id="da85f-170">若要在 Select 子句中投影一個欄位</span><span class="sxs-lookup"><span data-stu-id="da85f-170">To project one field in the Select clause</span></span>

1. <span data-ttu-id="da85f-171">`For Each`從這個區段加入查詢和迴圈，以建立查詢來產生一個序列，其專案與來源中的元素不同。</span><span class="sxs-lookup"><span data-stu-id="da85f-171">Add the query and `For Each` loop from this section to create a query that produces a sequence whose elements differ from the elements in the source.</span></span> <span data-ttu-id="da85f-172">在下列範例中，來源是物件的集合 `Student` ，但只會傳回每個物件的其中一個成員：姓氏為 Garcia 的學生名字。</span><span class="sxs-lookup"><span data-stu-id="da85f-172">In the following example, the source is a collection of `Student` objects, but only one member of each object is returned: the first name of students whose last name is Garcia.</span></span> <span data-ttu-id="da85f-173">因為 `currentStudent.First` 是字串，所傳回之序列的資料類型 `studentQuery3` 是，這是 `IEnumerable(Of String)` 一系列的字串。</span><span class="sxs-lookup"><span data-stu-id="da85f-173">Because `currentStudent.First` is a string, the data type of the sequence returned by `studentQuery3` is `IEnumerable(Of String)`, a sequence of strings.</span></span> <span data-ttu-id="da85f-174">如先前的範例所示，的資料類型指派 `studentQuery3` 會留給編譯器使用區欄位型別推斷來判斷。</span><span class="sxs-lookup"><span data-stu-id="da85f-174">As in earlier examples, the assignment of a data type for `studentQuery3` is left for the compiler to determine by using local type inference.</span></span>

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. <span data-ttu-id="da85f-175">將滑鼠指標停留 `studentQuery3` 在您的程式碼中，以確認指派的類型為 `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="da85f-175">Rest the mouse pointer over `studentQuery3` in your code to verify that the assigned type is `IEnumerable(Of String)`.</span></span>

3. <span data-ttu-id="da85f-176">按 CTRL + F5，建立並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="da85f-176">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="da85f-177">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-177">Note the results in the console window.</span></span>

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a><span data-ttu-id="da85f-178">若要在 Select 子句中建立匿名型別</span><span class="sxs-lookup"><span data-stu-id="da85f-178">To create an anonymous type in the Select clause</span></span>

1. <span data-ttu-id="da85f-179">加入本節中的程式碼，以查看如何在查詢中使用匿名型別。</span><span class="sxs-lookup"><span data-stu-id="da85f-179">Add the code from this section to see how anonymous types are used in queries.</span></span> <span data-ttu-id="da85f-180">當您想要從資料來源傳回數個欄位，而不是完成記錄（ `currentStudent` 先前範例中的記錄）或單一欄位（在上 `First` 一節中）時，您可以在查詢中使用它們。</span><span class="sxs-lookup"><span data-stu-id="da85f-180">You use them in queries when you want to return several fields from the data source rather than complete records (`currentStudent` records in previous examples) or single fields (`First` in the preceding section).</span></span> <span data-ttu-id="da85f-181">您可以指定子句中的欄位，而 `Select` 編譯器會建立具有這些欄位做為其屬性的匿名型別，而不是定義新的命名型別，其中包含您想要包含在結果中的欄位。</span><span class="sxs-lookup"><span data-stu-id="da85f-181">Instead of defining a new named type that contains the fields you want to include in the result, you specify the fields in the `Select` clause and the compiler creates an anonymous type with those fields as its properties.</span></span> <span data-ttu-id="da85f-182">如需詳細資訊，請參閱[匿名](../../language-features/objects-and-classes/anonymous-types.md)型別。</span><span class="sxs-lookup"><span data-stu-id="da85f-182">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>

    <span data-ttu-id="da85f-183">下列範例會建立一個查詢，以根據學術排名的順序，傳回其學術排名介於1到10之間的老年人名稱和順位。</span><span class="sxs-lookup"><span data-stu-id="da85f-183">The following example creates a query that returns the name and rank of seniors whose academic rank is between 1 and 10, in order of academic rank.</span></span> <span data-ttu-id="da85f-184">在此範例中，必須推斷的型別 `studentQuery4` ，因為 `Select` 子句會傳回匿名型別的實例，而且匿名型別沒有任何可用的名稱。</span><span class="sxs-lookup"><span data-stu-id="da85f-184">In this example, the type of `studentQuery4` must be inferred because the `Select` clause returns an instance of an anonymous type, and an anonymous type has no usable name.</span></span>

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. <span data-ttu-id="da85f-185">按 CTRL + F5，建立並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="da85f-185">Build and run the application by pressing CTRL+F5.</span></span> <span data-ttu-id="da85f-186">請注意主控台視窗中的結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-186">Note the results in the console window.</span></span>

## <a name="additional-examples"></a><span data-ttu-id="da85f-187">其他範例</span><span class="sxs-lookup"><span data-stu-id="da85f-187">Additional Examples</span></span>

<span data-ttu-id="da85f-188">既然您已瞭解基本概念，以下是說明 LINQ 查詢彈性和能力的其他範例清單。</span><span class="sxs-lookup"><span data-stu-id="da85f-188">Now that you understand the basics, the following is a list of additional examples to illustrate the flexibility and power of LINQ queries.</span></span> <span data-ttu-id="da85f-189">每個範例的前面都會加上其作用的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="da85f-189">Each example is preceded by a brief description of what it does.</span></span> <span data-ttu-id="da85f-190">將滑鼠指標停留在每個查詢的查詢結果變數上，以查看推斷的類型。</span><span class="sxs-lookup"><span data-stu-id="da85f-190">Rest the mouse pointer over the query result variable for each query to see the inferred type.</span></span> <span data-ttu-id="da85f-191">使用 `For Each` 迴圈來產生結果。</span><span class="sxs-lookup"><span data-stu-id="da85f-191">Use a `For Each` loop to produce the results.</span></span>

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a><span data-ttu-id="da85f-192">其他資訊</span><span class="sxs-lookup"><span data-stu-id="da85f-192">Additional Information</span></span>

<span data-ttu-id="da85f-193">在您熟悉使用查詢的基本概念之後，您就可以開始閱讀您感興趣之特定 LINQ 提供者類型的檔和範例：</span><span class="sxs-lookup"><span data-stu-id="da85f-193">After you are familiar with the basic concepts of working with queries, you are ready to read the documentation and samples for the specific type of LINQ provider that you are interested in:</span></span>

- [<span data-ttu-id="da85f-194">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="da85f-194">LINQ to Objects</span></span>](linq-to-objects.md)

- [<span data-ttu-id="da85f-195">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="da85f-195">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)

- [<span data-ttu-id="da85f-196">LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="da85f-196">LINQ to XML</span></span>](linq-to-xml.md)

- [<span data-ttu-id="da85f-197">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="da85f-197">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a><span data-ttu-id="da85f-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da85f-198">See also</span></span>

- [<span data-ttu-id="da85f-199">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da85f-199">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="da85f-200">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="da85f-200">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="da85f-201">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="da85f-201">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="da85f-202">物件初始設定式：具名和匿名型別</span><span class="sxs-lookup"><span data-stu-id="da85f-202">Object Initializers: Named and Anonymous Types</span></span>](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="da85f-203">匿名類型</span><span class="sxs-lookup"><span data-stu-id="da85f-203">Anonymous Types</span></span>](../../language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="da85f-204">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="da85f-204">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="da85f-205">LINQ</span><span class="sxs-lookup"><span data-stu-id="da85f-205">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="da85f-206">查詢</span><span class="sxs-lookup"><span data-stu-id="da85f-206">Queries</span></span>](../../../language-reference/queries/index.md)
