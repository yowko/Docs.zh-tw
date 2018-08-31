---
title: C# 的歷史 - C# 指南
description: 最早的語言版本有哪些內容，而在之後有什麼演變？
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 90f480d7b25ebe308d1f1cb3d4c117f36f7dd9bf
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2018
ms.locfileid: "42751978"
---
# <a name="the-history-of-c"></a><span data-ttu-id="0ddb7-103">C# 的歷史</span><span class="sxs-lookup"><span data-stu-id="0ddb7-103">The history of C#</span></span> #

<span data-ttu-id="0ddb7-104">最早的語言版本有哪些內容？</span><span class="sxs-lookup"><span data-stu-id="0ddb7-104">What did the language look like in its earliest incarnations?</span></span> <span data-ttu-id="0ddb7-105">而在那之後的幾年有什麼演變？</span><span class="sxs-lookup"><span data-stu-id="0ddb7-105">And how has it evolved in the years since?</span></span>

## <a name="c-version-10"></a><span data-ttu-id="0ddb7-106">C# 1.0 版</span><span class="sxs-lookup"><span data-stu-id="0ddb7-106">C# version 1.0</span></span>

<span data-ttu-id="0ddb7-107">當您回過頭看，C# 1.0 版很多看起來很像 Java。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-107">When you go back and look, C# version 1.0 looked a lot like Java.</span></span> <span data-ttu-id="0ddb7-108">在[其聲明的 ECMA 設計目標當中](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)，它試圖成為「簡單、現代化、一般用途的物件導向語言」。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-108">As [part of its stated design goals for ECMA](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), it sought to be a "simple, modern, general-purpose object-oriented language."</span></span>  <span data-ttu-id="0ddb7-109">同時，看似 Java 表示它達成了那些早期的設計目標。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-109">At the time, looking like Java meant it achieved those early design goals.</span></span>

<span data-ttu-id="0ddb7-110">但如果您現在回顧 C# 1.0，會覺得有點暈眩。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-110">But if you look back on C# 1.0 now, you'd find yourself a little dizzy.</span></span> <span data-ttu-id="0ddb7-111">它缺乏內建的非同步功能和部分圍繞著您視為理所當然的泛型熟練功能。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-111">It lacked the built-in async capabilities and some of the slick functionality around generics you take for granted.</span></span> <span data-ttu-id="0ddb7-112">事實上，它完全缺乏了泛型。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-112">As a matter of fact, it lacked generics altogether.</span></span>  <span data-ttu-id="0ddb7-113">那麼 [LINQ](../linq/index.md) 呢？</span><span class="sxs-lookup"><span data-stu-id="0ddb7-113">And [LINQ](../linq/index.md)?</span></span> <span data-ttu-id="0ddb7-114">尚無法使用。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-114">Not available yet.</span></span> <span data-ttu-id="0ddb7-115">那些新增項目需要好幾年才會出現。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-115">Those additions would take some years to come out.</span></span>

<span data-ttu-id="0ddb7-116">C# 1.0 版看起來與現今相比去除了一些功能。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-116">C# version 1.0 looked stripped of features, compared to today.</span></span> <span data-ttu-id="0ddb7-117">您會發現自己撰寫一些詳細的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-117">You'd find yourself writing some verbose code.</span></span> <span data-ttu-id="0ddb7-118">但您仍然必須從某處開始。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-118">But yet, you have to start somewhere.</span></span> <span data-ttu-id="0ddb7-119">C# 1.0 版是 Windows 平台上可行的 Java 替代方案。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-119">C# version 1.0 was a viable alternative to Java on the Windows platform.</span></span>

<span data-ttu-id="0ddb7-120">C# 1.0 的主要功能包含：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-120">The major features of C# 1.0 included:</span></span>

