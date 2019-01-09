---
title: F# 的教學課程
description: 檢查一些 F# 程式設計語言，在此教學課程利用程式碼範例的主要功能。
ms.date: 11/06/2018
ms.openlocfilehash: 72ecb9e71e5d039f5a62f74ad594fac82269f304
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145519"
---
# <a name="tour-of-f"></a><span data-ttu-id="35723-103">F# 的教學課程</span><span class="sxs-lookup"><span data-stu-id="35723-103">Tour of F#</span></span> #

<span data-ttu-id="35723-104">若要了解 F# 的最佳方式是讀取和寫入 F# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="35723-104">The best way to learn about F# is to read and write F# code.</span></span> <span data-ttu-id="35723-105">這篇文章會做為某些 F# 語言的重要功能的逐步教學課程，並提供您一些您可以在您的電腦執行的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="35723-105">This article will act as a tour through some of the key features of the F# language and give you some code snippets that you can execute on your machine.</span></span> <span data-ttu-id="35723-106">若要了解如何設定開發環境，請參閱[開始使用](tutorials/getting-started/index.md)。</span><span class="sxs-lookup"><span data-stu-id="35723-106">To learn about setting up a development environment, check out [Getting Started](tutorials/getting-started/index.md).</span></span>

<span data-ttu-id="35723-107">F# 中有兩個主要概念： 函式和類型。</span><span class="sxs-lookup"><span data-stu-id="35723-107">There are two primary concepts in F#: functions and types.</span></span>  <span data-ttu-id="35723-108">本教學課程會強調它們屬於這兩個概念的語言功能。</span><span class="sxs-lookup"><span data-stu-id="35723-108">This tour will emphasize features of the language which fall into these two concepts.</span></span>

## <a name="executing-the-code-online"></a><span data-ttu-id="35723-109">執行線上程式碼</span><span class="sxs-lookup"><span data-stu-id="35723-109">Executing the code online</span></span>

<span data-ttu-id="35723-110">如果您沒有F#安裝在您的電腦上，您可以執行所有使用線上的範例[神鬼寓言 REPL](https://fable.io/repl/)。</span><span class="sxs-lookup"><span data-stu-id="35723-110">If you don't have F# installed on your machine, you can execute all of the samples online with the [Fable REPL](https://fable.io/repl/).</span></span> <span data-ttu-id="35723-111">神鬼寓言是方言F#直接在您的瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="35723-111">Fable is a dialect of F# that executes directly in your browser.</span></span> <span data-ttu-id="35723-112">若要檢視的範例，請遵循在 REPL 中，請參閱**範例 > 深入了解 > 教學課程F#** 神鬼寓言 REPL 的左側功能表列中</span><span class="sxs-lookup"><span data-stu-id="35723-112">To view the samples that follow in the REPL, check out **Samples > Learn > Tour of F#** in the left-hand menu bar of the Fable REPL.</span></span>

## <a name="functions-and-modules"></a><span data-ttu-id="35723-113">函式和模組</span><span class="sxs-lookup"><span data-stu-id="35723-113">Functions and Modules</span></span>

<span data-ttu-id="35723-114">任何的 F# 程式的最基本的部分是***函式***分成***模組***。</span><span class="sxs-lookup"><span data-stu-id="35723-114">The most fundamental pieces of any F# program are ***functions*** organized into ***modules***.</span></span>  <span data-ttu-id="35723-115">[函式](language-reference/functions/index.md)來產生輸出的輸入上執行的工作和其下組織[模組](language-reference/modules.md)，這是主要的方式分組在 F# 中的項目。</span><span class="sxs-lookup"><span data-stu-id="35723-115">[Functions](language-reference/functions/index.md) perform work on inputs to produce outputs, and they are organized under [Modules](language-reference/modules.md), which are the primary way you group things in F#.</span></span>  <span data-ttu-id="35723-116">它們使用來定義[`let`繫結](language-reference/functions/let-bindings.md)，其中指定函式的名稱，並定義其引數。</span><span class="sxs-lookup"><span data-stu-id="35723-116">They are defined using the [`let` binding](language-reference/functions/let-bindings.md), which give the function a name and define its arguments.</span></span>

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

