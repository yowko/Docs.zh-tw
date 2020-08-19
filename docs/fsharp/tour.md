---
title: F# 的教學課程
description: '請在本教學課程中使用程式碼範例，檢查 F # 程式設計語言的一些主要功能。'
ms.date: 08/14/2020
ms.openlocfilehash: b115317e1f47ef7e18333cae4145b99e11645579
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558591"
---
# <a name="tour-of-f"></a><span data-ttu-id="54d10-103">F 教學課程\#</span><span class="sxs-lookup"><span data-stu-id="54d10-103">Tour of F\#</span></span>

<span data-ttu-id="54d10-104">瞭解 F # 的最佳方式是讀取和寫入 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="54d10-104">The best way to learn about F# is to read and write F# code.</span></span> <span data-ttu-id="54d10-105">本文將逐步解說 F # 語言的一些重要功能，並提供您一些可在電腦上執行的程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="54d10-105">This article will act as a tour through some of the key features of the F# language and give you some code snippets that you can execute on your machine.</span></span> <span data-ttu-id="54d10-106">若要瞭解如何設定開發環境，請參閱 [消費者入門](get-started/index.md)。</span><span class="sxs-lookup"><span data-stu-id="54d10-106">To learn about setting up a development environment, check out [Getting Started](get-started/index.md).</span></span>

<span data-ttu-id="54d10-107">F # 中有兩個主要概念：函數和類型。</span><span class="sxs-lookup"><span data-stu-id="54d10-107">There are two primary concepts in F#: functions and types.</span></span>  <span data-ttu-id="54d10-108">本教學課程將著重在這兩個概念中的語言功能。</span><span class="sxs-lookup"><span data-stu-id="54d10-108">This tour will emphasize features of the language which fall into these two concepts.</span></span>

## <a name="executing-the-code-online"></a><span data-ttu-id="54d10-109">線上執行程式碼</span><span class="sxs-lookup"><span data-stu-id="54d10-109">Executing the code online</span></span>

<span data-ttu-id="54d10-110">如果您的電腦上沒有安裝 F #，您可以在 [WebAssembly 上使用 Try F #](https://tryfsharp.fsbolero.io/)，在您的瀏覽器中執行所有範例。</span><span class="sxs-lookup"><span data-stu-id="54d10-110">If you don't have F# installed on your machine, you can execute all of the samples in your browser with [Try F# on WebAssembly](https://tryfsharp.fsbolero.io/).</span></span> <span data-ttu-id="54d10-111">Ncave 是 F # 的方言，可直接在您的瀏覽器中執行。</span><span class="sxs-lookup"><span data-stu-id="54d10-111">Fable is a dialect of F# that executes directly in your browser.</span></span> <span data-ttu-id="54d10-112">若要查看複寫中接下來的範例，請參閱 Ncave 複寫的左側功能表列中的 **範例，> 瞭解 F # > 導覽** 。</span><span class="sxs-lookup"><span data-stu-id="54d10-112">To view the samples that follow in the REPL, check out **Samples > Learn > Tour of F#** in the left-hand menu bar of the Fable REPL.</span></span>

## <a name="functions-and-modules"></a><span data-ttu-id="54d10-113">函數和模組</span><span class="sxs-lookup"><span data-stu-id="54d10-113">Functions and Modules</span></span>

<span data-ttu-id="54d10-114">任何 F # 程式最基本的 ***部分都是*** 組織成 ***模組***的函式。</span><span class="sxs-lookup"><span data-stu-id="54d10-114">The most fundamental pieces of any F# program are ***functions*** organized into ***modules***.</span></span>  <span data-ttu-id="54d10-115">函式[會對輸入執行工作](./language-reference/functions/index.md)以產生輸出，並在[模組](./language-reference/modules.md)下組織，這些是您在 F # 中將專案分組的主要方式。</span><span class="sxs-lookup"><span data-stu-id="54d10-115">[Functions](./language-reference/functions/index.md) perform work on inputs to produce outputs, and they are organized under [Modules](./language-reference/modules.md), which are the primary way you group things in F#.</span></span>  <span data-ttu-id="54d10-116">它們是使用系結定義[ `let` 的，它](./language-reference/functions/let-bindings.md)會為函式命名並定義其引數。</span><span class="sxs-lookup"><span data-stu-id="54d10-116">They are defined using the [`let` binding](./language-reference/functions/let-bindings.md), which give the function a name and define its arguments.</span></span>

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

