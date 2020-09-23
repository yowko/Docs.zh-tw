---
title: 撰寫第一個 LINQ 查詢
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: c7d0595b991bdad6ef05b567f95ead8c7fccdbc2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077276"
---
# <a name="writing-your-first-linq-query-visual-basic"></a><span data-ttu-id="2186b-102">撰寫第一個 LINQ 查詢 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2186b-102">Writing Your First LINQ Query (Visual Basic)</span></span>

<span data-ttu-id="2186b-103">「查詢」\*\* 是指從資料來源中擷取資料的運算式。</span><span class="sxs-lookup"><span data-stu-id="2186b-103">A *query* is an expression that retrieves data from a data source.</span></span> <span data-ttu-id="2186b-104">查詢是以專用的查詢語言來表示。</span><span class="sxs-lookup"><span data-stu-id="2186b-104">Queries are expressed in a dedicated query language.</span></span> <span data-ttu-id="2186b-105">經過一段時間之後，就會針對不同類型的資料來源開發不同的語言，例如，適用于關係資料庫的 SQL 和適用于 XML 的 XQuery。</span><span class="sxs-lookup"><span data-stu-id="2186b-105">Over time, different languages have been developed for different types of data sources, for example, SQL for relational databases and XQuery for XML.</span></span> <span data-ttu-id="2186b-106">這讓應用程式開發人員必須針對每一種支援的資料來源或資料格式，學習新的查詢語言。</span><span class="sxs-lookup"><span data-stu-id="2186b-106">This makes it necessary for the application developer to learn a new query language for each type of data source or data format that is supported.</span></span>  
  
 <span data-ttu-id="2186b-107">語言整合式查詢 (LINQ) 藉由提供一致的模型來處理各種資料來源和格式的資料，藉此簡化這種情況。</span><span class="sxs-lookup"><span data-stu-id="2186b-107">Language-Integrated Query (LINQ) simplifies the situation by offering a consistent model for working with data across various kinds of data sources and formats.</span></span> <span data-ttu-id="2186b-108">在 LINQ 查詢中，您永遠都是使用物件。</span><span class="sxs-lookup"><span data-stu-id="2186b-108">In a LINQ query, you are always working with objects.</span></span> <span data-ttu-id="2186b-109">您可以使用相同的基本程式碼撰寫模式來查詢及轉換 XML 檔、SQL 資料庫、ADO.NET 資料集和實體 .NET Framework 集合，以及可使用 LINQ 提供者的任何其他來源或格式的資料。</span><span class="sxs-lookup"><span data-stu-id="2186b-109">You use the same basic coding patterns to query and transform data in XML documents, SQL databases, ADO.NET datasets and entities, .NET Framework collections, and any other source or format for which a LINQ provider is available.</span></span> <span data-ttu-id="2186b-110">本檔說明建立和使用基本 LINQ 查詢的三個階段。</span><span class="sxs-lookup"><span data-stu-id="2186b-110">This document describes the three phases of the creation and use of basic LINQ queries.</span></span>  
  
## <a name="three-stages-of-a-query-operation"></a><span data-ttu-id="2186b-111">查詢作業的三個階段</span><span class="sxs-lookup"><span data-stu-id="2186b-111">Three Stages of a Query Operation</span></span>  

 <span data-ttu-id="2186b-112">LINQ 查詢作業包含三個動作：</span><span class="sxs-lookup"><span data-stu-id="2186b-112">LINQ query operations consist of three actions:</span></span>  
  
1. <span data-ttu-id="2186b-113">取得資料來源或來源。</span><span class="sxs-lookup"><span data-stu-id="2186b-113">Obtain the data source or sources.</span></span>  
  
2. <span data-ttu-id="2186b-114">建立查詢。</span><span class="sxs-lookup"><span data-stu-id="2186b-114">Create the query.</span></span>  
  
