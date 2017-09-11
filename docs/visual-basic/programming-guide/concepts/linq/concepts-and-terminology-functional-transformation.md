---
title: "概念和術語 （功能轉換） (Visual Basic) |Microsoft 文件"
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
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9b07bfffbb4f5c9d833f821c9c548892aab0e606
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017


---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a><span data-ttu-id="06ec3-102">概念和術語 （功能轉換） (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06ec3-102">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>
<span data-ttu-id="06ec3-103">本主題說明純功能性轉換的概念與術語。</span><span class="sxs-lookup"><span data-stu-id="06ec3-103">This topic introduces the concepts and terminology of pure functional transformations.</span></span> <span data-ttu-id="06ec3-104">轉換資料的功能性轉換方法所產生的程式碼通常比更傳統的命令性程式設計可以更快速地進行程式設計、更明確，而且更容易進行偵錯與維護。</span><span class="sxs-lookup"><span data-stu-id="06ec3-104">The functional transformation approach to transforming data yields code that is often quicker to program, more expressive, and easier to debug and maintain than more traditional, imperative programming.</span></span>  
  
 <span data-ttu-id="06ec3-105">請注意，本節中的主題用意不在於完整說明功能性程式設計。</span><span class="sxs-lookup"><span data-stu-id="06ec3-105">Note that the topics in this section are not intended to fully explain functional programming.</span></span> <span data-ttu-id="06ec3-106">而在於識別更容易將 XML 從一個組織結構轉換為另一個組織結構的某些功能性程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="06ec3-106">Instead, these topics identify some of the functional programming capabilities that make it easier to transform XML from one shape to another.</span></span>  
  
## <a name="what-is-pure-functional-transformation"></a><span data-ttu-id="06ec3-107">何謂純功能性轉換？</span><span class="sxs-lookup"><span data-stu-id="06ec3-107">What Is Pure Functional Transformation?</span></span>  
 <span data-ttu-id="06ec3-108">在*純功能性轉換*，一組函式，呼叫*純虛擬函式*，定義如何將一組結構化資料從其原始格式轉換成另一種形式。</span><span class="sxs-lookup"><span data-stu-id="06ec3-108">In *pure functional transformation*, a set of functions, called *pure functions*, define how to transform a set of structured data from its original form into another form.</span></span> <span data-ttu-id="06ec3-109">「 純 」 這個字表示的功能是*組合*，需要它們是︰</span><span class="sxs-lookup"><span data-stu-id="06ec3-109">The word "pure" indicates that the functions are *composable*, which requires that they are:</span></span>  
  
-   <span data-ttu-id="06ec3-110">*獨立*，以便他們可以自由地排序和重新整理，而不牽連或程式的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="06ec3-110">*Self-contained*, so that they can be freely ordered and rearranged without entanglement or interdependencies with the rest of the program.</span></span> <span data-ttu-id="06ec3-111">純轉換與其環境無關，也不會影響其環境。</span><span class="sxs-lookup"><span data-stu-id="06ec3-111">Pure transformations have no knowledge of or effect upon their environment.</span></span> <span data-ttu-id="06ec3-112">也就是用於轉換的函式沒有任何*副作用*。</span><span class="sxs-lookup"><span data-stu-id="06ec3-112">That is, the functions used in the transformation have no *side effects*.</span></span>  
  
-   <span data-ttu-id="06ec3-113">*無狀態*，以便在相同的輸入上執行相同的函數或特定一組函數永遠會導致相同的輸出。</span><span class="sxs-lookup"><span data-stu-id="06ec3-113">*Stateless*, so that executing the same function or specific set of functions on the same input will always result in the same output.</span></span> <span data-ttu-id="06ec3-114">純轉換絲毫不會記得其先前的用途。</span><span class="sxs-lookup"><span data-stu-id="06ec3-114">Pure transformations have no memory of their prior use.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06ec3-115">在本教學課程的其餘部分，「純虛擬函式」這個名詞用於一般含意，表示程式設計方法而非特定的語言功能。</span><span class="sxs-lookup"><span data-stu-id="06ec3-115">In the rest of this tutorial, the term "pure function" is used in a general sense to indicate a programming approach, and not a specific language feature.</span></span>  
>   
>  <span data-ttu-id="06ec3-116">請注意，必須實作純虛擬函式做為 Visual Basic 中的函式。</span><span class="sxs-lookup"><span data-stu-id="06ec3-116">Note that pure functions must be implemented as functions in Visual Basic.</span></span>  
>   
>  <span data-ttu-id="06ec3-117">同時，您不應將純虛擬函式誤解為 C++ 的純虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="06ec3-117">Also, you should not confuse pure functions with pure virtual methods in C++.</span></span> <span data-ttu-id="06ec3-118">後者表示包含的類別是抽象的，而且不會提供任何方法主體。</span><span class="sxs-lookup"><span data-stu-id="06ec3-118">The latter indicates that the containing class is abstract and that no method body is supplied.</span></span>  
  
### <a name="functional-programming"></a><span data-ttu-id="06ec3-119">功能性程式設計</span><span class="sxs-lookup"><span data-stu-id="06ec3-119">Functional Programming</span></span>  
 <span data-ttu-id="06ec3-120">*功能性程式設計*是一種程式設計方法可直接支援純功能性轉換。</span><span class="sxs-lookup"><span data-stu-id="06ec3-120">*Functional programming* is a programming approach that directly supports pure functional transformation.</span></span>  
  
 <span data-ttu-id="06ec3-121">在過去，一般用途的功能性程式設計語言，例如 ML、 配置、 Haskell 與 F # 中，已主要的學術團體的關心。</span><span class="sxs-lookup"><span data-stu-id="06ec3-121">Historically, general-purpose functional programming languages, such as ML, Scheme, Haskell, and F#, have been primarily of interest to the academic community.</span></span> <span data-ttu-id="06ec3-122">雖然它一直可以在 Visual Basic 中撰寫純功能性轉換，困難度因此未進行其大部分的程式設計人員的理想選擇。</span><span class="sxs-lookup"><span data-stu-id="06ec3-122">Although it has always been possible to write pure functional transformations in Visual Basic, the difficulty of doing so has not made it an attractive option to most programmers.</span></span> <span data-ttu-id="06ec3-123">更新版本的 Visual Basic 中，不過，新語言建構例如 lambda 運算式和型別推斷讓功能性程式設計更容易且更具生產力。</span><span class="sxs-lookup"><span data-stu-id="06ec3-123">With later versions of Visual Basic, however, new language constructs such as lambda expressions and type inference make it functional programming much easier and more productive.</span></span>  
  
 <span data-ttu-id="06ec3-124">如需函式程式設計的詳細資訊，請參閱[功能性程式設計與。命令式程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="06ec3-124">For more information about functional programming, see [Functional Programming vs. Imperative Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).</span></span>  
  
#### <a name="domain-specific-fp-languages"></a><span data-ttu-id="06ec3-125">網域指定的 FP 語言</span><span class="sxs-lookup"><span data-stu-id="06ec3-125">Domain-Specific FP Languages</span></span>  
 <span data-ttu-id="06ec3-126">雖然目前尚未廣泛採用一般功能性程式設計語言，但是特定網域指定的功能性程式設計語言比較受歡迎。</span><span class="sxs-lookup"><span data-stu-id="06ec3-126">Although general functional programming languages have not been widely adopted, specific domain-specific functional programming languages have had better success.</span></span> <span data-ttu-id="06ec3-127">例如，階層式樣式表 (CSS) 用於決定許多網頁的外觀及操作，而可延伸樣式表語言轉換 (XSLT) 樣式表則廣泛用於 XML 資料操作。</span><span class="sxs-lookup"><span data-stu-id="06ec3-127">For example, Cascading Style Sheets (CSS) are used to determine the look and feel of many Web pages, and Extensible Stylesheet Language Transformations (XSLT) style sheets are used extensively in XML data manipulation.</span></span> <span data-ttu-id="06ec3-128">如需 XSLT 的詳細資訊，請參閱[XSLT 轉換](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03)。</span><span class="sxs-lookup"><span data-stu-id="06ec3-128">For more information about XSLT, see [XSLT Transformations](http://msdn.microsoft.com/library/202f8820-224c-494f-b61e-cd127eac6e03).</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="06ec3-129">用語</span><span class="sxs-lookup"><span data-stu-id="06ec3-129">Terminology</span></span>  
 <span data-ttu-id="06ec3-130">下表定義與功能性轉換相關的一些辭彙。</span><span class="sxs-lookup"><span data-stu-id="06ec3-130">The following table defines some terms related to functional transformations.</span></span>  
  
 <span data-ttu-id="06ec3-131">高順序 (第一級) 函式</span><span class="sxs-lookup"><span data-stu-id="06ec3-131">higher-order (first-class) function</span></span>  
 <span data-ttu-id="06ec3-132">可以視為程式設計物件的函式。</span><span class="sxs-lookup"><span data-stu-id="06ec3-132">A function that can be treated as a programmatic object.</span></span> <span data-ttu-id="06ec3-133">例如，高順序函式可以傳遞到其他函式，或從其他函式傳回。</span><span class="sxs-lookup"><span data-stu-id="06ec3-133">For example, a higher-order function can be passed to or returned from other functions.</span></span> <span data-ttu-id="06ec3-134">在 Visual Basic 中，委派和 lambda 運算式，都是支援高順序函式的語言功能。</span><span class="sxs-lookup"><span data-stu-id="06ec3-134">In Visual Basic, delegates and lambda expressions are language features that support higher-order functions.</span></span> <span data-ttu-id="06ec3-135">若要撰寫高順序函式，您可以宣告一或多個引數以取得委派，而且在呼叫高順序函式時，您通常可以使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="06ec3-135">To write a higher-order function, you declare one or more arguments to take delegates, and you often use lambda expressions when calling it.</span></span> <span data-ttu-id="06ec3-136">許多標準查詢運算子都是高順序函式。</span><span class="sxs-lookup"><span data-stu-id="06ec3-136">Many of the standard query operators are higher-order functions.</span></span>  
  
 <span data-ttu-id="06ec3-137">如需詳細資訊，請參閱[標準查詢運算子概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="06ec3-137">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="06ec3-138">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="06ec3-138">lambda expression</span></span>  
 <span data-ttu-id="06ec3-139">基本上，這是可用於任何需要委派型別之處的內嵌匿名函式。</span><span class="sxs-lookup"><span data-stu-id="06ec3-139">Essentially, an inline anonymous function that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="06ec3-140">這是 Lambda 運算式的簡化定義，但這適用於此教學課程的用途。</span><span class="sxs-lookup"><span data-stu-id="06ec3-140">This is a simplified definition of lambda expressions, but it is adequate for the purposes of this tutorial.</span></span>  
  
 <span data-ttu-id="06ec3-141">如需詳細資訊，請參閱[Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="06ec3-141">For more information about, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="06ec3-142">集合</span><span class="sxs-lookup"><span data-stu-id="06ec3-142">collection</span></span>  
 <span data-ttu-id="06ec3-143">一組結構化的資料，通常屬於統一的型別。</span><span class="sxs-lookup"><span data-stu-id="06ec3-143">A structured set of data, usually of a uniform type.</span></span> <span data-ttu-id="06ec3-144">若要與 LINQ 相容，集合必須實作<xref:System.Collections.IEnumerable>介面或<xref:System.Linq.IQueryable>介面 (或其泛型對應項目，其中<xref:System.Collections.Generic.IEnumerator%601>或<xref:System.Linq.IQueryable%601>)。</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerator%601> </xref:System.Linq.IQueryable> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="06ec3-144">To be compatible with LINQ, a collection must implement the <xref:System.Collections.IEnumerable> interface or the <xref:System.Linq.IQueryable> interface (or one of their generic counterparts, <xref:System.Collections.Generic.IEnumerator%601> or <xref:System.Linq.IQueryable%601>).</span></span>  
  
 <span data-ttu-id="06ec3-145">Tuple (匿名型別)</span><span class="sxs-lookup"><span data-stu-id="06ec3-145">tuple (anonymous types)</span></span>  
 <span data-ttu-id="06ec3-146">這是一個數學概念，一個 Tuple 表示一個有限的物件順序，每個都有特定的型別。</span><span class="sxs-lookup"><span data-stu-id="06ec3-146">A mathematical concept, a tuple is a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="06ec3-147">Tuple 也稱為排序清單。</span><span class="sxs-lookup"><span data-stu-id="06ec3-147">A tuple is also known as an ordered list.</span></span> <span data-ttu-id="06ec3-148">匿名型別為此概念的語言實作，可以宣告未具名的類別型別，並同時具現化該類別的物件。</span><span class="sxs-lookup"><span data-stu-id="06ec3-148">Anonymous types are a language implementation of this concept, which enable an unnamed class type to be declared and an object of that type to be instantiated at the same time.</span></span>  
  
 <span data-ttu-id="06ec3-149">如需詳細資訊，請參閱[匿名型別](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="06ec3-149">For more information, see  [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="06ec3-150">型別推斷 (隱含型別)</span><span class="sxs-lookup"><span data-stu-id="06ec3-150">type inference (implicit typing)</span></span>  
 <span data-ttu-id="06ec3-151">編譯器在沒有明確的型別宣告時，判斷變數型別的能力。</span><span class="sxs-lookup"><span data-stu-id="06ec3-151">The ability of a compiler to determine the type of a variable in the absence of an explicit type declaration.</span></span>  
  
 <span data-ttu-id="06ec3-152">如需詳細資訊，請參閱[本機的型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="06ec3-152">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="06ec3-153">延後執行與延遲評估</span><span class="sxs-lookup"><span data-stu-id="06ec3-153">deferred execution and lazy evaluation</span></span>  
 <span data-ttu-id="06ec3-154">延後運算式的評估，直到實際需要其解決的值為止。</span><span class="sxs-lookup"><span data-stu-id="06ec3-154">The delaying of evaluation of an expression until its resolved value is actually required.</span></span> <span data-ttu-id="06ec3-155">在集合中，支援延後執行。</span><span class="sxs-lookup"><span data-stu-id="06ec3-155">Deferred execution is supported in collections.</span></span>  
  
 <span data-ttu-id="06ec3-156">如需詳細資訊，請參閱[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)和[延後執行與 LINQ to XML (Visual Basic) 中的延遲評估](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="06ec3-156">For more information, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) and [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="06ec3-157">這些語言功能將用於本節的所有程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="06ec3-157">These language features will be used in code samples throughout this section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06ec3-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06ec3-158">See Also</span></span>  
 <span data-ttu-id="06ec3-159">[純功能性轉換 (Visual Basic) 簡介](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="06ec3-159">[Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
<span data-ttu-id="06ec3-160"> [函數式程式設計與命令式程式設計 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)</span><span class="sxs-lookup"><span data-stu-id="06ec3-160"> [Functional Programming vs. Imperative Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)</span></span>