<span data-ttu-id="54d10-117">`let` 系結也是您將值系結至名稱的方式，類似于其他語言的變數。</span><span class="sxs-lookup"><span data-stu-id="54d10-117">`let` bindings are also how you bind a value to a name, similar to a variable in other languages.</span></span>  <span data-ttu-id="54d10-118">`let` 系結預設為 ***不可變*** ，這表示一旦值或函數系結至名稱之後，就無法就地變更。</span><span class="sxs-lookup"><span data-stu-id="54d10-118">`let` bindings are ***immutable*** by default, which means that once a value or function is bound to a name, it cannot be changed in-place.</span></span>  <span data-ttu-id="54d10-119">這與其他語言中的變數不同， ***這是可變動的，這***表示它們的值可以在任何時間點變更。</span><span class="sxs-lookup"><span data-stu-id="54d10-119">This is in contrast to variables in other languages, which are ***mutable***, meaning their values can be changed at any point in time.</span></span>  <span data-ttu-id="54d10-120">如果您需要可變的系結，您可以使用 `let mutable ...` 語法。</span><span class="sxs-lookup"><span data-stu-id="54d10-120">If you require a mutable binding, you can use `let mutable ...` syntax.</span></span>

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a><span data-ttu-id="54d10-121">數位、布林值和字串</span><span class="sxs-lookup"><span data-stu-id="54d10-121">Numbers, Booleans, and Strings</span></span>

<span data-ttu-id="54d10-122">作為 .NET 語言，F # 支援存在於 .NET 中的相同基礎基本 [類型](language-reference/basic-types.md) 。</span><span class="sxs-lookup"><span data-stu-id="54d10-122">As a .NET language, F# supports the same underlying [primitive types](language-reference/basic-types.md) that exist in .NET.</span></span>

<span data-ttu-id="54d10-123">以下是如何以 F # 表示不同的數位類型：</span><span class="sxs-lookup"><span data-stu-id="54d10-123">Here is how various numeric types are represented in F#:</span></span>

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

<span data-ttu-id="54d10-124">以下是布林值和執行基本條件式邏輯的樣子：</span><span class="sxs-lookup"><span data-stu-id="54d10-124">Here's what Boolean values and performing basic conditional logic looks like:</span></span>

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

<span data-ttu-id="54d10-125">以下是基本 [字串](./language-reference/strings.md) 操作的樣子：</span><span class="sxs-lookup"><span data-stu-id="54d10-125">And here's what basic [string](./language-reference/strings.md) manipulation looks like:</span></span>

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a><span data-ttu-id="54d10-126">Tuple</span><span class="sxs-lookup"><span data-stu-id="54d10-126">Tuples</span></span>

<span data-ttu-id="54d10-127">[元組](./language-reference/tuples.md) 在 F # 中是很大的交易。</span><span class="sxs-lookup"><span data-stu-id="54d10-127">[Tuples](./language-reference/tuples.md) are a big deal in F#.</span></span>  <span data-ttu-id="54d10-128">它們是未命名但排序值的群組，可視為值本身。</span><span class="sxs-lookup"><span data-stu-id="54d10-128">They are a grouping of unnamed, but ordered values, that can be treated as values themselves.</span></span>  <span data-ttu-id="54d10-129">將它們視為從其他值匯總的值。</span><span class="sxs-lookup"><span data-stu-id="54d10-129">Think of them as values which are aggregated from other values.</span></span>  <span data-ttu-id="54d10-130">它們有許多用途，例如方便從函式傳回多個值，或將值分組以進行某些特定的便利性。</span><span class="sxs-lookup"><span data-stu-id="54d10-130">They have many uses, such as conveniently returning multiple values from a function, or grouping values for some ad-hoc convenience.</span></span>

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

<span data-ttu-id="54d10-131">您也可以建立 `struct` 元組。</span><span class="sxs-lookup"><span data-stu-id="54d10-131">You can also create `struct` tuples.</span></span>  <span data-ttu-id="54d10-132">這些也會與 c # 7/Visual Basic 15 個元組（也就是元組）完全交互操作 `struct` ：</span><span class="sxs-lookup"><span data-stu-id="54d10-132">These also interoperate fully with C#7/Visual Basic 15 tuples, which are also `struct` tuples:</span></span>

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

<span data-ttu-id="54d10-133">請務必注意，因為 `struct` 元組是實值型別，所以無法隱含地轉換成參考元組，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="54d10-133">It's important to note that because `struct` tuples are value types, they cannot be implicitly converted to reference tuples, or vice versa.</span></span>  <span data-ttu-id="54d10-134">您必須在參考和結構元組之間明確地轉換。</span><span class="sxs-lookup"><span data-stu-id="54d10-134">You must explicitly convert between a reference and struct tuple.</span></span>

## <a name="pipelines-and-composition"></a><span data-ttu-id="54d10-135">管線和組合</span><span class="sxs-lookup"><span data-stu-id="54d10-135">Pipelines and Composition</span></span>

