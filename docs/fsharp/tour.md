---
title: F# 的教學課程
description: 檢查一些 F# 程式設計語言，在此教學課程利用程式碼範例的主要功能。
ms.date: 11/06/2018
ms.openlocfilehash: eba136da3cd829dcb2b0726dd4f1c24434aeba5b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182622"
---
# <a name="tour-of-f"></a><span data-ttu-id="db47b-103">F 的教學課程\#</span><span class="sxs-lookup"><span data-stu-id="db47b-103">Tour of F\#</span></span>

<span data-ttu-id="db47b-104">若要了解 F# 的最佳方式是讀取和寫入 F# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="db47b-104">The best way to learn about F# is to read and write F# code.</span></span> <span data-ttu-id="db47b-105">這篇文章會做為某些 F# 語言的重要功能的逐步教學課程，並提供您一些您可以在您的電腦執行的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="db47b-105">This article will act as a tour through some of the key features of the F# language and give you some code snippets that you can execute on your machine.</span></span> <span data-ttu-id="db47b-106">若要瞭解如何設定開發環境，請參閱[消費者入門](./tutorials/getting-started/index.md)。</span><span class="sxs-lookup"><span data-stu-id="db47b-106">To learn about setting up a development environment, check out [Getting Started](./tutorials/getting-started/index.md).</span></span>

<span data-ttu-id="db47b-107">F# 中有兩個主要概念： 函式和類型。</span><span class="sxs-lookup"><span data-stu-id="db47b-107">There are two primary concepts in F#: functions and types.</span></span>  <span data-ttu-id="db47b-108">本教學課程將強調屬於這兩個概念的語言功能。</span><span class="sxs-lookup"><span data-stu-id="db47b-108">This tour will emphasize features of the language which fall into these two concepts.</span></span>

## <a name="executing-the-code-online"></a><span data-ttu-id="db47b-109">線上執行程式碼</span><span class="sxs-lookup"><span data-stu-id="db47b-109">Executing the code online</span></span>

<span data-ttu-id="db47b-110">如果您的電腦F#上未安裝，您可以使用[WebAssembly 上的 Try F# ](https://tryfsharp.fsbolero.io/)來執行瀏覽器中的所有範例。</span><span class="sxs-lookup"><span data-stu-id="db47b-110">If you don't have F# installed on your machine, you can execute all of the samples in your browser with [Try F# on WebAssembly](https://tryfsharp.fsbolero.io/).</span></span> <span data-ttu-id="db47b-111">Fable 是直接在您F#的瀏覽器中執行的方言。</span><span class="sxs-lookup"><span data-stu-id="db47b-111">Fable is a dialect of F# that executes directly in your browser.</span></span> <span data-ttu-id="db47b-112">若要查看複寫中接下來的範例，請參閱**範例 > 瞭解F#**  Fable 複寫左側功能表列中的 > 導覽。</span><span class="sxs-lookup"><span data-stu-id="db47b-112">To view the samples that follow in the REPL, check out **Samples > Learn > Tour of F#** in the left-hand menu bar of the Fable REPL.</span></span>

## <a name="functions-and-modules"></a><span data-ttu-id="db47b-113">函數和模組</span><span class="sxs-lookup"><span data-stu-id="db47b-113">Functions and Modules</span></span>

<span data-ttu-id="db47b-114">任何的 F# 程式的最基本的部分是***函式***分成***模組***。</span><span class="sxs-lookup"><span data-stu-id="db47b-114">The most fundamental pieces of any F# program are ***functions*** organized into ***modules***.</span></span>  <span data-ttu-id="db47b-115">[函式](./language-reference/functions/index.md)來產生輸出的輸入上執行的工作和其下組織[模組](./language-reference/modules.md)，這是主要的方式分組在 F# 中的項目。</span><span class="sxs-lookup"><span data-stu-id="db47b-115">[Functions](./language-reference/functions/index.md) perform work on inputs to produce outputs, and they are organized under [Modules](./language-reference/modules.md), which are the primary way you group things in F#.</span></span>  <span data-ttu-id="db47b-116">它們是使用[ `let` ](./language-reference/functions/let-bindings.md)系結來定義，這會提供函式名稱並定義其引數。</span><span class="sxs-lookup"><span data-stu-id="db47b-116">They are defined using the [`let` binding](./language-reference/functions/let-bindings.md), which give the function a name and define its arguments.</span></span>

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