<span data-ttu-id="35723-117">`let` 繫結也是您如何結合其值為名稱，類似於其他語言中的變數。</span><span class="sxs-lookup"><span data-stu-id="35723-117">`let` bindings are also how you bind a value to a name, similar to a variable in other languages.</span></span>  <span data-ttu-id="35723-118">`let` 繫結***不可變***根據預設，這表示，值或函式繫結的名稱之後, 便無法變更就地。</span><span class="sxs-lookup"><span data-stu-id="35723-118">`let` bindings are ***immutable*** by default, which means that once a value or function is bound to a name, it cannot be changed in-place.</span></span>  <span data-ttu-id="35723-119">相較之下，在其他語言中，也就是變數***可變***，這表示其值可以變更在任何時間點的時間。</span><span class="sxs-lookup"><span data-stu-id="35723-119">This is in contrast to variables in other languages, which are ***mutable***, meaning their values can be changed at any point in time.</span></span>  <span data-ttu-id="35723-120">如果您需要的可變動的繫結時，您可以使用`let mutable ...`語法。</span><span class="sxs-lookup"><span data-stu-id="35723-120">If you require a mutable binding, you can use `let mutable ...` syntax.</span></span>

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a><span data-ttu-id="35723-121">數字、 布林值和字串</span><span class="sxs-lookup"><span data-stu-id="35723-121">Numbers, Booleans, and Strings</span></span>

<span data-ttu-id="35723-122">為.NET 語言，F# 支援相同的基礎[基本型別](language-reference/primitive-types.md)存在於.NET。</span><span class="sxs-lookup"><span data-stu-id="35723-122">As a .NET language, F# supports the same underlying [primitive types](language-reference/primitive-types.md) that exist in .NET.</span></span>

<span data-ttu-id="35723-123">以下是如何各種數值類型表示 F# 中：</span><span class="sxs-lookup"><span data-stu-id="35723-123">Here is how various numeric types are represented in F#:</span></span>

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

<span data-ttu-id="35723-124">以下是布林值，並執行基本的條件式邏輯如下所示：</span><span class="sxs-lookup"><span data-stu-id="35723-124">Here's what Boolean values and performing basic conditional logic looks like:</span></span>

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

<span data-ttu-id="35723-125">以下是哪些 basic[字串](language-reference/strings.md)操作如下所示：</span><span class="sxs-lookup"><span data-stu-id="35723-125">And here's what basic [string](language-reference/strings.md) manipulation looks like:</span></span>

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a><span data-ttu-id="35723-126">Tuple</span><span class="sxs-lookup"><span data-stu-id="35723-126">Tuples</span></span>

<span data-ttu-id="35723-127">[Tuple](language-reference/tuples.md)是 F# 中是什麼大問題。</span><span class="sxs-lookup"><span data-stu-id="35723-127">[Tuples](language-reference/tuples.md) are a big deal in F#.</span></span>  <span data-ttu-id="35723-128">也就是未命名，但已排序，可以視為值本身的值的群組。</span><span class="sxs-lookup"><span data-stu-id="35723-128">They are a grouping of unnamed, but ordered values, that can be treated as values themselves.</span></span>  <span data-ttu-id="35723-129">將它們視為與其他值彙總的值。</span><span class="sxs-lookup"><span data-stu-id="35723-129">Think of them as values which are aggregated from other values.</span></span>  <span data-ttu-id="35723-130">它們有許多用途，例如方便地從函式傳回多個值，或群組的一些特定便利的值。</span><span class="sxs-lookup"><span data-stu-id="35723-130">They have many uses, such as conveniently returning multiple values from a function, or grouping values for some ad-hoc convenience.</span></span>

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

<span data-ttu-id="35723-131">自 F# 4.1，您也可以建立`struct`tuple。</span><span class="sxs-lookup"><span data-stu-id="35723-131">As of F# 4.1, you can also create `struct` tuples.</span></span>  <span data-ttu-id="35723-132">這些也與交互操作完整 C# 7/Visual Basic 15 元組，這也是`struct`tuple:</span><span class="sxs-lookup"><span data-stu-id="35723-132">These also interoperate fully with C#7/Visual Basic 15 tuples, which are also `struct` tuples:</span></span>

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

<span data-ttu-id="35723-133">請務必請注意，因為`struct`tuple 是實值型別，它們無法以隱含方式轉換成參考 tuple，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="35723-133">It's important to note that because `struct` tuples are value types, they cannot be implicitly converted to reference tuples, or vice versa.</span></span>  <span data-ttu-id="35723-134">您必須明確轉換之間的參考和結構元組。</span><span class="sxs-lookup"><span data-stu-id="35723-134">You must explicitly convert between a reference and struct tuple.</span></span>

## <a name="pipelines-and-composition"></a><span data-ttu-id="35723-135">管線和組合</span><span class="sxs-lookup"><span data-stu-id="35723-135">Pipelines and Composition</span></span>