<span data-ttu-id="54d10-136">`|>`在 F # 中處理資料時，會廣泛使用管道運算子（例如）。</span><span class="sxs-lookup"><span data-stu-id="54d10-136">Pipe operators such as `|>` are used extensively when processing data in F#.</span></span> <span data-ttu-id="54d10-137">這些運算子是功能，可讓您以彈性的方式建立函式的「管線」。</span><span class="sxs-lookup"><span data-stu-id="54d10-137">These operators are functions that allow you to establish "pipelines" of functions in a flexible manner.</span></span> <span data-ttu-id="54d10-138">下列範例會逐步解說如何利用這些運算子來建立簡單的功能管線：</span><span class="sxs-lookup"><span data-stu-id="54d10-138">The following example walks through how you can take advantage of these operators to build a simple functional pipeline:</span></span>

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

<span data-ttu-id="54d10-139">先前的範例使用 F # 的許多功能，包括清單處理函式、第一級函式和 [部分應用程式](./language-reference/functions/index.md#partial-application-of-arguments)。</span><span class="sxs-lookup"><span data-stu-id="54d10-139">The previous sample made use of many features of F#, including list processing functions, first-class functions, and [partial application](./language-reference/functions/index.md#partial-application-of-arguments).</span></span> <span data-ttu-id="54d10-140">雖然對每個概念的深入瞭解都可能更簡單，但是在建立管線時，可以清楚地使用函式來處理資料。</span><span class="sxs-lookup"><span data-stu-id="54d10-140">Although a deep understanding of each of those concepts can become somewhat advanced, it should be clear how easily functions can be used to process data when building pipelines.</span></span>

## <a name="lists-arrays-and-sequences"></a><span data-ttu-id="54d10-141">清單、陣列和序列</span><span class="sxs-lookup"><span data-stu-id="54d10-141">Lists, Arrays, and Sequences</span></span>

<span data-ttu-id="54d10-142">清單、陣列和序列是 F # 核心程式庫中的三個主要集合類型。</span><span class="sxs-lookup"><span data-stu-id="54d10-142">Lists, Arrays, and Sequences are three primary collection types in the F# core library.</span></span>

<span data-ttu-id="54d10-143">[清單](./language-reference/lists.md) 是相同類型之專案的已排序、不可變的集合。</span><span class="sxs-lookup"><span data-stu-id="54d10-143">[Lists](./language-reference/lists.md) are ordered, immutable collections of elements of the same type.</span></span>  <span data-ttu-id="54d10-144">它們是單一連結的清單，這表示它們是用來進行列舉，但如果很大，則會有不佳的隨機存取和串連選項。</span><span class="sxs-lookup"><span data-stu-id="54d10-144">They are singly-linked lists, which means they are meant for enumeration, but a poor choice for random access and concatenation if they're large.</span></span>  <span data-ttu-id="54d10-145">這與其他熱門語言中的清單相較之下，通常不會使用單一連結的清單來表示清單。</span><span class="sxs-lookup"><span data-stu-id="54d10-145">This in contrast to Lists in other popular languages, which typically do not use a singly-linked list to represent Lists.</span></span>

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

<span data-ttu-id="54d10-146">[陣列](./language-reference/arrays.md) 是具有相同類型之專案的固定 *大小、可* 變動集合。</span><span class="sxs-lookup"><span data-stu-id="54d10-146">[Arrays](./language-reference/arrays.md) are fixed-size, *mutable* collections of elements of the same type.</span></span>  <span data-ttu-id="54d10-147">它們支援快速隨機存取專案，而且比 F # 清單更快，因為它們只是連續的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="54d10-147">They support fast random access of elements, and are faster than F# lists because they are just contiguous blocks of memory.</span></span>

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

<span data-ttu-id="54d10-148">[序列](./language-reference/sequences.md) 是元素的邏輯系列，全都是相同的類型。</span><span class="sxs-lookup"><span data-stu-id="54d10-148">[Sequences](./language-reference/sequences.md) are a logical series of elements, all of the same type.</span></span>  <span data-ttu-id="54d10-149">這些是比清單和陣列更一般的型別，可將您的「view」成任何邏輯系列元素。</span><span class="sxs-lookup"><span data-stu-id="54d10-149">These are a more general type than Lists and Arrays, capable of being your "view" into any logical series of elements.</span></span>  <span data-ttu-id="54d10-150">它們也有可能是 ***延遲***的，這表示只有在需要時，才可以計算元素。</span><span class="sxs-lookup"><span data-stu-id="54d10-150">They also stand out because they can be ***lazy***, which means that elements can be computed only when they are needed.</span></span>

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a><span data-ttu-id="54d10-151">遞迴函式</span><span class="sxs-lookup"><span data-stu-id="54d10-151">Recursive Functions</span></span>

