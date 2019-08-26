---
title: Tuple 型別 - C# 手冊
description: 了解 C# 中的未具名和具名 Tuple 類型
ms.date: 05/15/2018
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: dc02fceb2901fb9cb7bf71869213d8b178520900
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988410"
---
# <a name="c-tuple-types"></a><span data-ttu-id="07f65-103">C# Tuple 型別</span><span class="sxs-lookup"><span data-stu-id="07f65-103">C# tuple types</span></span>

<span data-ttu-id="07f65-104">C# Tuple 是您使用輕量型語法所定義的型別。</span><span class="sxs-lookup"><span data-stu-id="07f65-104">C# tuples are types that you define using a lightweight syntax.</span></span> <span data-ttu-id="07f65-105">優點包括更簡單的語法、以元素數目 (稱為基數) 與型別為依據的轉換規則，以及複本、相等測試與指派的一致性規則。</span><span class="sxs-lookup"><span data-stu-id="07f65-105">The advantages include a simpler syntax, rules for conversions based on number (referred to as cardinality) and types of elements, and consistent rules for copies, equality tests, and assignments.</span></span> <span data-ttu-id="07f65-106">折衷方式是，Tuple 不支援與繼承建立關聯的一些物件導向慣用語。</span><span class="sxs-lookup"><span data-stu-id="07f65-106">As a tradeoff, tuples do not support some of the object-oriented idioms associated with inheritance.</span></span> <span data-ttu-id="07f65-107">您可以在 [C# 7.0 新功能中的 Tuple](whats-new/csharp-7.md#tuples) 文章的一節中取得概觀。</span><span class="sxs-lookup"><span data-stu-id="07f65-107">You can get an overview in the section on [tuples in the What's new in C# 7.0](whats-new/csharp-7.md#tuples) article.</span></span>

<span data-ttu-id="07f65-108">在本文章中，您將了解在 C# 7.0 及更新版本中控管 Tuple 的語言規則、不同的 Tuple 使用方式，以及使用 Tuple 的初始指導。</span><span class="sxs-lookup"><span data-stu-id="07f65-108">In this article, you'll learn the language rules governing tuples in C# 7.0 and later versions, different ways to use them, and initial guidance on working with tuples.</span></span>

> [!NOTE]
> <span data-ttu-id="07f65-109">新的 Tuple 功能需要 <xref:System.ValueTuple> 類型。</span><span class="sxs-lookup"><span data-stu-id="07f65-109">The new tuples features require the <xref:System.ValueTuple> types.</span></span>
> <span data-ttu-id="07f65-110">您必須新增 NuGet 套件 [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/)，以將它用於不包含類型的平台。</span><span class="sxs-lookup"><span data-stu-id="07f65-110">You must add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) in order to use it on platforms that do not include the types.</span></span>
>
> <span data-ttu-id="07f65-111">這類似於依賴架構中所傳遞類型的其他語言功能。</span><span class="sxs-lookup"><span data-stu-id="07f65-111">This is similar to other language features that rely on types delivered in the framework.</span></span> <span data-ttu-id="07f65-112">範例包含依賴 `INotifyCompletion` 介面的 `async` 和 `await` 以及依賴 `IEnumerable<T>` 的 LINQ。</span><span class="sxs-lookup"><span data-stu-id="07f65-112">Examples include `async` and `await` relying on the `INotifyCompletion` interface, and LINQ relying on `IEnumerable<T>`.</span></span> <span data-ttu-id="07f65-113">不過，傳遞機制會變更，因為 .NET 變得與平台更為無關。</span><span class="sxs-lookup"><span data-stu-id="07f65-113">However, the delivery mechanism is changing as .NET is becoming more platform independent.</span></span> <span data-ttu-id="07f65-114">.NET Framework 可能不會永遠隨附於相同的步調，作為語言編譯器。</span><span class="sxs-lookup"><span data-stu-id="07f65-114">The .NET Framework may not always ship on the same cadence as the language compiler.</span></span> <span data-ttu-id="07f65-115">如果新語言功能依賴新類型，則在提供語言功能時，會以 NuGet 套件形式提供這些類型。</span><span class="sxs-lookup"><span data-stu-id="07f65-115">When new language features rely on new types, those types will be available as NuGet packages when the language features ship.</span></span> <span data-ttu-id="07f65-116">因為這些新類型會新增至 .NET Standard API 並傳遞為架構的一部分，所以將會移除 NuGet 套件需求。</span><span class="sxs-lookup"><span data-stu-id="07f65-116">As these new types get added to the .NET Standard API and delivered as part of the framework, the NuGet package requirement will be removed.</span></span>

<span data-ttu-id="07f65-117">讓我們開始了解新增 Tuple 支援的原因。</span><span class="sxs-lookup"><span data-stu-id="07f65-117">Let's start with the reasons for adding new tuple support.</span></span> <span data-ttu-id="07f65-118">方法會傳回單一物件。</span><span class="sxs-lookup"><span data-stu-id="07f65-118">Methods return a single object.</span></span> <span data-ttu-id="07f65-119">Tuple 可讓您更輕鬆地將多個值封裝在該單一物件中。</span><span class="sxs-lookup"><span data-stu-id="07f65-119">Tuples enable you to package multiple values in that single object more easily.</span></span>

