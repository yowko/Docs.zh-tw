---
title: 'F # 教學課程'
description: '檢查部份 F # 程式語言中的程式碼範例使用此教學課程的主要功能。'
ms.date: 02/28/2018
ms.openlocfilehash: 2ce251b90d5c202996e0b1673e8f7f378a38af5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="tour-of-f"></a><span data-ttu-id="dc4a9-103">F # 教學課程</span><span class="sxs-lookup"><span data-stu-id="dc4a9-103">Tour of F#</span></span> #

<span data-ttu-id="dc4a9-104">若要了解 F # 的最佳方式是讀取和寫入 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-104">The best way to learn about F# is to read and write F# code.</span></span>  <span data-ttu-id="dc4a9-105">這篇文章會做為瀏覽某些索引鍵的 F # 語言功能，並提供您一些您可以在您的電腦執行的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-105">This article will act as a tour through some of the key features of the F# language and give you some code snippets that you can execute on your machine.</span></span>  <span data-ttu-id="dc4a9-106">若要深入了解設定開發環境，請參閱[入門](tutorials/getting-started/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-106">To learn about setting up a development environment, check out [Getting Started](tutorials/getting-started/index.md).</span></span>

<span data-ttu-id="dc4a9-107">F # 中有兩個主要概念： 函式和類型。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-107">There are two primary concepts in F#: functions and types.</span></span>  <span data-ttu-id="dc4a9-108">此教學課程會強調可分為下列兩個概念的語言功能。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-108">This tour will emphasize features of the language which fall into these two concepts.</span></span>

## <a name="functions-and-modules"></a><span data-ttu-id="dc4a9-109">函式和模組</span><span class="sxs-lookup"><span data-stu-id="dc4a9-109">Functions and Modules</span></span>

<span data-ttu-id="dc4a9-110">任何 F # 程式的最基本的片段都***函式***組織成***模組***。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-110">The most fundamental pieces of any F# program are ***functions*** organized into ***modules***.</span></span>  <span data-ttu-id="dc4a9-111">[函式](language-reference/functions/index.md)為產生輸出，輸入上執行的工作和組織在[模組](language-reference/modules.md)，這是主要的方式分組在 F # 中的項目。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-111">[Functions](language-reference/functions/index.md) perform work on inputs to produce outputs, and they are organized under [Modules](language-reference/modules.md), which are the primary way you group things in F#.</span></span>  <span data-ttu-id="dc4a9-112">定義使用[`let`繫結](language-reference/functions/let-bindings.md)，其中指定函式的名稱，並且定義其引數。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-112">They are defined using the [`let` binding](language-reference/functions/let-bindings.md), which give the function a name and define its arguments.</span></span>

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

<span data-ttu-id="dc4a9-113">`let` 繫結也是您如何結合其值為名稱，類似於其他語言中的變數。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-113">`let` bindings are also how you bind a value to a name, similar to a variable in other languages.</span></span>  <span data-ttu-id="dc4a9-114">`let` 繫結是***不可變***根據預設，也就是說，一旦值或函式繫結的名稱，它無法變更就地。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-114">`let` bindings are ***immutable*** by default, which means that once a value or function is bound to a name, it cannot be changed in-place.</span></span>  <span data-ttu-id="dc4a9-115">這是相較於其他語言，也就是變數***可變動***，這表示它們的值可以變更在任何時間點的時間。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-115">This is in contrast to variables in other languages, which are ***mutable***, meaning their values can be changed at any point in time.</span></span>  <span data-ttu-id="dc4a9-116">如果您需要的可變動的繫結時，您可以使用`let mutable ...`語法。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-116">If you require a mutable binding, you can use `let mutable ...` syntax.</span></span>

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a><span data-ttu-id="dc4a9-117">數字、 布林值和字串</span><span class="sxs-lookup"><span data-stu-id="dc4a9-117">Numbers, Booleans, and Strings</span></span>