<span data-ttu-id="54d10-152">處理集合或元素的順序通常是以 F # 中的 [遞迴](./language-reference/functions/index.md#recursive-functions) 來完成。</span><span class="sxs-lookup"><span data-stu-id="54d10-152">Processing collections or sequences of elements is typically done with [recursion](./language-reference/functions/index.md#recursive-functions) in F#.</span></span>  <span data-ttu-id="54d10-153">雖然 F # 支援迴圈和命令式程式設計，但最好是遞迴，因為這樣可以更輕鬆地確保正確性。</span><span class="sxs-lookup"><span data-stu-id="54d10-153">Although F# has support for loops and imperative programming, recursion is preferred because it is easier to guarantee correctness.</span></span>

> [!NOTE]
> <span data-ttu-id="54d10-154">下列範例會利用運算式的模式比對 `match` 。</span><span class="sxs-lookup"><span data-stu-id="54d10-154">The following example makes use of the pattern matching via the `match` expression.</span></span>  <span data-ttu-id="54d10-155">本文稍後將說明此基礎結構。</span><span class="sxs-lookup"><span data-stu-id="54d10-155">This fundamental construct is covered later in this article.</span></span>

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

<span data-ttu-id="54d10-156">F # 也有 Tail 呼叫優化的完整支援，這是將遞迴呼叫優化，使其與迴圈結構一樣快的方式。</span><span class="sxs-lookup"><span data-stu-id="54d10-156">F# also has full support for Tail Call Optimization, which is a way to optimize recursive calls so that they are just as fast as a loop construct.</span></span>

## <a name="record-and-discriminated-union-types"></a><span data-ttu-id="54d10-157">記錄和區分聯集類型</span><span class="sxs-lookup"><span data-stu-id="54d10-157">Record and Discriminated Union Types</span></span>

<span data-ttu-id="54d10-158">記錄和等位類型是 F # 程式碼中使用的兩個基本資料類型，通常是在 F # 程式中表示資料的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="54d10-158">Record and Union types are two fundamental data types used in F# code, and are generally the best way to represent data in an F# program.</span></span>  <span data-ttu-id="54d10-159">雖然這會讓它們類似于其他語言的類別，但其中一個主要差異在於它們具有結構化相等的語法。</span><span class="sxs-lookup"><span data-stu-id="54d10-159">Although this makes them similar to classes in other languages, one of their primary differences is that they have structural equality semantics.</span></span>  <span data-ttu-id="54d10-160">這表示它們是「原生」可比較且相等的相等，只要檢查其中一個是否等於另一個。</span><span class="sxs-lookup"><span data-stu-id="54d10-160">This means that they are "natively" comparable and equality is straightforward - just check if one is equal to the other.</span></span>

<span data-ttu-id="54d10-161">[記錄](./language-reference/records.md) 是已命名值的匯總，具有選擇性成員 (例如) 方法。</span><span class="sxs-lookup"><span data-stu-id="54d10-161">[Records](./language-reference/records.md) are an aggregate of named values, with optional members (such as methods).</span></span>  <span data-ttu-id="54d10-162">如果您熟悉 c # 或 JAVA，則這些應該類似于 Poco 或 Pojo，只是結構相等且較不會發生。</span><span class="sxs-lookup"><span data-stu-id="54d10-162">If you're familiar with C# or Java, then these should feel similar to POCOs or POJOs - just with structural equality and less ceremony.</span></span>

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

<span data-ttu-id="54d10-163">您也可以將記錄表示為結構。</span><span class="sxs-lookup"><span data-stu-id="54d10-163">You can also represent Records as structs.</span></span> <span data-ttu-id="54d10-164">這是使用屬性來完成的 `[<Struct>]` ：</span><span class="sxs-lookup"><span data-stu-id="54d10-164">This is done with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

<span data-ttu-id="54d10-165">差異聯集[ (du) ](./language-reference/discriminated-unions.md)是可能是數個名稱的表單或案例的值。</span><span class="sxs-lookup"><span data-stu-id="54d10-165">[Discriminated Unions (DUs)](./language-reference/discriminated-unions.md) are values which could be a number of named forms or cases.</span></span>  <span data-ttu-id="54d10-166">儲存在類型中的資料可以是數個相異值的其中一個。</span><span class="sxs-lookup"><span data-stu-id="54d10-166">Data stored in the type can be one of several distinct values.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

