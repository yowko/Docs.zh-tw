---
title: 概念和術語 (功能性轉換) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: 763321d99edf404ee17e8ec29af5424a378f83b1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046599"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a><span data-ttu-id="a93aa-102">概念和術語 (功能性轉換) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a93aa-102">Concepts and Terminology (Functional Transformation) (Visual Basic)</span></span>
<span data-ttu-id="a93aa-103">本主題說明純功能性轉換的概念與術語。</span><span class="sxs-lookup"><span data-stu-id="a93aa-103">This topic introduces the concepts and terminology of pure functional transformations.</span></span> <span data-ttu-id="a93aa-104">轉換資料的功能性轉換方法所產生的程式碼通常比更傳統的命令性程式設計可以更快速地進行程式設計、更明確，而且更容易進行偵錯與維護。</span><span class="sxs-lookup"><span data-stu-id="a93aa-104">The functional transformation approach to transforming data yields code that is often quicker to program, more expressive, and easier to debug and maintain than more traditional, imperative programming.</span></span>

<span data-ttu-id="a93aa-105">請注意，本節中的主題用意不在於完整說明功能性程式設計。</span><span class="sxs-lookup"><span data-stu-id="a93aa-105">Note that the topics in this section are not intended to fully explain functional programming.</span></span> <span data-ttu-id="a93aa-106">而在於識別更容易將 XML 從一個組織結構轉換為另一個組織結構的某些功能性程式設計能力。</span><span class="sxs-lookup"><span data-stu-id="a93aa-106">Instead, these topics identify some of the functional programming capabilities that make it easier to transform XML from one shape to another.</span></span>

## <a name="what-is-pure-functional-transformation"></a><span data-ttu-id="a93aa-107">何謂純功能性轉換？</span><span class="sxs-lookup"><span data-stu-id="a93aa-107">What Is Pure Functional Transformation?</span></span>

<span data-ttu-id="a93aa-108">在「純功能性轉換」中，一組稱為「純虛擬函式」的函式會定義如何將一組結構化的資料從其原始格式轉換為另一個格式。</span><span class="sxs-lookup"><span data-stu-id="a93aa-108">In *pure functional transformation*, a set of functions, called *pure functions*, define how to transform a set of structured data from its original form into another form.</span></span> <span data-ttu-id="a93aa-109">「純」這個字表示這些函式是「可組合的」也就是說，這些函式需要是：</span><span class="sxs-lookup"><span data-stu-id="a93aa-109">The word "pure" indicates that the functions are *composable*, which requires that they are:</span></span>

- <span data-ttu-id="a93aa-110">「獨立的」，讓這些函式可以自由排列與重新整理，而不會與程式的其餘部分有任何牽連或互相依賴。</span><span class="sxs-lookup"><span data-stu-id="a93aa-110">*Self-contained*, so that they can be freely ordered and rearranged without entanglement or interdependencies with the rest of the program.</span></span> <span data-ttu-id="a93aa-111">純轉換與其環境無關，也不會影響其環境。</span><span class="sxs-lookup"><span data-stu-id="a93aa-111">Pure transformations have no knowledge of or effect upon their environment.</span></span> <span data-ttu-id="a93aa-112">也就是說，用於轉換的函式沒有「副作用」。</span><span class="sxs-lookup"><span data-stu-id="a93aa-112">That is, the functions used in the transformation have no *side effects*.</span></span>