<span data-ttu-id="dc4a9-118">為.NET 語言，F # 支援相同的基礎[基本型別](language-reference/primitive-types.md).NET 中存在。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-118">As a .NET language, F# supports the same underlying [primitive types](language-reference/primitive-types.md) that exist in .NET.</span></span>

<span data-ttu-id="dc4a9-119">以下是如何各種數值類型表示 F # 中：</span><span class="sxs-lookup"><span data-stu-id="dc4a9-119">Here is how various numeric types are represented in F#:</span></span>

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

<span data-ttu-id="dc4a9-120">以下是布林值，並執行基本的條件式邏輯看起來像：</span><span class="sxs-lookup"><span data-stu-id="dc4a9-120">Here's what Boolean values and performing basic conditional logic looks like:</span></span>

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

<span data-ttu-id="dc4a9-121">以下是何種 basic[字串](language-reference/strings.md)操作看起來像：</span><span class="sxs-lookup"><span data-stu-id="dc4a9-121">And here's what basic [string](language-reference/strings.md) manipulation looks like:</span></span>

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a><span data-ttu-id="dc4a9-122">Tuple</span><span class="sxs-lookup"><span data-stu-id="dc4a9-122">Tuples</span></span>

<span data-ttu-id="dc4a9-123">[Tuple](language-reference/tuples.md)是 F # 中是大問題。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-123">[Tuples](language-reference/tuples.md) are a big deal in F#.</span></span>  <span data-ttu-id="dc4a9-124">它們是未命名的但已排序，可以視為值本身的值的群組。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-124">They are a grouping of unnamed, but ordered values, that can be treated as values themselves.</span></span>  <span data-ttu-id="dc4a9-125">將它們視為彙總從其他值的值。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-125">Think of them as values which are aggregated from other values.</span></span>  <span data-ttu-id="dc4a9-126">它們有許多用途，例如輕鬆地從函式傳回多個值或群組的一些特定便利的值。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-126">They have many uses, such as conveniently returning multiple values from a function, or grouping values for some ad-hoc convenience.</span></span>

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

<span data-ttu-id="dc4a9-127">為準，F # 4.1，您也可以建立`struct`tuple。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-127">As of F# 4.1, you can also create `struct` tuples.</span></span>  <span data-ttu-id="dc4a9-128">這些也與交互操作完全也是 C# 7/Visual 基本 15 tuple `struct` tuple:</span><span class="sxs-lookup"><span data-stu-id="dc4a9-128">These also interoperate fully with C#7/Visual Basic 15 tuples, which are also `struct` tuples:</span></span>

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

<span data-ttu-id="dc4a9-129">請務必注意因為`struct`tuple 是實值類型，它們無法隱含地轉換成參考 tuple，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-129">It's important to note that because `struct` tuples are value types, they cannot be implicitly converted to reference tuples, or vice versa.</span></span>  <span data-ttu-id="dc4a9-130">您必須明確轉換之間的參考和結構的 tuple。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-130">You must explicitly convert between a reference and struct tuple.</span></span>

## <a name="pipelines-and-composition"></a><span data-ttu-id="dc4a9-131">管線和撰寫</span><span class="sxs-lookup"><span data-stu-id="dc4a9-131">Pipelines and Composition</span></span>

<span data-ttu-id="dc4a9-132">使用管線運算子 (`|>`， `<|`， `||>`， `<||`， `|||>`， `<|||`) 和運算子組合 (`>>`和`<<`) 會在處理 F # 中的資料時廣泛地使用。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-132">Pipe operators (`|>`, `<|`, `||>`, `<||`, `|||>`, `<|||`) and composition operators (`>>` and `<<`) are used extensively when processing data in F#.</span></span>  <span data-ttu-id="dc4a9-133">這些運算子都可讓您以有彈性的方式建立 「 管線 」 的函式的函式。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-133">These operators are functions which allow you to establish "pipelines" of functions in a flexible manner.</span></span>  <span data-ttu-id="dc4a9-134">下列範例逐步解說如何您無法利用這些運算子來建置簡單的功能性管線。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-134">The following example walks through how you could take advantage of these operators to build a simple functional pipeline.</span></span>

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

