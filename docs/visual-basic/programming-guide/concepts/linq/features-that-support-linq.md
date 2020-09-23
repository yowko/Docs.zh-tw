---
title: 支援 LINQ 的功能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: bd63cd36c1f85fd89349293a71ecc5b281165380
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078302"
---
# <a name="visual-basic-features-that-support-linq"></a><span data-ttu-id="2cdef-102">支援 LINQ 的 Visual Basic 功能</span><span class="sxs-lookup"><span data-stu-id="2cdef-102">Visual Basic Features That Support LINQ</span></span>

<span data-ttu-id="2cdef-103"> (LINQ) 的名稱語言整合式查詢，是指支援直接在語言中查詢語法和其他語言結構之 Visual Basic 中的技術。</span><span class="sxs-lookup"><span data-stu-id="2cdef-103">The name Language-Integrated Query (LINQ) refers to technology in Visual Basic that supports query syntax and other language constructs directly in the language.</span></span> <span data-ttu-id="2cdef-104">使用 LINQ 時，您不需要學習新的語言來查詢外部資料源。</span><span class="sxs-lookup"><span data-stu-id="2cdef-104">With LINQ, you do not have to learn a new language to query against an external data source.</span></span> <span data-ttu-id="2cdef-105">您可以使用 Visual Basic 來查詢關係資料庫、XML 存放區或物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="2cdef-105">You can query against data in relational databases, XML stores, or objects by using Visual Basic.</span></span> <span data-ttu-id="2cdef-106">這項查詢功能與語言的整合，可讓編譯時間檢查語法錯誤和型別安全。</span><span class="sxs-lookup"><span data-stu-id="2cdef-106">This integration of query capabilities into the language enables compile-time checking for syntax errors and type safety.</span></span> <span data-ttu-id="2cdef-107">這項整合也可確保您已瞭解在 Visual Basic 中撰寫豐富且不同的查詢時，您必須知道的大部分內容。</span><span class="sxs-lookup"><span data-stu-id="2cdef-107">This integration also ensures that you already know most of what you have to know to write rich, varied queries in Visual Basic.</span></span>  
  
 <span data-ttu-id="2cdef-108">下列各節描述支援 LINQ 的語言結構，以提供足夠的詳細資料，讓您可以開始閱讀簡介檔、程式碼範例和範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="2cdef-108">The following sections describe the language constructs that support LINQ in enough detail to enable you to get started in reading the introductory documentation, code examples, and sample applications.</span></span> <span data-ttu-id="2cdef-109">您也可以按一下連結來尋找更詳細的語言功能整合方式，以啟用語言整合查詢。</span><span class="sxs-lookup"><span data-stu-id="2cdef-109">You can also click the links to find more detailed explanations of how the language features come together to enable language-integrated query.</span></span> <span data-ttu-id="2cdef-110">[逐步解說：在 Visual Basic 中撰寫查詢](walkthrough-writing-queries.md)是不錯的開端。</span><span class="sxs-lookup"><span data-stu-id="2cdef-110">A good place to start is [Walkthrough: Writing Queries in Visual Basic](walkthrough-writing-queries.md).</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="2cdef-111">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="2cdef-111">Query Expressions</span></span>  

 <span data-ttu-id="2cdef-112">Visual Basic 中的查詢運算式可以用類似于 SQL 或 XQuery 的宣告式語法表示。</span><span class="sxs-lookup"><span data-stu-id="2cdef-112">Query expressions in Visual Basic can be expressed in a declarative syntax similar to that of SQL or XQuery.</span></span> <span data-ttu-id="2cdef-113">在編譯時期，查詢語法會轉換成 LINQ 提供者的標準查詢運算子擴充方法實作為方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="2cdef-113">At compile time, query syntax is converted into method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="2cdef-114">應用程式會使用語句來指定適當的命名空間，以控制哪些標準查詢運算子在範圍中 `Imports` 。</span><span class="sxs-lookup"><span data-stu-id="2cdef-114">Applications control which standard query operators are in scope by specifying the appropriate namespace with an `Imports` statement.</span></span> <span data-ttu-id="2cdef-115">Visual Basic 查詢運算式的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="2cdef-115">Syntax for a Visual Basic query expression looks like this:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="2cdef-116">如需詳細資訊，請參閱 [Visual Basic 中的 LINQ 簡介](../../language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdef-116">For more information, see [Introduction to LINQ in Visual Basic](../../language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="implicitly-typed-variables"></a><span data-ttu-id="2cdef-117">隱含類型變數</span><span class="sxs-lookup"><span data-stu-id="2cdef-117">Implicitly Typed Variables</span></span>  

 <span data-ttu-id="2cdef-118">您可以讓編譯器推斷並指派型別，而不是在宣告和初始化變數時明確指定型別。</span><span class="sxs-lookup"><span data-stu-id="2cdef-118">Instead of explicitly specifying a type when you declare and initialize a variable, you can enable the compiler to infer and assign the type.</span></span> <span data-ttu-id="2cdef-119">這稱為 *區欄位型別推斷*。</span><span class="sxs-lookup"><span data-stu-id="2cdef-119">This is referred to as *local type inference*.</span></span>  
  
 <span data-ttu-id="2cdef-120">推斷類型的變數是強型別，就像您明確指定其型別的變數一樣。</span><span class="sxs-lookup"><span data-stu-id="2cdef-120">Variables whose types are inferred are strongly typed, just like variables whose type you specify explicitly.</span></span> <span data-ttu-id="2cdef-121">只有在您定義方法主體內的區域變數時，區欄位型別推斷才能運作。</span><span class="sxs-lookup"><span data-stu-id="2cdef-121">Local type inference works only when you are defining a local variable inside a method body.</span></span> <span data-ttu-id="2cdef-122">如需詳細資訊，請參閱 [選項推斷語句](../../../language-reference/statements/option-infer-statement.md) 和 [區欄位型別推斷](../../language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdef-122">For more information, see [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="2cdef-123">下列範例說明區欄位型別推斷。</span><span class="sxs-lookup"><span data-stu-id="2cdef-123">The following example illustrates local type inference.</span></span> <span data-ttu-id="2cdef-124">若要使用此範例，您必須將設定 `Option Infer` 為 `On` 。</span><span class="sxs-lookup"><span data-stu-id="2cdef-124">To use this example, you must set `Option Infer` to `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2cdef-125">區欄位型別推斷也可讓您建立匿名型別，這些型別稍後會在本節中說明，而且是 LINQ 查詢的必要項。</span><span class="sxs-lookup"><span data-stu-id="2cdef-125">Local type inference also makes it possible to create anonymous types, which are described later in this section and are necessary for LINQ queries.</span></span>  
  
 <span data-ttu-id="2cdef-126">在下列 LINQ 範例中，如果是或，就會發生型別推斷 `Option Infer` `On` `Off` 。</span><span class="sxs-lookup"><span data-stu-id="2cdef-126">In the following LINQ example, type inference occurs if `Option Infer` is either `On` or `Off`.</span></span> <span data-ttu-id="2cdef-127">如果 `Option Infer` 是 `Off` 且為，就會發生編譯時期錯誤 `Option Strict` `On` 。</span><span class="sxs-lookup"><span data-stu-id="2cdef-127">A compile-time error occurs if `Option Infer` is `Off` and `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a><span data-ttu-id="2cdef-128">物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="2cdef-128">Object Initializers</span></span>  

 <span data-ttu-id="2cdef-129">當您必須建立匿名型別來保存查詢的結果時，查詢運算式中會使用物件初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="2cdef-129">Object initializers are used in query expressions when you have to create an anonymous type to hold the results of a query.</span></span> <span data-ttu-id="2cdef-130">它們也可以用來在查詢之外初始化命名類型的物件。</span><span class="sxs-lookup"><span data-stu-id="2cdef-130">They also can be used to initialize objects of named types outside of queries.</span></span> <span data-ttu-id="2cdef-131">藉由使用物件初始化運算式，您可以在單一行中初始化物件，而不需要明確呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="2cdef-131">By using an object initializer, you can initialize an object in a single line without explicitly calling a constructor.</span></span> <span data-ttu-id="2cdef-132">假設您有一個名為的類別，而 `Customer` 該類別具有公用 `Name` 和 `Phone` 屬性以及其他屬性，則可以用這種方式使用物件初始化運算式：</span><span class="sxs-lookup"><span data-stu-id="2cdef-132">Assuming that you have a class named `Customer` that has public `Name` and `Phone` properties, along with other properties, an object initializer can be used in this manner:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 <span data-ttu-id="2cdef-133">如需詳細資訊，請參閱 [物件初始化運算式：命名和匿名型別](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdef-133">For more information, see [Object Initializers: Named and Anonymous Types](../../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="2cdef-134">匿名類型</span><span class="sxs-lookup"><span data-stu-id="2cdef-134">Anonymous Types</span></span>  

 <span data-ttu-id="2cdef-135">匿名型別提供一個便利的方式，將一組屬性暫時分組到您想要包含在查詢結果中的元素。</span><span class="sxs-lookup"><span data-stu-id="2cdef-135">Anonymous types provide a convenient way to temporarily group a set of properties into an element that you want to include in a query result.</span></span> <span data-ttu-id="2cdef-136">這可讓您在查詢中選擇任何可用欄位的組合（以任何順序），而不需為專案定義命名的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2cdef-136">This enables you to choose any combination of available fields in the query, in any order, without defining a named data type for the element.</span></span>  
  
 <span data-ttu-id="2cdef-137">*匿名型*別是由編譯器動態進行。</span><span class="sxs-lookup"><span data-stu-id="2cdef-137">An *anonymous type* is constructed dynamically by the compiler.</span></span> <span data-ttu-id="2cdef-138">類型的名稱是由編譯器所指派，而且可能會隨著每個新的編譯而變更。</span><span class="sxs-lookup"><span data-stu-id="2cdef-138">The name of the type is assigned by the compiler, and it might change with each new compilation.</span></span> <span data-ttu-id="2cdef-139">因此，不能直接使用該名稱。</span><span class="sxs-lookup"><span data-stu-id="2cdef-139">Therefore, the name cannot be used directly.</span></span> <span data-ttu-id="2cdef-140">匿名型別會以下列方式初始化：</span><span class="sxs-lookup"><span data-stu-id="2cdef-140">Anonymous types are initialized in the following way:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 <span data-ttu-id="2cdef-141">如需詳細資訊，請參閱 [匿名型別](../../language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdef-141">For more information, see [Anonymous Types](../../language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="2cdef-142">擴充方法</span><span class="sxs-lookup"><span data-stu-id="2cdef-142">Extension Methods</span></span>  

 <span data-ttu-id="2cdef-143">擴充方法可讓您從定義外部將方法加入至資料類型或介面。</span><span class="sxs-lookup"><span data-stu-id="2cdef-143">Extension methods enable you to add methods to a data type or interface from outside the definition.</span></span> <span data-ttu-id="2cdef-144">這項功能可讓您將新的方法加入至現有的型別，而不需要實際修改型別。</span><span class="sxs-lookup"><span data-stu-id="2cdef-144">This feature enables you to, in effect, add new methods to an existing type without actually modifying the type.</span></span> <span data-ttu-id="2cdef-145">標準查詢運算子本身是一組擴充方法，可針對任何可執行檔型別提供 LINQ 查詢功能 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="2cdef-145">The standard query operators are themselves a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="2cdef-146"><xref:System.Collections.Generic.IEnumerable%601>包含、和的其他擴充功能 <xref:System.Linq.Enumerable.Count%2A> <xref:System.Linq.Enumerable.Union%2A> <xref:System.Linq.Enumerable.Intersect%2A> 。</span><span class="sxs-lookup"><span data-stu-id="2cdef-146">Other extensions to <xref:System.Collections.Generic.IEnumerable%601> include <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 <span data-ttu-id="2cdef-147">下列擴充方法會將 print 方法加入至 <xref:System.String> 類別。</span><span class="sxs-lookup"><span data-stu-id="2cdef-147">The following extension method adds a print method to the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 <span data-ttu-id="2cdef-148">方法的呼叫方式就像是的一般實例方法 <xref:System.String> ：</span><span class="sxs-lookup"><span data-stu-id="2cdef-148">The method is called like an ordinary instance method of <xref:System.String>:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 <span data-ttu-id="2cdef-149">如需詳細資訊，請參閱[擴充方法](../../language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdef-149">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="2cdef-150">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="2cdef-150">Lambda Expressions</span></span>  

 <span data-ttu-id="2cdef-151">Lambda 運算式是一種沒有名稱的函式，它會計算並傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="2cdef-151">A lambda expression is a function without a name that calculates and returns a single value.</span></span> <span data-ttu-id="2cdef-152">不同于命名函式，可以同時定義和執行 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="2cdef-152">Unlike named functions, a lambda expression can be defined and executed at the same time.</span></span> <span data-ttu-id="2cdef-153">下列範例會顯示4。</span><span class="sxs-lookup"><span data-stu-id="2cdef-153">The following example displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="2cdef-154">您可以將 lambda 運算式定義指派給變數名稱，然後使用該名稱來呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="2cdef-154">You can assign the lambda expression definition to a variable name and then use the name to call the function.</span></span> <span data-ttu-id="2cdef-155">下列範例也會顯示4。</span><span class="sxs-lookup"><span data-stu-id="2cdef-155">The following example also displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 <span data-ttu-id="2cdef-156">在 LINQ 中，lambda 運算式的標準是許多標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="2cdef-156">In LINQ, lambda expressions underlie many of the standard query operators.</span></span> <span data-ttu-id="2cdef-157">編譯器會建立 lambda 運算式來捕捉基礎查詢方法（例如 `Where` 、 `Select` 、 `Order By` 、 `Take While` 和其他）中所定義的計算。</span><span class="sxs-lookup"><span data-stu-id="2cdef-157">The compiler creates lambda expressions to capture the calculations that are defined in fundamental query methods such as `Where`, `Select`, `Order By`, `Take While`, and others.</span></span>  
  
 <span data-ttu-id="2cdef-158">例如，下列程式碼會定義一個查詢，以傳回學生清單中的所有資深學生。</span><span class="sxs-lookup"><span data-stu-id="2cdef-158">For example, the following code defines a query that returns all senior students from a list of students.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 <span data-ttu-id="2cdef-159">查詢定義會編譯成類似下列範例的程式碼，這會使用兩個 lambda 運算式來指定和的引數 `Where` `Select` 。</span><span class="sxs-lookup"><span data-stu-id="2cdef-159">The query definition is compiled into code that is similar to the following example, which uses two lambda expressions to specify the arguments for `Where` and `Select`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 <span data-ttu-id="2cdef-160">您可以使用迴圈來執行任一版本 `For Each` ：</span><span class="sxs-lookup"><span data-stu-id="2cdef-160">Either version can be run by using a `For Each` loop:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 <span data-ttu-id="2cdef-161">如需詳細資訊，請參閱 [Lambda 運算式](../../language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="2cdef-161">For more information, see [Lambda Expressions](../../language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cdef-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cdef-162">See also</span></span>

- [<span data-ttu-id="2cdef-163">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cdef-163">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="2cdef-164">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="2cdef-164">Getting Started with LINQ in Visual Basic</span></span>](getting-started-with-linq.md)
- [<span data-ttu-id="2cdef-165">LINQ 與字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cdef-165">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="2cdef-166">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="2cdef-166">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="2cdef-167">Long</span><span class="sxs-lookup"><span data-stu-id="2cdef-167">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