<span data-ttu-id="35723-136">透過管道傳送這類運算子`|>`廣泛處理 F# 中的資料時。</span><span class="sxs-lookup"><span data-stu-id="35723-136">Pipe operators such as `|>` are used extensively when processing data in F#.</span></span> <span data-ttu-id="35723-137">這些運算子都可讓您以有彈性的方式建立的函式為 「 管線 」 函式。</span><span class="sxs-lookup"><span data-stu-id="35723-137">These operators are functions that allow you to establish "pipelines" of functions in a flexible manner.</span></span> <span data-ttu-id="35723-138">下列範例逐步解說如何使用這些運算子，來建置簡單的功能性管線的利用：</span><span class="sxs-lookup"><span data-stu-id="35723-138">The following example walks through how you can take advantage of these operators to build a simple functional pipeline:</span></span>

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L282)]

<span data-ttu-id="35723-139">先前所做的範例使用的許多功能的 F#，包括清單處理函式，第一級函式，並[部分的應用程式](language-reference/functions/index.md#partial-application-of-arguments)。</span><span class="sxs-lookup"><span data-stu-id="35723-139">The previous sample made use of many features of F#, including list processing functions, first-class functions, and [partial application](language-reference/functions/index.md#partial-application-of-arguments).</span></span> <span data-ttu-id="35723-140">雖然每個這些概念的深入了解可以變得有點進階，應該很清楚如何輕鬆函式可用來建立管線時，處理資料。</span><span class="sxs-lookup"><span data-stu-id="35723-140">Although a deep understanding of each of those concepts can become somewhat advanced, it should be clear how easily functions can be used to process data when building pipelines.</span></span>

## <a name="lists-arrays-and-sequences"></a><span data-ttu-id="35723-141">清單、 陣列和順序</span><span class="sxs-lookup"><span data-stu-id="35723-141">Lists, Arrays, and Sequences</span></span>

<span data-ttu-id="35723-142">清單、 陣列和順序是 F# 核心程式庫中的三種主要集合類型。</span><span class="sxs-lookup"><span data-stu-id="35723-142">Lists, Arrays, and Sequences are three primary collection types in the F# core library.</span></span>

<span data-ttu-id="35723-143">[列出](language-reference/lists.md)是相同型別的項目排序、 不可變的集合。</span><span class="sxs-lookup"><span data-stu-id="35723-143">[Lists](language-reference/lists.md) are ordered, immutable collections of elements of the same type.</span></span>  <span data-ttu-id="35723-144">它們是單一連結清單中，這表示它們用於列舉型別，但不佳的選擇為隨機存取與串連很大時。</span><span class="sxs-lookup"><span data-stu-id="35723-144">They are singly-linked lists, which means they are meant for enumeration, but a poor choice for random access and concatenation if they're large.</span></span>  <span data-ttu-id="35723-145">這相較於其他熱門的語言，通常不會使用單向連結清單來代表清單中的清單。</span><span class="sxs-lookup"><span data-stu-id="35723-145">This in contrast to Lists in other popular languages, which typically do not use a singly-linked list to represent Lists.</span></span>

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

<span data-ttu-id="35723-146">[陣列](language-reference/arrays.md)是固定大小*可變動*相同型別的元素的集合。</span><span class="sxs-lookup"><span data-stu-id="35723-146">[Arrays](language-reference/arrays.md) are fixed-size, *mutable* collections of elements of the same type.</span></span>  <span data-ttu-id="35723-147">它們支援的項目，快速隨機存取，且速度比 F# 清單因為它們只是連續記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="35723-147">They support fast random access of elements, and are faster than F# lists because they are just contiguous blocks of memory.</span></span>

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

<span data-ttu-id="35723-148">[序列](language-reference/sequences.md)是一連串的項目，相同類型的所有邏輯。</span><span class="sxs-lookup"><span data-stu-id="35723-148">[Sequences](language-reference/sequences.md) are a logical series of elements, all of the same type.</span></span>  <span data-ttu-id="35723-149">這些是較普通的類型，比清單和陣列，在任何邏輯的一系列項目您 「 檢視 」。</span><span class="sxs-lookup"><span data-stu-id="35723-149">These are a more general type than Lists and Arrays, capable of being your "view" into any logical series of elements.</span></span>  <span data-ttu-id="35723-150">它們也凸顯因為他們可***延遲***，這表示只有在需要時，您可以計算項目。</span><span class="sxs-lookup"><span data-stu-id="35723-150">They also stand out because they can be ***lazy***, which means that elements can be computed only when they are needed.</span></span>

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a><span data-ttu-id="35723-151">遞迴函式</span><span class="sxs-lookup"><span data-stu-id="35723-151">Recursive Functions</span></span>