<span data-ttu-id="db47b-117">`let`系結也是您將值系結至名稱的方式，類似于其他語言中的變數。</span><span class="sxs-lookup"><span data-stu-id="db47b-117">`let` bindings are also how you bind a value to a name, similar to a variable in other languages.</span></span>  <span data-ttu-id="db47b-118">`let`系結預設為***不可變***，這表示一旦值或函式系結至名稱，就無法就地變更。</span><span class="sxs-lookup"><span data-stu-id="db47b-118">`let` bindings are ***immutable*** by default, which means that once a value or function is bound to a name, it cannot be changed in-place.</span></span>  <span data-ttu-id="db47b-119">這與其他語言中的變數相反，***這是可變動的，這***表示它們的值可以在任何時間點變更。</span><span class="sxs-lookup"><span data-stu-id="db47b-119">This is in contrast to variables in other languages, which are ***mutable***, meaning their values can be changed at any point in time.</span></span>  <span data-ttu-id="db47b-120">如果您需要可變的系結，您可以`let mutable ...`使用語法。</span><span class="sxs-lookup"><span data-stu-id="db47b-120">If you require a mutable binding, you can use `let mutable ...` syntax.</span></span>

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a><span data-ttu-id="db47b-121">數位、布林值和字串</span><span class="sxs-lookup"><span data-stu-id="db47b-121">Numbers, Booleans, and Strings</span></span>

<span data-ttu-id="db47b-122">為.NET 語言，F# 支援相同的基礎[基本型別](./language-reference/primitive-types.md)存在於.NET。</span><span class="sxs-lookup"><span data-stu-id="db47b-122">As a .NET language, F# supports the same underlying [primitive types](./language-reference/primitive-types.md) that exist in .NET.</span></span>

<span data-ttu-id="db47b-123">以下是如何各種數值類型表示 F# 中：</span><span class="sxs-lookup"><span data-stu-id="db47b-123">Here is how various numeric types are represented in F#:</span></span>

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

<span data-ttu-id="db47b-124">以下是布林值和執行基本條件式邏輯的樣子：</span><span class="sxs-lookup"><span data-stu-id="db47b-124">Here's what Boolean values and performing basic conditional logic looks like:</span></span>

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

<span data-ttu-id="db47b-125">以下是基本[字串](./language-reference/strings.md)操作的樣子：</span><span class="sxs-lookup"><span data-stu-id="db47b-125">And here's what basic [string](./language-reference/strings.md) manipulation looks like:</span></span>

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a><span data-ttu-id="db47b-126">Tuple</span><span class="sxs-lookup"><span data-stu-id="db47b-126">Tuples</span></span>

<span data-ttu-id="db47b-127">[Tuple](./language-reference/tuples.md)是 F# 中是什麼大問題。</span><span class="sxs-lookup"><span data-stu-id="db47b-127">[Tuples](./language-reference/tuples.md) are a big deal in F#.</span></span>  <span data-ttu-id="db47b-128">它們是未命名但已排序值的群組，可視為值本身。</span><span class="sxs-lookup"><span data-stu-id="db47b-128">They are a grouping of unnamed, but ordered values, that can be treated as values themselves.</span></span>  <span data-ttu-id="db47b-129">請將它們想成是從其他值匯總而來的值。</span><span class="sxs-lookup"><span data-stu-id="db47b-129">Think of them as values which are aggregated from other values.</span></span>  <span data-ttu-id="db47b-130">它們有許多用途，例如方便地從函式傳回多個值，或將值分組以進行特定的便利性。</span><span class="sxs-lookup"><span data-stu-id="db47b-130">They have many uses, such as conveniently returning multiple values from a function, or grouping values for some ad-hoc convenience.</span></span>

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

<span data-ttu-id="db47b-131">自 F# 4.1，您也可以建立`struct`tuple。</span><span class="sxs-lookup"><span data-stu-id="db47b-131">As of F# 4.1, you can also create `struct` tuples.</span></span>  <span data-ttu-id="db47b-132">這些也會與 c # 7/Visual Basic 15 元組（也`struct`就是元組）完全交互操作：</span><span class="sxs-lookup"><span data-stu-id="db47b-132">These also interoperate fully with C#7/Visual Basic 15 tuples, which are also `struct` tuples:</span></span>

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

<span data-ttu-id="db47b-133">請務必注意，因為`struct`元組是實值型別，所以不能隱含地轉換成參考元組，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="db47b-133">It's important to note that because `struct` tuples are value types, they cannot be implicitly converted to reference tuples, or vice versa.</span></span>  <span data-ttu-id="db47b-134">您必須在參考和結構元組之間明確轉換。</span><span class="sxs-lookup"><span data-stu-id="db47b-134">You must explicitly convert between a reference and struct tuple.</span></span>