- <span data-ttu-id="a93aa-113">「無狀態」，如此一來，在相同的輸入上執行相同的函式或特定一組函式時，永遠會導致相同的輸出。</span><span class="sxs-lookup"><span data-stu-id="a93aa-113">*Stateless*, so that executing the same function or specific set of functions on the same input will always result in the same output.</span></span> <span data-ttu-id="a93aa-114">純轉換絲毫不會記得其先前的用途。</span><span class="sxs-lookup"><span data-stu-id="a93aa-114">Pure transformations have no memory of their prior use.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a93aa-115">在本教學課程的其餘部分，「純虛擬函式」這個名詞用於一般含意，表示程式設計方法而非特定的語言功能。</span><span class="sxs-lookup"><span data-stu-id="a93aa-115">In the rest of this tutorial, the term "pure function" is used in a general sense to indicate a programming approach, and not a specific language feature.</span></span>
>
> <span data-ttu-id="a93aa-116">請注意, 純虛擬函式必須實作為 Visual Basic 中的函式。</span><span class="sxs-lookup"><span data-stu-id="a93aa-116">Note that pure functions must be implemented as functions in Visual Basic.</span></span>
>
> <span data-ttu-id="a93aa-117">同時，您不應將純虛擬函式誤解為 C++ 的純虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="a93aa-117">Also, you should not confuse pure functions with pure virtual methods in C++.</span></span> <span data-ttu-id="a93aa-118">後者表示包含的類別是抽象的，而且不會提供任何方法主體。</span><span class="sxs-lookup"><span data-stu-id="a93aa-118">The latter indicates that the containing class is abstract and that no method body is supplied.</span></span>

### <a name="functional-programming"></a><span data-ttu-id="a93aa-119">功能性程式設計</span><span class="sxs-lookup"><span data-stu-id="a93aa-119">Functional Programming</span></span>

<span data-ttu-id="a93aa-120">「函式程式設計」是一種程式設計方法，可直接支援純功能性轉換。</span><span class="sxs-lookup"><span data-stu-id="a93aa-120">*Functional programming* is a programming approach that directly supports pure functional transformation.</span></span>