<span data-ttu-id="35723-152">處理集合或序列的項目通常是使用[遞迴](language-reference/functions/index.md#recursive-functions)F# 中。</span><span class="sxs-lookup"><span data-stu-id="35723-152">Processing collections or sequences of elements is typically done with [recursion](language-reference/functions/index.md#recursive-functions) in F#.</span></span>  <span data-ttu-id="35723-153">雖然 F# 提供 for 迴圈和命令式程式設計的支援，但遞迴建議，因為很容易就能保證正確性。</span><span class="sxs-lookup"><span data-stu-id="35723-153">Although F# has support for loops and imperative programming, recursion is preferred because it is easier to guarantee correctness.</span></span>

> [!NOTE]
> <span data-ttu-id="35723-154">下列範例會使用透過模式比對`match`運算式。</span><span class="sxs-lookup"><span data-stu-id="35723-154">The following example makes use of the pattern matching via the `match` expression.</span></span>  <span data-ttu-id="35723-155">本文章稍候會說明這個基本建構。</span><span class="sxs-lookup"><span data-stu-id="35723-155">This fundamental construct is covered later in this article.</span></span>

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

<span data-ttu-id="35723-156">F# 也有完整支援 Tail 呼叫最佳化，這是一種最佳化，使其只是最快的速度迴圈建構的遞迴呼叫。</span><span class="sxs-lookup"><span data-stu-id="35723-156">F# also has full support for Tail Call Optimization, which is a way to optimize recursive calls so that they are just as fast as a loop construct.</span></span>

## <a name="record-and-discriminated-union-types"></a><span data-ttu-id="35723-157">記錄和差別聯集類型</span><span class="sxs-lookup"><span data-stu-id="35723-157">Record and Discriminated Union Types</span></span>

<span data-ttu-id="35723-158">記錄和等位型別中 F# 程式碼，使用兩種基本資料類型，通常的最佳方式來表示 F# 程式中的資料。</span><span class="sxs-lookup"><span data-stu-id="35723-158">Record and Union types are two fundamental data types used in F# code, and are generally the best way to represent data in an F# program.</span></span>  <span data-ttu-id="35723-159">雖然這可讓它們與類別類似其他語言中，其主要差異是它們具有結構相等語意。</span><span class="sxs-lookup"><span data-stu-id="35723-159">Although this makes them similar to classes in other languages, one of their primary differences is that they have structural equality semantics.</span></span>  <span data-ttu-id="35723-160">也就是說，它們是 「 原生 」 比較，相等相當簡單： 只檢查其中一個是否等於其他。</span><span class="sxs-lookup"><span data-stu-id="35723-160">This means that they are "natively" comparable and equality is straightforward - just check if one is equal to the other.</span></span>

<span data-ttu-id="35723-161">[記錄](language-reference/records.md)會與選擇性成員 （例如方法） 的具名值的彙總。</span><span class="sxs-lookup"><span data-stu-id="35723-161">[Records](language-reference/records.md) are an aggregate of named values, with optional members (such as methods).</span></span>  <span data-ttu-id="35723-162">如果您熟悉使用 C# 或 Java，然後這些應該感覺很像 Poco 或 Pojo-只與結構相等，並降低繁瑣細節。</span><span class="sxs-lookup"><span data-stu-id="35723-162">If you're familiar with C# or Java, then these should feel similar to POCOs or POJOs - just with structural equality and less ceremony.</span></span>

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

<span data-ttu-id="35723-163">自 F# 4.1，您也可以代表記錄當做`struct`s。</span><span class="sxs-lookup"><span data-stu-id="35723-163">As of F# 4.1, you can also represent Records as `struct`s.</span></span>  <span data-ttu-id="35723-164">做法是使用`[<Struct>]`屬性：</span><span class="sxs-lookup"><span data-stu-id="35723-164">This is done with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

<span data-ttu-id="35723-165">[差別聯集 (DUs)](language-reference/discriminated-unions.md)是可能在多個具名的表單或案例的值。</span><span class="sxs-lookup"><span data-stu-id="35723-165">[Discriminated Unions (DUs)](language-reference/discriminated-unions.md) are values which could be a number of named forms or cases.</span></span>  <span data-ttu-id="35723-166">類型中儲存的資料可以是數個相異值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="35723-166">Data stored in the type can be one of several distinct values.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

<span data-ttu-id="35723-167">您也可以使用為 DUs*單一案例差別聯集*，以協助進行基本類型的模型化的網域。</span><span class="sxs-lookup"><span data-stu-id="35723-167">You can also use DUs as *Single-Case Discriminated Unions*, to help with domain modeling over primitive types.</span></span>  <span data-ttu-id="35723-168">經常、 字串和其他基本型別用來代表項目，並因此會提供特定的意義。</span><span class="sxs-lookup"><span data-stu-id="35723-168">Often times, strings and other primitive types are used to represent something, and are thus given a particular meaning.</span></span>  <span data-ttu-id="35723-169">不過，使用資料的基本表示法可能會導致錯誤地指派值不正確 ！</span><span class="sxs-lookup"><span data-stu-id="35723-169">However, using only the primitive representation of the data can result in mistakenly assigning an incorrect value!</span></span>  <span data-ttu-id="35723-170">代表每一個不同的單一案例聯集的資訊類型，可以強制執行在此案例中的正確性。</span><span class="sxs-lookup"><span data-stu-id="35723-170">Representing each type of information as a distinct single-case union can enforce correctness in this scenario.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

<span data-ttu-id="35723-171">如上述範例所示，若要取得基礎值的單一案例差別聯集，您必須明確 unwrap。</span><span class="sxs-lookup"><span data-stu-id="35723-171">As the above sample demonstrates, to get the underlying value in a single-case Discriminated Union, you must explicitly unwrap it.</span></span>

<span data-ttu-id="35723-172">此外，DUs 也支援遞迴定義，可讓您輕鬆地代表樹狀結構和原本就是遞迴的資料。</span><span class="sxs-lookup"><span data-stu-id="35723-172">Additionally, DUs also support recursive definitions, allowing you to easily represent trees and inherently recursive data.</span></span>  <span data-ttu-id="35723-173">例如，以下是可以代表使用二進位搜尋樹狀結構的方式`exists`和`insert`函式。</span><span class="sxs-lookup"><span data-stu-id="35723-173">For example, here's how you can represent a Binary Search Tree with `exists` and `insert` functions.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

<span data-ttu-id="35723-174">DUs 可讓您代表遞迴結構的樹狀目錄中的資料類型，因為此遞迴結構上操作很簡單，可確保正確性。</span><span class="sxs-lookup"><span data-stu-id="35723-174">Because DUs allow you to represent the recursive structure of the tree in the data type, operating on this recursive structure is straightforward and guarantees correctness.</span></span>  <span data-ttu-id="35723-175">它也支援在模式比對，如下所示。</span><span class="sxs-lookup"><span data-stu-id="35723-175">It is also supported in pattern matching, as shown below.</span></span>

<span data-ttu-id="35723-176">此外，您可以在這裡表示為 DUs`struct`與`[<Struct>]`屬性：</span><span class="sxs-lookup"><span data-stu-id="35723-176">Additionally, you can represent DUs as `struct`s with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

<span data-ttu-id="35723-177">不過，有兩個要這麼做時，牢記在心的重要事項：</span><span class="sxs-lookup"><span data-stu-id="35723-177">However, there are two key things to keep in mind when doing so:</span></span>

1. <span data-ttu-id="35723-178">結構 DU 不得以遞迴方式定義。</span><span class="sxs-lookup"><span data-stu-id="35723-178">A struct DU cannot be recursively-defined.</span></span>
2. <span data-ttu-id="35723-179">結構 DU 必須有它的情況下的每個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="35723-179">A struct DU must have unique names for each of its cases.</span></span>

<span data-ttu-id="35723-180">遵循上述的失敗會導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="35723-180">Failure to follow the above will result in a compilation error.</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="35723-181">模式比對</span><span class="sxs-lookup"><span data-stu-id="35723-181">Pattern Matching</span></span>

<span data-ttu-id="35723-182">[模式比對](language-reference/pattern-matching.md)是 F# 語言功能，可讓 F# 類型上操作的正確性。</span><span class="sxs-lookup"><span data-stu-id="35723-182">[Pattern Matching](language-reference/pattern-matching.md) is the F# language feature which enables correctness for operating on F# types.</span></span>  <span data-ttu-id="35723-183">在上述範例中，您可能已經注意到一堆`match x with ...`語法。</span><span class="sxs-lookup"><span data-stu-id="35723-183">In the above samples, you probably noticed quite a bit of `match x with ...` syntax.</span></span>  <span data-ttu-id="35723-184">此建構可讓編譯器，這可以了解資料類型，若要強制您處理所有可能的情況下，使用透過已知的資料類型為詳盡的模式比對時的 「 形狀 」。</span><span class="sxs-lookup"><span data-stu-id="35723-184">This construct allows the compiler, which can understand the "shape" of data types, to force you to account for all possible cases when using a data type through what is known as Exhaustive Pattern Matching.</span></span>  <span data-ttu-id="35723-185">這是非常強大的正確性，並可以巧妙地用來 「 上移 」 項目通常會為編譯時間是執行階段問題。</span><span class="sxs-lookup"><span data-stu-id="35723-185">This is incredibly powerful for correctness, and can be cleverly used to "lift" what would normally be a runtime concern into compile-time.</span></span>

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L742)]

