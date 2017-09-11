---
title: "支援 LINQ 的 Visual Basic 功能 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
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
ms.openlocfilehash: 728018de7e38374875b15a809e5659003519d60f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="visual-basic-features-that-support-linq"></a><span data-ttu-id="92805-102">支援 LINQ 的 Visual Basic 功能</span><span class="sxs-lookup"><span data-stu-id="92805-102">Visual Basic Features That Support LINQ</span></span>
<span data-ttu-id="92805-103">名稱[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]指的是在 Visual Basic 中支援的查詢語法，並直接在語言中的其他語言建構的技術。</span><span class="sxs-lookup"><span data-stu-id="92805-103">The name [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] refers to technology in Visual Basic that supports query syntax and other language constructs directly in the language.</span></span> <span data-ttu-id="92805-104">使用[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]，您不需要學習新語言對外部資料來源進行查詢。</span><span class="sxs-lookup"><span data-stu-id="92805-104">With [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], you do not have to learn a new language to query against an external data source.</span></span> <span data-ttu-id="92805-105">您可以使用 Visual Basic 查詢對關聯式資料庫、 XML 存放區或物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="92805-105">You can query against data in relational databases, XML stores, or objects by using Visual Basic.</span></span> <span data-ttu-id="92805-106">這項整合的查詢語言功能可讓您編譯時期檢查語法錯誤和型別安全。</span><span class="sxs-lookup"><span data-stu-id="92805-106">This integration of query capabilities into the language enables compile-time checking for syntax errors and type safety.</span></span> <span data-ttu-id="92805-107">這項整合也可確保您已經知道大部分您必須知道要在 Visual Basic 中撰寫內容豐富且具有不同的查詢。</span><span class="sxs-lookup"><span data-stu-id="92805-107">This integration also ensures that you already know most of what you have to know to write rich, varied queries in Visual Basic.</span></span>  
  
 <span data-ttu-id="92805-108">下列章節說明足夠的詳細資料，可讓您開始閱讀簡介文件、 程式碼範例和範例應用程式中支援 LINQ 的語言建構。</span><span class="sxs-lookup"><span data-stu-id="92805-108">The following sections describe the language constructs that support LINQ in enough detail to enable you to get started in reading the introductory documentation, code examples, and sample applications.</span></span> <span data-ttu-id="92805-109">您也可以按一下連結，找出如何語言功能共同啟用語言整合查詢的詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="92805-109">You can also click the links to find more detailed explanations of how the language features come together to enable language-integrated query.</span></span> <span data-ttu-id="92805-110">很好的起點是[逐步解說︰ 在 Visual Basic 中撰寫查詢](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="92805-110">A good place to start is [Walkthrough: Writing Queries in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md).</span></span>  
  
## <a name="query-expressions"></a><span data-ttu-id="92805-111">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="92805-111">Query Expressions</span></span>  
 <span data-ttu-id="92805-112">Visual Basic 中的查詢運算式可以用類似的 SQL 或 XQuery 的宣告式語法來表示。</span><span class="sxs-lookup"><span data-stu-id="92805-112">Query expressions in Visual Basic can be expressed in a declarative syntax similar to that of SQL or XQuery.</span></span> <span data-ttu-id="92805-113">在編譯時期，查詢語法會轉換成標準查詢運算子擴充方法的 LINQ 提供者實作的方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="92805-113">At compile time, query syntax is converted into method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="92805-114">標準查詢運算子是藉由指定具有適當的命名空間範圍中的應用程式控制`Imports`陳述式。</span><span class="sxs-lookup"><span data-stu-id="92805-114">Applications control which standard query operators are in scope by specifying the appropriate namespace with an `Imports` statement.</span></span> <span data-ttu-id="92805-115">Visual Basic 查詢運算式語法看起來像這樣︰</span><span class="sxs-lookup"><span data-stu-id="92805-115">Syntax for a Visual Basic query expression looks like this:</span></span>  
  
 <span data-ttu-id="92805-116">[!code-vb[VbLINQVbFeatures #&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-116">[!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]</span></span>  
  
 <span data-ttu-id="92805-117">如需詳細資訊，請參閱[Visual Basic 中的 LINQ 簡介](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="92805-117">For more information, see [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).</span></span>  
  
## <a name="implicitly-typed-variables"></a><span data-ttu-id="92805-118">隱含型別的變數</span><span class="sxs-lookup"><span data-stu-id="92805-118">Implicitly Typed Variables</span></span>  
 <span data-ttu-id="92805-119">而不是明確指定型別，當您宣告並初始化變數時，您可以啟用編譯器推斷並指派類型。</span><span class="sxs-lookup"><span data-stu-id="92805-119">Instead of explicitly specifying a type when you declare and initialize a variable, you can enable the compiler to infer and assign the type.</span></span> <span data-ttu-id="92805-120">這指*區域型別推斷*。</span><span class="sxs-lookup"><span data-stu-id="92805-120">This is referred to as *local type inference*.</span></span>  
  
 <span data-ttu-id="92805-121">變數的型別推斷是強型別，如同您明確地指定的型別的變數。</span><span class="sxs-lookup"><span data-stu-id="92805-121">Variables whose types are inferred are strongly typed, just like variables whose type you specify explicitly.</span></span> <span data-ttu-id="92805-122">定義方法主體內的區域變數時，只有區域型別推斷的運作方式。</span><span class="sxs-lookup"><span data-stu-id="92805-122">Local type inference works only when you are defining a local variable inside a method body.</span></span> <span data-ttu-id="92805-123">如需詳細資訊，請參閱[Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md)和[本機的型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="92805-123">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="92805-124">下列範例說明區域型別推斷。</span><span class="sxs-lookup"><span data-stu-id="92805-124">The following example illustrates local type inference.</span></span> <span data-ttu-id="92805-125">若要使用此範例中，您必須設定`Option Infer`到`On`。</span><span class="sxs-lookup"><span data-stu-id="92805-125">To use this example, you must set `Option Infer` to `On`.</span></span>  
  
 <span data-ttu-id="92805-126">[!code-vb[VbLINQVbFeatures #&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-126">[!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]</span></span>  
  
 <span data-ttu-id="92805-127">區域型別推斷也可讓建立匿名型別，在本節稍後說明和所需的 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="92805-127">Local type inference also makes it possible to create anonymous types, which are described later in this section and are necessary for LINQ queries.</span></span>  
  
 <span data-ttu-id="92805-128">在下列 LINQ 範例中，型別推斷起因於`Option Infer`是`On`或`Off`。</span><span class="sxs-lookup"><span data-stu-id="92805-128">In the following LINQ example, type inference occurs if `Option Infer` is either `On` or `Off`.</span></span> <span data-ttu-id="92805-129">如果，就會發生編譯時期錯誤`Option Infer`是`Off`和`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="92805-129">A compile-time error occurs if `Option Infer` is `Off` and `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="92805-130">[!code-vb[VbLINQVbFeatures #&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-130">[!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]</span></span>  
  
## <a name="object-initializers"></a><span data-ttu-id="92805-131">物件初始設定式</span><span class="sxs-lookup"><span data-stu-id="92805-131">Object Initializers</span></span>  
 <span data-ttu-id="92805-132">當您必須建立匿名型別來保存查詢結果的查詢運算式中使用物件初始設定式。</span><span class="sxs-lookup"><span data-stu-id="92805-132">Object initializers are used in query expressions when you have to create an anonymous type to hold the results of a query.</span></span> <span data-ttu-id="92805-133">它們也可用來初始化物件的具名查詢之外的型別。</span><span class="sxs-lookup"><span data-stu-id="92805-133">They also can be used to initialize objects of named types outside of queries.</span></span> <span data-ttu-id="92805-134">藉由使用物件初始設定式，您可以初始化單一行中的物件，而不需要明確呼叫建構函式。</span><span class="sxs-lookup"><span data-stu-id="92805-134">By using an object initializer, you can initialize an object in a single line without explicitly calling a constructor.</span></span> <span data-ttu-id="92805-135">假設您有一個名為的類別`Customer`具有公用`Name`和`Phone`屬性，以及其他內容，物件初始設定式可以使用這種方式︰</span><span class="sxs-lookup"><span data-stu-id="92805-135">Assuming that you have a class named `Customer` that has public `Name` and `Phone` properties, along with other properties, an object initializer can be used in this manner:</span></span>  
  
 <span data-ttu-id="92805-136">[!code-vb[VbLINQVbFeatures #&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-136">[!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]</span></span>  
  
 <span data-ttu-id="92805-137">如需詳細資訊，請參閱[物件初始設定式︰ 具名和匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="92805-137">For more information, see [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).</span></span>  
  
## <a name="anonymous-types"></a><span data-ttu-id="92805-138">匿名類型</span><span class="sxs-lookup"><span data-stu-id="92805-138">Anonymous Types</span></span>  
 <span data-ttu-id="92805-139">匿名型別提供便利的方式，可以暫時將一組屬性，您想要在查詢結果中包含的項目。</span><span class="sxs-lookup"><span data-stu-id="92805-139">Anonymous types provide a convenient way to temporarily group a set of properties into an element that you want to include in a query result.</span></span> <span data-ttu-id="92805-140">這可讓您在查詢中，依任何順序選擇可用的欄位的任意組合，而不定義項目的具名的資料型別。</span><span class="sxs-lookup"><span data-stu-id="92805-140">This enables you to choose any combination of available fields in the query, in any order, without defining a named data type for the element.</span></span>  
  
 <span data-ttu-id="92805-141">*匿名型別*由編譯器所動態建構。</span><span class="sxs-lookup"><span data-stu-id="92805-141">An *anonymous type* is constructed dynamically by the compiler.</span></span> <span data-ttu-id="92805-142">由編譯器指派型別的名稱，可能會變更與每個新的編譯。</span><span class="sxs-lookup"><span data-stu-id="92805-142">The name of the type is assigned by the compiler, and it might change with each new compilation.</span></span> <span data-ttu-id="92805-143">因此，名稱不能直接使用。</span><span class="sxs-lookup"><span data-stu-id="92805-143">Therefore, the name cannot be used directly.</span></span> <span data-ttu-id="92805-144">初始化匿名型別是以下列方式︰</span><span class="sxs-lookup"><span data-stu-id="92805-144">Anonymous types are initialized in the following way:</span></span>  
  
 <span data-ttu-id="92805-145">[!code-vb[VbLINQVbFeatures #&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-145">[!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]</span></span>  
  
 <span data-ttu-id="92805-146">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="92805-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="extension-methods"></a><span data-ttu-id="92805-147">擴充方法</span><span class="sxs-lookup"><span data-stu-id="92805-147">Extension Methods</span></span>  
 <span data-ttu-id="92805-148">擴充方法可讓您將方法加入至資料型別或外部定義的介面。</span><span class="sxs-lookup"><span data-stu-id="92805-148">Extension methods enable you to add methods to a data type or interface from outside the definition.</span></span> <span data-ttu-id="92805-149">這項功能可讓您能，作用中，將新方法加入現有的型別而不實際修改型別。</span><span class="sxs-lookup"><span data-stu-id="92805-149">This feature enables you to, in effect, add new methods to an existing type without actually modifying the type.</span></span> <span data-ttu-id="92805-150">標準查詢運算子本身是一組延伸方法，提供[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]查詢實作<xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>任何類型的功能</span><span class="sxs-lookup"><span data-stu-id="92805-150">The standard query operators are themselves a set of extension methods that provide [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="92805-151">其他擴充功能<xref:System.Collections.Generic.IEnumerable%601>包括<xref:System.Linq.Enumerable.Count%2A>， <xref:System.Linq.Enumerable.Union%2A>，和<xref:System.Linq.Enumerable.Intersect%2A>.</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Union%2A> </xref:System.Linq.Enumerable.Count%2A> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="92805-151">Other extensions to <xref:System.Collections.Generic.IEnumerable%601> include <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Union%2A>, and <xref:System.Linq.Enumerable.Intersect%2A>.</span></span>  
  
 <span data-ttu-id="92805-152">下列擴充方法會將列印的方法加入至<xref:System.String>類別。</xref:System.String></span><span class="sxs-lookup"><span data-stu-id="92805-152">The following extension method adds a print method to the <xref:System.String> class.</span></span>  
  
 <span data-ttu-id="92805-153">[!code-vb[VbLINQVbFeatures #&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-153">[!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]</span></span>  
  
 <span data-ttu-id="92805-154">像<xref:System.String>::</xref:System.String>的一般執行個體方法呼叫方法</span><span class="sxs-lookup"><span data-stu-id="92805-154">The method is called like an ordinary instance method of <xref:System.String>:</span></span>  
  
 <span data-ttu-id="92805-155">[!code-vb[VbLINQVbFeatures #&7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-155">[!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]</span></span>  
  
 <span data-ttu-id="92805-156">如需詳細資訊，請參閱[擴充方法](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="92805-156">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="92805-157">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="92805-157">Lambda Expressions</span></span>  
 <span data-ttu-id="92805-158">Lambda 運算式是函式不會計算並傳回單一值的名稱。</span><span class="sxs-lookup"><span data-stu-id="92805-158">A lambda expression is a function without a name that calculates and returns a single value.</span></span> <span data-ttu-id="92805-159">不同於具名函式，可定義並執行一次的 lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="92805-159">Unlike named functions, a lambda expression can be defined and executed at the same time.</span></span> <span data-ttu-id="92805-160">下列範例顯示的是 4。</span><span class="sxs-lookup"><span data-stu-id="92805-160">The following example displays 4.</span></span>  
  
 <span data-ttu-id="92805-161">[!code-vb[VbLINQVbFeatures #&8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-161">[!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]</span></span>  
  
 <span data-ttu-id="92805-162">您可以將 lambda 運算式定義指派給變數的名稱，然後使用名稱來呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="92805-162">You can assign the lambda expression definition to a variable name and then use the name to call the function.</span></span> <span data-ttu-id="92805-163">下列範例也會顯示 4。</span><span class="sxs-lookup"><span data-stu-id="92805-163">The following example also displays 4.</span></span>  
  
 <span data-ttu-id="92805-164">[!code-vb[VbLINQVbFeatures #&12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-164">[!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]</span></span>  
  
 <span data-ttu-id="92805-165">在[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]，lambda 運算式是許多標準查詢運算子的基礎。</span><span class="sxs-lookup"><span data-stu-id="92805-165">In [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], lambda expressions underlie many of the standard query operators.</span></span> <span data-ttu-id="92805-166">編譯器會建立 lambda 運算式來擷取這類定義於基礎的查詢方法的計算`Where`， `Select`， `Order By`， `Take While`，等等。</span><span class="sxs-lookup"><span data-stu-id="92805-166">The compiler creates lambda expressions to capture the calculations that are defined in fundamental query methods such as `Where`, `Select`, `Order By`, `Take While`, and others.</span></span>  
  
 <span data-ttu-id="92805-167">例如，下列程式碼會定義傳回所有的資深學生的學生清單中的查詢。</span><span class="sxs-lookup"><span data-stu-id="92805-167">For example, the following code defines a query that returns all senior students from a list of students.</span></span>  
  
 <span data-ttu-id="92805-168">[!code-vb[VbLINQVbFeatures #&9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-168">[!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]</span></span>  
  
 <span data-ttu-id="92805-169">查詢定義會編譯成程式碼類似下列的範例中，使用兩個 lambda 運算式來指定的引數的`Where`和`Select`。</span><span class="sxs-lookup"><span data-stu-id="92805-169">The query definition is compiled into code that is similar to the following example, which uses two lambda expressions to specify the arguments for `Where` and `Select`.</span></span>  
  
 <span data-ttu-id="92805-170">[!code-vb[VbLINQVbFeatures #&10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-170">[!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]</span></span>  
  
 <span data-ttu-id="92805-171">其中一個版本可以執行使用`For Each`迴圈︰</span><span class="sxs-lookup"><span data-stu-id="92805-171">Either version can be run by using a `For Each` loop:</span></span>  
  
 <span data-ttu-id="92805-172">[!code-vb[VbLINQVbFeatures #&11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="92805-172">[!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]</span></span>  
  
 <span data-ttu-id="92805-173">如需詳細資訊，請參閱[Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="92805-173">For more information, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92805-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92805-174">See Also</span></span>  
 <span data-ttu-id="92805-175">[語言整合查詢 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="92805-175">[Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md) </span></span>  
<span data-ttu-id="92805-176"> [在 Visual Basic 中撰寫 LINQ 入門](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span><span class="sxs-lookup"><span data-stu-id="92805-176"> [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md) </span></span>  
<span data-ttu-id="92805-177"> [LINQ 和字串 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="92805-177"> [LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="92805-178"> [Option Infer 陳述式](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="92805-178"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="92805-179"> [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="92805-179"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