<span data-ttu-id="a93aa-121">根據過去的經驗，一般用途的函式程式設計語言 (例如，ML、Scheme、Haskell 與 F#) 主要受到學術團體的注意。</span><span class="sxs-lookup"><span data-stu-id="a93aa-121">Historically, general-purpose functional programming languages, such as ML, Scheme, Haskell, and F#, have been primarily of interest to the academic community.</span></span> <span data-ttu-id="a93aa-122">雖然永遠都可以在 Visual Basic 中撰寫純功能性轉換, 但是這麼做的困難並不是大多數程式設計人員都可以選擇使用。</span><span class="sxs-lookup"><span data-stu-id="a93aa-122">Although it has always been possible to write pure functional transformations in Visual Basic, the difficulty of doing so has not made it an attractive option to most programmers.</span></span> <span data-ttu-id="a93aa-123">不過, 在較新的 Visual Basic 版本中, lambda 運算式和型別推斷之類的新語言結構讓 it 功能的程式設計更容易且更具生產力。</span><span class="sxs-lookup"><span data-stu-id="a93aa-123">With later versions of Visual Basic, however, new language constructs such as lambda expressions and type inference make it functional programming much easier and more productive.</span></span>

<span data-ttu-id="a93aa-124">如需功能性程式設計的詳細資訊，請參閱[功能性程式設計與命令式程式設計 (Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md))。</span><span class="sxs-lookup"><span data-stu-id="a93aa-124">For more information about functional programming, see [Functional Programming vs. Imperative Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).</span></span>

#### <a name="domain-specific-fp-languages"></a><span data-ttu-id="a93aa-125">網域指定的 FP 語言</span><span class="sxs-lookup"><span data-stu-id="a93aa-125">Domain-Specific FP Languages</span></span>

<span data-ttu-id="a93aa-126">雖然目前尚未廣泛採用一般功能性程式設計語言，但是特定網域指定的功能性程式設計語言比較受歡迎。</span><span class="sxs-lookup"><span data-stu-id="a93aa-126">Although general functional programming languages have not been widely adopted, specific domain-specific functional programming languages have had better success.</span></span> <span data-ttu-id="a93aa-127">例如，階層式樣式表 (CSS) 用於決定許多網頁的外觀及操作，而可延伸樣式表語言轉換 (XSLT) 樣式表則廣泛用於 XML 資料操作。</span><span class="sxs-lookup"><span data-stu-id="a93aa-127">For example, Cascading Style Sheets (CSS) are used to determine the look and feel of many Web pages, and Extensible Stylesheet Language Transformations (XSLT) style sheets are used extensively in XML data manipulation.</span></span> <span data-ttu-id="a93aa-128">如需 XSLT 的詳細資訊，請參閱 [XSLT 轉換](../../../../standard/data/xml/xslt-transformations.md)。</span><span class="sxs-lookup"><span data-stu-id="a93aa-128">For more information about XSLT, see [XSLT Transformations](../../../../standard/data/xml/xslt-transformations.md).</span></span>

## <a name="terminology"></a><span data-ttu-id="a93aa-129">用語</span><span class="sxs-lookup"><span data-stu-id="a93aa-129">Terminology</span></span>

<span data-ttu-id="a93aa-130">下表定義與功能性轉換相關的一些辭彙。</span><span class="sxs-lookup"><span data-stu-id="a93aa-130">The following table defines some terms related to functional transformations.</span></span>

<span data-ttu-id="a93aa-131">較高順序 (第一類別) 函數 </span><span class="sxs-lookup"><span data-stu-id="a93aa-131">higher-order (first-class) function </span></span>\
<span data-ttu-id="a93aa-132">可以視為程式設計物件的函式。</span><span class="sxs-lookup"><span data-stu-id="a93aa-132">A function that can be treated as a programmatic object.</span></span> <span data-ttu-id="a93aa-133">例如，高順序函式可以傳遞到其他函式，或從其他函式傳回。</span><span class="sxs-lookup"><span data-stu-id="a93aa-133">For example, a higher-order function can be passed to or returned from other functions.</span></span> <span data-ttu-id="a93aa-134">在 Visual Basic 中, 委派和 lambda 運算式都是支援高順序函式的語言功能。</span><span class="sxs-lookup"><span data-stu-id="a93aa-134">In Visual Basic, delegates and lambda expressions are language features that support higher-order functions.</span></span> <span data-ttu-id="a93aa-135">若要撰寫高順序函式，您可以宣告一或多個引數以取得委派，而且在呼叫高順序函式時，您通常可以使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="a93aa-135">To write a higher-order function, you declare one or more arguments to take delegates, and you often use lambda expressions when calling it.</span></span> <span data-ttu-id="a93aa-136">許多標準查詢運算子都是高順序函式。</span><span class="sxs-lookup"><span data-stu-id="a93aa-136">Many of the standard query operators are higher-order functions.</span></span>

<span data-ttu-id="a93aa-137">如需詳細資訊, 請參閱[標準查詢運算子總覽 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a93aa-137">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="a93aa-138">lambda 運算式 </span><span class="sxs-lookup"><span data-stu-id="a93aa-138">lambda expression </span></span>\
<span data-ttu-id="a93aa-139">基本上，這是可用於任何需要委派型別之處的內嵌匿名函式。</span><span class="sxs-lookup"><span data-stu-id="a93aa-139">Essentially, an inline anonymous function that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="a93aa-140">這是 Lambda 運算式的簡化定義，但這適用於此教學課程的用途。</span><span class="sxs-lookup"><span data-stu-id="a93aa-140">This is a simplified definition of lambda expressions, but it is adequate for the purposes of this tutorial.</span></span>

<span data-ttu-id="a93aa-141">如需詳細資訊，請參閱 [Lambda 運算式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a93aa-141">For more information about, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

<span data-ttu-id="a93aa-142">集合</span><span class="sxs-lookup"><span data-stu-id="a93aa-142">collection \</span></span>
<span data-ttu-id="a93aa-143">一組結構化的資料，通常屬於統一的型別。</span><span class="sxs-lookup"><span data-stu-id="a93aa-143">A structured set of data, usually of a uniform type.</span></span> <span data-ttu-id="a93aa-144">為與 LINQ 相容，集合必須實作 <xref:System.Collections.IEnumerable> 介面或 <xref:System.Linq.IQueryable> 介面 (或以下其中一個泛型對應項目：<xref:System.Collections.Generic.IEnumerator%601> 或 <xref:System.Linq.IQueryable%601>)。</span><span class="sxs-lookup"><span data-stu-id="a93aa-144">To be compatible with LINQ, a collection must implement the <xref:System.Collections.IEnumerable> interface or the <xref:System.Linq.IQueryable> interface (or one of their generic counterparts, <xref:System.Collections.Generic.IEnumerator%601> or <xref:System.Linq.IQueryable%601>).</span></span>

<span data-ttu-id="a93aa-145">元組 (匿名型別) </span><span class="sxs-lookup"><span data-stu-id="a93aa-145">tuple (anonymous types) </span></span>\
<span data-ttu-id="a93aa-146">這是一個數學概念，一個 Tuple 表示一個有限的物件順序，每個都有特定的型別。</span><span class="sxs-lookup"><span data-stu-id="a93aa-146">A mathematical concept, a tuple is a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="a93aa-147">Tuple 也稱為排序清單。</span><span class="sxs-lookup"><span data-stu-id="a93aa-147">A tuple is also known as an ordered list.</span></span> <span data-ttu-id="a93aa-148">匿名型別為此概念的語言實作，可以宣告未具名的類別型別，並同時具現化該類別的物件。</span><span class="sxs-lookup"><span data-stu-id="a93aa-148">Anonymous types are a language implementation of this concept, which enable an unnamed class type to be declared and an object of that type to be instantiated at the same time.</span></span>

<span data-ttu-id="a93aa-149">如需詳細資訊, 請參閱[匿名](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)型別。</span><span class="sxs-lookup"><span data-stu-id="a93aa-149">For more information, see  [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

<span data-ttu-id="a93aa-150">型別推斷 (隱含類型) </span><span class="sxs-lookup"><span data-stu-id="a93aa-150">type inference (implicit typing) </span></span>\
<span data-ttu-id="a93aa-151">編譯器在沒有明確的型別宣告時，判斷變數型別的能力。</span><span class="sxs-lookup"><span data-stu-id="a93aa-151">The ability of a compiler to determine the type of a variable in the absence of an explicit type declaration.</span></span>

<span data-ttu-id="a93aa-152">如需詳細資訊, 請參閱[區欄位型別推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。</span><span class="sxs-lookup"><span data-stu-id="a93aa-152">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="a93aa-153">延後執行和延遲評估 </span><span class="sxs-lookup"><span data-stu-id="a93aa-153">deferred execution and lazy evaluation </span></span>\
<span data-ttu-id="a93aa-154">延後運算式的評估，直到實際需要其解決的值為止。</span><span class="sxs-lookup"><span data-stu-id="a93aa-154">The delaying of evaluation of an expression until its resolved value is actually required.</span></span> <span data-ttu-id="a93aa-155">在集合中，支援延後執行。</span><span class="sxs-lookup"><span data-stu-id="a93aa-155">Deferred execution is supported in collections.</span></span>

<span data-ttu-id="a93aa-156">如需詳細資訊, 請參閱[LINQ to XML (Visual Basic) 中的](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)[基本查詢作業 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)和延後執行和延遲評估。</span><span class="sxs-lookup"><span data-stu-id="a93aa-156">For more information, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) and [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="a93aa-157">這些語言功能將用於本節的所有程式碼範例中。</span><span class="sxs-lookup"><span data-stu-id="a93aa-157">These language features will be used in code samples throughout this section.</span></span>

## <a name="see-also"></a><span data-ttu-id="a93aa-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a93aa-158">See also</span></span>

- [<span data-ttu-id="a93aa-159">純功能性轉換簡介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a93aa-159">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="a93aa-160">函數式程式設計與命令式程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a93aa-160">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