<span data-ttu-id="35723-186">您也可以使用速記`function`建構用於模式比對，這非常有用，當您撰寫函式，請使用[部分的應用程式](language-reference/functions/index.md#partial-application-of-arguments):</span><span class="sxs-lookup"><span data-stu-id="35723-186">You can also use the shorthand `function` construct for pattern matching, which is useful when you're writing functions which make use of [Partial Application](language-reference/functions/index.md#partial-application-of-arguments):</span></span>

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L744-L762)]

<span data-ttu-id="35723-187">您可能已經發現的項目，就是使用`_`模式。</span><span class="sxs-lookup"><span data-stu-id="35723-187">Something you may have noticed is the use of the `_` pattern.</span></span>  <span data-ttu-id="35723-188">這就所謂[萬用字元模式](language-reference/pattern-matching.md#wildcard-pattern)，這是一種說: 「 我不用管事物 」。</span><span class="sxs-lookup"><span data-stu-id="35723-188">This is known as the [Wildcard Pattern](language-reference/pattern-matching.md#wildcard-pattern), which is a way of saying "I don't care what something is".</span></span>  <span data-ttu-id="35723-189">雖然很方便，您可以不小心略過詳盡的模式比對，如果您不小心使用，不會再受益編譯時期強制`_`。</span><span class="sxs-lookup"><span data-stu-id="35723-189">Although convenient, you can accidentally bypass Exhaustive Pattern Matching and no longer benefit from compile-time enforcements if you aren't careful in using `_`.</span></span>  <span data-ttu-id="35723-190">它最適合在您不在意特定資訊的分解的型別已列舉所有有意義的情況下的模式比對運算式時，當模式比對或最後一個子句。</span><span class="sxs-lookup"><span data-stu-id="35723-190">It is best used when you don't care about certain pieces of a decomposed type when pattern matching, or the final clause when you have enumerated all meaningful cases in a pattern matching expression.</span></span>

<span data-ttu-id="35723-191">[作用中的模式](language-reference/active-patterns.md)是另一個功能強大的建構函式來使用模式比對。</span><span class="sxs-lookup"><span data-stu-id="35723-191">[Active Patterns](language-reference/active-patterns.md) are another powerful construct to use with pattern matching.</span></span>  <span data-ttu-id="35723-192">可讓您輸入的資料分割成自訂的表單，將它們分解在模式比對呼叫站台。</span><span class="sxs-lookup"><span data-stu-id="35723-192">They allow you to partition input data into custom forms, decomposing them at the pattern match call site.</span></span>  <span data-ttu-id="35723-193">它們可以也進行參數化，因此資料分割定義為函式。</span><span class="sxs-lookup"><span data-stu-id="35723-193">They can also be parameterized, thus allowing to define the partition as a function.</span></span>  <span data-ttu-id="35723-194">展開上一個範例是為了支援作用中的模式看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="35723-194">Expanding the previous example to support Active Patterns looks something like this:</span></span>

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a><span data-ttu-id="35723-195">選擇性的類型</span><span class="sxs-lookup"><span data-stu-id="35723-195">Optional Types</span></span>

<span data-ttu-id="35723-196">差別聯集類型的其中一個特殊案例是選項類型，這很有用，它是 F# 核心程式庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="35723-196">One special case of Discriminated Union types is the Option Type, which is so useful that it's a part of the F# core library.</span></span>

<span data-ttu-id="35723-197">[選項類型](language-reference/options.md)是型別代表兩個案例之一： 某個值，或在所有執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="35723-197">[The Option Type](language-reference/options.md) is a type which represents one of two cases: a value, or nothing at all.</span></span>  <span data-ttu-id="35723-198">它可在任何案例中，值可能會或可能不會造成從特定作業。</span><span class="sxs-lookup"><span data-stu-id="35723-198">It is used in any scenario where a value may or may not result from a particular operation.</span></span>  <span data-ttu-id="35723-199">這會強制您處理這兩種情況，因此編譯時間需要考量，而不是執行階段問題。</span><span class="sxs-lookup"><span data-stu-id="35723-199">This then forces you to account for both cases, making it a compile-time concern rather than a runtime concern.</span></span>  <span data-ttu-id="35723-200">這些通常在 Api 中使用其中`null`用來表示"nothing"相反的而無需擔心`NullReferenceException`在許多情況下。</span><span class="sxs-lookup"><span data-stu-id="35723-200">These are often used in APIs where `null` is used to represent "nothing" instead, thus eliminating the need to worry about `NullReferenceException` in many circumstances.</span></span>

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a><span data-ttu-id="35723-201">測量單位</span><span class="sxs-lookup"><span data-stu-id="35723-201">Units of Measure</span></span>

<span data-ttu-id="35723-202">F# 型別系統的一項獨特功能是能夠透過單位的量值的數值常值的提供內容。</span><span class="sxs-lookup"><span data-stu-id="35723-202">One unique feature of F#'s type system is the ability to provide context for numeric literals through Units of Measure.</span></span>

<span data-ttu-id="35723-203">[測量單位](language-reference/units-of-measure.md)可讓您建立一個單位，計量，例如數值類型的關聯，並有函式上執行的工作單位，而不是數值常值。</span><span class="sxs-lookup"><span data-stu-id="35723-203">[Units of Measure](language-reference/units-of-measure.md) allow you to associate a numeric type to a unit, such as Meters, and have functions perform work on units rather than numeric literals.</span></span>  <span data-ttu-id="35723-204">這可讓編譯器無法驗證傳入的數值常值的類型在某些環境下合理，因此減少執行階段錯誤相關聯的工作，該類型。</span><span class="sxs-lookup"><span data-stu-id="35723-204">This enables the compiler to verify that the types of numeric literals passed in make sense under a certain context, thus eliminating runtime errors associated with that kind of work.</span></span>

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L817-L842)]

