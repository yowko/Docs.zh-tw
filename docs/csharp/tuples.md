---
title: "Tuple - C# 手冊"
description: "了解 C# 中的未具名和具名 Tuple 類型"
keywords: .NET, .NET Core, C#
author: BillWagner
ms-author: wiwagn
ms.date: 11/23/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 58f76332a8f3717fe10788382552598d6693e7e3
ms.sourcegitcommit: 882e02b086d7cb9c75f748494cf7a8d3377c5874
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="c-tuple-types"></a><span data-ttu-id="545fe-104">C# Tuple 類型</span><span class="sxs-lookup"><span data-stu-id="545fe-104">C# Tuple types</span></span> #

<span data-ttu-id="545fe-105">C# Tuple 是您使用輕量型語法所定義的類型。</span><span class="sxs-lookup"><span data-stu-id="545fe-105">C# Tuples are types that you define using a lightweight syntax.</span></span> <span data-ttu-id="545fe-106">優點包括更簡單的語法、以元素數目 (稱為基數) 與類型為依據的轉換規則，以及複本與指派的一致性規則。</span><span class="sxs-lookup"><span data-stu-id="545fe-106">The advantages include a simpler syntax, rules for conversions based on number (referred to as cardinality) and types of elements, and consistent rules for copies and assignments.</span></span> <span data-ttu-id="545fe-107">折衷方式是，Tuple 不支援與繼承建立關聯的一些物件導向慣用語。</span><span class="sxs-lookup"><span data-stu-id="545fe-107">As a tradeoff, Tuples do not support some of the object oriented idioms associated with inheritance.</span></span> <span data-ttu-id="545fe-108">您可以在 [C# 7 之新功能中的 Tuple](whats-new/csharp-7.md#tuples) 主題的一節中取得概觀。</span><span class="sxs-lookup"><span data-stu-id="545fe-108">You can get an overview in the section on [Tuples in the What's new in C# 7](whats-new/csharp-7.md#tuples) topic.</span></span>

<span data-ttu-id="545fe-109">在本主題中，您將了解在 C# 7 中控管 Tuple 的語言規則、不同的 Tuple 使用方式，以及使用 Tuple 的初始指導。</span><span class="sxs-lookup"><span data-stu-id="545fe-109">In this topic, you'll learn the language rules governing Tuples in C# 7, different ways to use them, and initial guidance on working with Tuples.</span></span>

> [!NOTE]
> <span data-ttu-id="545fe-110">新的 Tuple 功能需要 <xref:System.ValueTuple> 類型。</span><span class="sxs-lookup"><span data-stu-id="545fe-110">The new tuples features require the <xref:System.ValueTuple> types.</span></span>
> <span data-ttu-id="545fe-111">您必須新增 NuGet 套件 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/)，以將它用於不包含類型的平台。</span><span class="sxs-lookup"><span data-stu-id="545fe-111">You must add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) in order to use it on platforms that do not include the types.</span></span>
>
> <span data-ttu-id="545fe-112">這類似於依賴架構中所傳遞類型的其他語言功能。</span><span class="sxs-lookup"><span data-stu-id="545fe-112">This is similar to other language features that rely on types delivered in the framework.</span></span> <span data-ttu-id="545fe-113">範例包含依賴 `INotifyCompletion` 介面的 `async` 和 `await` 以及依賴 `IEnumerable<T>` 的 LINQ。</span><span class="sxs-lookup"><span data-stu-id="545fe-113">Examples include `async` and `await` relying on the `INotifyCompletion` interface, and LINQ relying on `IEnumerable<T>`.</span></span> <span data-ttu-id="545fe-114">不過，傳遞機制會變更，因為 .NET 變得與平台更為無關。</span><span class="sxs-lookup"><span data-stu-id="545fe-114">However, the delivery mechanism is changing as .NET is becoming more platform independent.</span></span> <span data-ttu-id="545fe-115">.NET Framework 可能不會永遠隨附於相同的步調，作為語言編譯器。</span><span class="sxs-lookup"><span data-stu-id="545fe-115">The .NET Framework may not always ship on the same cadence as the language compiler.</span></span> <span data-ttu-id="545fe-116">如果新語言功能依賴新類型，則在提供語言功能時，會以 NuGet 套件形式提供這些類型。</span><span class="sxs-lookup"><span data-stu-id="545fe-116">When new language features rely on new types, those types will be available as NuGet packages when the language features ship.</span></span> <span data-ttu-id="545fe-117">因為這些新類型會新增至 .NET Standard API 並傳遞為架構的一部分，所以將會移除 NuGet 套件需求。</span><span class="sxs-lookup"><span data-stu-id="545fe-117">As these new types get added to the .NET Standard API and delivered as part of the framework, the NuGet package requirement will be removed.</span></span>

<span data-ttu-id="545fe-118">讓我們開始了解新增 Tuple 支援的原因。</span><span class="sxs-lookup"><span data-stu-id="545fe-118">Let's start with the reasons for adding new Tuple support.</span></span> <span data-ttu-id="545fe-119">方法會傳回單一物件。</span><span class="sxs-lookup"><span data-stu-id="545fe-119">Methods return a single object.</span></span> <span data-ttu-id="545fe-120">Tuple 可讓您更輕鬆地將多個值封裝在該單一物件中。</span><span class="sxs-lookup"><span data-stu-id="545fe-120">Tuples enable you to package multiple values in that single object more easily.</span></span>