- [<span data-ttu-id="0ddb7-121">類別</span><span class="sxs-lookup"><span data-stu-id="0ddb7-121">Classes</span></span>](../programming-guide/classes-and-structs/classes.md)
- [<span data-ttu-id="0ddb7-122">結構</span><span class="sxs-lookup"><span data-stu-id="0ddb7-122">Structs</span></span>](../programming-guide/classes-and-structs/structs.md)
- [<span data-ttu-id="0ddb7-123">介面</span><span class="sxs-lookup"><span data-stu-id="0ddb7-123">Interfaces</span></span>](../programming-guide/interfaces/index.md)
- [<span data-ttu-id="0ddb7-124">事件</span><span class="sxs-lookup"><span data-stu-id="0ddb7-124">Events</span></span>](../events-overview.md)
- [<span data-ttu-id="0ddb7-125">屬性</span><span class="sxs-lookup"><span data-stu-id="0ddb7-125">Properties</span></span>](../properties.md)
- [<span data-ttu-id="0ddb7-126">委派</span><span class="sxs-lookup"><span data-stu-id="0ddb7-126">Delegates</span></span>](../delegates-overview.md)
- [<span data-ttu-id="0ddb7-127">運算式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-127">Expressions</span></span>](../programming-guide/statements-expressions-operators/expressions.md)
- [<span data-ttu-id="0ddb7-128">陳述式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-128">Statements</span></span>](../programming-guide/statements-expressions-operators/statements.md)
- [<span data-ttu-id="0ddb7-129">屬性</span><span class="sxs-lookup"><span data-stu-id="0ddb7-129">Attributes</span></span>](../programming-guide/concepts/attributes/index.md)
- <span data-ttu-id="0ddb7-130">常值</span><span class="sxs-lookup"><span data-stu-id="0ddb7-130">Literals</span></span>

## <a name="c-version-20"></a><span data-ttu-id="0ddb7-131">C# 2.0 版</span><span class="sxs-lookup"><span data-stu-id="0ddb7-131">C# version 2.0</span></span>

<span data-ttu-id="0ddb7-132">現在事情開始變得有趣。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-132">Now things start to get interesting.</span></span> <span data-ttu-id="0ddb7-133">讓我們看看 2005 年與 Visual Studio 2005 一起發行的 C# 2.0 中，一些主要功能：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-133">Let's take a look at some major features of C# 2.0, released in 2005, along with Visual Studio 2005:</span></span>

- [<span data-ttu-id="0ddb7-134">泛型</span><span class="sxs-lookup"><span data-stu-id="0ddb7-134">Generics</span></span>](../programming-guide/generics/index.md)
- [<span data-ttu-id="0ddb7-135">部分型別</span><span class="sxs-lookup"><span data-stu-id="0ddb7-135">Partial types</span></span>](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [<span data-ttu-id="0ddb7-136">匿名方法</span><span class="sxs-lookup"><span data-stu-id="0ddb7-136">Anonymous methods</span></span>](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [<span data-ttu-id="0ddb7-137">可為 Null 的型別</span><span class="sxs-lookup"><span data-stu-id="0ddb7-137">Nullable types</span></span>](../programming-guide/nullable-types/index.md)
- [<span data-ttu-id="0ddb7-138">迭代器</span><span class="sxs-lookup"><span data-stu-id="0ddb7-138">Iterators</span></span>](../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="0ddb7-139">共變數和反變數</span><span class="sxs-lookup"><span data-stu-id="0ddb7-139">Covariance and contravariance</span></span>](../programming-guide/concepts/covariance-contravariance/index.md)

<span data-ttu-id="0ddb7-140">其他 C# 2.0 功能將功能新增至現有功能：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-140">Other C# 2.0 features added capabilities to existing features:</span></span>

- <span data-ttu-id="0ddb7-141">Getter/setter 不同協助工具</span><span class="sxs-lookup"><span data-stu-id="0ddb7-141">Getter/setter separate accessibility</span></span>
- <span data-ttu-id="0ddb7-142">方法群組轉換 (委派)</span><span class="sxs-lookup"><span data-stu-id="0ddb7-142">Method group conversions (delegates)</span></span>
- <span data-ttu-id="0ddb7-143">靜態類別</span><span class="sxs-lookup"><span data-stu-id="0ddb7-143">Static classes</span></span>
- <span data-ttu-id="0ddb7-144">委派推斷</span><span class="sxs-lookup"><span data-stu-id="0ddb7-144">Delegate inference</span></span>

<span data-ttu-id="0ddb7-145">雖然 C# 一開始可能是泛型的物件導向 (OO) 語言，但 C# 2.0 版很急促地改變了。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-145">While C# may have started as a generic Object-Oriented (OO) language, C# version 2.0 changed that in a hurry.</span></span> <span data-ttu-id="0ddb7-146">穩定之後，它們追蹤一些嚴重的開發人員痛苦點。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-146">Once they had their feet under them, they went after some serious developer pain points.</span></span> <span data-ttu-id="0ddb7-147">而且是徹底地追隨。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-147">And they went after them in a significant way.</span></span>

<span data-ttu-id="0ddb7-148">使用泛型時，型別和方法可以操作任意型別，同時仍然保留型別安全。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-148">With generics, types and methods can operate on an arbitrary type while still retaining type safety.</span></span> <span data-ttu-id="0ddb7-149">例如，<xref:System.Collections.Generic.List%601> 可讓您具有 `List<string>` 或 `List<int>`，並且對那些字串或整數逐一執行型別安全的作業。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-149">For instance, having a <xref:System.Collections.Generic.List%601> lets you have `List<string>` or `List<int>` and perform type-safe operations on those strings or integers while you iterate through them.</span></span> <span data-ttu-id="0ddb7-150">使用泛型最好不要建立衍生自 `ArrayList` 的 `ListInt`，或針對每個作業從 `Object` 轉型。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-150">Using generics is better than create `ListInt` that derives from `ArrayList`  or casting from `Object` for every operation.</span></span>

<span data-ttu-id="0ddb7-151">C# 2.0 版帶來了迭代器。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-151">C# version 2.0 brought iterators.</span></span> <span data-ttu-id="0ddb7-152">簡單的說，迭代器讓您使用 `foreach` 迴圈檢查 `List` (或其他可列舉型別) 中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-152">To put it succinctly, iterators let you examine all the items in a `List` (or other Enumerable types) with a `foreach` loop.</span></span> <span data-ttu-id="0ddb7-153">將迭代器當成語言的頭等部分能大幅增強語言的可讀性，並讓人們能理解程式碼。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-153">Having iterators as a first-class part of the language dramatically enhanced readability of the language and people's ability to reason about the code.</span></span>

<span data-ttu-id="0ddb7-154">但 C# 仍繼續追趕 Java。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-154">And yet, C# continued to play a bit of catch-up with Java.</span></span> <span data-ttu-id="0ddb7-155">Java 已經發行了包含泛型和迭代器的版本。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-155">Java had already released versions that included generics and iterators.</span></span> <span data-ttu-id="0ddb7-156">但是，很快就會變更，因為語言會持續朝不同方向發展。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-156">But that would soon change as the languages continued to evolve apart.</span></span>

## <a name="c-version-30"></a><span data-ttu-id="0ddb7-157">C# 3.0 版</span><span class="sxs-lookup"><span data-stu-id="0ddb7-157">C# version 3.0</span></span>

<span data-ttu-id="0ddb7-158">C# 3.0 版在 2007 年晚期和 Visual Studio 2008 一起出現，不過語言功能的完整陣容實際上是在 .NET Framework 3.5 版時齊備。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-158">C# version 3.0 came in late 2007, along with Visual Studio 2008, though the full boat of language features would actually come with .NET Framework version 3.5.</span></span> <span data-ttu-id="0ddb7-159">這個版本標記了 C# 發展的一項重大變更。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-159">This version marked a major change in the growth of C#.</span></span> <span data-ttu-id="0ddb7-160">它將 C# 樹立為真正令人敬佩的程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-160">It established C# as a truly formidable programming language.</span></span> <span data-ttu-id="0ddb7-161">讓我們看看此版本的一些主要功能：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-161">Let's take a look at some major features in this version:</span></span>

- [<span data-ttu-id="0ddb7-162">自動實作屬性</span><span class="sxs-lookup"><span data-stu-id="0ddb7-162">Auto implemented properties</span></span>](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [<span data-ttu-id="0ddb7-163">匿名型別</span><span class="sxs-lookup"><span data-stu-id="0ddb7-163">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="0ddb7-164">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-164">Query expressions</span></span>](../linq/query-expression-basics.md)
- [<span data-ttu-id="0ddb7-165">Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-165">Lambda expression</span></span>](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [<span data-ttu-id="0ddb7-166">運算式樹狀架構</span><span class="sxs-lookup"><span data-stu-id="0ddb7-166">Expression trees</span></span>](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [<span data-ttu-id="0ddb7-167">擴充方法</span><span class="sxs-lookup"><span data-stu-id="0ddb7-167">Extension methods</span></span>](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)
- [<span data-ttu-id="0ddb7-168">隱含型別區域變數</span><span class="sxs-lookup"><span data-stu-id="0ddb7-168">Implicitly typed local variables</span></span>](../language-reference/keywords/var.md)
- [<span data-ttu-id="0ddb7-169">部分方法</span><span class="sxs-lookup"><span data-stu-id="0ddb7-169">Partial methods</span></span>](../language-reference/keywords/partial-method.md)
- [<span data-ttu-id="0ddb7-170">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-170">Object and collection initializers</span></span>](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

<span data-ttu-id="0ddb7-171">回顧以往，許多功能似乎無法避免和分離。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-171">In retrospect, many of these features seem both inevitable and inseparable.</span></span> <span data-ttu-id="0ddb7-172">它們全都因為策略的緣故而放在一起。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-172">They all fit together strategically.</span></span> <span data-ttu-id="0ddb7-173">一般認為 C# 版本的殺手級功能是查詢運算式，也稱為 Language-Integrated Query (LINQ)。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-173">It's generally thought that C# version's killer feature was the query expression, also known as Language-Integrated Query (LINQ).</span></span>

<span data-ttu-id="0ddb7-174">更細看的話，則會探討出運算式樹狀架構、Lambda 運算式及匿名型別才是建構 LINQ 的基礎。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-174">A more nuanced view examines expression trees, lambda expressions, and anonymous types as the foundation upon which LINQ is constructed.</span></span> <span data-ttu-id="0ddb7-175">但無論如何，C# 3.0 呈現了革命性的概念。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-175">But, in either case, C# 3.0 presented a revolutionary concept.</span></span> <span data-ttu-id="0ddb7-176">C# 3.0 已經開始打下基礎，將 C# 變成混合式的物件導向 / 功能性語言。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-176">C# 3.0 had begun to lay the groundwork for turning C# into a hybrid Object-Oriented / Functional language.</span></span>

<span data-ttu-id="0ddb7-177">具體來說，您現在可以撰寫 SQL 樣式的宣告式查詢，尤其是對集合執行作業。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-177">Specifically, you could now write SQL-style, declarative queries to perform operations on collections, among other things.</span></span> <span data-ttu-id="0ddb7-178">您不必撰寫 `for` 迴圈來計算整數清單的平均值，您現在只要用 `list.Average()` 就能做到。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-178">Instead of writing a `for` loop to compute the average of a list of integers, you could now do that as simply as `list.Average()`.</span></span> <span data-ttu-id="0ddb7-179">查詢運算式和擴充方法的組合，結果看似整數清單變得聰明許多。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-179">The combination of query expressions and extension methods made it look as though that list of integers had gotten a whole lot smarter.</span></span>

<span data-ttu-id="0ddb7-180">人們真正抓住並整合概念需要時間，但他們逐漸做到了。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-180">It took time for people to really grasp and integrate the concept, but they gradually did.</span></span> <span data-ttu-id="0ddb7-181">而多年之後的現在，程式碼已經精簡、簡單且功能強大許多。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-181">And now, years later, code is much more concise, simple, and functional.</span></span>

## <a name="c-version-40"></a><span data-ttu-id="0ddb7-182">C# 4.0 版</span><span class="sxs-lookup"><span data-stu-id="0ddb7-182">C# version 4.0</span></span>

<span data-ttu-id="0ddb7-183">C# 4.0 版要堅守 3.0 版的奠基狀態會很困難。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-183">C# version 4.0 would have had a difficult time living up to the groundbreaking status of version 3.0.</span></span> <span data-ttu-id="0ddb7-184">3.0 版開始，C# 讓語言穩固地擺脫 Java 的影子，並建立聲望。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-184">With version 3.0, C# had moved the language firmly out from the shadow of Java and into prominence.</span></span> <span data-ttu-id="0ddb7-185">語言很快地變優雅。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-185">The language was quickly becoming elegant.</span></span>

<span data-ttu-id="0ddb7-186">下一版確實導入了一些有趣的新功能：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-186">The next version did introduce some interesting new features:</span></span>

- [<span data-ttu-id="0ddb7-187">動態繫結</span><span class="sxs-lookup"><span data-stu-id="0ddb7-187">Dynamic binding</span></span>](../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="0ddb7-188">具名/選擇性引數</span><span class="sxs-lookup"><span data-stu-id="0ddb7-188">Named/optional arguments</span></span>](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="0ddb7-189">泛型 covariant 和 contravariant</span><span class="sxs-lookup"><span data-stu-id="0ddb7-189">Generic covariant and contravariant</span></span>](../../standard/generics/covariance-and-contravariance.md)
- [<span data-ttu-id="0ddb7-190">內嵌 Interop 型別</span><span class="sxs-lookup"><span data-stu-id="0ddb7-190">Embedded interop types</span></span>](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

<span data-ttu-id="0ddb7-191">內嵌 interop 型別能減輕部署痛苦。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-191">Embedded interop types alleviated a deployment pain.</span></span> <span data-ttu-id="0ddb7-192">泛型 covariance 和 contravariance 可讓您有更強大的功能來使用泛型，但它們有點學術，可能最受架構和程式庫作者欣賞。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-192">Generic covariance and contravariance give you more power to use generics, but they're a bit academic and probably most appreciated by framework and library authors.</span></span> <span data-ttu-id="0ddb7-193">具名和選擇性參數可讓您消除許多方法多載，並提供方便性。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-193">Named and optional parameters let you eliminate many method overloads and provide convenience.</span></span> <span data-ttu-id="0ddb7-194">但這些功能沒有一項能完全改變典範。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-194">But none of those features are exactly paradigm altering.</span></span>

<span data-ttu-id="0ddb7-195">主要功能是導入 `dynamic` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-195">The major feature was the introduction of the `dynamic` keyword.</span></span> <span data-ttu-id="0ddb7-196">`dynamic` 關鍵字為 C# 4.0 版導入在編譯時期型別設定時覆寫編譯器的功能。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-196">The `dynamic` keyword introduced into C# version 4.0 the ability to override the compiler on compile-time typing.</span></span> <span data-ttu-id="0ddb7-197">藉由使用動態關鍵字，您可以建立類似於動態型別語言 (例如 JavaScript) 的建構。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-197">By using the dynamic keyword, you can create constructs similar to dynamically typed languages like JavaScript.</span></span> <span data-ttu-id="0ddb7-198">您可以建立 `dynamic x = "a string"` 然後將它加六，留給執行階段找出接下來要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-198">You can create a `dynamic x = "a string"` and then add six to it, leaving it up to the runtime to sort out what should happen next.</span></span>

<span data-ttu-id="0ddb7-199">動態繫結可能會有錯誤，但也給予您語言內的強大功能。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-199">Dynamic binding gives you the potential for errors but also great power within the language.</span></span>

## <a name="c-version-50"></a><span data-ttu-id="0ddb7-200">C# 5.0 版</span><span class="sxs-lookup"><span data-stu-id="0ddb7-200">C# version 5.0</span></span>

<span data-ttu-id="0ddb7-201">C# 5.0 版是該語言的一個聚焦版本。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-201">C# version 5.0 was a focused version of the language.</span></span> <span data-ttu-id="0ddb7-202">幾乎該版本的所有心血都投入了另一項奠基的語言概念：非同步程式設計的 `async` 和 `await` 模型。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-202">Nearly all of the effort for that version went into another groundbreaking language concept: the `async` and `await` model for asynchronous programming .</span></span>  <span data-ttu-id="0ddb7-203">以下是主要的功能清單：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-203">Here is the major features list:</span></span>

- [<span data-ttu-id="0ddb7-204">非同步成員</span><span class="sxs-lookup"><span data-stu-id="0ddb7-204">Asynchronous members</span></span>](../async.md)
- [<span data-ttu-id="0ddb7-205">呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="0ddb7-205">Caller info attributes</span></span>](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a><span data-ttu-id="0ddb7-206">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ddb7-206">See Also</span></span>

* [<span data-ttu-id="0ddb7-207">程式碼專案：C# 5.0 中的呼叫端資訊屬性</span><span class="sxs-lookup"><span data-stu-id="0ddb7-207">Code Project: Caller Info Attributes in C# 5.0</span></span>](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

<span data-ttu-id="0ddb7-208">呼叫端資訊屬性可讓您輕鬆地擷取您正在執行的內容，而不必依賴大量的未定案反映程式碼。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-208">The caller info attribute lets you easily retrieve information about the context in which you're running without resorting to a ton of boilerplate reflection code.</span></span> <span data-ttu-id="0ddb7-209">它在診斷和記錄工作方面有許多用途。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-209">It has many uses in diagnostics and logging tasks.</span></span>

<span data-ttu-id="0ddb7-210">但是 `async` 和 `await` 是此版本真正的明星。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-210">But `async` and `await` are the real stars of this release.</span></span> <span data-ttu-id="0ddb7-211">當這些功能在 2012 年中推出時，C# 再次改變了遊戲，因為它將非同步深植在語言中，成為頭等參與者。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-211">When these features came out in 2012, C# changed the game again by baking asynchrony into the language as a first-class participant.</span></span> <span data-ttu-id="0ddb7-212">如果您曾經處理過長時間執行的作業，以及回撥網的實作，您可能會愛上這項語言功能。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-212">If you've ever dealt with long running operations and the implementation of webs of callbacks, you probably loved this language feature.</span></span>

## <a name="c-version-60"></a><span data-ttu-id="0ddb7-213">C# 6.0 版</span><span class="sxs-lookup"><span data-stu-id="0ddb7-213">C# version 6.0</span></span>

<span data-ttu-id="0ddb7-214">在 3.0 和 5.0 版本中，C# 在物件導向語言中新增了一些重大的新功能。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-214">With versions 3.0 and 5.0, C# had added major new features in an object-oriented language.</span></span> <span data-ttu-id="0ddb7-215">在 6.0 版中，它不再作為主控的殺手級功能，而是改為發表讓 C# 程式設計更具生產力的許多較小功能。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-215">With version 6.0, it would go away from doing a dominant killer feature and instead release many smaller features that made C# programming more productive.</span></span> <span data-ttu-id="0ddb7-216">這裡列出其中一些：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-216">Here are some of them:</span></span>

- [<span data-ttu-id="0ddb7-217">動態匯入</span><span class="sxs-lookup"><span data-stu-id="0ddb7-217">Static imports</span></span>](../language-reference/keywords/using-static.md)
- [<span data-ttu-id="0ddb7-218">例外狀況篩選條件</span><span class="sxs-lookup"><span data-stu-id="0ddb7-218">Exception filters</span></span>](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [<span data-ttu-id="0ddb7-219">屬性初始設定式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-219">Property initializers</span></span>](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [<span data-ttu-id="0ddb7-220">運算式主體的成員</span><span class="sxs-lookup"><span data-stu-id="0ddb7-220">Expression bodied members</span></span>](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [<span data-ttu-id="0ddb7-221">Null 傳播程式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-221">Null propagator</span></span>](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [<span data-ttu-id="0ddb7-222">字串內插補點</span><span class="sxs-lookup"><span data-stu-id="0ddb7-222">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
- [<span data-ttu-id="0ddb7-223">nameof 運算子</span><span class="sxs-lookup"><span data-stu-id="0ddb7-223">nameof operator</span></span>](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [<span data-ttu-id="0ddb7-224">索引初始設定式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-224">Index initializers</span></span>](csharp-6.md#index-initializers)

<span data-ttu-id="0ddb7-225">其他新功能包括：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-225">Other new features include:</span></span>

- <span data-ttu-id="0ddb7-226">catch/finally 區塊中的 Await</span><span class="sxs-lookup"><span data-stu-id="0ddb7-226">Await in catch/finally blocks</span></span>
- <span data-ttu-id="0ddb7-227">僅限 getter 屬性的預設值</span><span class="sxs-lookup"><span data-stu-id="0ddb7-227">Default values for getter-only properties</span></span>

<span data-ttu-id="0ddb7-228">這些功能每個本身都很有趣。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-228">Each of these features is interesting in its own right.</span></span> <span data-ttu-id="0ddb7-229">但是，如果您一起看它們，您會發現有趣的模式。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-229">But if you look at them altogether, you see an interesting pattern.</span></span> <span data-ttu-id="0ddb7-230">在此版本中，C# 排除語言樣本，以使程式碼更簡易、可讀性更高。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-230">In this version, C# eliminated language boilerplate to make code more terse and readable.</span></span> <span data-ttu-id="0ddb7-231">因此，對於喜好乾淨、簡單程式碼的人而言，這個語言版本大幅勝出。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-231">So for fans of clean, simple code, this language version was a huge win.</span></span>

<span data-ttu-id="0ddb7-232">雖然本身不是傳統的語言功能，他們在這個版本中做了另外一件事。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-232">They did one other thing along with this version, though it's not a traditional language feature in itself.</span></span> <span data-ttu-id="0ddb7-233">他們將 [Roslyn 編譯器發表為服務](https://github.com/dotnet/roslyn)。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-233">They released [Roslyn the compiler as a service](https://github.com/dotnet/roslyn).</span></span> <span data-ttu-id="0ddb7-234">C# 編譯器現在會以 C# 撰寫，您可以使用編譯器，作為程式設計工作的一部分。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-234">The C# compiler is now written in C#, and you can use the compiler as part of your programming efforts.</span></span>

## <a name="c-version-70"></a><span data-ttu-id="0ddb7-235">C# 7.0 版</span><span class="sxs-lookup"><span data-stu-id="0ddb7-235">C# version 7.0</span></span>

<span data-ttu-id="0ddb7-236">最新的主要版本是 C# 7.0 版。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-236">The most recent major version is C# version 7.0.</span></span> <span data-ttu-id="0ddb7-237">此版本擁有 C# 6.0 中的某些進化和酷炫的東西，但是沒有編譯器作為服務。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-237">This version has some evolutionary and cool stuff in the vein of C# 6.0, but without the compiler as a service.</span></span> <span data-ttu-id="0ddb7-238">下列為部分新功能：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-238">Here are some of the new features:</span></span>

- [<span data-ttu-id="0ddb7-239">Out 變數</span><span class="sxs-lookup"><span data-stu-id="0ddb7-239">Out variables</span></span>](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [<span data-ttu-id="0ddb7-240">Tuple 和解構</span><span class="sxs-lookup"><span data-stu-id="0ddb7-240">Tuples and deconstruction</span></span>](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [<span data-ttu-id="0ddb7-241">模式比對</span><span class="sxs-lookup"><span data-stu-id="0ddb7-241">Pattern matching</span></span>](./csharp-7.md#pattern-matching)
- [<span data-ttu-id="0ddb7-242">區域函式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-242">Local functions</span></span>](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [<span data-ttu-id="0ddb7-243">展開的運算式主體成員</span><span class="sxs-lookup"><span data-stu-id="0ddb7-243">Expanded expression bodied members</span></span>](./csharp-7.md#more-expression-bodied-members)
- [<span data-ttu-id="0ddb7-244">Ref 區域變數和傳回</span><span class="sxs-lookup"><span data-stu-id="0ddb7-244">Ref locals and returns</span></span>](./csharp-7.md#ref-locals-and-returns)

<span data-ttu-id="0ddb7-245">其他功能包括：</span><span class="sxs-lookup"><span data-stu-id="0ddb7-245">Other features included:</span></span>

- [<span data-ttu-id="0ddb7-246">捨棄</span><span class="sxs-lookup"><span data-stu-id="0ddb7-246">Discards</span></span>](../discards.md)
- [<span data-ttu-id="0ddb7-247">二進位常值</span><span class="sxs-lookup"><span data-stu-id="0ddb7-247">Binary Literals</span></span>](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/binary-literals.md)
- [<span data-ttu-id="0ddb7-248">數字分隔符號</span><span class="sxs-lookup"><span data-stu-id="0ddb7-248">Digit Separators</span></span>](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/digit-separators.md)
- <span data-ttu-id="0ddb7-249">ref 傳回值和區域變數</span><span class="sxs-lookup"><span data-stu-id="0ddb7-249">Ref returns and locals</span></span>
- [<span data-ttu-id="0ddb7-250">throw 運算式</span><span class="sxs-lookup"><span data-stu-id="0ddb7-250">Throw expressions</span></span>](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/throw-expression.md)

<span data-ttu-id="0ddb7-251">所有這些功能會提供開發人員很棒的新功能，以及撰寫出比以往更簡潔的程式碼的機會。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-251">All of these features offer cool new capabilities for developers and the opportunity to write even cleaner code than ever.</span></span> <span data-ttu-id="0ddb7-252">重點強調是將變數宣告緊縮為使用 `out` 關鍵字，以及允許透過 tuple 傳回多個值。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-252">A highlight is condensing the declaration of variables to use with the `out` keyword and by allowing multiple return values via tuple.</span></span>

<span data-ttu-id="0ddb7-253">但 C# 的運用範圍更廣了。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-253">But C# is being put to ever broader use.</span></span> <span data-ttu-id="0ddb7-254">.NET Core 現在以任何作業系統為目標，並堅定地關注雲端和可攜性。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-254">.NET Core now targets any operating system and has its eyes firmly on the cloud and on portability.</span></span>  <span data-ttu-id="0ddb7-255">除了提出新功能之外，這些新功能當然也會佔據語言設計人員的想法和時間。</span><span class="sxs-lookup"><span data-stu-id="0ddb7-255">These new capabilities certainly occupy the language designers' thoughts and time, in addition to coming up with new features.</span></span>

<span data-ttu-id="0ddb7-256">_文章_ [_最初發佈於 NDepend 部落格_](https://blog.ndepend.com/c-versions-look-language-history/)_，感謝 Erik Dietrich 和 Patrick Smacchia。_</span><span class="sxs-lookup"><span data-stu-id="0ddb7-256">_Article_ [_originally published on the NDepend blog_](https://blog.ndepend.com/c-versions-look-language-history/)_, courtesy of Erik Dietrich and Patrick Smacchia._</span></span>