<span data-ttu-id="35723-205">F# 核心程式庫會定義許多的 SI 單位類型和單位轉換。</span><span class="sxs-lookup"><span data-stu-id="35723-205">The F# Core library defines many SI unit types and unit conversions.</span></span>  <span data-ttu-id="35723-206">若要進一步了解，請參閱[Microsoft.FSharp.Data.UnitSystems.SI 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="35723-206">To learn more, check out the [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).</span></span>

## <a name="classes-and-interfaces"></a><span data-ttu-id="35723-207">類別和介面</span><span class="sxs-lookup"><span data-stu-id="35723-207">Classes and Interfaces</span></span>

<span data-ttu-id="35723-208">F# 也有完整的支援，.NET 類別[介面](language-reference/interfaces.md)，[抽象類別](language-reference/abstract-classes.md)，[繼承](language-reference/inheritance.md)，依此類推。</span><span class="sxs-lookup"><span data-stu-id="35723-208">F# also has full support for .NET classes, [Interfaces](language-reference/interfaces.md), [Abstract Classes](language-reference/abstract-classes.md), [Inheritance](language-reference/inheritance.md), and so on.</span></span>

<span data-ttu-id="35723-209">[類別](language-reference/classes.md)是.NET 物件，表示型別且可以包含屬性、 方法和事件中的當做其[成員](language-reference/members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="35723-209">[Classes](language-reference/classes.md) are types that represent .NET objects, which can have properties, methods, and events as its [Members](language-reference/members/index.md).</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L845-L880)]