<span data-ttu-id="dc4a9-135">上述範例中所使用的 F # 中，包括清單處理函式，第一級函式，許多功能和[部分應用程式](language-reference/functions/index.md#partial-application-of-arguments)。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-135">The above sample made use of many features of F#, including list processing functions, first-class functions, and [partial application](language-reference/functions/index.md#partial-application-of-arguments).</span></span>  <span data-ttu-id="dc4a9-136">雖然深入了解這些概念的每個可以成為稍微進階，應該很清楚如何輕鬆地函式可用來建立管線時，處理資料。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-136">Although a deep understanding of each of those concepts can become somewhat advanced, it should be clear how easily functions can be used to process data when building pipelines.</span></span>

## <a name="lists-arrays-and-sequences"></a><span data-ttu-id="dc4a9-137">清單、 陣列和順序</span><span class="sxs-lookup"><span data-stu-id="dc4a9-137">Lists, Arrays, and Sequences</span></span>

<span data-ttu-id="dc4a9-138">清單、 陣列和順序是 F # 核心程式庫中的三種主要集合類型。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-138">Lists, Arrays, and Sequences are three primary collection types in the F# core library.</span></span>

<span data-ttu-id="dc4a9-139">[列出](language-reference/lists.md)是相同型別的項目已排序、 不可變的集合。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-139">[Lists](language-reference/lists.md) are ordered, immutable collections of elements of the same type.</span></span>  <span data-ttu-id="dc4a9-140">它們是單向連結清單中，這表示它們一定會用於列舉型別，但不佳的適合隨機存取和串連很大時。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-140">They are singly-linked lists, which means they are meant for enumeration, but a poor choice for random access and concatenation if they're large.</span></span>  <span data-ttu-id="dc4a9-141">這相較於其他常用的語言，通常不會使用單向連結清單來表示清單中的清單。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-141">This in contrast to Lists in other popular languages, which typically do not use a singly-linked list to represent Lists.</span></span>

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

<span data-ttu-id="dc4a9-142">[陣列](language-reference/arrays.md)是固定大小*可變動*相同類型的元素的集合。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-142">[Arrays](language-reference/arrays.md) are fixed-size, *mutable* collections of elements of the same type.</span></span>  <span data-ttu-id="dc4a9-143">它們支援快速隨機存取項目，且會比 F # 列出因為它們是只連續記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-143">They support fast random access of elements, and are faster than F# lists because they are just contiguous blocks of memory.</span></span>

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

<span data-ttu-id="dc4a9-144">[序列](language-reference/sequences.md)是邏輯的一連串的項目全為相同的類型。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-144">[Sequences](language-reference/sequences.md) are a logical series of elements, all of the same type.</span></span>  <span data-ttu-id="dc4a9-145">這些是更廣泛的類型，比清單和陣列，在您 「 檢視 」 到任何邏輯系列的項目。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-145">These are a more general type than Lists and Arrays, capable of being your "view" into any logical series of elements.</span></span>  <span data-ttu-id="dc4a9-146">它們也突顯因為它們是***延遲***，這表示只在需要時，可以計算的項目。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-146">They also stand out because they can be ***lazy***, which means that elements can be computed only when they are needed.</span></span>

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a><span data-ttu-id="dc4a9-147">遞迴函式</span><span class="sxs-lookup"><span data-stu-id="dc4a9-147">Recursive Functions</span></span>