3. <span data-ttu-id="2186b-115">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="2186b-115">Execute the query.</span></span>  
  
 <span data-ttu-id="2186b-116">在 LINQ 中，查詢的執行與查詢的建立方式不同。</span><span class="sxs-lookup"><span data-stu-id="2186b-116">In LINQ, the execution of a query is distinct from the creation of the query.</span></span> <span data-ttu-id="2186b-117">您只需建立查詢就能取出任何資料。</span><span class="sxs-lookup"><span data-stu-id="2186b-117">You do not retrieve any data just by creating a query.</span></span> <span data-ttu-id="2186b-118">本主題稍後會詳細討論這一點。</span><span class="sxs-lookup"><span data-stu-id="2186b-118">This point is discussed in more detail later in this topic.</span></span>  
  
 <span data-ttu-id="2186b-119">下列範例說明查詢作業的三個部分。</span><span class="sxs-lookup"><span data-stu-id="2186b-119">The following example illustrates the three parts of a query operation.</span></span> <span data-ttu-id="2186b-120">此範例使用整數陣列作為示範用途的方便資料來源。</span><span class="sxs-lookup"><span data-stu-id="2186b-120">The example uses an array of integers as a convenient data source for demonstration purposes.</span></span> <span data-ttu-id="2186b-121">但是，相同的概念也適用于其他資料來源。</span><span class="sxs-lookup"><span data-stu-id="2186b-121">However, the same concepts also apply to other data sources.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2186b-122">在 [ [編譯] 頁面上， (Visual Basic) 的 [專案設計 ](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)工具]，確定 [ **選項推斷** ] 設定為 [ **開啟**]。</span><span class="sxs-lookup"><span data-stu-id="2186b-122">On the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), ensure that **Option infer** is set to **On**.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 <span data-ttu-id="2186b-123">輸出：</span><span class="sxs-lookup"><span data-stu-id="2186b-123">Output:</span></span>  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a><span data-ttu-id="2186b-124">資料來源</span><span class="sxs-lookup"><span data-stu-id="2186b-124">The Data Source</span></span>  

 <span data-ttu-id="2186b-125">因為上一個範例中的資料來源是陣列，所以它會隱含地支援泛型 <xref:System.Collections.Generic.IEnumerable%601> 介面。</span><span class="sxs-lookup"><span data-stu-id="2186b-125">Because the data source in the previous example is an array, it implicitly supports the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="2186b-126">這是可讓您使用陣列作為 LINQ 查詢資料來源的事實。</span><span class="sxs-lookup"><span data-stu-id="2186b-126">It is this fact that enables you to use an array as a data source for a LINQ query.</span></span> <span data-ttu-id="2186b-127">支援 <xref:System.Collections.Generic.IEnumerable%601> 或衍生介面的類型，例如泛型 <xref:System.Linq.IQueryable%601> 稱為*可查詢的類型*。</span><span class="sxs-lookup"><span data-stu-id="2186b-127">Types that support <xref:System.Collections.Generic.IEnumerable%601> or a derived interface such as the generic <xref:System.Linq.IQueryable%601> are called *queryable types*.</span></span>  
  
 <span data-ttu-id="2186b-128">陣列是一種隱含可查詢的類型，不需要修改或特殊處理以做為 LINQ 資料來源。</span><span class="sxs-lookup"><span data-stu-id="2186b-128">As an implicitly queryable type, the array requires no modification or special treatment to serve as a LINQ data source.</span></span> <span data-ttu-id="2186b-129">這也適用于任何支援的集合類型 <xref:System.Collections.Generic.IEnumerable%601> ，包括泛型 <xref:System.Collections.Generic.List%601> 、 <xref:System.Collections.Generic.Dictionary%602> 和 .NET Framework 類別庫中的其他類別。</span><span class="sxs-lookup"><span data-stu-id="2186b-129">The same is true for any collection type that supports <xref:System.Collections.Generic.IEnumerable%601>, including the generic <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>, and other classes in the .NET Framework class library.</span></span>  
  
 <span data-ttu-id="2186b-130">如果來源資料尚未執行 <xref:System.Collections.Generic.IEnumerable%601> ，則需要 LINQ 提供者來為該資料來源執行 *標準查詢運算子* 的功能。</span><span class="sxs-lookup"><span data-stu-id="2186b-130">If the source data does not already implement <xref:System.Collections.Generic.IEnumerable%601>, a LINQ provider is needed to implement the functionality of the *standard query operators* for that data source.</span></span> <span data-ttu-id="2186b-131">例如，會 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 處理將 XML 檔載入可查詢型別的工作 <xref:System.Xml.Linq.XElement> ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2186b-131">For example, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] handles the work of loading an XML document into a queryable <xref:System.Xml.Linq.XElement> type, as shown in the following example.</span></span> <span data-ttu-id="2186b-132">如需標準查詢運算子的詳細資訊，請參閱 [標準查詢運算子總覽 (Visual Basic) ](standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="2186b-132">For more information about standard query operators, see [Standard Query Operators Overview (Visual Basic)](standard-query-operators-overview.md).</span></span>  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2186b-133">在中 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] ，您會先在設計階段建立物件關聯式對應，不論是手動或使用 Visual Studio 中 [Visual Studio 的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) 。</span><span class="sxs-lookup"><span data-stu-id="2186b-133">With [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], you first create an object-relational mapping at design time, either manually or by using the [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) in Visual Studio.</span></span> <span data-ttu-id="2186b-134">您可以針對物件撰寫查詢，而 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 則會在執行階段處理與資料庫之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="2186b-134">You write your queries against the objects, and at run-time [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] handles the communication with the database.</span></span> <span data-ttu-id="2186b-135">在下列範例中， `customers` 代表資料庫中的特定資料表，並 <xref:System.Data.Linq.Table%601> 支援 generic <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="2186b-135">In the following example, `customers` represents a specific table in the database, and <xref:System.Data.Linq.Table%601> supports generic <xref:System.Linq.IQueryable%601>.</span></span>  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 <span data-ttu-id="2186b-136">如需有關如何建立特定資料來源類型的詳細資訊，請參閱各種 LINQ 提供者的檔。</span><span class="sxs-lookup"><span data-stu-id="2186b-136">For more information about how to create specific types of data sources, see the documentation for the various LINQ providers.</span></span> <span data-ttu-id="2186b-137"> (如需這些提供者的清單，請參閱 [LINQ (語言整合式查詢) ](index.md)。 ) 基本規則很簡單： LINQ 資料來源是支援泛型介面的任何物件 <xref:System.Collections.Generic.IEnumerable%601> ，或繼承自它的介面。</span><span class="sxs-lookup"><span data-stu-id="2186b-137">(For a list of these providers, see [LINQ (Language-Integrated Query)](index.md).) The basic rule is simple: a LINQ data source is any object that supports the generic <xref:System.Collections.Generic.IEnumerable%601> interface, or an interface that inherits from it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2186b-138"><xref:System.Collections.ArrayList>支援非泛型介面的類型 <xref:System.Collections.IEnumerable> 也可以當做 LINQ 資料來源使用。</span><span class="sxs-lookup"><span data-stu-id="2186b-138">Types such as <xref:System.Collections.ArrayList> that support the non-generic <xref:System.Collections.IEnumerable> interface can also be used as LINQ data sources.</span></span> <span data-ttu-id="2186b-139">如需使用的範例 <xref:System.Collections.ArrayList> ，請參閱 how [to：使用 LINQ 查詢 ArrayList (Visual Basic) ](how-to-query-an-arraylist-with-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="2186b-139">For an example that uses an <xref:System.Collections.ArrayList>, see [How to: Query an ArrayList with LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).</span></span>  
  