<span data-ttu-id="07f65-120">.NET Framework 已有泛型 `Tuple` 類別。</span><span class="sxs-lookup"><span data-stu-id="07f65-120">The .NET Framework already has generic `Tuple` classes.</span></span> <span data-ttu-id="07f65-121">不過，這些類別有兩個主要限制。</span><span class="sxs-lookup"><span data-stu-id="07f65-121">These classes, however, had two major limitations.</span></span> <span data-ttu-id="07f65-122">其中一個限制是，`Tuple` 已將其屬性命名為 `Item1`、`Item2` 等等。</span><span class="sxs-lookup"><span data-stu-id="07f65-122">For one, the `Tuple` classes named their properties `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="07f65-123">這些名稱未包含任何語意資訊。</span><span class="sxs-lookup"><span data-stu-id="07f65-123">Those names carry no semantic information.</span></span> <span data-ttu-id="07f65-124">使用這些 `Tuple` 類型無法表達各個屬性的意義。</span><span class="sxs-lookup"><span data-stu-id="07f65-124">Using these `Tuple` types does not enable communicating the meaning of each of the properties.</span></span> <span data-ttu-id="07f65-125">而新的語言功能則可讓您為元組中的元素宣告及使用具有語意意義的名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-125">The new language features enable you to declare and use semantically meaningful names for the elements in a tuple.</span></span>

<span data-ttu-id="07f65-126">`Tuple` 類別會造成更多的效能考量，因為它們都是參考型別。</span><span class="sxs-lookup"><span data-stu-id="07f65-126">The `Tuple` classes cause more performance concerns because they are reference types.</span></span> <span data-ttu-id="07f65-127">使用其中一個 `Tuple` 類型表示配置物件。</span><span class="sxs-lookup"><span data-stu-id="07f65-127">Using one of the `Tuple` types means allocating objects.</span></span> <span data-ttu-id="07f65-128">在最忙碌路徑上，配置許多小型物件可能會對您應用程式的效能造成可觀的衝擊。</span><span class="sxs-lookup"><span data-stu-id="07f65-128">On hot paths, allocating many small objects can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="07f65-129">因此，元組的語言支援會運用新的 `ValueTuple` 結構。</span><span class="sxs-lookup"><span data-stu-id="07f65-129">Therefore, the language support for tuples leverages the new `ValueTuple` structs.</span></span>

<span data-ttu-id="07f65-130">若要避免這些缺點，您可以建立 `class` 或 `struct` 來帶出多個元素。</span><span class="sxs-lookup"><span data-stu-id="07f65-130">To avoid those deficiencies, you could create a `class` or a `struct` to carry multiple elements.</span></span> <span data-ttu-id="07f65-131">不幸的是，您需要執行更多工作，並且會模糊您的設計目的。</span><span class="sxs-lookup"><span data-stu-id="07f65-131">Unfortunately, that's more work for you, and it obscures your design intent.</span></span> <span data-ttu-id="07f65-132">設定 `struct` 或 `class` 表示您定義的類型同時具有資料和行為。</span><span class="sxs-lookup"><span data-stu-id="07f65-132">Making a `struct` or `class` implies that you are defining a type with both data and behavior.</span></span> <span data-ttu-id="07f65-133">許多次，您都只想要將多個值儲存在單一物件中。</span><span class="sxs-lookup"><span data-stu-id="07f65-133">Many times, you simply want to store multiple values in a single object.</span></span>

<span data-ttu-id="07f65-134">語言功能和 `ValueTuple` 泛型結構會強制執行您無法將任何行為 (方法) 新增至這些 Tuple 類型的規則。</span><span class="sxs-lookup"><span data-stu-id="07f65-134">The language features and the `ValueTuple` generic structs enforce the rule that you cannot add any behavior (methods) to these tuple types.</span></span>
<span data-ttu-id="07f65-135">所有 `ValueTuple` 類型都是「可變動結構」  。</span><span class="sxs-lookup"><span data-stu-id="07f65-135">All the `ValueTuple` types are *mutable structs*.</span></span> <span data-ttu-id="07f65-136">每個成員欄位都是公用欄位。</span><span class="sxs-lookup"><span data-stu-id="07f65-136">Each member field is a public field.</span></span> <span data-ttu-id="07f65-137">這可將它們設為非常輕量型。</span><span class="sxs-lookup"><span data-stu-id="07f65-137">That makes them very lightweight.</span></span> <span data-ttu-id="07f65-138">不過，這表示，如果不變性十分重要，則不應該使用 Tuple。</span><span class="sxs-lookup"><span data-stu-id="07f65-138">However, that means tuples should not be used where immutability is important.</span></span>

<span data-ttu-id="07f65-139">Tuple 是比 `class` 和 `struct` 類型更為簡單且更具彈性的資料容器。</span><span class="sxs-lookup"><span data-stu-id="07f65-139">Tuples are both simpler and more flexible data containers than `class` and `struct` types.</span></span> <span data-ttu-id="07f65-140">讓我們來探索這些差異。</span><span class="sxs-lookup"><span data-stu-id="07f65-140">Let's explore those differences.</span></span>

## <a name="named-and-unnamed-tuples"></a><span data-ttu-id="07f65-141">具名和未具名 Tuple</span><span class="sxs-lookup"><span data-stu-id="07f65-141">Named and unnamed tuples</span></span>

<span data-ttu-id="07f65-142">`ValueTuple` 結構具有名為 `Item1`、`Item2`、`Item3` 等等的欄位，而這些欄位與現有 `Tuple` 型別中所定義的屬性類似。</span><span class="sxs-lookup"><span data-stu-id="07f65-142">The `ValueTuple` struct has fields named `Item1`, `Item2`, `Item3`, and so on, similar to the properties defined in the existing `Tuple` types.</span></span>
<span data-ttu-id="07f65-143">這些名稱只是您可用於「未具名 Tuple」  的名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-143">These names are the only names you can use for *unnamed tuples*.</span></span> <span data-ttu-id="07f65-144">當您未將任何替代欄位名稱提供給 Tuple 時，即已建立未具名 Tuple：</span><span class="sxs-lookup"><span data-stu-id="07f65-144">When you do not provide any alternative field names to a tuple, you've created an unnamed tuple:</span></span>

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

<span data-ttu-id="07f65-145">上述範例中使用了常值常數將 Tuple 初始化，且不會有在 C# 7.1 中使用「Tuple 欄位名稱投射轉換」  建立的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-145">The tuple in the previous example was initialized using literal constants and won't have element names created using *tuple field name projections* in C# 7.1.</span></span>

<span data-ttu-id="07f65-146">不過，當您初始化 Tuple 時，可以使用新的語言功能，讓每個欄位具有更適合的名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-146">However, when you initialize a tuple, you can use new language features that give better names to each field.</span></span> <span data-ttu-id="07f65-147">這麼做會建立「具名 Tuple」  。</span><span class="sxs-lookup"><span data-stu-id="07f65-147">Doing so creates a *named tuple*.</span></span>
<span data-ttu-id="07f65-148">具名元組仍會有名為 `Item1`、`Item2`、`Item3` 等等的元素。</span><span class="sxs-lookup"><span data-stu-id="07f65-148">Named tuples still have elements named `Item1`, `Item2`, `Item3` and so on.</span></span>
<span data-ttu-id="07f65-149">但對於您已命名的任一元素，也會有同義字。</span><span class="sxs-lookup"><span data-stu-id="07f65-149">But they also have synonyms for any of those elements that you have named.</span></span>
<span data-ttu-id="07f65-150">您可以指定每個元素的名稱來建立具名元組。</span><span class="sxs-lookup"><span data-stu-id="07f65-150">You create a named tuple by specifying the names for each element.</span></span> <span data-ttu-id="07f65-151">其中一個方式是在 Tuple 初始化期間指定名稱：</span><span class="sxs-lookup"><span data-stu-id="07f65-151">One way is to specify the names as part of the tuple initialization:</span></span>

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

<span data-ttu-id="07f65-152">這些同義字是由編譯器和語言所處理，讓您可以有效率地使用具名 Tuple。</span><span class="sxs-lookup"><span data-stu-id="07f65-152">These synonyms are handled by the compiler and the language so that you can use named tuples effectively.</span></span> <span data-ttu-id="07f65-153">IDE 和編輯器可以使用 Roslyn API 來讀取這些語意名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-153">IDEs and editors can read these semantic names using the Roslyn APIs.</span></span> <span data-ttu-id="07f65-154">您可以在相同組件的任何地方，依據這些語意名稱來參考具名 Tuple 的元素。</span><span class="sxs-lookup"><span data-stu-id="07f65-154">You can reference the elements of a named tuple by those semantic names anywhere in the same assembly.</span></span> <span data-ttu-id="07f65-155">產生所編譯的輸出時，編譯器會將您定義的名稱取代為 `Item*` 對等項目。</span><span class="sxs-lookup"><span data-stu-id="07f65-155">The compiler replaces the names you've defined with `Item*` equivalents when generating the compiled output.</span></span> <span data-ttu-id="07f65-156">編譯過的 Microsoft Intermediate Language (MSIL) 不會包括您為這些元素指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-156">The compiled Microsoft Intermediate Language (MSIL) does not include the names you've given these elements.</span></span>

<span data-ttu-id="07f65-157">從 C# 7.1 開始，元組的欄位名稱可從用來將元組初始化的變數提供。</span><span class="sxs-lookup"><span data-stu-id="07f65-157">Beginning with C# 7.1, the field names for a tuple may be provided from the variables used to initialize the tuple.</span></span> <span data-ttu-id="07f65-158">即為 **[元組投影初始設定式](#tuple-projection-initializers)** 。</span><span class="sxs-lookup"><span data-stu-id="07f65-158">This is referred to as **[tuple projection initializers](#tuple-projection-initializers)**.</span></span> <span data-ttu-id="07f65-159">下列程式碼會建立名為 `accumulation` 的元組，並有元素 `count` (整數) 與 `sum` (雙精度浮點數)。</span><span class="sxs-lookup"><span data-stu-id="07f65-159">The following code creates a tuple named `accumulation` with elements `count` (an integer), and `sum` (a double).</span></span>

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

<span data-ttu-id="07f65-160">編譯器必須知道您針對從公用方法或屬性傳回之 Tuple 所建立的名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-160">The compiler must communicate those names you created for tuples that are returned from public methods or properties.</span></span> <span data-ttu-id="07f65-161">在這些情況下，編譯器會在方法上新增 <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="07f65-161">In those cases, the compiler adds a <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> attribute on the method.</span></span> <span data-ttu-id="07f65-162">這個屬性包含 <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> 清單屬性，其中包含為 Tuple 中各元素指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-162">This attribute contains a <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> list property that contains the names given to each of the elements in the tuple.</span></span>

> [!NOTE]
> <span data-ttu-id="07f65-163">Visual Studio 這類開發工具也會讀取該中繼資料，並使用中繼資料欄位名稱來提供 IntelliSense 和其他功能。</span><span class="sxs-lookup"><span data-stu-id="07f65-163">Development Tools, such as Visual Studio, also read that metadata, and provide IntelliSense and other features using the metadata field names.</span></span>

<span data-ttu-id="07f65-164">請務必了解新 Tuple 的這些基礎基本項目和 `ValueTuple` 類型，以了解將具名 Tuple 指派給彼此的規則。</span><span class="sxs-lookup"><span data-stu-id="07f65-164">It is important to understand these underlying fundamentals of the new tuples and the `ValueTuple` type in order to understand the rules for assigning named tuples to each other.</span></span>

## <a name="tuple-projection-initializers"></a><span data-ttu-id="07f65-165">元組投影初始設定式</span><span class="sxs-lookup"><span data-stu-id="07f65-165">Tuple projection initializers</span></span>

<span data-ttu-id="07f65-166">一般來說，元組投影初始設定式會使用元組初始化陳述式右手邊的變數或欄位名稱來運作。</span><span class="sxs-lookup"><span data-stu-id="07f65-166">In general, tuple projection initializers work by using the variable or field names from the right-hand side of a tuple initialization statement.</span></span>
<span data-ttu-id="07f65-167">如有指定明確名稱，則會優先於任何投影名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-167">If an explicit name is given, that takes precedence over any projected name.</span></span> <span data-ttu-id="07f65-168">例如，在下列初始設定式中，元素為 `explicitFieldOne` 與 `explicitFieldTwo`，而非 `localVariableOne` 與 `localVariableTwo`：</span><span class="sxs-lookup"><span data-stu-id="07f65-168">For example, in the following initializer, the elements are `explicitFieldOne` and `explicitFieldTwo`, not `localVariableOne` and `localVariableTwo`:</span></span>

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

<span data-ttu-id="07f65-169">對於未提供明確名稱的任何欄位，會投影適用的隱含名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-169">For any field where an explicit name is not provided, an applicable implicit name is projected.</span></span> <span data-ttu-id="07f65-170">您不需要明確或隱含地提供語意名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-170">There is no requirement to provide semantic names, either explicitly or implicitly.</span></span> <span data-ttu-id="07f65-171">下列初始設定式會有值為 `42` 的欄位名稱 `Item1`，以及值為 "The answer to everything" 的欄位名稱 `stringContent`：</span><span class="sxs-lookup"><span data-stu-id="07f65-171">The following initializer has     field names `Item1`, whose value is `42` and `stringContent`, whose value is "The answer to everything":</span></span>

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

<span data-ttu-id="07f65-172">在兩種情況下，候選欄位名稱不會投影至元組欄位：</span><span class="sxs-lookup"><span data-stu-id="07f65-172">There are two conditions where candidate field names are not projected onto the tuple field:</span></span>

1. <span data-ttu-id="07f65-173">候選名稱是保留的元組名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-173">When the candidate name is a reserved tuple name.</span></span> <span data-ttu-id="07f65-174">範例包括 `Item3`、`ToString`，</span><span class="sxs-lookup"><span data-stu-id="07f65-174">Examples include `Item3`, `ToString`.</span></span> <span data-ttu-id="07f65-175">或 `Rest`。</span><span class="sxs-lookup"><span data-stu-id="07f65-175">or `Rest`.</span></span>
1. <span data-ttu-id="07f65-176">候選名稱與另一個明確或隱含的元組欄位名稱重複。</span><span class="sxs-lookup"><span data-stu-id="07f65-176">When the candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="07f65-177">這些情況可避免語意模糊。</span><span class="sxs-lookup"><span data-stu-id="07f65-177">These conditions avoid ambiguity.</span></span> <span data-ttu-id="07f65-178">如果將這些名稱作為元組中的欄位名稱使用，就會造成語意模糊。</span><span class="sxs-lookup"><span data-stu-id="07f65-178">These names would cause an ambiguity if they were used as the field names for a field in a tuple.</span></span> <span data-ttu-id="07f65-179">這兩種情況都不會造成編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="07f65-179">Neither of these conditions cause compile-time errors.</span></span> <span data-ttu-id="07f65-180">反之，沒有投影名稱的元素不會有語意名稱對其投影。</span><span class="sxs-lookup"><span data-stu-id="07f65-180">Instead, the elements without projected names do not have semantic names projected for them.</span></span>  <span data-ttu-id="07f65-181">下列範例將示範這些情況：</span><span class="sxs-lookup"><span data-stu-id="07f65-181">The following examples demonstrate these conditions:</span></span>

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

<span data-ttu-id="07f65-182">這些情況不會造成編譯器錯誤，因為這使用 C# 7.0 撰寫的程式碼而言會是重大變更，而當時元組欄位名稱投影還無法使用。</span><span class="sxs-lookup"><span data-stu-id="07f65-182">These situations do not cause compiler errors because that would be a breaking change for code written with C# 7.0, when tuple field name projections were not available.</span></span>

## <a name="equality-and-tuples"></a><span data-ttu-id="07f65-183">相等和 Tuple</span><span class="sxs-lookup"><span data-stu-id="07f65-183">Equality and tuples</span></span>

<span data-ttu-id="07f65-184">從 C# 7.3 開始，Tuple 型別支援 `==` 和 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="07f65-184">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="07f65-185">這些運算子的運作方式，是透過依順序比較左側引數的每個成員與右側引數的每個成員。</span><span class="sxs-lookup"><span data-stu-id="07f65-185">These operators work by comparing each member of the left argument to each member of the right argument in order.</span></span> <span data-ttu-id="07f65-186">這些比較會進行最少運算。</span><span class="sxs-lookup"><span data-stu-id="07f65-186">These comparisons short-circuit.</span></span> <span data-ttu-id="07f65-187">只要有一組不相等，它們就會停止評估成員。</span><span class="sxs-lookup"><span data-stu-id="07f65-187">They will stop evaluating members as soon as one pair is not equal.</span></span> <span data-ttu-id="07f65-188">下列程式碼範例使用 `==`，但比較規則均適用於 `!=`。</span><span class="sxs-lookup"><span data-stu-id="07f65-188">The following code examples use `==`, but the comparison rules all apply to `!=`.</span></span> <span data-ttu-id="07f65-189">下列程式碼範例顯示了兩組整數的相等比較：</span><span class="sxs-lookup"><span data-stu-id="07f65-189">The following code example shows an equality comparison for two pairs of integers:</span></span>

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#Equality "Testing tuples for equality")]

<span data-ttu-id="07f65-190">有數個規則讓 tuple 相等測試更加方便。</span><span class="sxs-lookup"><span data-stu-id="07f65-190">There are several rules that make tuple equality tests more convenient.</span></span> <span data-ttu-id="07f65-191">如果其中一個 Tuple 是可為 null 的 Tuple，則 Tuple 相等會執行[提升轉換](~/_csharplang/spec/conversions.md#lifted-conversion-operators)，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="07f65-191">Tuple equality performs [lifted conversions](~/_csharplang/spec/conversions.md#lifted-conversion-operators) if one of the tuples is a nullable tuple, as shown in the following code:</span></span>

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

<span data-ttu-id="07f65-192">Tuple 相等也會對這兩個 Tuple 的每個成員執行隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="07f65-192">Tuple equality also performs implicit conversions on each member of both tuples.</span></span> <span data-ttu-id="07f65-193">其中包括提升轉換、擴展轉換或其他的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="07f65-193">These include lifted conversions, widening conversions, or other implicit conversions.</span></span> <span data-ttu-id="07f65-194">下列範例顯示，由於從整數到長整數的隱含轉換，整數 2-tuple 可以與長整數 2-tuple 進行比較：</span><span class="sxs-lookup"><span data-stu-id="07f65-194">The following examples show that an integer 2-tuple can be compared to a long 2-tuple because of the implicit conversion from integer to long:</span></span>

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

<span data-ttu-id="07f65-195">Tuple 成員的名稱不會參與相等測試。</span><span class="sxs-lookup"><span data-stu-id="07f65-195">The names of the tuple members do not participate in tests for equality.</span></span> <span data-ttu-id="07f65-196">不過，如果其中一個運算元是具有明確名稱的 Tuple 常值，則編譯器會產生警告 CS8383，前提是這些名稱與另一個運算元的名稱不相符。</span><span class="sxs-lookup"><span data-stu-id="07f65-196">However, if one of the operands is a tuple literal with explicit names, the compiler generates warning CS8383 if those names do not match the names of the other operand.</span></span>
<span data-ttu-id="07f65-197">在兩個運算元都是 Tuple 常值的情況下，警告會在右邊的運算元上，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="07f65-197">In the case where both operands are tuple literals, the warning is on the right operand as shown in the following example:</span></span>

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

<span data-ttu-id="07f65-198">最後，Tuple 可能包含巢狀 Tuple。</span><span class="sxs-lookup"><span data-stu-id="07f65-198">Finally, tuples may contain nested tuples.</span></span> <span data-ttu-id="07f65-199">Tuple 相等會透過巢狀 Tuple 比較每個運算元的「圖形」，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="07f65-199">Tuple equality compares the "shape" of each operand through nested tuples as shown in the following example:</span></span>

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

<span data-ttu-id="07f65-200">它是當您有不同的圖形時，比較兩個 Tuple 是否相等 (或不相等) 的編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="07f65-200">It's a compile time error to compare two tuples for equality (or inequality) when they have different shapes.</span></span> <span data-ttu-id="07f65-201">編譯器不會為了比較而嘗試解構任何巢狀 Tuple。</span><span class="sxs-lookup"><span data-stu-id="07f65-201">The compiler won't attempt any deconstruction of nested tuples in order to compare them.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="07f65-202">指派和 Tuple</span><span class="sxs-lookup"><span data-stu-id="07f65-202">Assignment and tuples</span></span>

<span data-ttu-id="07f65-203">該語言支援具有相同元素數目之 Tuple 型別之間的指派，其中右側的每個元素可以隱含地轉換成其對應的左側元素。</span><span class="sxs-lookup"><span data-stu-id="07f65-203">The language supports assignment between tuple types that have the same number of elements, where each right-hand side element can be implicitly converted to its corresponding left-hand side element.</span></span> <span data-ttu-id="07f65-204">不會考慮對指派進行其他轉換。</span><span class="sxs-lookup"><span data-stu-id="07f65-204">Other conversions aren't considered for assignments.</span></span> <span data-ttu-id="07f65-205">它是當 Tuple 有不同圖形時，將一個 Tuple 指派到另一個 Tuple 的編譯時間錯誤。</span><span class="sxs-lookup"><span data-stu-id="07f65-205">It's a compile time error to assign one tuple to another when they have different shapes.</span></span> <span data-ttu-id="07f65-206">編譯器將不會嘗試任何巢狀 Tuple 的解構以指派它們。</span><span class="sxs-lookup"><span data-stu-id="07f65-206">The compiler won't attempt any deconstruction of nested tuples in order to assign them.</span></span>
<span data-ttu-id="07f65-207">讓我們看看 Tuple 類型之間允許的指派類型。</span><span class="sxs-lookup"><span data-stu-id="07f65-207">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="07f65-208">請考慮在下列範例中使用的這些參數：</span><span class="sxs-lookup"><span data-stu-id="07f65-208">Consider these variables used in the following examples:</span></span>

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

<span data-ttu-id="07f65-209">前兩個變數 `unnamed` 與 `anonymous` 都未提供元素的語意名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-209">The first two variables, `unnamed` and `anonymous` do not have semantic names provided for the elements.</span></span> <span data-ttu-id="07f65-210">欄位名稱為 `Item1` 和 `Item2`。</span><span class="sxs-lookup"><span data-stu-id="07f65-210">The field names are `Item1` and `Item2`.</span></span>
<span data-ttu-id="07f65-211">後兩個變數 `named` 與 `differentName` 皆有為元素指定的語意名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-211">The last two variables, `named` and `differentName` have semantic names given for the elements.</span></span> <span data-ttu-id="07f65-212">這兩個 Tuple 有不同的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-212">These two tuples have different names for the elements.</span></span>

<span data-ttu-id="07f65-213">這四個元組全都有相同數目的元素 (稱為「基數」)，而且這些元素的類型完全相同。</span><span class="sxs-lookup"><span data-stu-id="07f65-213">All four of these tuples have the same number of elements (referred to as 'cardinality') and the types of those elements are identical.</span></span> <span data-ttu-id="07f65-214">因此，所有這些指派都會運作︰</span><span class="sxs-lookup"><span data-stu-id="07f65-214">Therefore, all of these assignments work:</span></span>

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

<span data-ttu-id="07f65-215">請注意，不會指派 Tuple 的名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-215">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="07f65-216">元素的值會依照元組中的元素順序指派。</span><span class="sxs-lookup"><span data-stu-id="07f65-216">The values of the elements are assigned following the order of the elements in the tuple.</span></span>

<span data-ttu-id="07f65-217">類型或元素數目不同的元組則無法指派：</span><span class="sxs-lookup"><span data-stu-id="07f65-217">Tuples of different types or numbers of elements are not assignable:</span></span>

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="07f65-218">Tuple 作為方法傳回值</span><span class="sxs-lookup"><span data-stu-id="07f65-218">Tuples as method return values</span></span>

<span data-ttu-id="07f65-219">其中一個最常見的 Tuple 用法是作為方法傳回值。</span><span class="sxs-lookup"><span data-stu-id="07f65-219">One of the most common uses for tuples is as a method return value.</span></span> <span data-ttu-id="07f65-220">讓我們逐步解說一個範例。</span><span class="sxs-lookup"><span data-stu-id="07f65-220">Let's walk through one example.</span></span> <span data-ttu-id="07f65-221">請考慮使用這個計算一系列數字標準差的方法︰</span><span class="sxs-lookup"><span data-stu-id="07f65-221">Consider this method that computes the standard deviation for a sequence of numbers:</span></span>

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> <span data-ttu-id="07f65-222">這些範例會計算未修正的樣本標準差。</span><span class="sxs-lookup"><span data-stu-id="07f65-222">These examples compute the uncorrected sample standard deviation.</span></span>
> <span data-ttu-id="07f65-223">更正的範例標準差公式會將與平均值的平方差總和除以 (N-1)，而非 N，就像 `Average` 擴充方法一樣。</span><span class="sxs-lookup"><span data-stu-id="07f65-223">The corrected sample standard deviation formula would divide the sum of the squared differences from the mean by (N-1) instead of N, as the `Average` extension method does.</span></span> <span data-ttu-id="07f65-224">如需標準差的這些公式之差異的詳細資料，請參閱統計文字。</span><span class="sxs-lookup"><span data-stu-id="07f65-224">Consult a statistics text for more details on the differences between these formulas for standard deviation.</span></span>

<span data-ttu-id="07f65-225">上述程式碼會遵循標準差的文字方塊公式。</span><span class="sxs-lookup"><span data-stu-id="07f65-225">The preceding code follows the textbook formula for the standard deviation.</span></span> <span data-ttu-id="07f65-226">它會產生正確答案，但這是沒有效率的實作。</span><span class="sxs-lookup"><span data-stu-id="07f65-226">It produces the correct answer, but it's an inefficient implementation.</span></span> <span data-ttu-id="07f65-227">此方法會列舉序列兩次：一次是產生平均值，一次是產生平均值差之平方的平均值。</span><span class="sxs-lookup"><span data-stu-id="07f65-227">This method enumerates the sequence twice: Once to produce the average, and once to produce the average of the square of the difference of the average.</span></span>
<span data-ttu-id="07f65-228">(請記住，LINQ 查詢會變慢，因此，計算與平均值的差異以及這些差異的平均值只會建立一個列舉)。</span><span class="sxs-lookup"><span data-stu-id="07f65-228">(Remember that LINQ queries are evaluated lazily, so the computation of the differences from the mean and the average of those differences makes only one enumeration.)</span></span>

<span data-ttu-id="07f65-229">有替代公式可以只使用該序列的一個列舉來計算標準差。</span><span class="sxs-lookup"><span data-stu-id="07f65-229">There is an alternative formula that computes standard deviation using only one enumeration of the sequence.</span></span>  <span data-ttu-id="07f65-230">此計算會產生兩個值，因為它會列舉序列︰序列中所有項目的總和，以及每個值平方的總和︰</span><span class="sxs-lookup"><span data-stu-id="07f65-230">This computation produces two values as it enumerates the sequence: the sum of all items in the sequence, and the sum of the each value squared:</span></span>

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

<span data-ttu-id="07f65-231">此版本只會列舉序列一次。</span><span class="sxs-lookup"><span data-stu-id="07f65-231">This version enumerates the sequence exactly once.</span></span> <span data-ttu-id="07f65-232">但是它不是可重複使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="07f65-232">But it's not reusable code.</span></span> <span data-ttu-id="07f65-233">繼續工作時，會發現許多不同的統計運算使用序列中的項目數、序列總和，以及序列平方總和。</span><span class="sxs-lookup"><span data-stu-id="07f65-233">As you keep working, you'll find that many different statistical computations use the number of items in the sequence, the sum of the sequence, and the sum of the squares of the sequence.</span></span> <span data-ttu-id="07f65-234">讓我們重構這個方法，並撰寫可產生所有這三個值的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="07f65-234">Let's refactor this method and write a utility method that produces all three of those values.</span></span> <span data-ttu-id="07f65-235">所有這三個值都可以作為 Tuple 傳回。</span><span class="sxs-lookup"><span data-stu-id="07f65-235">All three values can be returned as a tuple.</span></span>

<span data-ttu-id="07f65-236">讓我們更新這個方法，因此在列舉期間計算的三個值會儲存在 Tuple 中。</span><span class="sxs-lookup"><span data-stu-id="07f65-236">Let's update this method so the three values computed during the enumeration are stored in a tuple.</span></span> <span data-ttu-id="07f65-237">這會建立這個版本：</span><span class="sxs-lookup"><span data-stu-id="07f65-237">That creates this version:</span></span>

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

<span data-ttu-id="07f65-238">Visual Studio 的重構支援可輕鬆地將核心統計資料的功能擷取至私用方法。</span><span class="sxs-lookup"><span data-stu-id="07f65-238">Visual Studio's Refactoring support makes it easy to extract the functionality for the core statistics into a private method.</span></span> <span data-ttu-id="07f65-239">這會提供 `private static` 方法，以傳回具有 `Sum`、`SumOfSquares` 和 `Count` 這三個值的 Tuple 類型：</span><span class="sxs-lookup"><span data-stu-id="07f65-239">That gives you a `private static` method that returns the tuple type with the three values of `Sum`, `SumOfSquares`, and `Count`:</span></span>

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
<span data-ttu-id="07f65-240">如果您想要手動進行一些快速編輯，則語言會啟用可讓您使用的更多選項。</span><span class="sxs-lookup"><span data-stu-id="07f65-240">The language enables a couple more options that you can use, if you want to make a few quick edits by hand.</span></span> <span data-ttu-id="07f65-241">首先，您可以使用 `var` 宣告來初始化 `ComputeSumAndSumOfSquares` 方法呼叫的 Tuple 結果。</span><span class="sxs-lookup"><span data-stu-id="07f65-241">First, you can use the `var` declaration to initialize the tuple result from the `ComputeSumAndSumOfSquares` method call.</span></span> <span data-ttu-id="07f65-242">您也可以在 `ComputeSumAndSumOfSquares` 方法內建立三個不連續變數。</span><span class="sxs-lookup"><span data-stu-id="07f65-242">You can also create three discrete variables inside the `ComputeSumAndSumOfSquares` method.</span></span> <span data-ttu-id="07f65-243">最終版本如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="07f65-243">The final version is shown in the following code:</span></span>

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

<span data-ttu-id="07f65-244">這個最終版本可以用於任何需要這三個值的方法或其任何子集。</span><span class="sxs-lookup"><span data-stu-id="07f65-244">This final version can be used for any method that needs those three values, or any subset of them.</span></span>

<span data-ttu-id="07f65-245">語言支援其他選項來管理這些元組傳回方法中的元素名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-245">The language supports other options in managing the names of the elements in these tuple-returning methods.</span></span>

<span data-ttu-id="07f65-246">您可以從傳回值宣告中移除欄位名稱，並傳回未具名 Tuple：</span><span class="sxs-lookup"><span data-stu-id="07f65-246">You can remove the field names from the return value declaration and return an unnamed tuple:</span></span>

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

<span data-ttu-id="07f65-247">這個 Tuple 的欄位會命名為 `Item1`、`Item2` 和 `Item3`。</span><span class="sxs-lookup"><span data-stu-id="07f65-247">The fields of this tuple are named `Item1`, `Item2`, and `Item3`.</span></span>
<span data-ttu-id="07f65-248">建議您為方法中傳回的元組元素提供語意名稱。</span><span class="sxs-lookup"><span data-stu-id="07f65-248">It's recommended that you provide semantic names to the elements of tuples returned from methods.</span></span>

<span data-ttu-id="07f65-249">Tuple 很有用的另一個習慣用法是當您撰寫 LINQ 查詢時。</span><span class="sxs-lookup"><span data-stu-id="07f65-249">Another idiom where tuples can be useful is when you are authoring LINQ queries.</span></span> <span data-ttu-id="07f65-250">最終投射結果通常包含所選取物件的部分屬性，但不是全部屬性。</span><span class="sxs-lookup"><span data-stu-id="07f65-250">The final projected result often contains some, but not all, of the properties of the objects being selected.</span></span>

<span data-ttu-id="07f65-251">您傳統上會將查詢結果投影至具有匿名型別的一系列物件。</span><span class="sxs-lookup"><span data-stu-id="07f65-251">You would traditionally project the results of the query into a sequence of objects that were an anonymous type.</span></span> <span data-ttu-id="07f65-252">這有許多限制，主要是因為無法在方法的傳回型別中方便地命名匿名型別。</span><span class="sxs-lookup"><span data-stu-id="07f65-252">That presented many limitations, primarily because anonymous types could not conveniently be named in the return type for a method.</span></span> <span data-ttu-id="07f65-253">使用 `object` 或 `dynamic` 作為結果類型的替代方式，其效果成本相當可觀。</span><span class="sxs-lookup"><span data-stu-id="07f65-253">Alternatives using `object` or `dynamic` as the type of the result came with significant performance costs.</span></span>

<span data-ttu-id="07f65-254">傳回一系列的元組類型十分簡單，而且在編譯時間以及透過 IDE 工具都可以使用元素的名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="07f65-254">Returning a sequence of a tuple type is easy, and the names and types of the elements are available at compile time and through IDE tools.</span></span>
<span data-ttu-id="07f65-255">例如，請考慮使用 ToDo 應用程式。</span><span class="sxs-lookup"><span data-stu-id="07f65-255">For example, consider a ToDo application.</span></span> <span data-ttu-id="07f65-256">您可以定義與下面類似的類別，以代表 ToDo 清單中的單一項目︰</span><span class="sxs-lookup"><span data-stu-id="07f65-256">You might define a class similar to the following to represent a single entry in the ToDo list:</span></span>

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

<span data-ttu-id="07f65-257">行動應用程式可能支援只顯示標題之目前 ToDo 項目的壓縮格式。</span><span class="sxs-lookup"><span data-stu-id="07f65-257">Your mobile applications may support a compact form of the current ToDo items that only displays the title.</span></span> <span data-ttu-id="07f65-258">該 LINQ 查詢會建立只包含識別碼和標題的投影。</span><span class="sxs-lookup"><span data-stu-id="07f65-258">That LINQ query would make a projection that includes only the ID and the title.</span></span> <span data-ttu-id="07f65-259">傳回一系列 Tuple 的方法表示該設計良好︰</span><span class="sxs-lookup"><span data-stu-id="07f65-259">A method that returns a sequence of tuples expresses that design well:</span></span>

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> <span data-ttu-id="07f65-260">在 C# 7.1 中，元組投影可讓您使用元素建立具名元組，方式與匿名型別中的屬性命名相似。</span><span class="sxs-lookup"><span data-stu-id="07f65-260">In C# 7.1, tuple projections enable you to create named tuples using elements, in a manner similar to the property naming in anonymous types.</span></span> <span data-ttu-id="07f65-261">在上述的程式碼中，查詢投影的 `select` 陳述式會建立具有元素 `ID` 與 `Title` 的元組。</span><span class="sxs-lookup"><span data-stu-id="07f65-261">In the above code, the `select` statement in the query projection creates a tuple that has elements `ID` and `Title`.</span></span>

<span data-ttu-id="07f65-262">具名 Tuple 可以是簽章的一部分。</span><span class="sxs-lookup"><span data-stu-id="07f65-262">The named tuple can be part of the signature.</span></span> <span data-ttu-id="07f65-263">它可讓編譯器和 IDE 工具提供您正確使用結果的靜態檢查。</span><span class="sxs-lookup"><span data-stu-id="07f65-263">It lets the compiler and IDE tools provide static checking that you are using the result correctly.</span></span> <span data-ttu-id="07f65-264">具名 Tuple 也帶有靜態類型資訊，因此不需要使用昂貴的執行階段功能，例如使用結果的反射或動態繫結。</span><span class="sxs-lookup"><span data-stu-id="07f65-264">The named tuple also carries the static type information so there is no need to use expensive run time features like reflection or dynamic binding to work with the results.</span></span>

## <a name="deconstruction"></a><span data-ttu-id="07f65-265">解構</span><span class="sxs-lookup"><span data-stu-id="07f65-265">Deconstruction</span></span>

<span data-ttu-id="07f65-266">您可以「解構」  方法所傳回的 Tuple，來解除封裝 Tuple 中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="07f65-266">You can unpackage all the items in a tuple by *deconstructing* the tuple returned by a method.</span></span> <span data-ttu-id="07f65-267">有三種不同的方法可以解構 Tuple。</span><span class="sxs-lookup"><span data-stu-id="07f65-267">There are three different approaches to deconstructing tuples.</span></span>  <span data-ttu-id="07f65-268">首先，您可以在括弧內明確宣告每個欄位的類型，以建立元組中每個元素的離散變數：</span><span class="sxs-lookup"><span data-stu-id="07f65-268">First, you can explicitly declare the type of each field inside parentheses to create discrete variables for each of the elements in the tuple:</span></span>

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

<span data-ttu-id="07f65-269">您可以在括弧外部使用 `var` 關鍵字，以宣告 Tuple 中每個欄位的隱含類型變數︰</span><span class="sxs-lookup"><span data-stu-id="07f65-269">You can also declare implicitly typed variables for each field in a tuple by using the `var` keyword outside the parentheses:</span></span>

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

<span data-ttu-id="07f65-270">它也可以搭配使用 `var` 關鍵字與括弧內的任何或所有變數宣告。</span><span class="sxs-lookup"><span data-stu-id="07f65-270">It is also legal to use the `var` keyword with any, or all of the variable declarations inside the parentheses.</span></span> 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

<span data-ttu-id="07f65-271">您無法在括弧外部使用特定型別，即使 Tuple 中的每個欄位都有相同的型別也是一樣。</span><span class="sxs-lookup"><span data-stu-id="07f65-271">You cannot use a specific type outside the parentheses, even if every field in the tuple has the same type.</span></span>

<span data-ttu-id="07f65-272">您可以解構 Tuple 以及現有宣告：</span><span class="sxs-lookup"><span data-stu-id="07f65-272">You can deconstruct tuples with existing declarations as well:</span></span>

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> <span data-ttu-id="07f65-273">您不能混用現有宣告與括弧內的宣告。</span><span class="sxs-lookup"><span data-stu-id="07f65-273">You cannot mix existing declarations with declarations inside the parentheses.</span></span> <span data-ttu-id="07f65-274">例如，不允許使用下列項目：`(var x, y) = MyMethod();`。</span><span class="sxs-lookup"><span data-stu-id="07f65-274">For instance, the following is not allowed: `(var x, y) = MyMethod();`.</span></span> <span data-ttu-id="07f65-275">這會產生錯誤 CS8184，因為 *x* 是在括弧內宣告，而 *y* 先前已在其他位置宣告。</span><span class="sxs-lookup"><span data-stu-id="07f65-275">This produces error CS8184 because *x* is declared inside the parentheses and *y* is previously declared elsewhere.</span></span>

### <a name="deconstructing-user-defined-types"></a><span data-ttu-id="07f65-276">解構使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="07f65-276">Deconstructing user-defined types</span></span>

<span data-ttu-id="07f65-277">任何 Tuple 類型都可以如上進行解構。</span><span class="sxs-lookup"><span data-stu-id="07f65-277">Any tuple type can be deconstructed as shown above.</span></span> <span data-ttu-id="07f65-278">也很容易在任何使用者定義型別 (類別、結構，甚至是介面) 上啟用解構。</span><span class="sxs-lookup"><span data-stu-id="07f65-278">It's also easy to enable deconstruction on any user-defined type (classes, structs, or even interfaces).</span></span>

<span data-ttu-id="07f65-279">類型作者可以定義一或多個 `Deconstruct` 方法，以將值指派給任意數目的 `out` 變數，而變數代表構成類型的資料項目。</span><span class="sxs-lookup"><span data-stu-id="07f65-279">The type author can define one or more `Deconstruct` methods that assign values to any number of `out` variables representing the data elements that make up the type.</span></span> <span data-ttu-id="07f65-280">例如，下列 `Person` 類型會定義 `Deconstruct` 方法，以將人員物件解構為代表名字和姓氏的元素：</span><span class="sxs-lookup"><span data-stu-id="07f65-280">For example, the following `Person` type defines a `Deconstruct` method that deconstructs a person object into the elements representing the first name and last name:</span></span>

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

<span data-ttu-id="07f65-281">解構方法會啟用從 `Person` 到兩個字串的指派，而這兩個字串代表 `FirstName` 和 `LastName` 屬性：</span><span class="sxs-lookup"><span data-stu-id="07f65-281">The deconstruct method enables assignment from a `Person` to two strings, representing the `FirstName` and `LastName` properties:</span></span>

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

<span data-ttu-id="07f65-282">您甚至可以針對不是由您撰寫的類型啟用解構。</span><span class="sxs-lookup"><span data-stu-id="07f65-282">You can enable deconstruction even for types you did not author.</span></span>
<span data-ttu-id="07f65-283">`Deconstruct` 方法可以是解除封裝物件的可存取資料成員的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="07f65-283">The `Deconstruct` method can be an extension method that unpackages the accessible data members of an object.</span></span> <span data-ttu-id="07f65-284">下列範例示範衍生自 `Person` 型別的 `Student` 型別，以及將 `Student` 解構為三個變數的擴充方法，而這三個變數代表 `FirstName`、`LastName` 和 `GPA`：</span><span class="sxs-lookup"><span data-stu-id="07f65-284">The example below shows a `Student` type, derived from the `Person` type, and an extension method that deconstructs a `Student` into three variables, representing the `FirstName`, the `LastName`, and the `GPA`:</span></span>

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

<span data-ttu-id="07f65-285">`Student` 物件現在有兩個可存取的 `Deconstruct` 方法︰針對 `Student` 類型所宣告的擴充方法，以及 `Person` 類型的成員。</span><span class="sxs-lookup"><span data-stu-id="07f65-285">A `Student` object now has two accessible `Deconstruct` methods: the extension method declared for `Student` types, and the member of the `Person` type.</span></span> <span data-ttu-id="07f65-286">兩者都在範圍內，並可將 `Student` 解構為兩個或三個變數。</span><span class="sxs-lookup"><span data-stu-id="07f65-286">Both are in scope, and that enables a `Student` to be deconstructed into either two variables or three.</span></span>
<span data-ttu-id="07f65-287">如果您將一位學生指派給三個變數，則都會傳回名字、姓氏和 GPA。</span><span class="sxs-lookup"><span data-stu-id="07f65-287">If you assign a student to three variables, the first name, last name, and GPA are all returned.</span></span> <span data-ttu-id="07f65-288">如果您將一位學生指派給兩個變數，則只會傳回名字和姓氏。</span><span class="sxs-lookup"><span data-stu-id="07f65-288">If you assign a student to two variables, only the first name and the last name are returned.</span></span>

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

<span data-ttu-id="07f65-289">定義類別或類別階層中的多個 `Deconstruct` 方法時必須特別小心。</span><span class="sxs-lookup"><span data-stu-id="07f65-289">You should be careful defining multiple `Deconstruct` methods in a class or a class hierarchy.</span></span> <span data-ttu-id="07f65-290">`out` 參數數目相同的多個 `Deconstruct` 方法可能會快速地造成模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="07f65-290">Multiple `Deconstruct` methods that have the same number of `out` parameters can quickly cause ambiguities.</span></span> <span data-ttu-id="07f65-291">呼叫端可能無法輕鬆地呼叫所需的 `Deconstruct` 方法。</span><span class="sxs-lookup"><span data-stu-id="07f65-291">Callers may not be able to easily call the desired `Deconstruct` method.</span></span>

<span data-ttu-id="07f65-292">在此範例中，模稜兩可呼叫的機率最小，因為 `Person` 的 `Deconstruct` 方法有兩個輸出參數，而 `Student` 的 `Deconstruct` 方法則有三個。</span><span class="sxs-lookup"><span data-stu-id="07f65-292">In this example, there is minimal chance for an ambiguous call because the `Deconstruct` method for `Person` has two output parameters, and the `Deconstruct` method for `Student` has three.</span></span>

<span data-ttu-id="07f65-293">解構運算子不會參與相等測試。</span><span class="sxs-lookup"><span data-stu-id="07f65-293">Deconstruction operators do not participate in testing equality.</span></span> <span data-ttu-id="07f65-294">下列範例會產生編譯器錯誤 CS0019：</span><span class="sxs-lookup"><span data-stu-id="07f65-294">The following example generates compiler error CS0019:</span></span>

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

<span data-ttu-id="07f65-295">`Deconstruct` 方法可以將 `Person` 物件 `p` 轉換為包含兩個字串的 Tuple，但它並不適用於相等測試的內容中。</span><span class="sxs-lookup"><span data-stu-id="07f65-295">The `Deconstruct` method could convert the `Person` object `p` to a tuple containing two strings, but it is not applicable in the context of equality tests.</span></span>

## <a name="conclusion"></a><span data-ttu-id="07f65-296">結論</span><span class="sxs-lookup"><span data-stu-id="07f65-296">Conclusion</span></span> 

<span data-ttu-id="07f65-297">具名元組的新語言和程式庫支援可讓您更輕鬆地處理使用可儲存多個元素的資料結構但未定義行為的設計，就像類別與結構一樣。</span><span class="sxs-lookup"><span data-stu-id="07f65-297">The new language and library support for named tuples makes it much easier to work with designs that use data structures that store multiple elements but do not define behavior, as classes and structs do.</span></span> <span data-ttu-id="07f65-298">將 Tuple 用於這些類型十分簡單且簡潔。</span><span class="sxs-lookup"><span data-stu-id="07f65-298">It's easy and concise to use tuples for those types.</span></span> <span data-ttu-id="07f65-299">您會獲得靜態類型檢查的所有優點，而不需要使用更詳細的 `class` 或 `struct` 語法來撰寫類型。</span><span class="sxs-lookup"><span data-stu-id="07f65-299">You get all the benefits of static type checking, without needing to author types using the more verbose `class` or `struct` syntax.</span></span> <span data-ttu-id="07f65-300">即便如此，它們還是最適用於為 `private` 或 `internal` 的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="07f65-300">Even so, they are most useful for utility methods that are `private`, or `internal`.</span></span> <span data-ttu-id="07f65-301">公用方法傳回具有多個元素的值時，請建立使用者定義型別，即 `class` 或 `struct` 型別。</span><span class="sxs-lookup"><span data-stu-id="07f65-301">Create user-defined types, either `class` or `struct` types when your public methods return a value that has multiple elements.</span></span>