<span data-ttu-id="dc4a9-148">處理集合或序列的項目通常是與[遞迴](language-reference/functions/index.md#recursive-functions)F # 中。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-148">Processing collections or sequences of elements is typically done with [recursion](language-reference/functions/index.md#recursive-functions) in F#.</span></span>  <span data-ttu-id="dc4a9-149">雖然 F # 具有迴圈及命令式程式設計支援，但遞迴，因為很容易就能保證正確性。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-149">Although F# has support for loops and imperative programming, recursion is preferred because it is easier to guarantee correctness.</span></span>

>[!NOTE]
<span data-ttu-id="dc4a9-150">下列範例會使用模式比對透過`match`運算式。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-150">The following example makes use of the pattern matching via the `match` expression.</span></span>  <span data-ttu-id="dc4a9-151">這個基本建構涵蓋在本文稍後。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-151">This fundamental construct is covered later in this article.</span></span>

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

<span data-ttu-id="dc4a9-152">F # 也具有完整支援 Tail 呼叫最佳化，這是一種最佳化遞迴呼叫，以使其速度會一樣快迴圈建構。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-152">F# also has full support for Tail Call Optimization, which is a way to optimize recursive calls so that they are just as fast as a loop construct.</span></span>

## <a name="record-and-discriminated-union-types"></a><span data-ttu-id="dc4a9-153">記錄和差別聯集類型</span><span class="sxs-lookup"><span data-stu-id="dc4a9-153">Record and Discriminated Union Types</span></span>

<span data-ttu-id="dc4a9-154">記錄和等位型別在 F # 程式碼，使用兩種基本資料類型，通常代表資料在 F # 程式中的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-154">Record and Union types are two fundamental data types used in F# code, and are generally the best way to represent data in an F# program.</span></span>  <span data-ttu-id="dc4a9-155">雖然這使其與類別類似其他語言中，其主要差異是它們具有結構相等語意。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-155">Although this makes them similar to classes in other languages, one of their primary differences is that they have structural equality semantics.</span></span>  <span data-ttu-id="dc4a9-156">這表示它們是 「 原生 」 可比較而且十分簡單的等號比較-只檢查其中一個是否等於其他。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-156">This means that they are "natively" comparable and equality is straightforward - just check if one is equal to the other.</span></span>

<span data-ttu-id="dc4a9-157">[記錄](language-reference/records.md)會與選擇性成員 （例如方法） 的具名值的彙總。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-157">[Records](language-reference/records.md) are an aggregate of named values, with optional members (such as methods).</span></span>  <span data-ttu-id="dc4a9-158">如果您熟悉 C# 或 Java，然後這些應該可以類似 POCOs 或 POJOs-只是具有結構相等和較低的儀式。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-158">If you're familiar with C# or Java, then these should feel similar to POCOs or POJOs - just with structural equality and less ceremony.</span></span>

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

<span data-ttu-id="dc4a9-159">您也可以為準，F # 4.1，代表做為記錄`struct`s。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-159">As of F# 4.1, you can also represent Records as `struct`s.</span></span>  <span data-ttu-id="dc4a9-160">做法是使用`[<Struct>]`屬性：</span><span class="sxs-lookup"><span data-stu-id="dc4a9-160">This is done with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

<span data-ttu-id="dc4a9-161">[差別等位 (DUs)](language-reference/discriminated-unions.md)可能是具名的表單或案例數的值。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-161">[Discriminated Unions (DUs)](language-reference/discriminated-unions.md) are values which could be a number of named forms or cases.</span></span>  <span data-ttu-id="dc4a9-162">類型中儲存的資料可以是數個相異值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-162">Data stored in the type can be one of several distinct values.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

<span data-ttu-id="dc4a9-163">您也可以使用為 DUs*單一案例差別等位*，以協助進行網域模型基本類型。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-163">You can also use DUs as *Single-Case Discriminated Unions*, to help with domain modeling over primitive types.</span></span>  <span data-ttu-id="dc4a9-164">經常、 字串和其他基本型別用來代表某樣東西，且都因此各有特定意義。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-164">Often times, strings and other primitive types are used to represent something, and are thus given a particular meaning.</span></span>  <span data-ttu-id="dc4a9-165">不過，使用資料的基本表示法可能會導致錯誤地指派值不正確 ！</span><span class="sxs-lookup"><span data-stu-id="dc4a9-165">However, using only the primitive representation of the data can result in mistakenly assigning an incorrect value!</span></span>  <span data-ttu-id="dc4a9-166">代表每一種不同的單一案例聯集的資訊，可以強制在此案例中的正確性。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-166">Representing each type of information as a distinct single-case union can enforce correctness in this scenario.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

<span data-ttu-id="dc4a9-167">如上述範例所示，若要取得基礎值中單一案例差別聯集，您必須明確 unwrap。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-167">As the above sample demonstrates, to get the underlying value in a single-case Discriminated Union, you must explicitly unwrap it.</span></span>

<span data-ttu-id="dc4a9-168">此外，DUs 也支援遞迴定義可讓您輕易地表示樹狀結構和原本就是遞迴的資料。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-168">Additionally, DUs also support recursive definitions, allowing you to easily represent trees and inherently recursive data.</span></span>  <span data-ttu-id="dc4a9-169">例如，以下是可以代表具有的二進位搜尋樹狀目錄的方式`exists`和`insert`函式。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-169">For example, here's how you can represent a Binary Search Tree with `exists` and `insert` functions.</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

<span data-ttu-id="dc4a9-170">DUs 允許您將代表遞迴結構的樹狀結構中的資料類型，因為此遞迴結構上運作很直接，而且可保證正確性。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-170">Because DUs allow you to represent the recursive structure of the tree in the data type, operating on this recursive structure is straightforward and guarantees correctness.</span></span>  <span data-ttu-id="dc4a9-171">它也支援在模式比對，如下所示。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-171">It is also supported in pattern matching, as shown below.</span></span>

<span data-ttu-id="dc4a9-172">此外，您可以在這裡表示為 DUs`struct`與`[<Struct>]`屬性：</span><span class="sxs-lookup"><span data-stu-id="dc4a9-172">Additionally, you can represent DUs as `struct`s with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

<span data-ttu-id="dc4a9-173">不過，有兩個重要的事情，若要這麼做時請記住以下幾點：</span><span class="sxs-lookup"><span data-stu-id="dc4a9-173">However, there are two key things to keep in mind when doing so:</span></span>

1. <span data-ttu-id="dc4a9-174">法蘭西結構不能以遞迴方式定義。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-174">A struct DU cannot be recursively-defined.</span></span>
2. <span data-ttu-id="dc4a9-175">結構法蘭西必須有它的情況下的每個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-175">A struct DU must have unique names for each of its cases.</span></span>

<span data-ttu-id="dc4a9-176">遵循上述的失敗會導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-176">Failure to follow the above will result in a compilation error.</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="dc4a9-177">模式比對</span><span class="sxs-lookup"><span data-stu-id="dc4a9-177">Pattern Matching</span></span>

<span data-ttu-id="dc4a9-178">[模式比對](language-reference/pattern-matching.md)是 F # 語言功能，可讓 F # 類型上運作的正確性。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-178">[Pattern Matching](language-reference/pattern-matching.md) is the F# language feature which enables correctness for operating on F# types.</span></span>  <span data-ttu-id="dc4a9-179">在上述範例中，您可能注意到相當多的`match x with ...`語法。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-179">In the above samples, you probably noticed quite a bit of `match x with ...` syntax.</span></span>  <span data-ttu-id="dc4a9-180">此建構可讓編譯器，可了解"shape"的資料類型，以強制要求您使用透過已知的資料類型為徹底的模式比對時，考量所有可能案例。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-180">This construct allows the compiler, which can understand the "shape" of data types, to force you to account for all possible cases when using a data type through what is known as Exhaustive Pattern Matching.</span></span>  <span data-ttu-id="dc4a9-181">這是非常強大的正確性，並巧妙可用來 「 增益 」 通常會產生編譯成執行階段問題。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-181">This is incredibly powerful for correctness, and can be cleverly used to "lift" what would normally be a runtime concern into compile-time.</span></span>

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

<span data-ttu-id="dc4a9-182">您也可以使用縮寫`function`建構用於模式比對，這非常有用，當您撰寫函式，這會導致使用[部分應用程式](language-reference/functions/index.md#partial-application-of-arguments):</span><span class="sxs-lookup"><span data-stu-id="dc4a9-182">You can also use the shorthand `function` construct for pattern matching, which is useful when you're writing functions which make use of [Partial Application](language-reference/functions/index.md#partial-application-of-arguments):</span></span>

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

<span data-ttu-id="dc4a9-183">您可能已注意到的項目，就是使用`_`模式。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-183">Something you may have noticed is the use of the `_` pattern.</span></span>  <span data-ttu-id="dc4a9-184">這稱為[萬用字元模式](language-reference/pattern-matching.md#wildcard-pattern)，這是一種說 「 我不在意的項目為何 」。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-184">This is known as the [Wildcard Pattern](language-reference/pattern-matching.md#wildcard-pattern), which is a way of saying "I don't care what something is".</span></span>  <span data-ttu-id="dc4a9-185">雖然方便，您可以不小心略過詳盡的模式比對，如果您不小心使用，不會再受益編譯時期強制`_`。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-185">Although convenient, you can accidentally bypass Exhaustive Pattern Matching and no longer benefit from compile-time enforcements if you aren't careful in using `_`.</span></span>  <span data-ttu-id="dc4a9-186">最好使用當您不在意分解類型的某些部分已經列舉所有有意義的情況下在模式比對運算式時，當模式比對或最後一個子句。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-186">It is best used when you don't care about certain pieces of a decomposed type when pattern matching, or the final clause when you have enumerated all meaningful cases in a pattern matching expression.</span></span>

<span data-ttu-id="dc4a9-187">[現用模式](language-reference/active-patterns.md)是另一個功能強大的建構函式來使用搭配模式比對。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-187">[Active Patterns](language-reference/active-patterns.md) are another powerful construct to use with pattern matching.</span></span>  <span data-ttu-id="dc4a9-188">它們可讓您輸入的資料分割成自訂表單，將其分解在模式比對呼叫站台。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-188">They allow you to partition input data into custom forms, decomposing them at the pattern match call site.</span></span>  <span data-ttu-id="dc4a9-189">它們可以也是參數化，如此可讓資料分割定義為函式。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-189">They can also be parameterized, thus allowing to define the partition as a function.</span></span>  <span data-ttu-id="dc4a9-190">展開上一個範例是為了支援現用模式看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="dc4a9-190">Expanding the previous example to support Active Patterns looks something like this:</span></span>

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a><span data-ttu-id="dc4a9-191">選用的類型</span><span class="sxs-lookup"><span data-stu-id="dc4a9-191">Optional Types</span></span>

<span data-ttu-id="dc4a9-192">差別聯集類型的其中一個特殊案例是選項類型，會很有用，它是 F # 核心程式庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-192">One special case of Discriminated Union types is the Option Type, which is so useful that it's a part of the F# core library.</span></span>

<span data-ttu-id="dc4a9-193">[選項類型](language-reference/options.md)是型別代表兩個案例的其中一個： 一個值，或不完全。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-193">[The Option Type](language-reference/options.md) is a type which represents one of two cases: a value, or nothing at all.</span></span>  <span data-ttu-id="dc4a9-194">它用在任何情況下，值可能會或可能不會造成從特定作業的位置。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-194">It is used in any scenario where a value may or may not result from a particular operation.</span></span>  <span data-ttu-id="dc4a9-195">這會強制您帳戶的這兩種情況，因此是編譯時期問題，而不是執行階段問題。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-195">This then forces you to account for both cases, making it a compile-time concern rather than a runtime concern.</span></span>  <span data-ttu-id="dc4a9-196">這些通常用於應用程式開發介面其中`null`用來代表"nothing"相反地，因此不需要擔心`NullReferenceException`在許多情況下。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-196">These are often used in APIs where `null` is used to represent "nothing" instead, thus eliminating the need to worry about `NullReferenceException` in many circumstances.</span></span>

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a><span data-ttu-id="dc4a9-197">測量單位</span><span class="sxs-lookup"><span data-stu-id="dc4a9-197">Units of Measure</span></span>

<span data-ttu-id="dc4a9-198">F # 型別系統的一項獨特功能是能夠提供透過測量單位的數值常值的內容。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-198">One unique feature of F#'s type system is the ability to provide context for numeric literals through Units of Measure.</span></span>

<span data-ttu-id="dc4a9-199">[測量單位](language-reference/units-of-measure.md)可讓您將為單位，例如公尺來測量，數值類型產生關聯，並具有函式上執行的工作單位，而不是數值常值。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-199">[Units of Measure](language-reference/units-of-measure.md) allow you to associate a numeric type to a unit, such as Meters, and have functions perform work on units rather than numeric literals.</span></span>  <span data-ttu-id="dc4a9-200">這可讓編譯器驗證傳入的數值常值的類型，在某些環境下的意義上，因此減少執行階段錯誤與該類型的工作相關聯。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-200">This enables the compiler to verify that the types of numeric literals passed in make sense under a certain context, thus eliminating runtime errors associated with that kind of work.</span></span>

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

<span data-ttu-id="dc4a9-201">F # 核心程式庫定義許多 SI 單位類型和單位轉換。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-201">The F# Core library defines many SI unit types and unit conversions.</span></span>  <span data-ttu-id="dc4a9-202">若要進一步了解，請參閱[Microsoft.FSharp.Data.UnitSystems.SI 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-202">To learn more, check out the [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).</span></span>

## <a name="classes-and-interfaces"></a><span data-ttu-id="dc4a9-203">類別和介面</span><span class="sxs-lookup"><span data-stu-id="dc4a9-203">Classes and Interfaces</span></span>

<span data-ttu-id="dc4a9-204">F # 也有.NET 類別的完整支援[介面](language-reference/interfaces.md)，[抽象類別](language-reference/abstract-classes.md)，[繼承](language-reference/inheritance.md)，依此類推。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-204">F# also has full support for .NET classes, [Interfaces](language-reference/interfaces.md), [Abstract Classes](language-reference/abstract-classes.md), [Inheritance](language-reference/inheritance.md), and so on.</span></span>

<span data-ttu-id="dc4a9-205">[類別](language-reference/classes.md)是代表.NET 物件的型別且可以包含屬性、 方法和事件中的當做其[成員](language-reference/members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-205">[Classes](language-reference/classes.md) are types that represent .NET objects, which can have properties, methods, and events as its [Members](language-reference/members/index.md).</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

<span data-ttu-id="dc4a9-206">定義泛型類別也是非常簡單。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-206">Defining generic classes is also very straightforward.</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

<span data-ttu-id="dc4a9-207">若要實作介面，您可以使用`interface ... with`語法或[物件運算式](language-reference/object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-207">To implement an Interface, you can use either `interface ... with` syntax or an [Object Expression](language-reference/object-expressions.md).</span></span>

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a><span data-ttu-id="dc4a9-208">若要使用哪些類型</span><span class="sxs-lookup"><span data-stu-id="dc4a9-208">Which Types to Use</span></span>

<span data-ttu-id="dc4a9-209">類別、 記錄、 差別等位和 Tuple 的存在會導致重要的問題： 您應該使用它？</span><span class="sxs-lookup"><span data-stu-id="dc4a9-209">The presence of Classes, Records, Discriminated Unions, and Tuples leads to an important question: which should you use?</span></span>  <span data-ttu-id="dc4a9-210">大部分的所有項目在生活中，例如答案需視您的情況。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-210">Like most everything in life, the answer depends on your circumstances.</span></span>

<span data-ttu-id="dc4a9-211">Tuple 非常適合用來從函式，傳回多個值，並用作值本身的特定彙總的值。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-211">Tuples are great for returning multiple values from a function, and using an ad-hoc aggregate of values as a value itself.</span></span>

<span data-ttu-id="dc4a9-212">記錄會 「 逐步向上 」 從具有名為標籤和支援選擇性成員的 Tuple。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-212">Records are a "step up" from Tuples, having named labels and support for optional members.</span></span>  <span data-ttu-id="dc4a9-213">它們很適合用於資料傳輸中執行您的程式的低儀式表示法。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-213">They are great for a low-ceremony representation of data in-transit through your program.</span></span>  <span data-ttu-id="dc4a9-214">具有結構相等，因為它們是容易使用的比較。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-214">Because they have structural equality, they are easy to use with comparison.</span></span>

<span data-ttu-id="dc4a9-215">差別等位有許多用途，但核心優點是能夠利用它們搭配模式比對所有可能 「 圖形 」 可以有資料的帳戶。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-215">Discriminated Unions have many uses, but the core benefit is to be able to utilize them in conjunction with Pattern Matching to account for all possible "shapes" that a data can have.</span></span>  

<span data-ttu-id="dc4a9-216">類別最適合用於大量的原因，例如當您需要代表資訊也連接該功能的資訊。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-216">Classes are great for a huge number of reasons, such as when you need to represent information and also tie that information to functionality.</span></span>  <span data-ttu-id="dc4a9-217">根據經驗法則，當您擁有的功能可在概念上繫結至部分資料，使用類別和 Object-Oriented 程式設計的原則是一大優點。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-217">As a rule of thumb, when you have functionality which is conceptually tied to some data, using Classes and the principles of Object-Oriented Programming is a big benefit.</span></span>  <span data-ttu-id="dc4a9-218">類別也是慣用的資料類型與 C# 和 Visual Basic 中，搭配使用時為這些語言幾乎所有項目使用的類別。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-218">Classes are also the preferred data type when interoperating with C# and Visual Basic, as these languages use classes for nearly everything.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dc4a9-219">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dc4a9-219">Next Steps</span></span>

<span data-ttu-id="dc4a9-220">既然您已看過的一些主要功能的語言，您應該準備好開始撰寫第一個 F # 程式 ！</span><span class="sxs-lookup"><span data-stu-id="dc4a9-220">Now that you've seen some of the primary features of the language, you should be ready to write your first F# programs!</span></span>  <span data-ttu-id="dc4a9-221">簽出[入門](tutorials/getting-started/index.md)以了解如何設定您的開發環境，並撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-221">Check out [Getting Started](tutorials/getting-started/index.md) to learn how to set up your development environment and write some code.</span></span>

<span data-ttu-id="dc4a9-222">接下來的步驟來學習更多可以是任何您喜歡，但我們建議您[函式做為第一級值](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)-->取得熟悉核心功能的程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-222">The next steps for learning more can be whatever you like, but we recommend [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)--> to get comfortable with core Functional Programming concepts.</span></span>  <span data-ttu-id="dc4a9-223">這些會在建置穩固的應用程式在 F # 中不可或缺。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-223">These will be essential in building robust programs in F#.</span></span>

<span data-ttu-id="dc4a9-224">此外，請參閱[F # 語言參考](language-reference/index.md)若要查看在 F # 的概念性內容的完整集合。</span><span class="sxs-lookup"><span data-stu-id="dc4a9-224">Also, check out the [F# Language Reference](language-reference/index.md) to see a comprehensive collection of conceptual content on F#.</span></span>
