---
title: 支援 LINQ 的 Visual Basic 功能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 155d5c36483accc12d066a5530fea20a563e1498
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814493"
---
# <a name="visual-basic-features-that-support-linq"></a><span data-ttu-id="feefb-102">支援 LINQ 的 Visual Basic 功能</span><span class="sxs-lookup"><span data-stu-id="feefb-102">Visual Basic Features That Support LINQ</span></span>
<span data-ttu-id="feefb-103">名稱[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]指的是支援的查詢語法，並直接在語言中的其他語言建構的 Visual Basic 中的技術。</span><span class="sxs-lookup"><span data-stu-id="feefb-103">The name [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] refers to technology in Visual Basic that supports query syntax and other language constructs directly in the language.</span></span> <span data-ttu-id="feefb-104">使用[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，您不必學習新語言來查詢外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="feefb-104">With [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], you do not have to learn a new language to query against an external data source.</span></span> <span data-ttu-id="feefb-105">您可以使用 Visual Basic，就可查詢對關聯式資料庫、 XML 存放區或物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="feefb-105">You can query against data in relational databases, XML stores, or objects by using Visual Basic.</span></span> <span data-ttu-id="feefb-106">這項整合到語言的查詢功能可讓您編譯時間檢查有語法錯誤和型別安全。</span><span class="sxs-lookup"><span data-stu-id="feefb-106">This integration of query capabilities into the language enables compile-time checking for syntax errors and type safety.</span></span> <span data-ttu-id="feefb-107">這項整合也可確保您已經知道大部分的您必須知道要在 Visual Basic 中撰寫內容豐富且各種查詢。</span><span class="sxs-lookup"><span data-stu-id="feefb-107">This integration also ensures that you already know most of what you have to know to write rich, varied queries in Visual Basic.</span></span>  
  
 <span data-ttu-id="feefb-108">下列各節說明在足夠的詳細資料，可讓您開始閱讀簡介文件、 程式碼範例和範例應用程式中支援 LINQ 的語言建構。</span><span class="sxs-lookup"><span data-stu-id="feefb-108">The following sections describe the language constructs that support LINQ in enough detail to enable you to get started in reading the introductory documentation, code examples, and sample applications.</span></span> <span data-ttu-id="feefb-109">您也可以按一下連結，找出的語言功能即在一起的 language integrated query，以便更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="feefb-109">You can also click the links to find more detailed explanations of how the language features come together to enable language-integrated query.</span></span> <span data-ttu-id="feefb-110">很好的起點開始[逐步解說：在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="feefb-110">A good place to start is [Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="feefb-111">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="feefb-111">Query Expressions</span></span>  
 <span data-ttu-id="feefb-112">在 Visual Basic 中的查詢運算式可以是以類似於 SQL 或 XQuery 的宣告式語法來表示。</span><span class="sxs-lookup"><span data-stu-id="feefb-112">Query expressions in Visual Basic can be expressed in a declarative syntax similar to that of SQL or XQuery.</span></span> <span data-ttu-id="feefb-113">在編譯時期，查詢語法會轉換成方法呼叫的標準查詢運算子擴充方法的 LINQ 提供者的實作。</span><span class="sxs-lookup"><span data-stu-id="feefb-113">At compile time, query syntax is converted into method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="feefb-114">藉由指定適當的命名空間與標準查詢運算子是在範圍內的應用程式控制項`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="feefb-114">Applications control which standard query operators are in scope by specifying the appropriate namespace with an `Imports` statement.</span></span> <span data-ttu-id="feefb-115">Visual Basic 查詢運算式語法看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="feefb-115">Syntax for a Visual Basic query expression looks like this:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="feefb-116">如需詳細資訊，請參閱 <<c0> [ 在 Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="feefb-116">For more information, see [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="implicitly-typed-variables"></a><span data-ttu-id="feefb-117">隱含類型的變數</span><span class="sxs-lookup"><span data-stu-id="feefb-117">Implicitly Typed Variables</span></span>  
 <span data-ttu-id="feefb-118">而不是明確指定類型，當您宣告並初始化變數時，您可以讓編譯器推斷並指派類型。</span><span class="sxs-lookup"><span data-stu-id="feefb-118">Instead of explicitly specifying a type when you declare and initialize a variable, you can enable the compiler to infer and assign the type.</span></span> <span data-ttu-id="feefb-119">這指*區域型別推斷*。</span><span class="sxs-lookup"><span data-stu-id="feefb-119">This is referred to as *local type inference*.</span></span>  
  
 <span data-ttu-id="feefb-120">其型別推斷的變數是強型別，就像您明確地指定的型別的變數。</span><span class="sxs-lookup"><span data-stu-id="feefb-120">Variables whose types are inferred are strongly typed, just like variables whose type you specify explicitly.</span></span> <span data-ttu-id="feefb-121">區域類型推斷僅適用於您要定義方法主體內區域變數。</span><span class="sxs-lookup"><span data-stu-id="feefb-121">Local type inference works only when you are defining a local variable inside a method body.</span></span> <span data-ttu-id="feefb-122">如需詳細資訊，請參閱 < [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)並[區域型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="feefb-122">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="feefb-123">下列範例會說明區域類型推斷。</span><span class="sxs-lookup"><span data-stu-id="feefb-123">The following example illustrates local type inference.</span></span> <span data-ttu-id="feefb-124">若要使用此範例中，您必須設定`Option Infer`至`On`。</span><span class="sxs-lookup"><span data-stu-id="feefb-124">To use this example, you must set `Option Infer` to `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="feefb-125">區域類型推斷也讓您能夠建立匿名型別，而且在這一節稍後說明所需的 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="feefb-125">Local type inference also makes it possible to create anonymous types, which are described later in this section and are necessary for LINQ queries.</span></span>  
  
 <span data-ttu-id="feefb-126">在下列 LINQ 範例中，型別推斷如果就會發生`Option Infer`可能`On`或`Off`。</span><span class="sxs-lookup"><span data-stu-id="feefb-126">In the following LINQ example, type inference occurs if `Option Infer` is either `On` or `Off`.</span></span> <span data-ttu-id="feefb-127">如果，就會發生編譯時期錯誤`Option Infer`已`Off`並`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="feefb-127">A compile-time error occurs if `Option Infer` is `Off` and `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a><span data-ttu-id="feefb-128">物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="feefb-128">Object Initializers</span></span>  
 <span data-ttu-id="feefb-129">當您必須建立匿名型別來保存查詢的結果查詢運算式中使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="feefb-129">Object initializers are used in query expressions when you have to create an anonymous type to hold the results of a query.</span></span> <span data-ttu-id="feefb-130">它們也可用來初始化查詢之外的具名類型的物件。</span><span class="sxs-lookup"><span data-stu-id="feefb-130">They also can be used to initialize objects of named types outside of queries.</span></span> <span data-ttu-id="feefb-131">藉由使用物件初始設定式，您可以初始化單一行中的物件，而不需要明確呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="feefb-131">By using an object initializer, you can initialize an object in a single line without explicitly calling a constructor.</span></span> <span data-ttu-id="feefb-132">假設您有一個名為類別`Customer`具有公用`Name`和`Phone`屬性，以及其他屬性，可以使用物件初始設定式以這種方式：</span><span class="sxs-lookup"><span data-stu-id="feefb-132">Assuming that you have a class named `Customer` that has public `Name` and `Phone` properties, along with other properties, an object initializer can be used in this manner:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 <span data-ttu-id="feefb-133">如需詳細資訊，請參閱[物件初始設定式：具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="feefb-133">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="feefb-134">匿名類型</span><span class="sxs-lookup"><span data-stu-id="feefb-134">Anonymous Types</span></span>  
 <span data-ttu-id="feefb-135">匿名型別提供便利的方式，可以暫時將一組屬性，到您想要在查詢結果中包含的項目。</span><span class="sxs-lookup"><span data-stu-id="feefb-135">Anonymous types provide a convenient way to temporarily group a set of properties into an element that you want to include in a query result.</span></span> <span data-ttu-id="feefb-136">這可讓您選擇在查詢中，依任何順序的可用欄位的任何組合，而不定義具名的資料型別項目。</span><span class="sxs-lookup"><span data-stu-id="feefb-136">This enables you to choose any combination of available fields in the query, in any order, without defining a named data type for the element.</span></span>  
  
 <span data-ttu-id="feefb-137">*匿名型別*由編譯器所動態建構。</span><span class="sxs-lookup"><span data-stu-id="feefb-137">An *anonymous type* is constructed dynamically by the compiler.</span></span> <span data-ttu-id="feefb-138">由編譯器指派型別的名稱，它可能會變更與每個新的編譯。</span><span class="sxs-lookup"><span data-stu-id="feefb-138">The name of the type is assigned by the compiler, and it might change with each new compilation.</span></span> <span data-ttu-id="feefb-139">因此，名稱不能直接使用。</span><span class="sxs-lookup"><span data-stu-id="feefb-139">Therefore, the name cannot be used directly.</span></span> <span data-ttu-id="feefb-140">匿名型別會以下列方式初始化：</span><span class="sxs-lookup"><span data-stu-id="feefb-140">Anonymous types are initialized in the following way:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 <span data-ttu-id="feefb-141">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="feefb-141">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="feefb-142">擴充方法</span><span class="sxs-lookup"><span data-stu-id="feefb-142">Extension Methods</span></span>  
 <span data-ttu-id="feefb-143">擴充方法可讓您將方法加入至資料型別或從外部定義的介面。</span><span class="sxs-lookup"><span data-stu-id="feefb-143">Extension methods enable you to add methods to a data type or interface from outside the definition.</span></span> <span data-ttu-id="feefb-144">這項功能可讓您，而不需要實際修改型別，作用中，將新方法新增至現有的類型。</span><span class="sxs-lookup"><span data-stu-id="feefb-144">This feature enables you to, in effect, add new methods to an existing type without actually modifying the type.</span></span> <span data-ttu-id="feefb-145">標準查詢運算子本身是一組提供的擴充方法[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]的查詢功能會實作任何型別<xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="feefb-145">The standard query operators are themselves a set of extension methods that provide [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="feefb-146">其他擴充功能<xref:System.Collections.Generic.IEnumerable%601>包括<xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Intersect%2A>。</span><span class="sxs-lookup"><span data-stu-id="feefb-146">Other extensions to <xref:System.Collections.Generic.IEnumerable%601> include <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 <span data-ttu-id="feefb-147">下列擴充方法新增至列印方法<xref:System.String>類別。</span><span class="sxs-lookup"><span data-stu-id="feefb-147">The following extension method adds a print method to the <xref:System.String> class.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 <span data-ttu-id="feefb-148">類似的一般執行個體方法呼叫的方法<xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="feefb-148">The method is called like an ordinary instance method of <xref:System.String>:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 <span data-ttu-id="feefb-149">如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="feefb-149">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="feefb-150">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="feefb-150">Lambda Expressions</span></span>  
 <span data-ttu-id="feefb-151">Lambda 運算式是函式不會計算並傳回單一值的名稱。</span><span class="sxs-lookup"><span data-stu-id="feefb-151">A lambda expression is a function without a name that calculates and returns a single value.</span></span> <span data-ttu-id="feefb-152">不同於具名函式，lambda 運算式可定義並執行一次。</span><span class="sxs-lookup"><span data-stu-id="feefb-152">Unlike named functions, a lambda expression can be defined and executed at the same time.</span></span> <span data-ttu-id="feefb-153">下列範例會顯示 4。</span><span class="sxs-lookup"><span data-stu-id="feefb-153">The following example displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="feefb-154">您可以將 lambda 運算式定義指派給變數的名稱，並接著使用名稱來呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="feefb-154">You can assign the lambda expression definition to a variable name and then use the name to call the function.</span></span> <span data-ttu-id="feefb-155">下列範例也會顯示 4。</span><span class="sxs-lookup"><span data-stu-id="feefb-155">The following example also displays 4.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 <span data-ttu-id="feefb-156">在  [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]，lambda 運算式，構成許多標準查詢運算子。</span><span class="sxs-lookup"><span data-stu-id="feefb-156">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], lambda expressions underlie many of the standard query operators.</span></span> <span data-ttu-id="feefb-157">編譯器會建立 lambda 運算式來擷取這類定義基本的查詢方法中的計算`Where`， `Select`， `Order By`， `Take While`，和其他人。</span><span class="sxs-lookup"><span data-stu-id="feefb-157">The compiler creates lambda expressions to capture the calculations that are defined in fundamental query methods such as `Where`, `Select`, `Order By`, `Take While`, and others.</span></span>  
  
 <span data-ttu-id="feefb-158">例如，下列程式碼定義的查詢會傳回所有的資深學生從學生的清單。</span><span class="sxs-lookup"><span data-stu-id="feefb-158">For example, the following code defines a query that returns all senior students from a list of students.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 <span data-ttu-id="feefb-159">查詢定義會編譯成類似於下列的範例中，使用指定的引數的兩個 lambda 運算式的程式碼`Where`和`Select`。</span><span class="sxs-lookup"><span data-stu-id="feefb-159">The query definition is compiled into code that is similar to the following example, which uses two lambda expressions to specify the arguments for `Where` and `Select`.</span></span>  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 <span data-ttu-id="feefb-160">其中一個版本可以執行使用`For Each`迴圈：</span><span class="sxs-lookup"><span data-stu-id="feefb-160">Either version can be run by using a `For Each` loop:</span></span>  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 <span data-ttu-id="feefb-161">如需詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="feefb-161">For more information, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feefb-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="feefb-162">See also</span></span>

- [<span data-ttu-id="feefb-163">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feefb-163">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="feefb-164">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="feefb-164">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="feefb-165">LINQ 和字串 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feefb-165">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="feefb-166">Option Infer 陳述式</span><span class="sxs-lookup"><span data-stu-id="feefb-166">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="feefb-167">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="feefb-167">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