## <a name="the-query"></a><span data-ttu-id="2186b-140">查詢</span><span class="sxs-lookup"><span data-stu-id="2186b-140">The Query</span></span>  

 <span data-ttu-id="2186b-141">在查詢中，您會指定要從資料來源或來源取得哪些資訊。</span><span class="sxs-lookup"><span data-stu-id="2186b-141">In the query, you specify what information you want to retrieve from the data source or sources.</span></span> <span data-ttu-id="2186b-142">您也可以選擇指定應該如何排序、分組或結構化資訊，再傳回該資訊。</span><span class="sxs-lookup"><span data-stu-id="2186b-142">You also have the option of specifying how that information should be sorted, grouped, or structured before it is returned.</span></span> <span data-ttu-id="2186b-143">為了啟用查詢建立，Visual Basic 已將新的查詢語法併入語言中。</span><span class="sxs-lookup"><span data-stu-id="2186b-143">To enable query creation, Visual Basic has incorporated new query syntax into the language.</span></span>  
  
 <span data-ttu-id="2186b-144">執行時，下列範例中的查詢會傳回整數陣列中的所有偶數（偶數） `numbers` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-144">When it is executed, the query in the following example returns all the even numbers from an integer array, `numbers`.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 <span data-ttu-id="2186b-145">查詢運算式包含三個子句： `From` 、 `Where` 和 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-145">The query expression contains three clauses: `From`, `Where`, and `Select`.</span></span> <span data-ttu-id="2186b-146">[ (Visual Basic) 的基本查詢作業](basic-query-operations.md)中，會討論每個查詢運算式子句的特定函數和用途。</span><span class="sxs-lookup"><span data-stu-id="2186b-146">The specific function and purpose of each query expression clause is discussed in [Basic Query Operations (Visual Basic)](basic-query-operations.md).</span></span> <span data-ttu-id="2186b-147">如需詳細資訊，請參閱 [查詢](../../../language-reference/queries/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2186b-147">For more information, see [Queries](../../../language-reference/queries/index.md).</span></span> <span data-ttu-id="2186b-148">請注意，在 LINQ 中，查詢定義通常會儲存在變數中並在稍後執行。</span><span class="sxs-lookup"><span data-stu-id="2186b-148">Note that in LINQ, a query definition often is stored in a variable and executed later.</span></span> <span data-ttu-id="2186b-149">查詢變數（如 `evensQuery` 上述範例所示）必須是可查詢的型別。</span><span class="sxs-lookup"><span data-stu-id="2186b-149">The query variable, such as `evensQuery` in the previous example, must be a queryable type.</span></span> <span data-ttu-id="2186b-150">的類型 `evensQuery` 是 `IEnumerable(Of Integer)` 由編譯器使用區欄位型別推斷所指派。</span><span class="sxs-lookup"><span data-stu-id="2186b-150">The type of `evensQuery` is `IEnumerable(Of Integer)`, assigned by the compiler using local type inference.</span></span>  
  
 <span data-ttu-id="2186b-151">請務必記住，查詢變數本身不會採取任何動作，也不會傳回任何資料。</span><span class="sxs-lookup"><span data-stu-id="2186b-151">It is important to remember that the query variable itself takes no action and returns no data.</span></span> <span data-ttu-id="2186b-152">它只會儲存查詢定義。</span><span class="sxs-lookup"><span data-stu-id="2186b-152">It only stores the query definition.</span></span> <span data-ttu-id="2186b-153">在上述範例中，這是 `For Each` 執行查詢的迴圈。</span><span class="sxs-lookup"><span data-stu-id="2186b-153">In the previous example, it is the `For Each` loop that executes the query.</span></span>  
  
## <a name="query-execution"></a><span data-ttu-id="2186b-154">查詢執行</span><span class="sxs-lookup"><span data-stu-id="2186b-154">Query Execution</span></span>  

 <span data-ttu-id="2186b-155">查詢執行與查詢建立不同。</span><span class="sxs-lookup"><span data-stu-id="2186b-155">Query execution is separate from query creation.</span></span> <span data-ttu-id="2186b-156">建立查詢會定義查詢，但會以不同的機制觸發執行。</span><span class="sxs-lookup"><span data-stu-id="2186b-156">Query creation defines the query, but execution is triggered by a different mechanism.</span></span> <span data-ttu-id="2186b-157">只要查詢定義 (*立即執行*) ，就可以執行查詢，或者可以儲存定義，然後在稍後 (*延後執行*) 執行查詢。</span><span class="sxs-lookup"><span data-stu-id="2186b-157">A query can be executed as soon as it is defined (*immediate execution*), or the definition can be stored and the query can be executed later (*deferred execution*).</span></span>  
  
### <a name="deferred-execution"></a><span data-ttu-id="2186b-158">延後執行</span><span class="sxs-lookup"><span data-stu-id="2186b-158">Deferred Execution</span></span>  

 <span data-ttu-id="2186b-159">一般 LINQ 查詢類似于上一個範例中定義的查詢 `evensQuery` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-159">A typical LINQ query resembles the one in the previous example, in which `evensQuery` is defined.</span></span> <span data-ttu-id="2186b-160">它會建立查詢，但不會立即執行。</span><span class="sxs-lookup"><span data-stu-id="2186b-160">It creates the query but does not execute it immediately.</span></span> <span data-ttu-id="2186b-161">相反地，查詢定義會儲存在查詢變數中 `evensQuery` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-161">Instead, the query definition is stored in the query variable `evensQuery`.</span></span> <span data-ttu-id="2186b-162">您稍後會執行查詢，通常是使用 `For Each` 迴圈傳回值的序列，或套用標準的查詢運算子（例如 `Count` 或） `Max` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-162">You execute the query later, typically by using a `For Each` loop, which returns a sequence of values, or by applying a standard query operator, such as `Count` or `Max`.</span></span> <span data-ttu-id="2186b-163">此進程稱為 *延後執行*。</span><span class="sxs-lookup"><span data-stu-id="2186b-163">This process is referred to as *deferred execution*.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 <span data-ttu-id="2186b-164">針對一系列的值，您可以使用 `For Each` `number` 上一個範例)  (迴圈中的反覆運算變數來存取取出的資料。</span><span class="sxs-lookup"><span data-stu-id="2186b-164">For a sequence of values, you access the retrieved data by using the iteration variable in the `For Each` loop (`number` in the previous example).</span></span> <span data-ttu-id="2186b-165">因為查詢變數（ `evensQuery` ）會保留查詢定義，而不是查詢結果，所以您可以使用查詢變數多次執行查詢。</span><span class="sxs-lookup"><span data-stu-id="2186b-165">Because the query variable, `evensQuery`, holds the query definition rather than the query results, you can execute a query as often as you want by using the query variable more than one time.</span></span> <span data-ttu-id="2186b-166">例如，您的應用程式中可能會有另一個應用程式持續更新的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2186b-166">For example, you might have a database in your application that is being updated continually by a separate application.</span></span> <span data-ttu-id="2186b-167">在您建立從該資料庫抓取資料的查詢之後，您可以使用 `For Each` 迴圈來重複執行查詢，每次都會抓取最新的資料。</span><span class="sxs-lookup"><span data-stu-id="2186b-167">After you have created a query that retrieves data from that database, you can use a `For Each` loop to execute the query repeatedly, retrieving the most recent data every time.</span></span>  
  
 <span data-ttu-id="2186b-168">下列範例將示範延後執行的運作方式。</span><span class="sxs-lookup"><span data-stu-id="2186b-168">The following example demonstrates how deferred execution works.</span></span> <span data-ttu-id="2186b-169">`evensQuery2`使用迴圈來定義和執行之後（ `For Each` 如先前的範例所示），資料來源中的某些元素 `numbers` 會變更。</span><span class="sxs-lookup"><span data-stu-id="2186b-169">After `evensQuery2` is defined and executed with a `For Each` loop, as in the previous examples, some elements in the data source `numbers` are changed.</span></span> <span data-ttu-id="2186b-170">然後再次執行第二個 `For Each` 迴圈 `evensQuery2` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-170">Then a second `For Each` loop runs `evensQuery2` again.</span></span> <span data-ttu-id="2186b-171">第二次的結果會不同，因為 `For Each` 迴圈會使用中的新值，再次執行查詢 `numbers` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-171">The results are different the second time, because the `For Each` loop executes the query again, using the new values in `numbers`.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 <span data-ttu-id="2186b-172">輸出：</span><span class="sxs-lookup"><span data-stu-id="2186b-172">Output:</span></span>  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a><span data-ttu-id="2186b-173">立即執行</span><span class="sxs-lookup"><span data-stu-id="2186b-173">Immediate Execution</span></span>  

 <span data-ttu-id="2186b-174">在順延強制查詢時，查詢定義會儲存在查詢變數中，以便稍後執行。</span><span class="sxs-lookup"><span data-stu-id="2186b-174">In deferred execution of queries, the query definition is stored in a query variable for later execution.</span></span> <span data-ttu-id="2186b-175">在立即執行時，會在其定義時執行查詢。</span><span class="sxs-lookup"><span data-stu-id="2186b-175">In immediate execution, the query is executed at the time of its definition.</span></span> <span data-ttu-id="2186b-176">當您套用需要存取查詢結果之個別元素的方法時，就會觸發執行。</span><span class="sxs-lookup"><span data-stu-id="2186b-176">Execution is triggered when you apply a method that requires access to individual elements of the query result.</span></span> <span data-ttu-id="2186b-177">通常會使用其中一個會傳回單一值的標準查詢運算子來強制執行立即執行。</span><span class="sxs-lookup"><span data-stu-id="2186b-177">Immediate execution often is forced by using one of the standard query operators that return single values.</span></span> <span data-ttu-id="2186b-178">範例包括 `Count` 、 `Max` 、 `Average` 和 `First` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-178">Examples are `Count`, `Max`, `Average`, and `First`.</span></span> <span data-ttu-id="2186b-179">這些標準查詢運算子會在套用查詢時立即執行查詢，以便計算並傳回單一結果。</span><span class="sxs-lookup"><span data-stu-id="2186b-179">These standard query operators execute the query as soon as they are applied in order to calculate and return a singleton result.</span></span> <span data-ttu-id="2186b-180">如需傳回單一值之標準查詢運算子的詳細資訊，請參閱 [匯總作業](aggregation-operations.md)、 [元素作業](element-operations.md)和 [數量詞作業](quantifier-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="2186b-180">For more information about standard query operators that return single values, see [Aggregation Operations](aggregation-operations.md), [Element Operations](element-operations.md), and [Quantifier Operations](quantifier-operations.md).</span></span>  
  
 <span data-ttu-id="2186b-181">下列查詢會傳回整數陣列中偶數數目的計數。</span><span class="sxs-lookup"><span data-stu-id="2186b-181">The following query returns a count of the even numbers in an array of integers.</span></span> <span data-ttu-id="2186b-182">查詢定義不會儲存，而且 `numEvens` 很簡單 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-182">The query definition is not saved, and `numEvens` is a simple `Integer`.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 <span data-ttu-id="2186b-183">您可以使用方法來達到相同的結果 `Aggregate` 。</span><span class="sxs-lookup"><span data-stu-id="2186b-183">You can achieve the same result by using the `Aggregate` method.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 <span data-ttu-id="2186b-184">您也可以 `ToList` 在查詢上呼叫或方法來強制執行查詢 `ToArray` (立即) 或查詢變數 (延後) ，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="2186b-184">You can also force execution of a query by calling the `ToList` or `ToArray` method on a query (immediate) or query variable (deferred), as shown in the following code.</span></span>  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 <span data-ttu-id="2186b-185">在上述範例中， `evensQuery3` 是查詢變數，但是 `evensList` 清單，而且 `evensArray` 是陣列。</span><span class="sxs-lookup"><span data-stu-id="2186b-185">In the previous examples, `evensQuery3` is a query variable, but `evensList` is a list and `evensArray` is an array.</span></span>  
  
 <span data-ttu-id="2186b-186">`ToList` `ToArray` 在您想要立即執行查詢，並將結果快取在單一集合物件中時，使用或強制立即執行會特別有用。</span><span class="sxs-lookup"><span data-stu-id="2186b-186">Using `ToList` or `ToArray` to force immediate execution is especially useful in scenarios in which you want to execute the query immediately and cache the results in a single collection object.</span></span> <span data-ttu-id="2186b-187">如需這些方法的詳細資訊，請參閱 [轉換資料類型](converting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2186b-187">For more information about these methods, see [Converting Data Types](converting-data-types.md).</span></span>  
  
 <span data-ttu-id="2186b-188">您也可以使用方法（例如方法）來執行查詢 `IEnumerable` <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> 。</span><span class="sxs-lookup"><span data-stu-id="2186b-188">You can also cause a query to be executed by using an `IEnumerable` method such as the <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2186b-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2186b-189">See also</span></span>

- [<span data-ttu-id="2186b-190">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="2186b-190">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="2186b-191">區域型別推斷</span><span class="sxs-lookup"><span data-stu-id="2186b-191">Local Type Inference</span></span>](../../language-features/variables/local-type-inference.md)
- [<span data-ttu-id="2186b-192">標準查詢運算子概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2186b-192">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="2186b-193">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="2186b-193">Introduction to LINQ in Visual Basic</span></span>](../../language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="2186b-194">LINQ</span><span class="sxs-lookup"><span data-stu-id="2186b-194">LINQ</span></span>](../../language-features/linq/index.md)
- [<span data-ttu-id="2186b-195">查詢</span><span class="sxs-lookup"><span data-stu-id="2186b-195">Queries</span></span>](../../../language-reference/queries/index.md)