<span data-ttu-id="54d10-167">您也可以使用 Du 作為 *單一案例*的差異聯集，以協助您在基本類型上進行領域模型化。</span><span class="sxs-lookup"><span data-stu-id="54d10-167">You can also use DUs as *Single-Case Discriminated Unions*, to help with domain modeling over primitive types.</span></span>  <span data-ttu-id="54d10-168">通常會使用時間、字串和其他基本型別來代表某個東西，因此會提供特定意義。</span><span class="sxs-lookup"><span data-stu-id="54d10-168">Often times, strings and other primitive types are used to represent something, and are thus given a particular meaning.</span></span>  <span data-ttu-id="54d10-169">不過，僅使用資料的基本標記法可能會導致錯誤地指派不正確的值！</span><span class="sxs-lookup"><span data-stu-id="54d10-169">However, using only the primitive representation of the data can result in mistakenly assigning an incorrect value!</span></span>  <span data-ttu-id="54d10-170">將每一種類型的資訊表示為不同的單一案例聯集，可以在此案例中強制執行正確性。</span><span class="sxs-lookup"><span data-stu-id="54d10-170">Representing each type of information as a distinct single-case union can enforce correctness in this scenario.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

<span data-ttu-id="54d10-171">如上一個範例所示，若要取得單一案例差異聯集的基礎值，您必須明確地將它解除包裝。</span><span class="sxs-lookup"><span data-stu-id="54d10-171">As the above sample demonstrates, to get the underlying value in a single-case Discriminated Union, you must explicitly unwrap it.</span></span>

<span data-ttu-id="54d10-172">此外，Du 也支援遞迴定義，可讓您輕鬆地表示樹狀結構和原本遞迴的資料。</span><span class="sxs-lookup"><span data-stu-id="54d10-172">Additionally, DUs also support recursive definitions, allowing you to easily represent trees and inherently recursive data.</span></span>  <span data-ttu-id="54d10-173">例如，以下是您可以使用和函式來表示二進位搜尋樹狀結構的方式 `exists` `insert` 。</span><span class="sxs-lookup"><span data-stu-id="54d10-173">For example, here's how you can represent a Binary Search Tree with `exists` and `insert` functions.</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

<span data-ttu-id="54d10-174">由於 Du 可讓您以資料類型代表樹狀結構的遞迴結構，因此在此遞迴結構上運作相當簡單，而且保證正確性。</span><span class="sxs-lookup"><span data-stu-id="54d10-174">Because DUs allow you to represent the recursive structure of the tree in the data type, operating on this recursive structure is straightforward and guarantees correctness.</span></span>  <span data-ttu-id="54d10-175">在模式比對中也支援，如下所示。</span><span class="sxs-lookup"><span data-stu-id="54d10-175">It is also supported in pattern matching, as shown below.</span></span>

<span data-ttu-id="54d10-176">此外，您可以 `struct` 使用屬性將 du 表示為 s `[<Struct>]` ：</span><span class="sxs-lookup"><span data-stu-id="54d10-176">Additionally, you can represent DUs as `struct`s with the `[<Struct>]` attribute:</span></span>

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

<span data-ttu-id="54d10-177">不過，在這種情況下，有兩個重要事項要牢記在心：</span><span class="sxs-lookup"><span data-stu-id="54d10-177">However, there are two key things to keep in mind when doing so:</span></span>

1. <span data-ttu-id="54d10-178">無法遞迴定義結構 DU。</span><span class="sxs-lookup"><span data-stu-id="54d10-178">A struct DU cannot be recursively-defined.</span></span>
2. <span data-ttu-id="54d10-179">結構 DU 的每個案例都必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="54d10-179">A struct DU must have unique names for each of its cases.</span></span>

<span data-ttu-id="54d10-180">無法遵循上述動作將會導致編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="54d10-180">Failure to follow the above will result in a compilation error.</span></span>

## <a name="pattern-matching"></a><span data-ttu-id="54d10-181">模式比對</span><span class="sxs-lookup"><span data-stu-id="54d10-181">Pattern Matching</span></span>

