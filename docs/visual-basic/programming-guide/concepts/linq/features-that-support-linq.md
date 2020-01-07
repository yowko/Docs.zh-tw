---
title: 支援 LINQ 的功能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 57c0566f9a76715e48b20f2e6493aa1a506c64be
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636857"
---
# <a name="visual-basic-features-that-support-linq"></a><span data-ttu-id="c425d-102">支援 LINQ 的 Visual Basic 功能</span><span class="sxs-lookup"><span data-stu-id="c425d-102">Visual Basic Features That Support LINQ</span></span>
<span data-ttu-id="c425d-103">「語言整合式查詢」（LINQ）是指支援直接在語言中查詢語法和其他語言結構的 Visual Basic 技術。</span><span class="sxs-lookup"><span data-stu-id="c425d-103">The name Language-Integrated Query (LINQ) refers to technology in Visual Basic that supports query syntax and other language constructs directly in the language.</span></span> <span data-ttu-id="c425d-104">有了 LINQ，您就不需要學習新的語言來查詢外部資料源。</span><span class="sxs-lookup"><span data-stu-id="c425d-104">With LINQ, you do not have to learn a new language to query against an external data source.</span></span> <span data-ttu-id="c425d-105">您可以使用 Visual Basic 來查詢關係資料庫、XML 存放區或物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="c425d-105">You can query against data in relational databases, XML stores, or objects by using Visual Basic.</span></span> <span data-ttu-id="c425d-106">將查詢功能整合到語言中，可讓編譯時間檢查語法錯誤和型別安全。</span><span class="sxs-lookup"><span data-stu-id="c425d-106">This integration of query capabilities into the language enables compile-time checking for syntax errors and type safety.</span></span> <span data-ttu-id="c425d-107">這項整合也可確保您已經知道在 Visual Basic 中撰寫豐富、多樣化查詢所需知道的大部分知識。</span><span class="sxs-lookup"><span data-stu-id="c425d-107">This integration also ensures that you already know most of what you have to know to write rich, varied queries in Visual Basic.</span></span>  
  
 <span data-ttu-id="c425d-108">下列各節將說明支援 LINQ 的語言結構，以提供足夠的詳細資料，讓您能夠開始閱讀簡介檔、程式碼範例和範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="c425d-108">The following sections describe the language constructs that support LINQ in enough detail to enable you to get started in reading the introductory documentation, code examples, and sample applications.</span></span> <span data-ttu-id="c425d-109">您也可以按一下連結，尋找如何將語言功能結合在一起，以啟用語言整合式查詢的詳細說明。</span><span class="sxs-lookup"><span data-stu-id="c425d-109">You can also click the links to find more detailed explanations of how the language features come together to enable language-integrated query.</span></span> <span data-ttu-id="c425d-110">一個不錯的起點是[逐步解說：在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c425d-110">A good place to start is [Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="c425d-111">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="c425d-111">Query Expressions</span></span>  
 <span data-ttu-id="c425d-112">Visual Basic 中的查詢運算式可以用類似 SQL 或 XQuery 的宣告式語法來表示。</span><span class="sxs-lookup"><span data-stu-id="c425d-112">Query expressions in Visual Basic can be expressed in a declarative syntax similar to that of SQL or XQuery.</span></span> <span data-ttu-id="c425d-113">在編譯時期，查詢語法會轉換成 LINQ 提供者的標準查詢運算子擴充方法的實作為方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="c425d-113">At compile time, query syntax is converted into method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="c425d-114">應用程式會藉由使用 `Imports` 語句來指定適當的命名空間，以控制哪些標準查詢運算子在範圍內。</span><span class="sxs-lookup"><span data-stu-id="c425d-114">Applications control which standard query operators are in scope by specifying the appropriate namespace with an `Imports` statement.</span></span> <span data-ttu-id="c425d-115">Visual Basic 查詢運算式的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="c425d-115">Syntax for a Visual Basic query expression looks like this:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="c425d-116">如需詳細資訊，請參閱[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="c425d-116">For more information, see [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="implicitly-typed-variables"></a><span data-ttu-id="c425d-117">隱含類型變數</span><span class="sxs-lookup"><span data-stu-id="c425d-117">Implicitly Typed Variables</span></span>  
 <span data-ttu-id="c425d-118">您可以讓編譯器推斷並指派型別，而不是在宣告和初始化變數時明確指定型別。</span><span class="sxs-lookup"><span data-stu-id="c425d-118">Instead of explicitly specifying a type when you declare and initialize a variable, you can enable the compiler to infer and assign the type.</span></span> <span data-ttu-id="c425d-119">這稱為*區欄位型別推斷*。</span><span class="sxs-lookup"><span data-stu-id="c425d-119">This is referred to as *local type inference*.</span></span>  
  
 <span data-ttu-id="c425d-120">推斷其類型的變數是強型別，就像您明確指定型別的變數一樣。</span><span class="sxs-lookup"><span data-stu-id="c425d-120">Variables whose types are inferred are strongly typed, just like variables whose type you specify explicitly.</span></span> <span data-ttu-id="c425d-121">區欄位型別推斷僅適用于您在方法主體內定義區域變數的情況。</span><span class="sxs-lookup"><span data-stu-id="c425d-121">Local type inference works only when you are defining a local variable inside a method body.</span></span> <span data-ttu-id="c425d-122">如需詳細資訊，請參閱[Option 推斷語句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區欄位型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="c425d-122">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="c425d-123">下列範例說明區域型別推斷。</span><span class="sxs-lookup"><span data-stu-id="c425d-123">The following example illustrates local type inference.</span></span> <span data-ttu-id="c425d-124">若要使用此範例，您必須將 `Option Infer` 設定為 `On`。</span><span class="sxs-lookup"><span data-stu-id="c425d-124">To use this example, you must set `Option Infer` to `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="c425d-125">區欄位型別推斷也可以建立匿名型別，這會在本節稍後說明，而且對於 LINQ 查詢而言是必要的。</span><span class="sxs-lookup"><span data-stu-id="c425d-125">Local type inference also makes it possible to create anonymous types, which are described later in this section and are necessary for LINQ queries.</span></span>  
  
 <span data-ttu-id="c425d-126">在下列 LINQ 範例中，如果 `Option Infer` 是 `On` 或 `Off`，就會發生型別推斷。</span><span class="sxs-lookup"><span data-stu-id="c425d-126">In the following LINQ example, type inference occurs if `Option Infer` is either `On` or `Off`.</span></span> <span data-ttu-id="c425d-127">如果 `Option Infer` `Off` 且 `Option Strict` `On`，就會發生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="c425d-127">A compile-time error occurs if `Option Infer` is `Off` and `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a><span data-ttu-id="c425d-128">物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="c425d-128">Object Initializers</span></span>  
 <span data-ttu-id="c425d-129">當您必須建立匿名型別來保存查詢的結果時，就會在查詢運算式中使用物件初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="c425d-129">Object initializers are used in query expressions when you have to create an anonymous type to hold the results of a query.</span></span> <span data-ttu-id="c425d-130">它們也可以用來初始化查詢以外的命名類型物件。</span><span class="sxs-lookup"><span data-stu-id="c425d-130">They also can be used to initialize objects of named types outside of queries.</span></span> <span data-ttu-id="c425d-131">藉由使用物件初始化運算式，您可以在單一行中初始化物件，而不需要明確呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="c425d-131">By using an object initializer, you can initialize an object in a single line without explicitly calling a constructor.</span></span> <span data-ttu-id="c425d-132">假設您有一個名為 `Customer` 的類別，其中具有公用的 `Name` 和 `Phone` 屬性，還有其他屬性，則可以透過這種方式來使用物件初始化運算式：</span><span class="sxs-lookup"><span data-stu-id="c425d-132">Assuming that you have a class named `Customer` that has public `Name` and `Phone` properties, along with other properties, an object initializer can be used in this manner:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 <span data-ttu-id="c425d-133">如需詳細資訊，請參閱[物件初始化運算式：名稱和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c425d-133">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="c425d-134">匿名類型</span><span class="sxs-lookup"><span data-stu-id="c425d-134">Anonymous Types</span></span>  
 <span data-ttu-id="c425d-135">匿名型別提供一個方便的方式，將一組屬性暫時分組到您想要包含在查詢結果中的元素。</span><span class="sxs-lookup"><span data-stu-id="c425d-135">Anonymous types provide a convenient way to temporarily group a set of properties into an element that you want to include in a query result.</span></span> <span data-ttu-id="c425d-136">這可讓您依任何順序選取查詢中可用欄位的任意組合，而不需要定義專案的命名資料類型。</span><span class="sxs-lookup"><span data-stu-id="c425d-136">This enables you to choose any combination of available fields in the query, in any order, without defining a named data type for the element.</span></span>  
  
 <span data-ttu-id="c425d-137">*匿名型*別是由編譯器動態地建造。</span><span class="sxs-lookup"><span data-stu-id="c425d-137">An *anonymous type* is constructed dynamically by the compiler.</span></span> <span data-ttu-id="c425d-138">類型的名稱是由編譯器指派，而且可能會隨著每個新的編譯而變更。</span><span class="sxs-lookup"><span data-stu-id="c425d-138">The name of the type is assigned by the compiler, and it might change with each new compilation.</span></span> <span data-ttu-id="c425d-139">因此，您無法直接使用此名稱。</span><span class="sxs-lookup"><span data-stu-id="c425d-139">Therefore, the name cannot be used directly.</span></span> <span data-ttu-id="c425d-140">匿名型別會以下列方式初始化：</span><span class="sxs-lookup"><span data-stu-id="c425d-140">Anonymous types are initialized in the following way:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 <span data-ttu-id="c425d-141">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c425d-141">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="c425d-142">擴充方法</span><span class="sxs-lookup"><span data-stu-id="c425d-142">Extension Methods</span></span>  
 <span data-ttu-id="c425d-143">擴充方法可讓您將方法加入至定義以外的資料類型或介面。</span><span class="sxs-lookup"><span data-stu-id="c425d-143">Extension methods enable you to add methods to a data type or interface from outside the definition.</span></span> <span data-ttu-id="c425d-144">這項功能可讓您將新方法加入至現有的類型，而不需要實際修改類型。</span><span class="sxs-lookup"><span data-stu-id="c425d-144">This feature enables you to, in effect, add new methods to an existing type without actually modifying the type.</span></span> <span data-ttu-id="c425d-145">標準查詢運算子本身是一組擴充方法，可為任何可執行 <xref:System.Collections.Generic.IEnumerable%601>的型別提供 LINQ 查詢功能。</span><span class="sxs-lookup"><span data-stu-id="c425d-145">The standard query operators are themselves a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="c425d-146"><xref:System.Collections.Generic.IEnumerable%601> 的其他延伸模組包括 <xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Union%2A>和 <xref:System.Linq.Enumerable.Intersect%2A>。</span><span class="sxs-lookup"><span data-stu-id="c425d-146">Other extensions to <xref:System.Collections.Generic.IEnumerable%601> include <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 <span data-ttu-id="c425d-147">下列擴充方法會將 print 方法加入至 <xref:System.String> 類別。</span><span class="sxs-lookup"><span data-stu-id="c425d-147">The following extension method adds a print method to the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 <span data-ttu-id="c425d-148">方法的呼叫方式就像 <xref:System.String>的一般實例方法：</span><span class="sxs-lookup"><span data-stu-id="c425d-148">The method is called like an ordinary instance method of <xref:System.String>:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 <span data-ttu-id="c425d-149">如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="c425d-149">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="c425d-150">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="c425d-150">Lambda Expressions</span></span>  
 <span data-ttu-id="c425d-151">Lambda 運算式是沒有名稱的函式，會計算並傳回單一值。</span><span class="sxs-lookup"><span data-stu-id="c425d-151">A lambda expression is a function without a name that calculates and returns a single value.</span></span> <span data-ttu-id="c425d-152">不同于命名函數，可以同時定義和執行 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="c425d-152">Unlike named functions, a lambda expression can be defined and executed at the same time.</span></span> <span data-ttu-id="c425d-153">下列範例會顯示4。</span><span class="sxs-lookup"><span data-stu-id="c425d-153">The following example displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="c425d-154">您可以將 lambda 運算式定義指派給變數名稱，然後使用此名稱來呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="c425d-154">You can assign the lambda expression definition to a variable name and then use the name to call the function.</span></span> <span data-ttu-id="c425d-155">下列範例也會顯示4。</span><span class="sxs-lookup"><span data-stu-id="c425d-155">The following example also displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 <span data-ttu-id="c425d-156">在 LINQ 中，lambda 運算式的基礎是許多標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="c425d-156">In LINQ, lambda expressions underlie many of the standard query operators.</span></span> <span data-ttu-id="c425d-157">編譯器會建立 lambda 運算式來捕捉基本查詢方法（例如 `Where`、`Select`、`Order By`、`Take While`和其他專案）中定義的計算。</span><span class="sxs-lookup"><span data-stu-id="c425d-157">The compiler creates lambda expressions to capture the calculations that are defined in fundamental query methods such as `Where`, `Select`, `Order By`, `Take While`, and others.</span></span>  
  
 <span data-ttu-id="c425d-158">例如，下列程式碼會定義一個查詢，以傳回一份學生清單中的所有資深學生。</span><span class="sxs-lookup"><span data-stu-id="c425d-158">For example, the following code defines a query that returns all senior students from a list of students.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 <span data-ttu-id="c425d-159">查詢定義會編譯成類似下列範例的程式碼，其使用兩個 lambda 運算式來指定 `Where` 和 `Select`的引數。</span><span class="sxs-lookup"><span data-stu-id="c425d-159">The query definition is compiled into code that is similar to the following example, which uses two lambda expressions to specify the arguments for `Where` and `Select`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 <span data-ttu-id="c425d-160">任一版本都可以使用 `For Each` 迴圈來執行：</span><span class="sxs-lookup"><span data-stu-id="c425d-160">Either version can be run by using a `For Each` loop:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 <span data-ttu-id="c425d-161">如需詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c425d-161">For more information, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c425d-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="c425d-162">See also</span></span>

- [<span data-ttu-id="c425d-163">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c425d-163">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="c425d-164">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="c425d-164">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="c425d-165">LINQ 和字串（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c425d-165">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="c425d-166">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="c425d-166">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="c425d-167">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="c425d-167">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
