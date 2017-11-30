---
title: "支援 LINQ 的 Visual Basic 功能"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42465dbb168b7961792aec6b3c2bb7ae8f0a3355
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-features-that-support-linq"></a><span data-ttu-id="d3674-102">支援 LINQ 的 Visual Basic 功能</span><span class="sxs-lookup"><span data-stu-id="d3674-102">Visual Basic Features That Support LINQ</span></span>
<span data-ttu-id="d3674-103">名稱[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]指的是在 Visual Basic 中支援的查詢語法，並直接在語言中的其他語言建構的技術。</span><span class="sxs-lookup"><span data-stu-id="d3674-103">The name [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] refers to technology in Visual Basic that supports query syntax and other language constructs directly in the language.</span></span> <span data-ttu-id="d3674-104">與[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，您不必學習新語言對外部資料來源進行查詢。</span><span class="sxs-lookup"><span data-stu-id="d3674-104">With [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], you do not have to learn a new language to query against an external data source.</span></span> <span data-ttu-id="d3674-105">您可以使用 Visual Basic 查詢針對關聯式資料庫、 XML 存放區或物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="d3674-105">You can query against data in relational databases, XML stores, or objects by using Visual Basic.</span></span> <span data-ttu-id="d3674-106">這項整合的查詢語言功能可讓編譯時間檢查語法錯誤和型別安全。</span><span class="sxs-lookup"><span data-stu-id="d3674-106">This integration of query capabilities into the language enables compile-time checking for syntax errors and type safety.</span></span> <span data-ttu-id="d3674-107">這項整合也可確保您已經知道大部分的您必須知道要在 Visual Basic 中撰寫豐富多變的查詢。</span><span class="sxs-lookup"><span data-stu-id="d3674-107">This integration also ensures that you already know most of what you have to know to write rich, varied queries in Visual Basic.</span></span>  
  
 <span data-ttu-id="d3674-108">下列章節說明支援 LINQ 足夠的詳細資料，您可以開始閱讀簡介文件、 程式碼範例和範例應用程式中的語言建構。</span><span class="sxs-lookup"><span data-stu-id="d3674-108">The following sections describe the language constructs that support LINQ in enough detail to enable you to get started in reading the introductory documentation, code examples, and sample applications.</span></span> <span data-ttu-id="d3674-109">您也可以按一下連結，詳細的說明如何語言功能共同啟用語言整合式查詢。</span><span class="sxs-lookup"><span data-stu-id="d3674-109">You can also click the links to find more detailed explanations of how the language features come together to enable language-integrated query.</span></span> <span data-ttu-id="d3674-110">若要啟動很好的起點[逐步解說： 在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="d3674-110">A good place to start is [Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="d3674-111">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="d3674-111">Query Expressions</span></span>  
 <span data-ttu-id="d3674-112">在 Visual Basic 中的查詢運算式可以類似的 SQL 或 XQuery 的宣告式語法來表示。</span><span class="sxs-lookup"><span data-stu-id="d3674-112">Query expressions in Visual Basic can be expressed in a declarative syntax similar to that of SQL or XQuery.</span></span> <span data-ttu-id="d3674-113">在編譯時期的查詢語法會轉換成標準查詢運算子擴充方法的 LINQ 提供者實作的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="d3674-113">At compile time, query syntax is converted into method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="d3674-114">標準查詢運算子，藉以指定具有適當的命名空間是在範圍內的應用程式控制項`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="d3674-114">Applications control which standard query operators are in scope by specifying the appropriate namespace with an `Imports` statement.</span></span> <span data-ttu-id="d3674-115">Visual Basic 查詢運算式語法看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="d3674-115">Syntax for a Visual Basic query expression looks like this:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 <span data-ttu-id="d3674-116">如需詳細資訊，請參閱[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="d3674-116">For more information, see [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="implicitly-typed-variables"></a><span data-ttu-id="d3674-117">隱含類型的變數</span><span class="sxs-lookup"><span data-stu-id="d3674-117">Implicitly Typed Variables</span></span>  
 <span data-ttu-id="d3674-118">而不是明確指定型別，如果您宣告並初始化的變數，您可以啟用編譯器推斷並指派類型。</span><span class="sxs-lookup"><span data-stu-id="d3674-118">Instead of explicitly specifying a type when you declare and initialize a variable, you can enable the compiler to infer and assign the type.</span></span> <span data-ttu-id="d3674-119">這指*區域類型推斷*。</span><span class="sxs-lookup"><span data-stu-id="d3674-119">This is referred to as *local type inference*.</span></span>  
  
 <span data-ttu-id="d3674-120">強類型推斷其類型的變數，就像您明確指定的型別的變數。</span><span class="sxs-lookup"><span data-stu-id="d3674-120">Variables whose types are inferred are strongly typed, just like variables whose type you specify explicitly.</span></span> <span data-ttu-id="d3674-121">區域類型推斷僅適用於您正在定義的方法主體內的本機變數。</span><span class="sxs-lookup"><span data-stu-id="d3674-121">Local type inference works only when you are defining a local variable inside a method body.</span></span> <span data-ttu-id="d3674-122">如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="d3674-122">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="d3674-123">下列範例說明區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="d3674-123">The following example illustrates local type inference.</span></span> <span data-ttu-id="d3674-124">若要使用此範例中，您必須設定`Option Infer`至`On`。</span><span class="sxs-lookup"><span data-stu-id="d3674-124">To use this example, you must set `Option Infer` to `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 <span data-ttu-id="d3674-125">區域類型推斷也可以建立匿名型別，會在這一節稍後描述和所需的 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="d3674-125">Local type inference also makes it possible to create anonymous types, which are described later in this section and are necessary for LINQ queries.</span></span>  
  
 <span data-ttu-id="d3674-126">在下列 LINQ 範例中，型別推斷如果就會發生`Option Infer`是`On`或`Off`。</span><span class="sxs-lookup"><span data-stu-id="d3674-126">In the following LINQ example, type inference occurs if `Option Infer` is either `On` or `Off`.</span></span> <span data-ttu-id="d3674-127">如果會發生編譯時間錯誤`Option Infer`是`Off`和`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="d3674-127">A compile-time error occurs if `Option Infer` is `Off` and `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a><span data-ttu-id="d3674-128">物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="d3674-128">Object Initializers</span></span>  
 <span data-ttu-id="d3674-129">當您必須建立匿名型別來保留查詢的結果查詢運算式中使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="d3674-129">Object initializers are used in query expressions when you have to create an anonymous type to hold the results of a query.</span></span> <span data-ttu-id="d3674-130">它們也可用來初始化外部查詢的具名類型的物件。</span><span class="sxs-lookup"><span data-stu-id="d3674-130">They also can be used to initialize objects of named types outside of queries.</span></span> <span data-ttu-id="d3674-131">藉由使用物件初始設定式，您可以初始化單一行中的物件，而不需明確呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="d3674-131">By using an object initializer, you can initialize an object in a single line without explicitly calling a constructor.</span></span> <span data-ttu-id="d3674-132">假設您有類別，名為`Customer`具有公用`Name`和`Phone`屬性，以及其他內容中，物件初始設定式可用於這種方式：</span><span class="sxs-lookup"><span data-stu-id="d3674-132">Assuming that you have a class named `Customer` that has public `Name` and `Phone` properties, along with other properties, an object initializer can be used in this manner:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 <span data-ttu-id="d3674-133">如需詳細資訊，請參閱[物件初始設定式： 具名和匿名類型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d3674-133">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="d3674-134">匿名類型</span><span class="sxs-lookup"><span data-stu-id="d3674-134">Anonymous Types</span></span>  
 <span data-ttu-id="d3674-135">匿名型別提供便利的方式，可以暫時將一組屬性到您想要在查詢結果中包含的項目。</span><span class="sxs-lookup"><span data-stu-id="d3674-135">Anonymous types provide a convenient way to temporarily group a set of properties into an element that you want to include in a query result.</span></span> <span data-ttu-id="d3674-136">這可讓您在查詢中，依任何順序選擇可用的欄位的任意組合，但未定義具名的資料類型的項目。</span><span class="sxs-lookup"><span data-stu-id="d3674-136">This enables you to choose any combination of available fields in the query, in any order, without defining a named data type for the element.</span></span>  
  
 <span data-ttu-id="d3674-137">*匿名型別*由編譯器所動態建構。</span><span class="sxs-lookup"><span data-stu-id="d3674-137">An *anonymous type* is constructed dynamically by the compiler.</span></span> <span data-ttu-id="d3674-138">編譯器，系統會指派類型的名稱，它可能會變更與每個新的編譯。</span><span class="sxs-lookup"><span data-stu-id="d3674-138">The name of the type is assigned by the compiler, and it might change with each new compilation.</span></span> <span data-ttu-id="d3674-139">因此，名稱不能直接使用。</span><span class="sxs-lookup"><span data-stu-id="d3674-139">Therefore, the name cannot be used directly.</span></span> <span data-ttu-id="d3674-140">初始化匿名型別是以下列方式：</span><span class="sxs-lookup"><span data-stu-id="d3674-140">Anonymous types are initialized in the following way:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 <span data-ttu-id="d3674-141">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d3674-141">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="d3674-142">擴充方法</span><span class="sxs-lookup"><span data-stu-id="d3674-142">Extension Methods</span></span>  
 <span data-ttu-id="d3674-143">擴充方法可讓您將方法加入至資料類型或從外部定義的介面。</span><span class="sxs-lookup"><span data-stu-id="d3674-143">Extension methods enable you to add methods to a data type or interface from outside the definition.</span></span> <span data-ttu-id="d3674-144">這項功能可讓您，但不修改類型，作用中，將新方法新增至現有的類型。</span><span class="sxs-lookup"><span data-stu-id="d3674-144">This feature enables you to, in effect, add new methods to an existing type without actually modifying the type.</span></span> <span data-ttu-id="d3674-145">標準查詢運算子本身是擴充方法，可提供一組[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]的查詢功能實作的任何類型<xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="d3674-145">The standard query operators are themselves a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d3674-146">其他擴充功能<xref:System.Collections.Generic.IEnumerable%601>包含<xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Intersect%2A>。</span><span class="sxs-lookup"><span data-stu-id="d3674-146">Other extensions to <xref:System.Collections.Generic.IEnumerable%601> include <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 <span data-ttu-id="d3674-147">下列擴充方法會加入列印方法至<xref:System.String>類別。</span><span class="sxs-lookup"><span data-stu-id="d3674-147">The following extension method adds a print method to the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 <span data-ttu-id="d3674-148">此方法會像一般的執行個體方法的呼叫<xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="d3674-148">The method is called like an ordinary instance method of <xref:System.String>:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 <span data-ttu-id="d3674-149">如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="d3674-149">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="d3674-150">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="d3674-150">Lambda Expressions</span></span>  
 <span data-ttu-id="d3674-151">Lambda 運算式是函式不會計算並傳回單一值的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3674-151">A lambda expression is a function without a name that calculates and returns a single value.</span></span> <span data-ttu-id="d3674-152">不同於具名函式，可定義並在相同時間執行的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="d3674-152">Unlike named functions, a lambda expression can be defined and executed at the same time.</span></span> <span data-ttu-id="d3674-153">下列範例會顯示 4。</span><span class="sxs-lookup"><span data-stu-id="d3674-153">The following example displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 <span data-ttu-id="d3674-154">您可以將 lambda 運算式定義指派給變數的名稱，然後呼叫函式中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3674-154">You can assign the lambda expression definition to a variable name and then use the name to call the function.</span></span> <span data-ttu-id="d3674-155">下列範例也會顯示 4。</span><span class="sxs-lookup"><span data-stu-id="d3674-155">The following example also displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 <span data-ttu-id="d3674-156">在[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，lambda 運算式的基礎許多標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="d3674-156">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], lambda expressions underlie many of the standard query operators.</span></span> <span data-ttu-id="d3674-157">編譯器會建立 lambda 運算式來擷取這類定義於基本查詢方法的計算`Where`， `Select`， `Order By`， `Take While`，和其他人。</span><span class="sxs-lookup"><span data-stu-id="d3674-157">The compiler creates lambda expressions to capture the calculations that are defined in fundamental query methods such as `Where`, `Select`, `Order By`, `Take While`, and others.</span></span>  
  
 <span data-ttu-id="d3674-158">例如，下列程式碼定義學員清單中傳回所有高年級的學生的查詢。</span><span class="sxs-lookup"><span data-stu-id="d3674-158">For example, the following code defines a query that returns all senior students from a list of students.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 <span data-ttu-id="d3674-159">查詢定義會編譯到程式碼類似下列的範例中，使用兩個 lambda 運算式來指定的引數的`Where`和`Select`。</span><span class="sxs-lookup"><span data-stu-id="d3674-159">The query definition is compiled into code that is similar to the following example, which uses two lambda expressions to specify the arguments for `Where` and `Select`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 <span data-ttu-id="d3674-160">其中一個版本可以執行使用`For Each`迴圈：</span><span class="sxs-lookup"><span data-stu-id="d3674-160">Either version can be run by using a `For Each` loop:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 <span data-ttu-id="d3674-161">如需詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="d3674-161">For more information, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3674-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3674-162">See Also</span></span>  
 [<span data-ttu-id="d3674-163">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3674-163">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="d3674-164">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="d3674-164">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="d3674-165">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3674-165">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [<span data-ttu-id="d3674-166">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="d3674-166">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="d3674-167">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="d3674-167">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