<span data-ttu-id="54d10-182">[模式](./language-reference/pattern-matching.md) 比對是 f # 語言功能，可讓您在 f # 類型上操作的正確性。</span><span class="sxs-lookup"><span data-stu-id="54d10-182">[Pattern Matching](./language-reference/pattern-matching.md) is the F# language feature which enables correctness for operating on F# types.</span></span>  <span data-ttu-id="54d10-183">在上述範例中，您可能已注意到很多 `match x with ...` 語法。</span><span class="sxs-lookup"><span data-stu-id="54d10-183">In the above samples, you probably noticed quite a bit of `match x with ...` syntax.</span></span>  <span data-ttu-id="54d10-184">此結構可讓編譯器瞭解資料類型的「圖形」，以強制您在使用資料類型時，透過所謂的完整模式比對來考慮所有可能的情況。</span><span class="sxs-lookup"><span data-stu-id="54d10-184">This construct allows the compiler, which can understand the "shape" of data types, to force you to account for all possible cases when using a data type through what is known as Exhaustive Pattern Matching.</span></span>  <span data-ttu-id="54d10-185">這在正確性方面相當強大，而且可以用來「增益」，這通常是執行時間在編譯時間方面的顧慮。</span><span class="sxs-lookup"><span data-stu-id="54d10-185">This is incredibly powerful for correctness, and can be cleverly used to "lift" what would normally be a runtime concern into compile-time.</span></span>

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

<span data-ttu-id="54d10-186">您可能已經注意到，這是使用 `_` 模式。</span><span class="sxs-lookup"><span data-stu-id="54d10-186">Something you may have noticed is the use of the `_` pattern.</span></span>  <span data-ttu-id="54d10-187">這就是所謂的 [萬用字元模式](./language-reference/pattern-matching.md#wildcard-pattern)，也就是說「我不在意什麼東西」的方法。</span><span class="sxs-lookup"><span data-stu-id="54d10-187">This is known as the [Wildcard Pattern](./language-reference/pattern-matching.md#wildcard-pattern), which is a way of saying "I don't care what something is".</span></span>  <span data-ttu-id="54d10-188">雖然很方便，但您可以不小心略過詳盡的模式比對，如果您不小心使用，則無法再從編譯時期大規模地規範獲益 `_` 。</span><span class="sxs-lookup"><span data-stu-id="54d10-188">Although convenient, you can accidentally bypass Exhaustive Pattern Matching and no longer benefit from compile-time enforcements if you aren't careful in using `_`.</span></span>  <span data-ttu-id="54d10-189">當您在模式比對時不在意某些分解型別的片段，或是當您在模式比對運算式中列舉所有有意義的案例時，最好使用它。</span><span class="sxs-lookup"><span data-stu-id="54d10-189">It is best used when you don't care about certain pieces of a decomposed type when pattern matching, or the final clause when you have enumerated all meaningful cases in a pattern matching expression.</span></span>

<span data-ttu-id="54d10-190">在下列範例中， `_` 當剖析作業失敗時，會使用案例。</span><span class="sxs-lookup"><span data-stu-id="54d10-190">In the following example, the `_` case is used when a parse operation fails.</span></span>

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L744-L762)]

<span data-ttu-id="54d10-191">[現用模式](./language-reference/active-patterns.md) 是另一種功能強大的結構，可搭配模式比對使用。</span><span class="sxs-lookup"><span data-stu-id="54d10-191">[Active Patterns](./language-reference/active-patterns.md) are another powerful construct to use with pattern matching.</span></span>  <span data-ttu-id="54d10-192">它們可讓您將輸入資料分割成自訂表單，並在模式比對呼叫位置分解它們。</span><span class="sxs-lookup"><span data-stu-id="54d10-192">They allow you to partition input data into custom forms, decomposing them at the pattern match call site.</span></span>  <span data-ttu-id="54d10-193">它們也可以參數化，因此可讓您將資料分割定義為函數。</span><span class="sxs-lookup"><span data-stu-id="54d10-193">They can also be parameterized, thus allowing to define the partition as a function.</span></span>  <span data-ttu-id="54d10-194">擴充先前的範例以支援現用模式看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="54d10-194">Expanding the previous example to support Active Patterns looks something like this:</span></span>

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a><span data-ttu-id="54d10-195">選用類型</span><span class="sxs-lookup"><span data-stu-id="54d10-195">Optional Types</span></span>

<span data-ttu-id="54d10-196">差異聯集類型的一個特殊案例是選項類型，因此它是 F # 核心程式庫的一部分。</span><span class="sxs-lookup"><span data-stu-id="54d10-196">One special case of Discriminated Union types is the Option Type, which is so useful that it's a part of the F# core library.</span></span>

