---
title: "逐步解說：在 C# 中撰寫查詢 (LINQ)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
helpviewer_keywords:
- LINQ [C#], walkthroughs
- LINQ [C#], writing queries
- queries [LINQ in C#], writing
- writing LINQ queries
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8db1b59bd8de523ae74ca198302f814c2d43f25a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-writing-queries-in-c-linq"></a><span data-ttu-id="795b3-102">逐步解說：在 C# 中撰寫查詢 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="795b3-102">Walkthrough: Writing Queries in C# (LINQ)</span></span>
<span data-ttu-id="795b3-103">本逐步解說示範用以撰寫 LINQ 查詢運算式的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="795b3-103">This walkthrough demonstrates the C# language features that are used to write LINQ query expressions.</span></span>  
  
## <a name="create-a-c-project"></a><span data-ttu-id="795b3-104">建立 C# 專案</span><span class="sxs-lookup"><span data-stu-id="795b3-104">Create a C# Project</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="795b3-105">下列指示適用於 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="795b3-105">The following instructions are for Visual Studio.</span></span> <span data-ttu-id="795b3-106">如果您使用不同的開發環境，可搭配 System.Core.dll 的參考和 <xref:System.Linq?displayProperty=nameWithType> 命名空間的 `using` 指示詞來建立主控台專案。</span><span class="sxs-lookup"><span data-stu-id="795b3-106">If you are using a different development environment, create a console project with a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
#### <a name="to-create-a-project-in-visual-studio"></a><span data-ttu-id="795b3-107">若要在 Visual Studio 中建立專案</span><span class="sxs-lookup"><span data-stu-id="795b3-107">To create a project in Visual Studio</span></span>  
  
1.  <span data-ttu-id="795b3-108">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="795b3-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="795b3-109">在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。</span><span class="sxs-lookup"><span data-stu-id="795b3-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="795b3-110">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="795b3-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="795b3-111">依序展開 [已安裝]、[範本] 和 [Visual C#]，然後選擇 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="795b3-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="795b3-112">在 [名稱] 文字方塊中，輸入不同的名稱或接受預設名稱，然後按一下 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="795b3-112">In the **Name** text box, enter a different name or accept the default name, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="795b3-113">新的專案隨即會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="795b3-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="795b3-114">您會發現專案具有 System.Core.dll 的參考和 <xref:System.Linq?displayProperty=nameWithType> 命名空間的 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="795b3-114">Notice that your project has a reference to System.Core.dll and a `using` directive for the <xref:System.Linq?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="create-an-in-memory-data-source"></a><span data-ttu-id="795b3-115">建立記憶體內部資料來源</span><span class="sxs-lookup"><span data-stu-id="795b3-115">Create an in-Memory Data Source</span></span>  
 <span data-ttu-id="795b3-116">查詢的資料來源是 `Student` 物件的簡單清單。</span><span class="sxs-lookup"><span data-stu-id="795b3-116">The data source for the queries is a simple list of `Student` objects.</span></span> <span data-ttu-id="795b3-117">每個 `Student` 記錄都有名字、姓氏和整數的陣列，表示其在班級上的測驗分數。</span><span class="sxs-lookup"><span data-stu-id="795b3-117">Each `Student` record has a first name, last name, and an array of integers that represents their test scores in the class.</span></span> <span data-ttu-id="795b3-118">將此程式碼複製到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="795b3-118">Copy this code into your project.</span></span> <span data-ttu-id="795b3-119">並注意下列特性：</span><span class="sxs-lookup"><span data-stu-id="795b3-119">Note the following characteristics:</span></span>  
  
-   <span data-ttu-id="795b3-120">`Student` 類別是由自動實作的屬性所組成。</span><span class="sxs-lookup"><span data-stu-id="795b3-120">The `Student` class consists of auto-implemented properties.</span></span>  
  
-   <span data-ttu-id="795b3-121">使用物件初始設定式，初始化清單中的每一位學生。</span><span class="sxs-lookup"><span data-stu-id="795b3-121">Each student in the list is initialized with an object initializer.</span></span>  
  
-   <span data-ttu-id="795b3-122">系統會使用集合初始設定式，來初始化清單本身。</span><span class="sxs-lookup"><span data-stu-id="795b3-122">The list itself is initialized with a collection initializer.</span></span>  
  
 <span data-ttu-id="795b3-123">系統會初始化整個資料結構，並將其具現化，而不需要明確呼叫任何建構函式，亦不需明確的成員存取。</span><span class="sxs-lookup"><span data-stu-id="795b3-123">This whole data structure will be initialized and instantiated without explicit calls to any constructor or explicit member access.</span></span> <span data-ttu-id="795b3-124">如需這些新功能的詳細資訊，請參閱[自動實作的屬性](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)以及[物件和集合初始設定式](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)。</span><span class="sxs-lookup"><span data-stu-id="795b3-124">For more information about these new features, see [Auto-Implemented Properties](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
#### <a name="to-add-the-data-source"></a><span data-ttu-id="795b3-125">若要新增資料來源</span><span class="sxs-lookup"><span data-stu-id="795b3-125">To add the data source</span></span>  
  
-   <span data-ttu-id="795b3-126">將 `Student` 類別和學生的初始化清單，新增至專案中的 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="795b3-126">Add the `Student` class and the initialized list of students to the `Program` class in your project.</span></span>  
  
     [!code-csharp[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a><span data-ttu-id="795b3-127">若要將新的學生新增至學生清單</span><span class="sxs-lookup"><span data-stu-id="795b3-127">To add a new Student to the Students list</span></span>  
  
1.  <span data-ttu-id="795b3-128">將新的 `Student` 新增至 `Students` 清單，並使用您所選擇的名稱和測驗分數。</span><span class="sxs-lookup"><span data-stu-id="795b3-128">Add a new `Student` to the `Students` list and use a name and test scores of your choice.</span></span> <span data-ttu-id="795b3-129">請嘗試輸入新的學生資訊，以便進一步了解物件初始設定式語法。</span><span class="sxs-lookup"><span data-stu-id="795b3-129">Try typing all the new student information in order to better learn the syntax for the object initializer.</span></span>  
  
## <a name="create-the-query"></a><span data-ttu-id="795b3-130">建立查詢</span><span class="sxs-lookup"><span data-stu-id="795b3-130">Create the Query</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="795b3-131">建立簡單查詢</span><span class="sxs-lookup"><span data-stu-id="795b3-131">To create a simple query</span></span>  
  
-   <span data-ttu-id="795b3-132">在應用程式的 `Main` 方法中，建立簡單的查詢，即可在執行查詢時產生第一次測驗分數超過 90 分之所有學生的清單。</span><span class="sxs-lookup"><span data-stu-id="795b3-132">In the application's `Main` method, create a simple query that, when it is executed, will produce a list of all students whose score on the first test was greater than 90.</span></span> <span data-ttu-id="795b3-133">請注意，因為已選取整個 `Student` 物件，所以查詢的類型是 `IEnumerable<Student>`。</span><span class="sxs-lookup"><span data-stu-id="795b3-133">Note that because the whole `Student` object is selected, the type of the query is `IEnumerable<Student>`.</span></span> <span data-ttu-id="795b3-134">雖然程式碼也可以藉由 [var](../../../../csharp/language-reference/keywords/var.md) 關鍵字來使用隱含類型，但需使用明確類型來清楚說明結果 </span><span class="sxs-lookup"><span data-stu-id="795b3-134">Although the code could also use implicit typing by using the [var](../../../../csharp/language-reference/keywords/var.md) keyword, explicit typing is used to clearly illustrate results.</span></span> <span data-ttu-id="795b3-135">(如需 `var` 的詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md))。</span><span class="sxs-lookup"><span data-stu-id="795b3-135">(For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).)</span></span>  
  
     <span data-ttu-id="795b3-136">另請注意，查詢的範圍變數 `student` 可作為來源中每個 `Student` 的參考，並提供每個物件的成員存取。</span><span class="sxs-lookup"><span data-stu-id="795b3-136">Note also that the query's range variable, `student`, serves as a reference to each `Student` in the source, providing member access for each object.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## <a name="execute-the-query"></a><span data-ttu-id="795b3-137">執行查詢</span><span class="sxs-lookup"><span data-stu-id="795b3-137">Execute the Query</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="795b3-138">查詢查詢</span><span class="sxs-lookup"><span data-stu-id="795b3-138">To execute the query</span></span>  
  
1.  <span data-ttu-id="795b3-139">現在，請撰寫 `foreach` 迴圈以執行查詢。</span><span class="sxs-lookup"><span data-stu-id="795b3-139">Now write the `foreach` loop that will cause the query to execute.</span></span> <span data-ttu-id="795b3-140">請注意下列程式碼的相關重點：</span><span class="sxs-lookup"><span data-stu-id="795b3-140">Note the following about the code:</span></span>  
  
    -   <span data-ttu-id="795b3-141">您可透過 `foreach` 迴圈中的反覆運算變數，存取傳回序列中的每個項目。</span><span class="sxs-lookup"><span data-stu-id="795b3-141">Each element in the returned sequence is accessed through the iteration variable in the `foreach` loop.</span></span>  
  
    -   <span data-ttu-id="795b3-142">此變數的類型是 `Student`，其與 `IEnumerable<Student>` 查詢變數類型相容。</span><span class="sxs-lookup"><span data-stu-id="795b3-142">The type of this variable is `Student`, and the type of the query variable is compatible, `IEnumerable<Student>`.</span></span>  
  
2.  <span data-ttu-id="795b3-143">加入此程式碼之後，建置並執行應用程式，即可在 [主控台] 視窗中查看結果。</span><span class="sxs-lookup"><span data-stu-id="795b3-143">After you have added this code, build and run the application to see the results in the **Console** window.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### <a name="to-add-another-filter-condition"></a><span data-ttu-id="795b3-144">若要新增其他篩選條件</span><span class="sxs-lookup"><span data-stu-id="795b3-144">To add another filter condition</span></span>  
  
1.  <span data-ttu-id="795b3-145">您可以在 `where` 中結合多個布林條件，以進一步精簡查詢子句。</span><span class="sxs-lookup"><span data-stu-id="795b3-145">You can combine multiple Boolean conditions in the `where` clause in order to further refine a query.</span></span> <span data-ttu-id="795b3-146">下列程式碼會新增條件，讓查詢傳回第一次分數高於 90 分，但最後一次的分數低於 80 分的學生。</span><span class="sxs-lookup"><span data-stu-id="795b3-146">The following code adds a condition so that the query returns those students whose first score was over 90 and whose last score was less than 80.</span></span> <span data-ttu-id="795b3-147">`where` 子句應類似於下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="795b3-147">The `where` clause should resemble the following code.</span></span>  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     <span data-ttu-id="795b3-148">如需詳細資訊，請參閱 [where 子句](../../../../csharp/language-reference/keywords/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="795b3-148">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="modify-the-query"></a><span data-ttu-id="795b3-149">修改查詢</span><span class="sxs-lookup"><span data-stu-id="795b3-149">Modify the Query</span></span>  
  
#### <a name="to-order-the-results"></a><span data-ttu-id="795b3-150">若要排序結果</span><span class="sxs-lookup"><span data-stu-id="795b3-150">To order the results</span></span>  
  
1.  <span data-ttu-id="795b3-151">如果結果有依照某種順序排列，會比較容易進行掃描。</span><span class="sxs-lookup"><span data-stu-id="795b3-151">It will be easier to scan the results if they are in some kind of order.</span></span> <span data-ttu-id="795b3-152">您可以依據來源項目中任何可存取的欄位，來排序傳回的序列。</span><span class="sxs-lookup"><span data-stu-id="795b3-152">You can order the returned sequence by any accessible field in the source elements.</span></span> <span data-ttu-id="795b3-153">例如，下列 `orderby` 子句會根據每個學生的姓氏，依字母 A 到 Z 順序，來排序結果。</span><span class="sxs-lookup"><span data-stu-id="795b3-153">For example, the following `orderby` clause orders the results in alphabetical order from A to Z according to the last name of each student.</span></span> <span data-ttu-id="795b3-154">請在 `where` 陳述式正後方、`select` 陳述式正前方，將下列 `orderby` 子句新增至查詢：</span><span class="sxs-lookup"><span data-stu-id="795b3-154">Add the following `orderby` clause to your query, right after the `where` statement and before the `select` statement:</span></span>  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  <span data-ttu-id="795b3-155">現在，變更 `orderby` 子句，以根據第一個測驗，依最低分到最高分的相反順序來排序結果。</span><span class="sxs-lookup"><span data-stu-id="795b3-155">Now change the `orderby` clause so that it orders the results in reverse order according to the score on the first test, from the highest score to the lowest score.</span></span>  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  <span data-ttu-id="795b3-156">變更 `WriteLine` 格式字串，以便查看分數：</span><span class="sxs-lookup"><span data-stu-id="795b3-156">Change the `WriteLine` format string so that you can see the scores:</span></span>  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     <span data-ttu-id="795b3-157">如需詳細資訊，請參閱 [orderby 子句](../../../../csharp/language-reference/keywords/orderby-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="795b3-157">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
#### <a name="to-group-the-results"></a><span data-ttu-id="795b3-158">若要將結果分組</span><span class="sxs-lookup"><span data-stu-id="795b3-158">To group the results</span></span>  
  
1.  <span data-ttu-id="795b3-159">查詢運算式中提供分組這項強大的功能。</span><span class="sxs-lookup"><span data-stu-id="795b3-159">Grouping is a powerful capability in query expressions.</span></span> <span data-ttu-id="795b3-160">使用 group 子句進行查詢時，會產生一個群組序列，且每個群組本身會包含 `Key` 以及組成該群組之所有成員的序列。</span><span class="sxs-lookup"><span data-stu-id="795b3-160">A query with a group clause produces a sequence of groups, and each group itself contains a `Key` and a sequence that consists of all the members of that group.</span></span> <span data-ttu-id="795b3-161">下列新查詢會以學生姓氏的第一個字母作為索引鍵，來進行分組。</span><span class="sxs-lookup"><span data-stu-id="795b3-161">The following new query groups the students by using the first letter of their last name as the key.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  <span data-ttu-id="795b3-162">請注意，查詢類型現在已變更。</span><span class="sxs-lookup"><span data-stu-id="795b3-162">Note that the type of the query has now changed.</span></span> <span data-ttu-id="795b3-163">現在，即會產生具有 `char` 類型索引鍵的群組序列，以及 `Student` 物件的序列。</span><span class="sxs-lookup"><span data-stu-id="795b3-163">It now produces a sequence of groups that have a `char` type as a key, and a sequence of `Student` objects.</span></span> <span data-ttu-id="795b3-164">由於查詢類型已變更，因此下列程式碼也會變更 `foreach` 執行迴圈：</span><span class="sxs-lookup"><span data-stu-id="795b3-164">Because the type of the query has changed, the following code changes the `foreach` execution loop also:</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  <span data-ttu-id="795b3-165">執行應用程式，並在 [主控台] 視窗中檢視結果。</span><span class="sxs-lookup"><span data-stu-id="795b3-165">Run the application and view the results in the **Console** window.</span></span>  
  
     <span data-ttu-id="795b3-166">如需詳細資訊，請參閱 [group 子句](../../../../csharp/language-reference/keywords/group-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="795b3-166">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
#### <a name="to-make-the-variables-implicitly-typed"></a><span data-ttu-id="795b3-167">若要將變數設為隱含類型</span><span class="sxs-lookup"><span data-stu-id="795b3-167">To make the variables implicitly typed</span></span>  
  
1.  <span data-ttu-id="795b3-168">在明確撰寫 `IGroupings` 的 `IEnumerables` 程式碼時，可能很快就會感到枯燥乏味。</span><span class="sxs-lookup"><span data-stu-id="795b3-168">Explicitly coding `IEnumerables` of `IGroupings` can quickly become tedious.</span></span> <span data-ttu-id="795b3-169">為了方便起見，您可以使用 `var` 來撰寫相同的查詢和 `foreach` 迴圈。</span><span class="sxs-lookup"><span data-stu-id="795b3-169">You can write the same query and `foreach` loop much more conveniently by using `var`.</span></span> <span data-ttu-id="795b3-170">`var` 關鍵字不會變更物件的類型，而只會指示編譯器推斷類型。</span><span class="sxs-lookup"><span data-stu-id="795b3-170">The `var` keyword does not change the types of your objects; it just instructs the compiler to infer the types.</span></span> <span data-ttu-id="795b3-171">將 `studentQuery` 類型和反覆運算變數 `group` 變更為 `var`，然後重新執行查詢。</span><span class="sxs-lookup"><span data-stu-id="795b3-171">Change the type of `studentQuery` and the iteration variable `group` to `var` and rerun the query.</span></span> <span data-ttu-id="795b3-172">請注意，在內部 `foreach` 迴圈中，反覆運算變數類型仍為 `Student`，查詢亦會如往常般運作。</span><span class="sxs-lookup"><span data-stu-id="795b3-172">Note that in the inner `foreach` loop, the iteration variable is still typed as `Student`, and the query works just as before.</span></span> <span data-ttu-id="795b3-173">將 `s` 反覆運算變數變更為 `var`，然後再次執行查詢。</span><span class="sxs-lookup"><span data-stu-id="795b3-173">Change the `s` iteration variable to `var` and run the query again.</span></span> <span data-ttu-id="795b3-174">您會發現結果完全相同。</span><span class="sxs-lookup"><span data-stu-id="795b3-174">You see that you get exactly the same results.</span></span>  
  
     [!code-csharp[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     <span data-ttu-id="795b3-175">如需 [var](../../../../csharp/language-reference/keywords/var.md) 的詳細資訊，請參閱[隱含類型區域變數](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="795b3-175">For more information about [var](../../../../csharp/language-reference/keywords/var.md), see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
#### <a name="to-order-the-groups-by-their-key-value"></a><span data-ttu-id="795b3-176">若要依索引鍵值排序群組</span><span class="sxs-lookup"><span data-stu-id="795b3-176">To order the groups by their key value</span></span>  
  
1.  <span data-ttu-id="795b3-177">當您執行上述查詢時，您會發現群組不是依字母順序排列。</span><span class="sxs-lookup"><span data-stu-id="795b3-177">When you run the previous query, you notice that the groups are not in alphabetical order.</span></span> <span data-ttu-id="795b3-178">若要變更這種情況，您必須在 `group` 子句之後提供 `orderby` 子句。</span><span class="sxs-lookup"><span data-stu-id="795b3-178">To change this, you must provide an `orderby` clause after the `group` clause.</span></span> <span data-ttu-id="795b3-179">不過，若要使用 `orderby` 子句，您必須先取得識別項，以作為 `group` 子句所建立的群組參考。</span><span class="sxs-lookup"><span data-stu-id="795b3-179">But to use an `orderby` clause, you first need an identifier that serves as a reference to the groups created by the `group` clause.</span></span> <span data-ttu-id="795b3-180">您可以使用 `into` 關鍵字來提供識別項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="795b3-180">You provide the identifier by using the `into` keyword, as follows:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     <span data-ttu-id="795b3-181">在您執行此查詢時，會發現群組現已依照字母順序排列。</span><span class="sxs-lookup"><span data-stu-id="795b3-181">When you run this query, you will see the groups are now sorted in alphabetical order.</span></span>  
  
#### <a name="to-introduce-an-identifier-by-using-let"></a><span data-ttu-id="795b3-182">若要使用 let 引進識別項</span><span class="sxs-lookup"><span data-stu-id="795b3-182">To introduce an identifier by using let</span></span>  
  
1.  <span data-ttu-id="795b3-183">針對查詢運算式中的任何運算式結果，您可以使用 `let` 關鍵字引進識別項。</span><span class="sxs-lookup"><span data-stu-id="795b3-183">You can use the `let` keyword to introduce an identifier for any expression result in the query expression.</span></span> <span data-ttu-id="795b3-184">如下列範例所示，此識別項非常方便，它也可以儲存運算式的結果，而不需進行多次計算，藉此提高效能。</span><span class="sxs-lookup"><span data-stu-id="795b3-184">This identifier can be a convenience, as in the following example, or it can enhance performance by storing the results of an expression so that it does not have to be calculated multiple times.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     <span data-ttu-id="795b3-185">如需詳細資訊，請參閱 [let 子句](../../../../csharp/language-reference/keywords/let-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="795b3-185">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
#### <a name="to-use-method-syntax-in-a-query-expression"></a><span data-ttu-id="795b3-186">若要在查詢運算式中使用方法語法</span><span class="sxs-lookup"><span data-stu-id="795b3-186">To use method syntax in a query expression</span></span>  
  
1.  <span data-ttu-id="795b3-187">如 [LINQ 中的查詢語法及方法語法](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)中所述，某些查詢作業只能使用方法語法來表示。</span><span class="sxs-lookup"><span data-stu-id="795b3-187">As described in [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), some query operations can only be expressed by using method syntax.</span></span> <span data-ttu-id="795b3-188">下列程式碼會針對來源序列中的每個 `Student` 計算總分，然後在該查詢結果上呼叫 `Average()` 方法以計算班級的平均分數。</span><span class="sxs-lookup"><span data-stu-id="795b3-188">The following code calculates the total score for each `Student` in the source sequence, and then calls the `Average()` method on the results of that query to calculate the average score of the class.</span></span> <span data-ttu-id="795b3-189">請注意查詢運算式前後的括弧位置。</span><span class="sxs-lookup"><span data-stu-id="795b3-189">Note the placement of parentheses around the query expression.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### <a name="to-transform-or-project-in-the-select-clause"></a><span data-ttu-id="795b3-190">若要在 select 子句中轉換或投影</span><span class="sxs-lookup"><span data-stu-id="795b3-190">To transform or project in the select clause</span></span>  
  
1.  <span data-ttu-id="795b3-191">這是一種非常普遍的查詢，產生的序列項目與來源序列中的項目不同。</span><span class="sxs-lookup"><span data-stu-id="795b3-191">It is very common for a query to produce a sequence whose elements differ from the elements in the source sequences.</span></span> <span data-ttu-id="795b3-192">刪除或註解您先前的查詢和執行迴圈，並將其取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="795b3-192">Delete or comment out your previous query and execution loop, and replace it with the following code.</span></span> <span data-ttu-id="795b3-193">請注意，查詢會傳回一個字串序列 (而不是 `Students`)，且這項事實會反映在 `foreach` 迴圈中。</span><span class="sxs-lookup"><span data-stu-id="795b3-193">Note that the query returns a sequence of strings (not `Students`), and this fact is reflected in the `foreach` loop.</span></span>  
  
     [!code-csharp[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  <span data-ttu-id="795b3-194">此逐步解說中稍早的程式碼指出，班級平均成績約 334 分。</span><span class="sxs-lookup"><span data-stu-id="795b3-194">Code earlier in this walkthrough indicated that the average class score is approximately 334.</span></span> <span data-ttu-id="795b3-195">若要產生一個總分高於班級平均分數並包含 `Student ID` 的 `Students` 序列，您可以使用 `select` 陳述式中的匿名型別：</span><span class="sxs-lookup"><span data-stu-id="795b3-195">To produce a sequence of `Students` whose total score is greater than the class average, together with their `Student ID`, you can use an anonymous type in the `select` statement:</span></span>  
  
     [!code-csharp[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## <a name="next-steps"></a><span data-ttu-id="795b3-196">後續步驟</span><span class="sxs-lookup"><span data-stu-id="795b3-196">Next Steps</span></span>  
 <span data-ttu-id="795b3-197">熟悉使用 C# 進行查詢的基本概念之後，您即可開始閱讀自己感興趣之特定類型 LINQ 提供者的相關文件和範例：</span><span class="sxs-lookup"><span data-stu-id="795b3-197">After you are familiar with the basic aspects of working with queries in C#, you are ready to read the documentation and samples for the specific type of LINQ provider you are interested in:</span></span>  
  
 [<span data-ttu-id="795b3-198">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="795b3-198">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
  
 [<span data-ttu-id="795b3-199">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="795b3-199">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
  
 [<span data-ttu-id="795b3-200">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="795b3-200">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [<span data-ttu-id="795b3-201">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="795b3-201">LINQ to Objects (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
  
## <a name="see-also"></a><span data-ttu-id="795b3-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="795b3-202">See Also</span></span>  
 [<span data-ttu-id="795b3-203">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="795b3-203">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="795b3-204">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="795b3-204">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="795b3-205">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="795b3-205">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