<span data-ttu-id="545fe-121">.NET Framework 已有泛型 `Tuple` 類別。</span><span class="sxs-lookup"><span data-stu-id="545fe-121">The .NET Framework already has generic `Tuple` classes.</span></span> <span data-ttu-id="545fe-122">不過，這些類別有兩個主要限制。</span><span class="sxs-lookup"><span data-stu-id="545fe-122">These classes, however, had two major limitations.</span></span> <span data-ttu-id="545fe-123">其中一個限制是，`Tuple` 已將其屬性命名為 `Item1`、`Item2` 等等。</span><span class="sxs-lookup"><span data-stu-id="545fe-123">For one, the `Tuple` classes named their properties `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="545fe-124">這些名稱未包含任何語意資訊。</span><span class="sxs-lookup"><span data-stu-id="545fe-124">Those names carry no semantic information.</span></span> <span data-ttu-id="545fe-125">使用這些 `Tuple` 類型無法表達各個屬性的意義。</span><span class="sxs-lookup"><span data-stu-id="545fe-125">Using these `Tuple` types does not enable communicating the meaning of each of the properties.</span></span> <span data-ttu-id="545fe-126">而新的語言功能則可讓您為元組中的元素宣告及使用具有語意意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-126">The new language features enable you to declare and use semantically meaningful names for the elements in a tuple.</span></span>

<span data-ttu-id="545fe-127">另一個問題是 `Tuple` 類別為參考型別。</span><span class="sxs-lookup"><span data-stu-id="545fe-127">Another concern is that the `Tuple` classes are reference types.</span></span> <span data-ttu-id="545fe-128">使用其中一個 `Tuple` 類型表示配置物件。</span><span class="sxs-lookup"><span data-stu-id="545fe-128">Using one of the `Tuple` types means allocating objects.</span></span> <span data-ttu-id="545fe-129">在最忙碌路徑上，這可能會對您應用程式的效能造成可觀的衝擊。</span><span class="sxs-lookup"><span data-stu-id="545fe-129">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="545fe-130">因此，元組的語言支援會運用新的 `ValueTuple` 結構。</span><span class="sxs-lookup"><span data-stu-id="545fe-130">Therefore, the language support for tuples leverages the new `ValueTuple` structs.</span></span>

<span data-ttu-id="545fe-131">若要避免這些缺點，您可以建立 `class` 或 `struct` 來帶出多個元素。</span><span class="sxs-lookup"><span data-stu-id="545fe-131">To avoid those deficiencies, you could create a `class` or a `struct` to carry multiple elements.</span></span> <span data-ttu-id="545fe-132">不幸的是，您需要執行更多工作，並且會模糊您的設計目的。</span><span class="sxs-lookup"><span data-stu-id="545fe-132">Unfortunately, that's more work for you, and it obscures your design intent.</span></span> <span data-ttu-id="545fe-133">設定 `struct` 或 `class` 表示您定義的類型同時具有資料和行為。</span><span class="sxs-lookup"><span data-stu-id="545fe-133">Making a `struct` or `class` implies that you are defining a type with both data and behavior.</span></span> <span data-ttu-id="545fe-134">許多次，您都只想要將多個值儲存在單一物件中。</span><span class="sxs-lookup"><span data-stu-id="545fe-134">Many times, you simply want to store multiple values in a single object.</span></span>

<span data-ttu-id="545fe-135">語言功能和 `ValueTuple` 泛型結構會強制執行您無法將任何行為 (方法) 新增至這些 Tuple 類型的規則。</span><span class="sxs-lookup"><span data-stu-id="545fe-135">The language features and the `ValueTuple` generic structs enforce the rule that you cannot add any behavior (methods) to these tuple types.</span></span>
<span data-ttu-id="545fe-136">所有 `ValueTuple` 類型都是「可變動結構」。</span><span class="sxs-lookup"><span data-stu-id="545fe-136">All the `ValueTuple` types are *mutable structs*.</span></span> <span data-ttu-id="545fe-137">每個成員欄位都是公用欄位。</span><span class="sxs-lookup"><span data-stu-id="545fe-137">Each member field is a public field.</span></span> <span data-ttu-id="545fe-138">這可將它們設為非常輕量型。</span><span class="sxs-lookup"><span data-stu-id="545fe-138">That makes them very lightweight.</span></span> <span data-ttu-id="545fe-139">不過，這表示，如果不變性十分重要，則不應該使用 Tuple。</span><span class="sxs-lookup"><span data-stu-id="545fe-139">However, that means tuples should not be used where immutability is important.</span></span>

<span data-ttu-id="545fe-140">Tuple 是比 `class` 和 `struct` 類型更為簡單且更具彈性的資料容器。</span><span class="sxs-lookup"><span data-stu-id="545fe-140">Tuples are both simpler and more flexible data containers than `class` and `struct` types.</span></span> <span data-ttu-id="545fe-141">讓我們來探索這些差異。</span><span class="sxs-lookup"><span data-stu-id="545fe-141">Let's explore those differences.</span></span>

## <a name="named-and-unnamed-tuples"></a><span data-ttu-id="545fe-142">具名和未具名 Tuple</span><span class="sxs-lookup"><span data-stu-id="545fe-142">Named and unnamed tuples</span></span>

<span data-ttu-id="545fe-143">`ValueTuple` 結構具有名為 `Item1`、`Item2`、`Item3` 等等的欄位，而這些欄位與現有 `Tuple` 類型中所定義的屬性類似。</span><span class="sxs-lookup"><span data-stu-id="545fe-143">The `ValueTuple` struct has fields named `Item1`, `Item2`, `Item3` and so on, similar to the properties defined in the existing `Tuple` types.</span></span>
<span data-ttu-id="545fe-144">這些名稱只是您可用於「未具名 Tuple」的名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-144">These names are the only names you can use for *unnamed tuples*.</span></span> <span data-ttu-id="545fe-145">當您未將任何替代欄位名稱提供給 Tuple 時，即已建立未具名 Tuple：</span><span class="sxs-lookup"><span data-stu-id="545fe-145">When you do not provide any alternative field names to a tuple, you've created an unnamed tuple:</span></span>

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

<span data-ttu-id="545fe-146">上述範例中使用了常值常數將元組初始化，且不會有在 C# 7.1 中使用「元組欄位名稱投影」建立的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-146">The tuple in the previous example was initialized using literal constants and won't have element names created using *Tuple field name projections* in C# 7.1.</span></span>

<span data-ttu-id="545fe-147">不過，當您初始化 Tuple 時，可以使用新的語言功能，讓每個欄位具有更適合的名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-147">However, when you initialize a tuple, you can use new language features that give better names to each field.</span></span> <span data-ttu-id="545fe-148">這麼做會建立「具名 Tuple」。</span><span class="sxs-lookup"><span data-stu-id="545fe-148">Doing so creates a *named tuple*.</span></span>
<span data-ttu-id="545fe-149">具名元組仍會有名為 `Item1`、`Item2`、`Item3` 等等的元素。</span><span class="sxs-lookup"><span data-stu-id="545fe-149">Named tuples still have elements named `Item1`, `Item2`, `Item3` and so on.</span></span>
<span data-ttu-id="545fe-150">但對於您已命名的任一元素，也會有同義字。</span><span class="sxs-lookup"><span data-stu-id="545fe-150">But they also have synonyms for any of those elements that you have named.</span></span>
<span data-ttu-id="545fe-151">您可以指定每個元素的名稱來建立具名元組。</span><span class="sxs-lookup"><span data-stu-id="545fe-151">You create a named tuple by specifying the names for each element.</span></span> <span data-ttu-id="545fe-152">其中一個方式是在 Tuple 初始化期間指定名稱：</span><span class="sxs-lookup"><span data-stu-id="545fe-152">One way is to specify the names as part of the tuple initialization:</span></span>

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

<span data-ttu-id="545fe-153">這些同義字是由編譯器和語言所處理，讓您可以有效率地使用具名 Tuple。</span><span class="sxs-lookup"><span data-stu-id="545fe-153">These synonyms are handled by the compiler and the language so that you can use named tuples effectively.</span></span> <span data-ttu-id="545fe-154">IDE 和編輯器可以使用 Roslyn API 來讀取這些語意名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-154">IDEs and editors can read these semantic names using the Roslyn APIs.</span></span> <span data-ttu-id="545fe-155">這讓您能夠在相同組件的任何地方，依據這些語意名稱來參考具名元組的元素。</span><span class="sxs-lookup"><span data-stu-id="545fe-155">This enables you to reference the elements of a named tuple by those semantic names anywhere in the same assembly.</span></span> <span data-ttu-id="545fe-156">產生所編譯的輸出時，編譯器會將您定義的名稱取代為 `Item*` 對等項目。</span><span class="sxs-lookup"><span data-stu-id="545fe-156">The compiler replaces the names you've defined with `Item*` equivalents when generating the compiled output.</span></span> <span data-ttu-id="545fe-157">編譯過的 Microsoft Intermediate Language (MSIL) 不會包括您為這些元素指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-157">The compiled Microsoft Intermediate Language (MSIL) does not include the names you've given these elements.</span></span>

<span data-ttu-id="545fe-158">從 C# 7.1 開始，元組的欄位名稱可從用來將元組初始化的變數提供。</span><span class="sxs-lookup"><span data-stu-id="545fe-158">Beginning with C# 7.1, the field names for a tuple may be provided from the variables used to initialize the tuple.</span></span> <span data-ttu-id="545fe-159">即為**[元組投影初始設定式](#tuple-projection-initializers)**。</span><span class="sxs-lookup"><span data-stu-id="545fe-159">This is referred to as **[tuple projection initializers](#tuple-projection-initializers)**.</span></span> <span data-ttu-id="545fe-160">下列程式碼會建立名為 `accumulation` 的元組，並有元素 `count` (整數) 與 `sum` (雙精度浮點數)。</span><span class="sxs-lookup"><span data-stu-id="545fe-160">The following code creates a tuple named `accumulation` with elements `count` (an integer), and `sum` (a double).</span></span>

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

<span data-ttu-id="545fe-161">編譯器必須知道您針對從公用方法或屬性傳回之 Tuple 所建立的名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-161">The compiler must communicate those names you created for tuples that are returned from public methods or properties.</span></span> <span data-ttu-id="545fe-162">在這些情況下，編譯器會在方法上新增 <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="545fe-162">In those cases, the compiler adds a <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> attribute on the method.</span></span> <span data-ttu-id="545fe-163">這個屬性包含 <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> 清單屬性，其中包含為元組中各元素指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-163">This attribute contains a <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> list property that contains the names given to each of the elements in the Tuple.</span></span>

> [!NOTE]
> <span data-ttu-id="545fe-164">Visual Studio 這類開發工具也會讀取該中繼資料，並使用中繼資料欄位名稱來提供 IntelliSense 和其他功能。</span><span class="sxs-lookup"><span data-stu-id="545fe-164">Development Tools, such as Visual Studio, also read that metadata, and provide IntelliSense and other features using the metadata field names.</span></span>

<span data-ttu-id="545fe-165">請務必了解新 Tuple 的這些基礎基本項目和 `ValueTuple` 類型，以了解將具名 Tuple 指派給彼此的規則。</span><span class="sxs-lookup"><span data-stu-id="545fe-165">It is important to understand these underlying fundamentals of the new tuples and the `ValueTuple` type in order to understand the rules for assigning named tuples to each other.</span></span>

## <a name="tuple-projection-initializers"></a><span data-ttu-id="545fe-166">元組投影初始設定式</span><span class="sxs-lookup"><span data-stu-id="545fe-166">Tuple projection initializers</span></span>

<span data-ttu-id="545fe-167">一般來說，元組投影初始設定式會使用元組初始化陳述式右手邊的變數或欄位名稱來運作。</span><span class="sxs-lookup"><span data-stu-id="545fe-167">In general, tuple projection initializers work by using the variable or field names from the right-hand side of a tuple initialization statement.</span></span>
<span data-ttu-id="545fe-168">如有指定明確名稱，則會優先於任何投影名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-168">If an explicit name is given, that takes precedence over any projected name.</span></span> <span data-ttu-id="545fe-169">例如，在下列初始設定式中，元素為 `explicitFieldOne` 與 `explicitFieldTwo`，而非 `localVariableOne` 與 `localVariableTwo`：</span><span class="sxs-lookup"><span data-stu-id="545fe-169">For example, in the following initializer, the elements are `explicitFieldOne` and `explicitFieldTwo`, not `localVariableOne` and `localVariableTwo`:</span></span>

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

<span data-ttu-id="545fe-170">對於未提供明確名稱的任何欄位，會投影適用的隱含名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-170">For any field where an explicit name is not provided, an applicable implicit name will be projected.</span></span> <span data-ttu-id="545fe-171">請注意，您不需要明確或隱含地提供語意名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-171">Note that there is no requirement to provide semantic names, either explicitly or implicitly.</span></span> <span data-ttu-id="545fe-172">下列的初始設定式會有欄位名稱`Item1`，其值是`42`和`StringContent`，其值是 「 可以存取所有的回答 」:</span><span class="sxs-lookup"><span data-stu-id="545fe-172">The following initializer will have field names `Item1`, whose value is `42` and `StringContent`, whose value is "The answer to everything":</span></span>

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

<span data-ttu-id="545fe-173">在兩種情況下，候選欄位名稱不會投影至元組欄位：</span><span class="sxs-lookup"><span data-stu-id="545fe-173">There are two conditions where candidate field names are not projected onto the tuple field:</span></span>

1. <span data-ttu-id="545fe-174">候選名稱是保留的元組名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-174">When the candidate name is a reserved tuple name.</span></span> <span data-ttu-id="545fe-175">範例包括 `Item3`、`ToString` 或 `Rest`。</span><span class="sxs-lookup"><span data-stu-id="545fe-175">Examples include `Item3`, `ToString` or `Rest`.</span></span>
1. <span data-ttu-id="545fe-176">候選名稱與另一個明確或隱含的元組欄位名稱重複。</span><span class="sxs-lookup"><span data-stu-id="545fe-176">When the candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="545fe-177">這些情況可避免語意模糊。</span><span class="sxs-lookup"><span data-stu-id="545fe-177">These conditions avoid ambiguity.</span></span> <span data-ttu-id="545fe-178">如果將這些名稱作為元組中的欄位名稱使用，就會造成語意模糊。</span><span class="sxs-lookup"><span data-stu-id="545fe-178">These names would cause an ambiguity if they were used as the field names for a field in a tuple.</span></span> <span data-ttu-id="545fe-179">這兩種情況都不會造成編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="545fe-179">Neither of these conditions cause compile time errors.</span></span> <span data-ttu-id="545fe-180">反之，沒有投影名稱的元素不會有語意名稱對其投影。</span><span class="sxs-lookup"><span data-stu-id="545fe-180">Instead, the elements without projected names do not have semantic names projected for them.</span></span>  <span data-ttu-id="545fe-181">下列範例將示範這些情況：</span><span class="sxs-lookup"><span data-stu-id="545fe-181">The following examples demonstrate these conditions:</span></span>

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

<span data-ttu-id="545fe-182">這些情況不會造成編譯器錯誤，因為這使用 C# 7.0 撰寫的程式碼而言會是重大變更，而當時元組欄位名稱投影還無法使用。</span><span class="sxs-lookup"><span data-stu-id="545fe-182">These situations do not cause compiler errors because that would be a breaking change for code written with C# 7.0, when tuple field name projections were not available.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="545fe-183">指派和 Tuple</span><span class="sxs-lookup"><span data-stu-id="545fe-183">Assignment and tuples</span></span>

<span data-ttu-id="545fe-184">語言支援在元素數目相同的元組類型間指派，以及這些元素各類型的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="545fe-184">The language supports assignment between tuple types that have the same number of elements and implicit conversions for the types for each of those elements.</span></span> <span data-ttu-id="545fe-185">不會考慮對指派進行其他轉換。</span><span class="sxs-lookup"><span data-stu-id="545fe-185">Other conversions are not considered for assignments.</span></span> <span data-ttu-id="545fe-186">讓我們看看 Tuple 類型之間允許的指派類型。</span><span class="sxs-lookup"><span data-stu-id="545fe-186">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="545fe-187">請考慮在下列範例中使用的這些參數：</span><span class="sxs-lookup"><span data-stu-id="545fe-187">Consider these variables used in the following examples:</span></span>

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

<span data-ttu-id="545fe-188">前兩個變數 `unnamed` 與 `anonymous` 都未提供元素的語意名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-188">The first two variables, `unnamed` and `anonymous` do not have semantic names provided for the elements.</span></span> <span data-ttu-id="545fe-189">欄位名稱為 `Item1` 和 `Item2`。</span><span class="sxs-lookup"><span data-stu-id="545fe-189">The field names are `Item1` and `Item2`.</span></span>
<span data-ttu-id="545fe-190">後兩個變數 `named` 與 `differentName` 皆有為元素指定的語意名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-190">The last two variables, `named` and `differentName` have semantic names given for the elements.</span></span> <span data-ttu-id="545fe-191">請注意，這兩個元組有不同的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-191">Note that these two tuples have different names for the elements.</span></span>

<span data-ttu-id="545fe-192">這四個元組全都有相同數目的元素 (稱為「基數」)，而且這些元素的類型完全相同。</span><span class="sxs-lookup"><span data-stu-id="545fe-192">All four of these tuples have the same number of elements (referred to as 'cardinality') and the types of those elements are identical.</span></span> <span data-ttu-id="545fe-193">因此，所有這些指派都會運作︰</span><span class="sxs-lookup"><span data-stu-id="545fe-193">Therefore, all of these assignments work:</span></span>

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

<span data-ttu-id="545fe-194">請注意，不會指派 Tuple 的名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-194">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="545fe-195">元素的值會依照元組中的元素順序指派。</span><span class="sxs-lookup"><span data-stu-id="545fe-195">The values of the elements are assigned following the order of the elements in the tuple.</span></span>

<span data-ttu-id="545fe-196">類型或元素數目不同的元組則無法指派：</span><span class="sxs-lookup"><span data-stu-id="545fe-196">Tuples of different types or numbers of elements are not assignable:</span></span>

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="545fe-197">Tuple 作為方法傳回值</span><span class="sxs-lookup"><span data-stu-id="545fe-197">Tuples as method return values</span></span>

<span data-ttu-id="545fe-198">其中一個最常見的 Tuple 用法是作為方法傳回值。</span><span class="sxs-lookup"><span data-stu-id="545fe-198">One of the most common uses for Tuples is as a method return value.</span></span> <span data-ttu-id="545fe-199">讓我們逐步解說一個範例。</span><span class="sxs-lookup"><span data-stu-id="545fe-199">Let's walk through one example.</span></span> <span data-ttu-id="545fe-200">請考慮使用這個計算一系列數字標準差的方法︰</span><span class="sxs-lookup"><span data-stu-id="545fe-200">Consider this method that computes the standard deviation for a sequence of numbers:</span></span>

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> <span data-ttu-id="545fe-201">這些範例會計算未修正的樣本標準差。</span><span class="sxs-lookup"><span data-stu-id="545fe-201">These examples compute the uncorrected sample standard deviation.</span></span>
> <span data-ttu-id="545fe-202">更正的範例標準差公式會將與平均值的平方差總和除以 (N-1)，而非 N，就像 `Average` 擴充方法一樣。</span><span class="sxs-lookup"><span data-stu-id="545fe-202">The corrected sample standard deviation formula would divide the sum of the squared differences from the mean by (N-1) instead of N, as the `Average` extension method does.</span></span> <span data-ttu-id="545fe-203">如需標準差的這些公式之差異的詳細資料，請參閱統計文字。</span><span class="sxs-lookup"><span data-stu-id="545fe-203">Consult a statistics text for more details on the differences between these formulas for standard deviation.</span></span>

<span data-ttu-id="545fe-204">這會遵循標準差的文字方塊公式。</span><span class="sxs-lookup"><span data-stu-id="545fe-204">This follows the textbook formula for the standard deviation.</span></span> <span data-ttu-id="545fe-205">它會產生正確答案，但這是十分沒有效率的實作。</span><span class="sxs-lookup"><span data-stu-id="545fe-205">It produces the correct answer, but it's a very inefficient implementation.</span></span> <span data-ttu-id="545fe-206">這個方法會列舉序列兩次︰一次是產生平均值，一次是產生平均值差之平方的平均值。</span><span class="sxs-lookup"><span data-stu-id="545fe-206">This method enumerates the sequence twice: Once to produce the average, and once to produce the average of the square of the difference of the average.</span></span>
<span data-ttu-id="545fe-207">(請記住，LINQ 查詢會變慢，因此，計算與平均值的差異以及這些差異的平均值只會建立一個列舉)。</span><span class="sxs-lookup"><span data-stu-id="545fe-207">(Remember that LINQ queries are evaluated lazily, so the computation of the differences from the mean and the average of those differences makes only one enumeration.)</span></span>

<span data-ttu-id="545fe-208">有替代公式可以只使用該序列的一個列舉來計算標準差。</span><span class="sxs-lookup"><span data-stu-id="545fe-208">There is an alternative formula that computes standard deviation using only one enumeration of the sequence.</span></span>  <span data-ttu-id="545fe-209">此計算會產生兩個值，因為它會列舉序列︰序列中所有項目的總和，以及每個值平方的總和︰</span><span class="sxs-lookup"><span data-stu-id="545fe-209">This computation produces two values as it enumerates the sequence: the sum of all items in the sequence, and the sum of the each value squared:</span></span>

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

<span data-ttu-id="545fe-210">此版本只會列舉序列一次。</span><span class="sxs-lookup"><span data-stu-id="545fe-210">This version enumerates the sequence exactly once.</span></span> <span data-ttu-id="545fe-211">但是它不是容易重複使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="545fe-211">But, it's not very reusable code.</span></span> <span data-ttu-id="545fe-212">繼續工作時，會發現許多不同的統計運算使用序列中的項目數、序列總和，以及序列平方總和。</span><span class="sxs-lookup"><span data-stu-id="545fe-212">As you keep working, you'll find that many different statistical computations use the number of items in the sequence, the sum of the sequence, and the sum of the squares of the sequence.</span></span> <span data-ttu-id="545fe-213">讓我們重構這個方法，並撰寫可產生所有這三個值的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="545fe-213">Let's refactor this method and write a utility method that produces all three of those values.</span></span>

<span data-ttu-id="545fe-214">這是 Tuple 十分有用的位置。</span><span class="sxs-lookup"><span data-stu-id="545fe-214">This is where tuples come in very useful.</span></span> 

<span data-ttu-id="545fe-215">讓我們更新這個方法，因此在列舉期間計算的三個值會儲存在 Tuple 中。</span><span class="sxs-lookup"><span data-stu-id="545fe-215">Let's update this method so the three values computed during the enumeration are stored in a tuple.</span></span> <span data-ttu-id="545fe-216">這會建立這個版本：</span><span class="sxs-lookup"><span data-stu-id="545fe-216">That creates this version:</span></span>

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

<span data-ttu-id="545fe-217">Visual Studio 的重構支援可讓您更輕鬆地擷取到的私用方法核心統計資料的功能。</span><span class="sxs-lookup"><span data-stu-id="545fe-217">Visual Studio's Refactoring support makes it easy to extract the functionality for the core statistics into a private method.</span></span> <span data-ttu-id="545fe-218">這會提供 `private static` 方法，以傳回具有 `Sum`、`SumOfSquares` 和 `Count` 這三個值的 Tuple 類型：</span><span class="sxs-lookup"><span data-stu-id="545fe-218">That gives you a `private static` method that returns the tuple type with the three values of `Sum`, `SumOfSquares`, and `Count`:</span></span>

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
<span data-ttu-id="545fe-219">如果您想要手動進行一些快速編輯，則語言會啟用可讓您使用的更多選項。</span><span class="sxs-lookup"><span data-stu-id="545fe-219">The language enables a couple more options that you can use, if you want to make a few quick edits by hand.</span></span> <span data-ttu-id="545fe-220">首先，您可以使用 `var` 宣告來初始化 `ComputeSumAndSumOfSquares` 方法呼叫的 Tuple 結果。</span><span class="sxs-lookup"><span data-stu-id="545fe-220">First, you can use the `var` declaration to initialize the tuple result from the `ComputeSumAndSumOfSquares` method call.</span></span> <span data-ttu-id="545fe-221">您也可以在 `ComputeSumAndSumOfSquares` 方法內建立三個不連續變數。</span><span class="sxs-lookup"><span data-stu-id="545fe-221">You can also create three discrete variables inside the `ComputeSumAndSumOfSquares` method.</span></span> <span data-ttu-id="545fe-222">最終版本如下︰</span><span class="sxs-lookup"><span data-stu-id="545fe-222">The final version is below:</span></span>

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

<span data-ttu-id="545fe-223">這個最終版本可以用於任何需要這三個值的方法或其任何子集。</span><span class="sxs-lookup"><span data-stu-id="545fe-223">This final version can be used for any method that needs those three values, or any subset of them.</span></span>

<span data-ttu-id="545fe-224">語言支援其他選項來管理這些元組傳回方法中的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-224">The language supports other options in managing the names of the elements in these tuple-returning methods.</span></span>

<span data-ttu-id="545fe-225">您可以從傳回值宣告中移除欄位名稱，並傳回未具名 Tuple：</span><span class="sxs-lookup"><span data-stu-id="545fe-225">You can remove the field names from the return value declaration and return an unnamed tuple:</span></span>

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

<span data-ttu-id="545fe-226">您必須將此 Tuple 的欄位處理為 `Item1`、`Item2` 和 `Item3`。</span><span class="sxs-lookup"><span data-stu-id="545fe-226">You must address the fields of this tuple as `Item1`, `Item2`, and `Item3`.</span></span>
<span data-ttu-id="545fe-227">建議您為方法中傳回的元組元素提供語意名稱。</span><span class="sxs-lookup"><span data-stu-id="545fe-227">It's recommended that you provide semantic names to the elements of tuples returned from methods.</span></span>

<span data-ttu-id="545fe-228">Tuple 可能十分有用的另一個慣用語是編寫 LINQ 查詢時，而在這類查詢中，最終結果為包含所選取物件的一些但非所有屬性的投影。</span><span class="sxs-lookup"><span data-stu-id="545fe-228">Another idiom where tuples can be very useful is when you are authoring LINQ queries where the final result is a projection that contains some, but not all, of the properties of the objects being selected.</span></span>

<span data-ttu-id="545fe-229">您傳統上會將查詢結果投影至具有匿名型別的一系列物件。</span><span class="sxs-lookup"><span data-stu-id="545fe-229">You would traditionally project the results of the query into a sequence of objects that were an anonymous type.</span></span> <span data-ttu-id="545fe-230">這有許多限制，主要是因為無法在方法的傳回型別中方便地命名匿名型別。</span><span class="sxs-lookup"><span data-stu-id="545fe-230">That presented many limitations, primarily because anonymous types could not conveniently be named in the return type for a method.</span></span> <span data-ttu-id="545fe-231">使用 `object` 或 `dynamic` 作為結果類型的替代方式，其效果成本相當可觀。</span><span class="sxs-lookup"><span data-stu-id="545fe-231">Alternatives using `object` or `dynamic` as the type of the result came with significant performance costs.</span></span>

<span data-ttu-id="545fe-232">傳回一系列的元組類型十分簡單，而且在編譯時間以及透過 IDE 工具都可以使用元素的名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="545fe-232">Returning a sequence of a tuple type is easy, and the names and types of the elements are available at compile time and through IDE tools.</span></span>
<span data-ttu-id="545fe-233">例如，請考慮使用 ToDo 應用程式。</span><span class="sxs-lookup"><span data-stu-id="545fe-233">For example, consider a ToDo application.</span></span> <span data-ttu-id="545fe-234">您可以定義與下面類似的類別，以代表 ToDo 清單中的單一項目︰</span><span class="sxs-lookup"><span data-stu-id="545fe-234">You might define a class similar to the following to represent a single entry in the ToDo list:</span></span>

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

<span data-ttu-id="545fe-235">行動應用程式可能支援只顯示標題之目前 ToDo 項目的壓縮格式。</span><span class="sxs-lookup"><span data-stu-id="545fe-235">Your mobile applications may support a compact form of the current ToDo items that only displays the title.</span></span> <span data-ttu-id="545fe-236">該 LINQ 查詢會建立只包含識別碼和標題的投影。</span><span class="sxs-lookup"><span data-stu-id="545fe-236">That LINQ query would make a projection that includes only the ID and the title.</span></span> <span data-ttu-id="545fe-237">傳回一系列 Tuple 的方法表示該設計良好︰</span><span class="sxs-lookup"><span data-stu-id="545fe-237">A method that returns a sequence of tuples expresses that design very well:</span></span>

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> <span data-ttu-id="545fe-238">在 C# 7.1 中，元組投影可讓您使用元素建立具名元組，方式與匿名型別中的屬性命名相似。</span><span class="sxs-lookup"><span data-stu-id="545fe-238">In C# 7.1, tuple projections enable you to create named tuples using elements, in a manner similar to the property naming in anonymous types.</span></span> <span data-ttu-id="545fe-239">在上述的程式碼中，查詢投影的 `select` 陳述式會建立具有元素 `ID` 與 `Title` 的元組。</span><span class="sxs-lookup"><span data-stu-id="545fe-239">In the above code, the `select` statement in the query projection creates a tuple that has elements `ID` and `Title`.</span></span>

<span data-ttu-id="545fe-240">具名 Tuple 可以是簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="545fe-240">The named tuple can be part of the signature.</span></span> <span data-ttu-id="545fe-241">它可讓編譯器和 IDE 工具提供您正確使用結果的靜態檢查。</span><span class="sxs-lookup"><span data-stu-id="545fe-241">It lets the compiler and IDE tools provide static checking that you are using the result correctly.</span></span> <span data-ttu-id="545fe-242">具名 Tuple 也帶有靜態類型資訊，因此不需要使用昂貴的執行階段功能，例如使用結果的反射或動態繫結。</span><span class="sxs-lookup"><span data-stu-id="545fe-242">The named tuple also carries the static type information so there is no need to use expensive run time features like reflection or dynamic binding to work with the results.</span></span>

## <a name="deconstruction"></a><span data-ttu-id="545fe-243">解構</span><span class="sxs-lookup"><span data-stu-id="545fe-243">Deconstruction</span></span>

<span data-ttu-id="545fe-244">您可以「解構」方法所傳回的 Tuple，來解除封裝 Tuple 中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="545fe-244">You can unpackage all the items in a tuple by *deconstructing* the tuple returned by a method.</span></span> <span data-ttu-id="545fe-245">有三種解構 tuple 的不同方法。</span><span class="sxs-lookup"><span data-stu-id="545fe-245">There are three different approaches to deconstructing tuples.</span></span>  <span data-ttu-id="545fe-246">首先，您可以在括弧內明確宣告每個欄位的類型，以建立元組中每個元素的離散變數：</span><span class="sxs-lookup"><span data-stu-id="545fe-246">First, you can explicitly declare the type of each field inside parentheses to create discrete variables for each of the elements in the tuple:</span></span>

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

<span data-ttu-id="545fe-247">您可以在括弧外部使用 `var` 關鍵字，以宣告 Tuple 中每個欄位的隱含類型變數︰</span><span class="sxs-lookup"><span data-stu-id="545fe-247">You can also declare implicitly typed variables for each field in a tuple by using the `var` keyword outside the parentheses:</span></span>

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

<span data-ttu-id="545fe-248">它也可以搭配使用 `var` 關鍵字與括弧內的任何或所有變數宣告。</span><span class="sxs-lookup"><span data-stu-id="545fe-248">It is also legal to use the `var` keyword with any, or all of the variable declarations inside the parentheses.</span></span> 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

<span data-ttu-id="545fe-249">請注意，您無法在括弧外部使用特定類型，即使 Tuple 中的每個欄位都有相同的類型也是一樣。</span><span class="sxs-lookup"><span data-stu-id="545fe-249">Note that you cannot use a specific type outside the parentheses, even if every field in the tuple has the same type.</span></span>

<span data-ttu-id="545fe-250">您可以解構 tuple 以及現有宣告：</span><span class="sxs-lookup"><span data-stu-id="545fe-250">You can deconstruct tuples with existing declarations as well:</span></span>

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  <span data-ttu-id="545fe-251">您不能混用括號內的宣告與現有的宣告。</span><span class="sxs-lookup"><span data-stu-id="545fe-251">You cannot mix existing declarations with declarations inside the parentheses.</span></span> <span data-ttu-id="545fe-252">比方說，不允許下列： `(var x, y) = MyMethod();`。</span><span class="sxs-lookup"><span data-stu-id="545fe-252">For instance, the following is not allowed: `(var x, y) = MyMethod();`.</span></span> <span data-ttu-id="545fe-253">這會產生錯誤 CS8184 因為*x*在括號內宣告和*y*先前宣告其他位置。</span><span class="sxs-lookup"><span data-stu-id="545fe-253">This produces error CS8184 because *x* is declared inside the parentheses and *y* is previously declared elsewhere.</span></span>

### <a name="deconstructing-user-defined-types"></a><span data-ttu-id="545fe-254">解構使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="545fe-254">Deconstructing user defined types</span></span>

<span data-ttu-id="545fe-255">任何 Tuple 類型都可以如上進行解構。</span><span class="sxs-lookup"><span data-stu-id="545fe-255">Any tuple type can be deconstructed as shown above.</span></span> <span data-ttu-id="545fe-256">也很容易在任何使用者定義型別 (類別、結構，甚至是介面) 上啟用解構。</span><span class="sxs-lookup"><span data-stu-id="545fe-256">It's also easy to enable deconstruction on any user defined type (classes, structs, or even interfaces).</span></span>

<span data-ttu-id="545fe-257">類型作者可以定義一或多個 `Deconstruct` 方法，以將值指派給任意數目的 `out` 變數，而變數代表構成類型的資料項目。</span><span class="sxs-lookup"><span data-stu-id="545fe-257">The type author can define one or more `Deconstruct` methods that assign values to any number of `out` variables representing the data elements that make up the type.</span></span> <span data-ttu-id="545fe-258">例如，下列 `Person` 類型會定義 `Deconstruct` 方法，以將人員物件解構為代表名字和姓氏的元素：</span><span class="sxs-lookup"><span data-stu-id="545fe-258">For example, the following `Person` type defines a `Deconstruct` method that deconstructs a person object into the elements representing the first name and last name:</span></span>

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

<span data-ttu-id="545fe-259">解構方法會啟用從 `Person` 到兩個字串的指派，而這兩個字串代表 `FirstName` 和 `LastName` 屬性：</span><span class="sxs-lookup"><span data-stu-id="545fe-259">The deconstruct method enables assignment from a `Person` to two strings, representing the `FirstName` and `LastName` properties:</span></span>

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

<span data-ttu-id="545fe-260">您甚至可以針對不是由您撰寫的類型啟用解構。</span><span class="sxs-lookup"><span data-stu-id="545fe-260">You can enable deconstruction even for types you did not author.</span></span>
<span data-ttu-id="545fe-261">`Deconstruct` 方法可以是解除封裝物件的可存取資料成員的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="545fe-261">The `Deconstruct` method can be an extension method that unpackages the accessible data members of an object.</span></span> <span data-ttu-id="545fe-262">下列範例示範衍生自 `Person` 類型的 `Student` 類型，以及將 `Student` 解構為三個變數的擴充方法，而這三個變數代表 `FirstName`、`LastName` 和 `GPA`：</span><span class="sxs-lookup"><span data-stu-id="545fe-262">The example below shows a `Student` type, derived from the `Person` type, and an extension method that deconstructs a `Student` into three variables, representing the `FirstName`, the `LastName` and the `GPA`:</span></span>

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

<span data-ttu-id="545fe-263">`Student` 物件現在有兩個可存取的 `Deconstruct` 方法︰針對 `Student` 類型所宣告的擴充方法，以及 `Person` 類型的成員。</span><span class="sxs-lookup"><span data-stu-id="545fe-263">A `Student` object now has two accessible `Deconstruct` methods: the extension method declared for `Student` types, and the member of the `Person` type.</span></span> <span data-ttu-id="545fe-264">兩者都在範圍內，並可將 `Student` 解構為兩個或三個變數。</span><span class="sxs-lookup"><span data-stu-id="545fe-264">Both are in scope, and that enables a `Student` to be deconstructed into either two variables or three.</span></span>
<span data-ttu-id="545fe-265">如果您將一位學生指派給三個變數，則都會傳回名字、姓氏和 GPA。</span><span class="sxs-lookup"><span data-stu-id="545fe-265">If you assign a student to three variables, the first name, last name, and GPA are all returned.</span></span> <span data-ttu-id="545fe-266">如果您將一位學生指派給兩個變數，則只會傳回名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="545fe-266">If you assign a student to two variables, only the first name and the last name are returned.</span></span>

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

<span data-ttu-id="545fe-267">定義類別或類別階層中的多個 `Deconstruct` 方法時必須十分小心。</span><span class="sxs-lookup"><span data-stu-id="545fe-267">You should be very careful defining multiple `Deconstruct` methods in a class or a class hierarchy.</span></span> <span data-ttu-id="545fe-268">`out` 參數數目相同的多個 `Deconstruct` 方法可能會快速地造成模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="545fe-268">Multiple `Deconstruct` methods that have the same number of `out` parameters can quickly cause ambiguities.</span></span> <span data-ttu-id="545fe-269">呼叫端可能無法輕鬆地呼叫所需的 `Deconstruct` 方法。</span><span class="sxs-lookup"><span data-stu-id="545fe-269">Callers may not be able to easily call the desired `Deconstruct` method.</span></span>

<span data-ttu-id="545fe-270">在此範例中，模稜兩可呼叫的機率最小，因為 `Person` 的 `Deconstruct` 方法有兩個輸出參數，而 `Student` 的 `Deconstruct` 方法則有三個。</span><span class="sxs-lookup"><span data-stu-id="545fe-270">In this example, there is minimal chance for an ambiguous call because the `Deconstruct` method for `Person` has two output parameters, and the `Deconstruct` method for `Student` has three.</span></span>

## <a name="conclusion"></a><span data-ttu-id="545fe-271">結論</span><span class="sxs-lookup"><span data-stu-id="545fe-271">Conclusion</span></span> 

<span data-ttu-id="545fe-272">具名元組的新語言和程式庫支援可讓您更輕鬆地處理使用可儲存多個元素的資料結構但未定義行為的設計，就像類別與結構一樣。</span><span class="sxs-lookup"><span data-stu-id="545fe-272">The new language and library support for named tuples makes it much easier to work with designs that use data structures that store multiple elements but do not define behavior, as classes and structs do.</span></span> <span data-ttu-id="545fe-273">將 Tuple 用於這些類型十分簡單且簡潔。</span><span class="sxs-lookup"><span data-stu-id="545fe-273">It's easy and concise to use tuples for those types.</span></span> <span data-ttu-id="545fe-274">您會獲得靜態類型檢查的所有優點，而不需要使用更詳細的 `class` 或 `struct` 語法來撰寫類型。</span><span class="sxs-lookup"><span data-stu-id="545fe-274">You get all the benefits of static type checking, without needing to author types using the more verbose `class` or `struct` syntax.</span></span> <span data-ttu-id="545fe-275">即便如此，它們還是最適用於為 `private` 或 `internal` 的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="545fe-275">Even so, they are most useful for utility methods that are `private`, or `internal`.</span></span> <span data-ttu-id="545fe-276">公用方法傳回具有多個元素的值時，請建立使用者定義型別，即 `class` 或 `struct` 型別。</span><span class="sxs-lookup"><span data-stu-id="545fe-276">Create user defined types, either `class` or `struct` types when your public methods return a value that has multiple elements.</span></span>