<span data-ttu-id="54d10-197">[選項類型](./language-reference/options.md) 是代表兩種情況之一的類型：值，或完全沒有。</span><span class="sxs-lookup"><span data-stu-id="54d10-197">[The Option Type](./language-reference/options.md) is a type which represents one of two cases: a value, or nothing at all.</span></span>  <span data-ttu-id="54d10-198">在任何情況下，其值可能會或可能不會由特定作業產生。</span><span class="sxs-lookup"><span data-stu-id="54d10-198">It is used in any scenario where a value may or may not result from a particular operation.</span></span>  <span data-ttu-id="54d10-199">然後，這會強制您考慮這兩種情況，使其成為編譯時期的考慮，而不是執行時間的考慮。</span><span class="sxs-lookup"><span data-stu-id="54d10-199">This then forces you to account for both cases, making it a compile-time concern rather than a runtime concern.</span></span>  <span data-ttu-id="54d10-200">這些通常用於用來代表「nothing」的 Api `null` ，因此 `NullReferenceException` 在許多情況下都不需要擔心。</span><span class="sxs-lookup"><span data-stu-id="54d10-200">These are often used in APIs where `null` is used to represent "nothing" instead, thus eliminating the need to worry about `NullReferenceException` in many circumstances.</span></span>

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a><span data-ttu-id="54d10-201">測量單位</span><span class="sxs-lookup"><span data-stu-id="54d10-201">Units of Measure</span></span>

<span data-ttu-id="54d10-202">F # 類型系統的一項獨特功能，就是能夠透過測量單位提供數值常值的內容。</span><span class="sxs-lookup"><span data-stu-id="54d10-202">One unique feature of F#'s type system is the ability to provide context for numeric literals through Units of Measure.</span></span>

<span data-ttu-id="54d10-203">[測量單位](./language-reference/units-of-measure.md) 可讓您將數數值型別與某個單位（例如計量）建立關聯，並讓函式對單位（而非數值常值）執行工作。</span><span class="sxs-lookup"><span data-stu-id="54d10-203">[Units of Measure](./language-reference/units-of-measure.md) allow you to associate a numeric type to a unit, such as Meters, and have functions perform work on units rather than numeric literals.</span></span>  <span data-ttu-id="54d10-204">如此一來，編譯器就可以驗證在特定內容下傳遞的數值常數值型別是否合理，從而消除與該工作類型相關聯的執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="54d10-204">This enables the compiler to verify that the types of numeric literals passed in make sense under a certain context, thus eliminating runtime errors associated with that kind of work.</span></span>

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

<span data-ttu-id="54d10-205">F # 核心程式庫會定義許多 SI 單位類型和單位轉換。</span><span class="sxs-lookup"><span data-stu-id="54d10-205">The F# Core library defines many SI unit types and unit conversions.</span></span>  <span data-ttu-id="54d10-206">若要深入瞭解，請參閱 [fsharp.core. UnitSystems. Unitsymbols.s 命名空間](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitsymbols.html)。</span><span class="sxs-lookup"><span data-stu-id="54d10-206">To learn more, check out the [FSharp.Data.UnitSystems.SI.UnitSymbols Namespace](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitsymbols.html).</span></span>

## <a name="classes-and-interfaces"></a><span data-ttu-id="54d10-207">類別和介面</span><span class="sxs-lookup"><span data-stu-id="54d10-207">Classes and Interfaces</span></span>

<span data-ttu-id="54d10-208">F # 也有 .NET 類別、 [介面](./language-reference/interfaces.md)、 [抽象類別](./language-reference/abstract-classes.md)、 [繼承](./language-reference/inheritance.md)等的完整支援。</span><span class="sxs-lookup"><span data-stu-id="54d10-208">F# also has full support for .NET classes, [Interfaces](./language-reference/interfaces.md), [Abstract Classes](./language-reference/abstract-classes.md), [Inheritance](./language-reference/inheritance.md), and so on.</span></span>

<span data-ttu-id="54d10-209">[類別](./language-reference/classes.md) 是代表 .net 物件的類型，其 [成員](./language-reference/members/index.md)可以有屬性、方法和事件。</span><span class="sxs-lookup"><span data-stu-id="54d10-209">[Classes](./language-reference/classes.md) are types that represent .NET objects, which can have properties, methods, and events as its [Members](./language-reference/members/index.md).</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

<span data-ttu-id="54d10-210">定義泛型類別也非常簡單。</span><span class="sxs-lookup"><span data-stu-id="54d10-210">Defining generic classes is also very straightforward.</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