<span data-ttu-id="35723-210">定義泛型類別也是非常簡單。</span><span class="sxs-lookup"><span data-stu-id="35723-210">Defining generic classes is also very straightforward.</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L883-L908)]

<span data-ttu-id="35723-211">若要實作的介面，您可以使用`interface ... with`語法或[物件運算式](language-reference/object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="35723-211">To implement an Interface, you can use either `interface ... with` syntax or an [Object Expression](language-reference/object-expressions.md).</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a><span data-ttu-id="35723-212">若要使用哪些類型</span><span class="sxs-lookup"><span data-stu-id="35723-212">Which Types to Use</span></span>

<span data-ttu-id="35723-213">類別、 記錄、 差別聯集和 Tuple 的存在會產生重要的問題： 您應該使用？</span><span class="sxs-lookup"><span data-stu-id="35723-213">The presence of Classes, Records, Discriminated Unions, and Tuples leads to an important question: which should you use?</span></span>  <span data-ttu-id="35723-214">大部分所有項目在生活中，例如答案需視您的情況。</span><span class="sxs-lookup"><span data-stu-id="35723-214">Like most everything in life, the answer depends on your circumstances.</span></span>

<span data-ttu-id="35723-215">Tuple 是適用於從函式傳回多個值，以及使用特定彙總的值做為值本身。</span><span class="sxs-lookup"><span data-stu-id="35723-215">Tuples are great for returning multiple values from a function, and using an ad-hoc aggregate of values as a value itself.</span></span>

<span data-ttu-id="35723-216">記錄會 「 步驟向上 」 的標籤和支援選擇性的成員具有名為的 Tuple。</span><span class="sxs-lookup"><span data-stu-id="35723-216">Records are a "step up" from Tuples, having named labels and support for optional members.</span></span>  <span data-ttu-id="35723-217">它們是適合用來傳輸資料到您的程式的低儀式表示法。</span><span class="sxs-lookup"><span data-stu-id="35723-217">They are great for a low-ceremony representation of data in-transit through your program.</span></span>  <span data-ttu-id="35723-218">他們有結構相等，因為它們是容易使用的比較。</span><span class="sxs-lookup"><span data-stu-id="35723-218">Because they have structural equality, they are easy to use with comparison.</span></span>

<span data-ttu-id="35723-219">差別聯的集有許多用途，但核心優勢能夠使用它們搭配模式比對來處理所有可能 「 圖形 」 可以有資料。</span><span class="sxs-lookup"><span data-stu-id="35723-219">Discriminated Unions have many uses, but the core benefit is to be able to utilize them in conjunction with Pattern Matching to account for all possible "shapes" that a data can have.</span></span>  

<span data-ttu-id="35723-220">類別是適合大量的原因，例如當您需要代表資訊也將繫結該功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="35723-220">Classes are great for a huge number of reasons, such as when you need to represent information and also tie that information to functionality.</span></span>  <span data-ttu-id="35723-221">根據經驗法則，當您有功能可在概念上會繫結至一些資料，使用類別和物件導向程式設計的原則是一大優點。</span><span class="sxs-lookup"><span data-stu-id="35723-221">As a rule of thumb, when you have functionality which is conceptually tied to some data, using Classes and the principles of Object-Oriented Programming is a big benefit.</span></span>  <span data-ttu-id="35723-222">類別也會慣用的資料型別時使用 C# 和 Visual Basic 中，因為這些語言的幾乎所有的作業使用類別。</span><span class="sxs-lookup"><span data-stu-id="35723-222">Classes are also the preferred data type when interoperating with C# and Visual Basic, as these languages use classes for nearly everything.</span></span>

## <a name="next-steps"></a><span data-ttu-id="35723-223">後續步驟</span><span class="sxs-lookup"><span data-stu-id="35723-223">Next Steps</span></span>

<span data-ttu-id="35723-224">既然您已了解的一些主要功能的語言，您應該準備好開始撰寫第一個 F# 程式 ！</span><span class="sxs-lookup"><span data-stu-id="35723-224">Now that you've seen some of the primary features of the language, you should be ready to write your first F# programs!</span></span>  <span data-ttu-id="35723-225">請參閱[開始使用](tutorials/getting-started/index.md)以了解如何設定開發環境，並撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="35723-225">Check out [Getting Started](tutorials/getting-started/index.md) to learn how to set up your development environment and write some code.</span></span>

<span data-ttu-id="35723-226">深入了下的一步可以是任何您喜歡，但我們建議您[中的功能性程式設計簡介F#](introduction-to-functional-programming/index.md)熟悉核心功能性程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="35723-226">The next steps for learning more can be whatever you like, but we recommend [Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md) to get comfortable with core Functional Programming concepts.</span></span>  <span data-ttu-id="35723-227">這些會在建置強固的程式，在 F# 不可或缺。</span><span class="sxs-lookup"><span data-stu-id="35723-227">These will be essential in building robust programs in F#.</span></span>

<span data-ttu-id="35723-228">此外，請參閱[F# 語言參考](language-reference/index.md)在 F# 中看到完整的概念性內容。</span><span class="sxs-lookup"><span data-stu-id="35723-228">Also, check out the [F# Language Reference](language-reference/index.md) to see a comprehensive collection of conceptual content on F#.</span></span>