## <a name="pipelines-and-composition"></a><span data-ttu-id="db47b-135">管線和組合</span><span class="sxs-lookup"><span data-stu-id="db47b-135">Pipelines and Composition</span></span>

<span data-ttu-id="db47b-136">透過管道傳送這類運算子`|>`廣泛處理 F# 中的資料時。</span><span class="sxs-lookup"><span data-stu-id="db47b-136">Pipe operators such as `|>` are used extensively when processing data in F#.</span></span> <span data-ttu-id="db47b-137">這些運算子是函數，可讓您以彈性的方式建立函式的「管線」。</span><span class="sxs-lookup"><span data-stu-id="db47b-137">These operators are functions that allow you to establish "pipelines" of functions in a flexible manner.</span></span> <span data-ttu-id="db47b-138">下列範例會逐步解說如何利用這些運算子來建立簡單的功能管線：</span><span class="sxs-lookup"><span data-stu-id="db47b-138">The following example walks through how you can take advantage of these operators to build a simple functional pipeline:</span></span>

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

<span data-ttu-id="db47b-139">先前所做的範例使用的許多功能的 F#，包括清單處理函式，第一級函式，並[部分的應用程式](./language-reference/functions/index.md#partial-application-of-arguments)。</span><span class="sxs-lookup"><span data-stu-id="db47b-139">The previous sample made use of many features of F#, including list processing functions, first-class functions, and [partial application](./language-reference/functions/index.md#partial-application-of-arguments).</span></span> <span data-ttu-id="db47b-140">雖然深入瞭解每個概念可能會變得很重要，但請清楚瞭解在建立管線時，函數可以如何用來處理資料。</span><span class="sxs-lookup"><span data-stu-id="db47b-140">Although a deep understanding of each of those concepts can become somewhat advanced, it should be clear how easily functions can be used to process data when building pipelines.</span></span>

## <a name="lists-arrays-and-sequences"></a><span data-ttu-id="db47b-141">清單、陣列和順序</span><span class="sxs-lookup"><span data-stu-id="db47b-141">Lists, Arrays, and Sequences</span></span>

<span data-ttu-id="db47b-142">清單、 陣列和順序是 F# 核心程式庫中的三種主要集合類型。</span><span class="sxs-lookup"><span data-stu-id="db47b-142">Lists, Arrays, and Sequences are three primary collection types in the F# core library.</span></span>

<span data-ttu-id="db47b-143">[清單](./language-reference/lists.md)是相同類型之元素的已排序、不可變集合。</span><span class="sxs-lookup"><span data-stu-id="db47b-143">[Lists](./language-reference/lists.md) are ordered, immutable collections of elements of the same type.</span></span>  <span data-ttu-id="db47b-144">它們是單一連結的清單，這表示它們是用來進行列舉，但如果很大，則不適合用于隨機存取和串連。</span><span class="sxs-lookup"><span data-stu-id="db47b-144">They are singly-linked lists, which means they are meant for enumeration, but a poor choice for random access and concatenation if they're large.</span></span>  <span data-ttu-id="db47b-145">相較于其他熱門語言的清單，通常不會使用單一連結的清單來表示清單。</span><span class="sxs-lookup"><span data-stu-id="db47b-145">This in contrast to Lists in other popular languages, which typically do not use a singly-linked list to represent Lists.</span></span>

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

<span data-ttu-id="db47b-146">[陣列](./language-reference/arrays.md)是一種固定大小 *、可*變動的元素集合，屬於相同類型的專案。</span><span class="sxs-lookup"><span data-stu-id="db47b-146">[Arrays](./language-reference/arrays.md) are fixed-size, *mutable* collections of elements of the same type.</span></span>  <span data-ttu-id="db47b-147">它們支援的項目，快速隨機存取，且速度比 F# 清單因為它們只是連續記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="db47b-147">They support fast random access of elements, and are faster than F# lists because they are just contiguous blocks of memory.</span></span>

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

<span data-ttu-id="db47b-148">[序列](./language-reference/sequences.md)是專案的邏輯系列，全都是相同的類型。</span><span class="sxs-lookup"><span data-stu-id="db47b-148">[Sequences](./language-reference/sequences.md) are a logical series of elements, all of the same type.</span></span>  <span data-ttu-id="db47b-149">這些是比清單和陣列更一般的類型，可以將您的「視圖」放入任何邏輯專案序列中。</span><span class="sxs-lookup"><span data-stu-id="db47b-149">These are a more general type than Lists and Arrays, capable of being your "view" into any logical series of elements.</span></span>  <span data-ttu-id="db47b-150">它們也會脫穎而出，因為它們可能是***延遲***的，也就是說，只有在需要時才會計算元素。</span><span class="sxs-lookup"><span data-stu-id="db47b-150">They also stand out because they can be ***lazy***, which means that elements can be computed only when they are needed.</span></span>

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a><span data-ttu-id="db47b-151">遞迴函式</span><span class="sxs-lookup"><span data-stu-id="db47b-151">Recursive Functions</span></span>