<span data-ttu-id="54d10-211">若要執行介面，您可以使用 `interface ... with` 語法或 [物件運算式](./language-reference/object-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="54d10-211">To implement an Interface, you can use either `interface ... with` syntax or an [Object Expression](./language-reference/object-expressions.md).</span></span>

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a><span data-ttu-id="54d10-212">要使用的類型</span><span class="sxs-lookup"><span data-stu-id="54d10-212">Which Types to Use</span></span>

<span data-ttu-id="54d10-213">類別、記錄、差別聯集和元組的存在會導致重要問題：您應該使用哪一項？</span><span class="sxs-lookup"><span data-stu-id="54d10-213">The presence of Classes, Records, Discriminated Unions, and Tuples leads to an important question: which should you use?</span></span>  <span data-ttu-id="54d10-214">就像大部分的生活一樣，答案都取決於您的情況。</span><span class="sxs-lookup"><span data-stu-id="54d10-214">Like most everything in life, the answer depends on your circumstances.</span></span>

<span data-ttu-id="54d10-215">元組很適合用來傳回函式的多個值，並使用特定值的隨選匯總作為值本身。</span><span class="sxs-lookup"><span data-stu-id="54d10-215">Tuples are great for returning multiple values from a function, and using an ad-hoc aggregate of values as a value itself.</span></span>

<span data-ttu-id="54d10-216">記錄是來自元組的「逐步執行」，具有命名標籤和選擇性成員的支援。</span><span class="sxs-lookup"><span data-stu-id="54d10-216">Records are a "step up" from Tuples, having named labels and support for optional members.</span></span>  <span data-ttu-id="54d10-217">它們很適合用於透過您的程式傳輸中資料的低人員表示。</span><span class="sxs-lookup"><span data-stu-id="54d10-217">They are great for a low-ceremony representation of data in-transit through your program.</span></span>  <span data-ttu-id="54d10-218">因為它們的結構相等，所以很容易與比較使用。</span><span class="sxs-lookup"><span data-stu-id="54d10-218">Because they have structural equality, they are easy to use with comparison.</span></span>

<span data-ttu-id="54d10-219">差別聯集有許多用途，但核心優點是能夠搭配模式比對使用，以考慮資料可擁有的所有可能「圖形」。</span><span class="sxs-lookup"><span data-stu-id="54d10-219">Discriminated Unions have many uses, but the core benefit is to be able to utilize them in conjunction with Pattern Matching to account for all possible "shapes" that a data can have.</span></span>  

<span data-ttu-id="54d10-220">類別很適合許多原因，例如當您需要表示資訊，同時也將該資訊系結至功能時。</span><span class="sxs-lookup"><span data-stu-id="54d10-220">Classes are great for a huge number of reasons, such as when you need to represent information and also tie that information to functionality.</span></span>  <span data-ttu-id="54d10-221">根據經驗法則，當您有在概念上系結至某些資料的功能時，使用類別和麵向物件程式設計的原則是一項很大的好處。</span><span class="sxs-lookup"><span data-stu-id="54d10-221">As a rule of thumb, when you have functionality which is conceptually tied to some data, using Classes and the principles of Object-Oriented Programming is a big benefit.</span></span>  <span data-ttu-id="54d10-222">與 c # 和 Visual Basic 交互操作時，類別也是慣用的資料類型，因為這些語言幾乎都是使用類別。</span><span class="sxs-lookup"><span data-stu-id="54d10-222">Classes are also the preferred data type when interoperating with C# and Visual Basic, as these languages use classes for nearly everything.</span></span>

## <a name="next-steps"></a><span data-ttu-id="54d10-223">後續步驟</span><span class="sxs-lookup"><span data-stu-id="54d10-223">Next Steps</span></span>

<span data-ttu-id="54d10-224">現在您已看過語言的一些主要功能，接下來您應該準備好撰寫您的第一個 F # 程式！</span><span class="sxs-lookup"><span data-stu-id="54d10-224">Now that you've seen some of the primary features of the language, you should be ready to write your first F# programs!</span></span>  <span data-ttu-id="54d10-225">查看 [消費者入門](get-started/index.md) ，瞭解如何設定您的開發環境並撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="54d10-225">Check out [Getting Started](get-started/index.md) to learn how to set up your development environment and write some code.</span></span>

<span data-ttu-id="54d10-226">後續學習的步驟可以是您喜歡的任何內容，但我們建議使用 [F # 中的功能程式設計](./introduction-to-functional-programming/index.md) ，以熟悉核心功能程式設計概念。</span><span class="sxs-lookup"><span data-stu-id="54d10-226">The next steps for learning more can be whatever you like, but we recommend [Introduction to Functional Programming in F#](./introduction-to-functional-programming/index.md) to get comfortable with core Functional Programming concepts.</span></span>  <span data-ttu-id="54d10-227">在 F # 中建立強大的程式時，這些都是不可或缺的。</span><span class="sxs-lookup"><span data-stu-id="54d10-227">These will be essential in building robust programs in F#.</span></span>

<span data-ttu-id="54d10-228">此外，請參閱 [f # 語言參考](./language-reference/index.md) ，以查看 f # 的完整概念內容集合。</span><span class="sxs-lookup"><span data-stu-id="54d10-228">Also, check out the [F# Language Reference](./language-reference/index.md) to see a comprehensive collection of conceptual content on F#.</span></span>