<span data-ttu-id="db47b-152">處理集合或序列的項目通常是使用[遞迴](./language-reference/functions/index.md#recursive-functions)F# 中。</span><span class="sxs-lookup"><span data-stu-id="db47b-152">Processing collections or sequences of elements is typically done with [recursion](./language-reference/functions/index.md#recursive-functions) in F#.</span></span>  <span data-ttu-id="db47b-153">雖然 F# 提供 for 迴圈和命令式程式設計的支援，但遞迴建議，因為很容易就能保證正確性。</span><span class="sxs-lookup"><span data-stu-id="db47b-153">Although F# has support for loops and imperative programming, recursion is preferred because it is easier to guarantee correctness.</span></span>

> [!NOTE]
> <span data-ttu-id="db47b-154">下列範例會使用透過`match`運算式的模式比對。</span><span class="sxs-lookup"><span data-stu-id="db47b-154">The following example makes use of the pattern matching via the `match` expression.</span></span>  <span data-ttu-id="db47b-155">本文稍後將討論此基本結構。</span><span class="sxs-lookup"><span data-stu-id="db47b-155">This fundamental construct is covered later in this article.</span></span>

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

<span data-ttu-id="db47b-156">F# 也有完整支援 Tail 呼叫最佳化，這是一種最佳化，使其只是最快的速度迴圈建構的遞迴呼叫。</span><span class="sxs-lookup"><span data-stu-id="db47b-156">F# also has full support for Tail Call Optimization, which is a way to optimize recursive calls so that they are just as fast as a loop construct.</span></span>

## <a name="record-and-discriminated-union-types"></a><span data-ttu-id="db47b-157">記錄和區分聯集類型</span><span class="sxs-lookup"><span data-stu-id="db47b-157">Record and Discriminated Union Types</span></span>

<span data-ttu-id="db47b-158">記錄和等位型別中 F# 程式碼，使用兩種基本資料類型，通常的最佳方式來表示 F# 程式中的資料。</span><span class="sxs-lookup"><span data-stu-id="db47b-158">Record and Union types are two fundamental data types used in F# code, and are generally the best way to represent data in an F# program.</span></span>  <span data-ttu-id="db47b-159">雖然這會使它們類似于其他語言中的類別，但其中一個主要差異在於它們有結構相等的語義。</span><span class="sxs-lookup"><span data-stu-id="db47b-159">Although this makes them similar to classes in other languages, one of their primary differences is that they have structural equality semantics.</span></span>  <span data-ttu-id="db47b-160">這表示它們是「原生」的可比較和相等，只需檢查其中一個是否等於另一個。</span><span class="sxs-lookup"><span data-stu-id="db47b-160">This means that they are "natively" comparable and equality is straightforward - just check if one is equal to the other.</span></span>

<span data-ttu-id="db47b-161">[記錄](./language-reference/records.md)是已命名值的匯總，具有選擇性成員（例如方法）。</span><span class="sxs-lookup"><span data-stu-id="db47b-161">[Records](./language-reference/records.md) are an aggregate of named values, with optional members (such as methods).</span></span>  <span data-ttu-id="db47b-162">如果您熟悉C#或 JAVA，則這些內容應該類似于 Poco 或 pojo，只是結構化的相等和較少的儀式。</span><span class="sxs-lookup"><span data-stu-id="db47b-162">If you're familiar with C# or Java, then these should feel similar to POCOs or POJOs - just with structural equality and less ceremony.</span></span>

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

<span data-ttu-id="db47b-163">自 F# 4.1，您也可以代表記錄當做`struct`s。</span><span class="sxs-lookup"><span data-stu-id="db47b-163">As of F# 4.1, you can also represent Records as `struct`s.</span></span>  <span data-ttu-id="db47b-164">這會透過`[<Struct>]`屬性來完成：</span><span class="sxs-lookup"><span data-stu-id="db47b-164">This is done with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

<span data-ttu-id="db47b-165">[區分等位（DUs）](./language-reference/discriminated-unions.md)是可能是一些命名表單或案例的值。</span><span class="sxs-lookup"><span data-stu-id="db47b-165">[Discriminated Unions (DUs)](./language-reference/discriminated-unions.md) are values which could be a number of named forms or cases.</span></span>  <span data-ttu-id="db47b-166">儲存在類型中的資料可以是數個相異值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="db47b-166">Data stored in the type can be one of several distinct values.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

<span data-ttu-id="db47b-167">您也可以使用 DUs 作為*單一案例的區分等位*，以協助透過基本型別進行領域模型化。</span><span class="sxs-lookup"><span data-stu-id="db47b-167">You can also use DUs as *Single-Case Discriminated Unions*, to help with domain modeling over primitive types.</span></span>  <span data-ttu-id="db47b-168">通常會使用字串和其他基本型別來代表某個專案，因此會提供特定意義。</span><span class="sxs-lookup"><span data-stu-id="db47b-168">Often times, strings and other primitive types are used to represent something, and are thus given a particular meaning.</span></span>  <span data-ttu-id="db47b-169">不過，只使用資料的基本標記法可能會造成錯誤地指派不正確的值！</span><span class="sxs-lookup"><span data-stu-id="db47b-169">However, using only the primitive representation of the data can result in mistakenly assigning an incorrect value!</span></span>  <span data-ttu-id="db47b-170">將每一種類型的資訊表示為不同的單一案例聯集，可以在此案例中強制執行正確性。</span><span class="sxs-lookup"><span data-stu-id="db47b-170">Representing each type of information as a distinct single-case union can enforce correctness in this scenario.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

<span data-ttu-id="db47b-171">如上述範例所示，若要取得單一案例的區分等位中的基礎值，您必須明確地將它解除包裝。</span><span class="sxs-lookup"><span data-stu-id="db47b-171">As the above sample demonstrates, to get the underlying value in a single-case Discriminated Union, you must explicitly unwrap it.</span></span>

<span data-ttu-id="db47b-172">此外，DUs 也支援遞迴定義，可讓您輕鬆地表示樹狀結構和原本就遞迴的資料。</span><span class="sxs-lookup"><span data-stu-id="db47b-172">Additionally, DUs also support recursive definitions, allowing you to easily represent trees and inherently recursive data.</span></span>  <span data-ttu-id="db47b-173">例如，以下說明如何使用`exists`和`insert`函式來表示二進位搜尋樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="db47b-173">For example, here's how you can represent a Binary Search Tree with `exists` and `insert` functions.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

<span data-ttu-id="db47b-174">由於 DUs 可讓您以資料類型表示樹狀結構的遞迴結構，因此在此遞迴結構上操作十分簡單，並保證正確性。</span><span class="sxs-lookup"><span data-stu-id="db47b-174">Because DUs allow you to represent the recursive structure of the tree in the data type, operating on this recursive structure is straightforward and guarantees correctness.</span></span>  <span data-ttu-id="db47b-175">模式比對也支援，如下所示。</span><span class="sxs-lookup"><span data-stu-id="db47b-175">It is also supported in pattern matching, as shown below.</span></span>

<span data-ttu-id="db47b-176">此外，您可以`struct` `[<Struct>]`使用屬性來將 DUs 表示為：</span><span class="sxs-lookup"><span data-stu-id="db47b-176">Additionally, you can represent DUs as `struct`s with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

<span data-ttu-id="db47b-177">不過，在這麼做時，有兩個重要的事項要牢記在心：</span><span class="sxs-lookup"><span data-stu-id="db47b-177">However, there are two key things to keep in mind when doing so:</span></span>

1. <span data-ttu-id="db47b-178">結構 DU 無法以遞迴方式定義。</span><span class="sxs-lookup"><span data-stu-id="db47b-178">A struct DU cannot be recursively-defined.</span></span>
2. <span data-ttu-id="db47b-179">結構 DU 的每一個案例都必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="db47b-179">A struct DU must have unique names for each of its cases.</span></span>

<span data-ttu-id="db47b-180">如果無法遵循上述動作，將會導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="db47b-180">Failure to follow the above will result in a compilation error.</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="db47b-181">模式比對</span><span class="sxs-lookup"><span data-stu-id="db47b-181">Pattern Matching</span></span>

<span data-ttu-id="db47b-182">[模式比對](./language-reference/pattern-matching.md)是 F# 語言功能，可讓 F# 類型上操作的正確性。</span><span class="sxs-lookup"><span data-stu-id="db47b-182">[Pattern Matching](./language-reference/pattern-matching.md) is the F# language feature which enables correctness for operating on F# types.</span></span>  <span data-ttu-id="db47b-183">在上述範例中，您可能已注意到相當多`match x with ...`的語法。</span><span class="sxs-lookup"><span data-stu-id="db47b-183">In the above samples, you probably noticed quite a bit of `match x with ...` syntax.</span></span>  <span data-ttu-id="db47b-184">此結構可讓編譯器（可以瞭解資料類型的「圖形」）在使用資料類型時，透過所謂的完整模式比對來強制您考慮所有可能的情況。</span><span class="sxs-lookup"><span data-stu-id="db47b-184">This construct allows the compiler, which can understand the "shape" of data types, to force you to account for all possible cases when using a data type through what is known as Exhaustive Pattern Matching.</span></span>  <span data-ttu-id="db47b-185">這在正確性方面非常強大，而且可以應變用來「增益」通常會在編譯時期發生的執行時間問題。</span><span class="sxs-lookup"><span data-stu-id="db47b-185">This is incredibly powerful for correctness, and can be cleverly used to "lift" what would normally be a runtime concern into compile-time.</span></span>

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

<span data-ttu-id="db47b-186">您可能已經注意到，使用`_`模式。</span><span class="sxs-lookup"><span data-stu-id="db47b-186">Something you may have noticed is the use of the `_` pattern.</span></span>  <span data-ttu-id="db47b-187">這就是所謂的[萬用字元模式](./language-reference/pattern-matching.md#wildcard-pattern)，這是一個指出「我不在意什麼東西」的方法。</span><span class="sxs-lookup"><span data-stu-id="db47b-187">This is known as the [Wildcard Pattern](./language-reference/pattern-matching.md#wildcard-pattern), which is a way of saying "I don't care what something is".</span></span>  <span data-ttu-id="db47b-188">雖然方便，但如果您不小心使用`_`，可以不小心略過完整的模式比對，而不再受益于編譯時期實行原則。</span><span class="sxs-lookup"><span data-stu-id="db47b-188">Although convenient, you can accidentally bypass Exhaustive Pattern Matching and no longer benefit from compile-time enforcements if you aren't careful in using `_`.</span></span>  <span data-ttu-id="db47b-189">在模式比對時，如果您不在意分解類型的特定片段，或當您在模式比對運算式中列舉了所有有意義的案例時，最好使用此方式。</span><span class="sxs-lookup"><span data-stu-id="db47b-189">It is best used when you don't care about certain pieces of a decomposed type when pattern matching, or the final clause when you have enumerated all meaningful cases in a pattern matching expression.</span></span>

<span data-ttu-id="db47b-190">[現用模式](./language-reference/active-patterns.md)是另一個搭配模式比對使用的強大結構。</span><span class="sxs-lookup"><span data-stu-id="db47b-190">[Active Patterns](./language-reference/active-patterns.md) are another powerful construct to use with pattern matching.</span></span>  <span data-ttu-id="db47b-191">它們可讓您將輸入資料分割成自訂表單，並在模式比對呼叫位置分解它們。</span><span class="sxs-lookup"><span data-stu-id="db47b-191">They allow you to partition input data into custom forms, decomposing them at the pattern match call site.</span></span>  <span data-ttu-id="db47b-192">它們也可以參數化，因此可讓將資料分割定義為函數。</span><span class="sxs-lookup"><span data-stu-id="db47b-192">They can also be parameterized, thus allowing to define the partition as a function.</span></span>  <span data-ttu-id="db47b-193">展開先前的範例以支援現用模式看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="db47b-193">Expanding the previous example to support Active Patterns looks something like this:</span></span>

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a><span data-ttu-id="db47b-194">選擇性類型</span><span class="sxs-lookup"><span data-stu-id="db47b-194">Optional Types</span></span>

<span data-ttu-id="db47b-195">差別聯集類型的其中一個特殊案例是選項類型，這很有用，它是 F# 核心程式庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="db47b-195">One special case of Discriminated Union types is the Option Type, which is so useful that it's a part of the F# core library.</span></span>

<span data-ttu-id="db47b-196">[選項類型](./language-reference/options.md)是代表兩個案例之一的類型：值，或完全沒有。</span><span class="sxs-lookup"><span data-stu-id="db47b-196">[The Option Type](./language-reference/options.md) is a type which represents one of two cases: a value, or nothing at all.</span></span>  <span data-ttu-id="db47b-197">在任何情況下，如果值不一定是由特定作業所產生，就會使用它。</span><span class="sxs-lookup"><span data-stu-id="db47b-197">It is used in any scenario where a value may or may not result from a particular operation.</span></span>  <span data-ttu-id="db47b-198">這會強制您將這兩種情況都列入考慮，使其成為編譯時期的考慮，而不是執行時間的顧慮。</span><span class="sxs-lookup"><span data-stu-id="db47b-198">This then forces you to account for both cases, making it a compile-time concern rather than a runtime concern.</span></span>  <span data-ttu-id="db47b-199">這些通常用於用來代表「 `null`無」的 api，因此`NullReferenceException`在許多情況下都不需要擔心。</span><span class="sxs-lookup"><span data-stu-id="db47b-199">These are often used in APIs where `null` is used to represent "nothing" instead, thus eliminating the need to worry about `NullReferenceException` in many circumstances.</span></span>

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a><span data-ttu-id="db47b-200">測量單位</span><span class="sxs-lookup"><span data-stu-id="db47b-200">Units of Measure</span></span>

<span data-ttu-id="db47b-201">F# 型別系統的一項獨特功能是能夠透過單位的量值的數值常值的提供內容。</span><span class="sxs-lookup"><span data-stu-id="db47b-201">One unique feature of F#'s type system is the ability to provide context for numeric literals through Units of Measure.</span></span>

<span data-ttu-id="db47b-202">[測量單位](./language-reference/units-of-measure.md)可讓您建立數數值型別與單位（例如計量）的關聯，並讓函式在單位上執行工作，而不是數值常值。</span><span class="sxs-lookup"><span data-stu-id="db47b-202">[Units of Measure](./language-reference/units-of-measure.md) allow you to associate a numeric type to a unit, such as Meters, and have functions perform work on units rather than numeric literals.</span></span>  <span data-ttu-id="db47b-203">這可讓編譯器確認傳入的數值常數值型別在特定內容之下有意義，因而排除與該類型工作相關聯的執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="db47b-203">This enables the compiler to verify that the types of numeric literals passed in make sense under a certain context, thus eliminating runtime errors associated with that kind of work.</span></span>

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

<span data-ttu-id="db47b-204">F# 核心程式庫會定義許多的 SI 單位類型和單位轉換。</span><span class="sxs-lookup"><span data-stu-id="db47b-204">The F# Core library defines many SI unit types and unit conversions.</span></span>  <span data-ttu-id="db47b-205">若要深入瞭解，請參閱[Microsoft.FSharp.Data.UnitSystems.SI 命名空間](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="db47b-205">To learn more, check out the [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).</span></span>

## <a name="classes-and-interfaces"></a><span data-ttu-id="db47b-206">類別和介面</span><span class="sxs-lookup"><span data-stu-id="db47b-206">Classes and Interfaces</span></span>

<span data-ttu-id="db47b-207">F# 也有完整的支援，.NET 類別[介面](./language-reference/interfaces.md)，[抽象類別](./language-reference/abstract-classes.md)，[繼承](./language-reference/inheritance.md)，依此類推。</span><span class="sxs-lookup"><span data-stu-id="db47b-207">F# also has full support for .NET classes, [Interfaces](./language-reference/interfaces.md), [Abstract Classes](./language-reference/abstract-classes.md), [Inheritance](./language-reference/inheritance.md), and so on.</span></span>

<span data-ttu-id="db47b-208">[類別](./language-reference/classes.md)是代表 .net 物件的類型，可以有屬性、方法和事件做為其[成員](./language-reference/members/index.md)。</span><span class="sxs-lookup"><span data-stu-id="db47b-208">[Classes](./language-reference/classes.md) are types that represent .NET objects, which can have properties, methods, and events as its [Members](./language-reference/members/index.md).</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

<span data-ttu-id="db47b-209">定義泛型類別也非常簡單。</span><span class="sxs-lookup"><span data-stu-id="db47b-209">Defining generic classes is also very straightforward.</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

<span data-ttu-id="db47b-210">若要執行介面，您可以使用`interface ... with`語法或[物件運算式](./language-reference/object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="db47b-210">To implement an Interface, you can use either `interface ... with` syntax or an [Object Expression](./language-reference/object-expressions.md).</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a><span data-ttu-id="db47b-211">要使用的類型</span><span class="sxs-lookup"><span data-stu-id="db47b-211">Which Types to Use</span></span>

<span data-ttu-id="db47b-212">類別、記錄、區分等位和元組的存在會導致一個重要的問題：您應該使用哪一項？</span><span class="sxs-lookup"><span data-stu-id="db47b-212">The presence of Classes, Records, Discriminated Unions, and Tuples leads to an important question: which should you use?</span></span>  <span data-ttu-id="db47b-213">就像生活中的大部分專案一樣，答案取決於您的情況。</span><span class="sxs-lookup"><span data-stu-id="db47b-213">Like most everything in life, the answer depends on your circumstances.</span></span>

<span data-ttu-id="db47b-214">元組非常適合用來從函式傳回多個值，並使用值的臨機操作匯總作為值本身。</span><span class="sxs-lookup"><span data-stu-id="db47b-214">Tuples are great for returning multiple values from a function, and using an ad-hoc aggregate of values as a value itself.</span></span>

<span data-ttu-id="db47b-215">記錄是來自元組的「逐步執行」，具有選擇性成員的命名標籤和支援。</span><span class="sxs-lookup"><span data-stu-id="db47b-215">Records are a "step up" from Tuples, having named labels and support for optional members.</span></span>  <span data-ttu-id="db47b-216">它們非常適合用來透過您的程式進行傳輸中的資料的低人。</span><span class="sxs-lookup"><span data-stu-id="db47b-216">They are great for a low-ceremony representation of data in-transit through your program.</span></span>  <span data-ttu-id="db47b-217">因為它們的結構相等，所以比較容易使用。</span><span class="sxs-lookup"><span data-stu-id="db47b-217">Because they have structural equality, they are easy to use with comparison.</span></span>

<span data-ttu-id="db47b-218">區分聯集有許多用途，但核心優點是能夠將它們與模式比對搭配使用，以考慮資料可擁有的所有可能「圖形」。</span><span class="sxs-lookup"><span data-stu-id="db47b-218">Discriminated Unions have many uses, but the core benefit is to be able to utilize them in conjunction with Pattern Matching to account for all possible "shapes" that a data can have.</span></span>  

<span data-ttu-id="db47b-219">類別非常適用于許多因素，例如當您需要表示資訊，以及將該資訊系結至功能時。</span><span class="sxs-lookup"><span data-stu-id="db47b-219">Classes are great for a huge number of reasons, such as when you need to represent information and also tie that information to functionality.</span></span>  <span data-ttu-id="db47b-220">根據經驗法則，當您具有概念上與某些資料系結的功能時，使用類別和麵向物件程式設計的原則是一個很大的好處。</span><span class="sxs-lookup"><span data-stu-id="db47b-220">As a rule of thumb, when you have functionality which is conceptually tied to some data, using Classes and the principles of Object-Oriented Programming is a big benefit.</span></span>  <span data-ttu-id="db47b-221">當與C#和 Visual Basic 交互操作時，類別也是慣用的資料類型，因為這些語言幾乎都是使用類別。</span><span class="sxs-lookup"><span data-stu-id="db47b-221">Classes are also the preferred data type when interoperating with C# and Visual Basic, as these languages use classes for nearly everything.</span></span>

## <a name="next-steps"></a><span data-ttu-id="db47b-222">後續步驟</span><span class="sxs-lookup"><span data-stu-id="db47b-222">Next Steps</span></span>

<span data-ttu-id="db47b-223">既然您已了解的一些主要功能的語言，您應該準備好開始撰寫第一個 F# 程式 ！</span><span class="sxs-lookup"><span data-stu-id="db47b-223">Now that you've seen some of the primary features of the language, you should be ready to write your first F# programs!</span></span>  <span data-ttu-id="db47b-224">查看[消費者入門](./tutorials/getting-started/index.md)以瞭解如何設定您的開發環境，並撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="db47b-224">Check out [Getting Started](./tutorials/getting-started/index.md) to learn how to set up your development environment and write some code.</span></span>

<span data-ttu-id="db47b-225">進一步瞭解的後續步驟可以是您喜歡的任何方式，但我們建議您[在中F#進行功能程式設計的簡介](./introduction-to-functional-programming/index.md)，以熟悉核心功能程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="db47b-225">The next steps for learning more can be whatever you like, but we recommend [Introduction to Functional Programming in F#](./introduction-to-functional-programming/index.md) to get comfortable with core Functional Programming concepts.</span></span>  <span data-ttu-id="db47b-226">這些會在建置強固的程式，在 F# 不可或缺。</span><span class="sxs-lookup"><span data-stu-id="db47b-226">These will be essential in building robust programs in F#.</span></span>

<span data-ttu-id="db47b-227">此外，請參閱[F# 語言參考](./language-reference/index.md)在 F# 中看到完整的概念性內容。</span><span class="sxs-lookup"><span data-stu-id="db47b-227">Also, check out the [F# Language Reference](./language-reference/index.md) to see a comprehensive collection of conceptual content on F#.</span></span>
