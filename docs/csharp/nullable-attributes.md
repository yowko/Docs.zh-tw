---
title: 使用定義 null 值預期的屬性來升級可為 null 的參考型別的 Api
description: 瞭解如何使用描述性屬性 AllowNull、DisallowNull、MaybeNull、NotNull 等，以完整描述 Api 的 null 狀態。
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 7142fe0566b1cc7373f5dc777c36443041114c4f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204626"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a><span data-ttu-id="5a7ad-103">更新程式庫以使用可為 null 的參考型別，並將可為 null 的規則與呼叫</span><span class="sxs-lookup"><span data-stu-id="5a7ad-103">Update libraries to use nullable reference types and communicate nullable rules to callers</span></span>

<span data-ttu-id="5a7ad-104">加入[可為 null 的參考型別](nullable-references.md)表示您可以宣告每個變數是否允許或預期 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-104">The addition of [nullable reference types](nullable-references.md) means you can declare whether or not a `null` value is allowed or expected for every variable.</span></span> <span data-ttu-id="5a7ad-105">此外，您可以套用一些屬性： `AllowNull`、`DisallowNull`、`MaybeNull`、`NotNull`、`NotNullWhen`、`MaybeNullWhen`和 `NotNullWhenNotNull`，以完整描述引數和傳回值的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-105">In addition, you can apply a number of attributes: `AllowNull`, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, and `NotNullWhenNotNull` to completely describe the null states of argument and return values.</span></span> <span data-ttu-id="5a7ad-106">這會在您撰寫程式碼時提供絕佳的體驗。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-106">That provides a great experience as you write code.</span></span> <span data-ttu-id="5a7ad-107">如果不可為 null 的變數可能設定為 `null`，您會收到警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-107">You get warnings if a non-nullable variable might be set to `null`.</span></span> <span data-ttu-id="5a7ad-108">如果可為 null 的變數不是 null，則您會收到警告，然後再對其進行取值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-108">You get warnings if a nullable variable isn't null-checked before you dereference it.</span></span> <span data-ttu-id="5a7ad-109">更新您的程式庫可能需要一些時間，但回報值得一提。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-109">Updating your libraries can take time, but the payoffs are worth it.</span></span> <span data-ttu-id="5a7ad-110">您提供給編譯器的詳細資訊，是允許或禁止 `null` 值*時*，API 的使用者將會得到更好的警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-110">The more information you provide to the compiler about *when* a `null` value is allowed or prohibited, the better warnings users of your API will get.</span></span> <span data-ttu-id="5a7ad-111">讓我們從熟悉的範例開始。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-111">Let's start with a familiar example.</span></span> <span data-ttu-id="5a7ad-112">假設您的程式庫具有下列 API 來抓取資源字串：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="5a7ad-113">上述範例遵循 .NET 中熟悉的 `Try*` 模式。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="5a7ad-114">此 API 有兩個參考引數： `key` 和 `message` 參數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="5a7ad-115">此 API 具有下列與這些引數的 null 相關的規則：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="5a7ad-116">呼叫端不應該傳遞 `null` 做為 `key`的引數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="5a7ad-117">呼叫端可以傳遞一個變數，其值 `null` 為 `message`的引數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="5a7ad-118">如果 `TryGetMessage` 方法傳回 `true`，`message` 的值就不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="5a7ad-119">如果傳回值為 `false,` `message` 的值（和其 null 狀態）為 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="5a7ad-120">`key` 的規則可由變數類型完全表示： `key` 應該是不可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-120">The rule for `key` can be completely expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="5a7ad-121">`message` 參數較複雜。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="5a7ad-122">它允許 `null` 做為引數，但可保證在成功時，`out` 引數不是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="5a7ad-123">在這些情況下，您需要更豐富的詞彙來描述預期。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="5a7ad-124">更新您的程式庫以取得可為 null 的參考，在某些變數和類型名稱上需要超過隨處揮灑 threadpool.queueuserworkitem `?`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-124">Updating your library for nullable references requires more than sprinkling `?` on some of the variables and type names.</span></span> <span data-ttu-id="5a7ad-125">上述範例顯示您需要檢查您的 Api，並考慮每個輸入引數的預期。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-125">The preceding example shows that you need to examine your APIs and consider your expectations for each input argument.</span></span> <span data-ttu-id="5a7ad-126">請考慮傳回值的保證，以及方法傳回時的任何 `out` 或 `ref` 引數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-126">Consider the guarantees for the return value, and any `out` or `ref` arguments upon the method's return.</span></span> <span data-ttu-id="5a7ad-127">然後將這些規則傳達給編譯器，而編譯器會在呼叫者不遵守這些規則時提供警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-127">Then communicate those rules to the compiler, and the compiler will provide warnings when callers don't abide by those rules.</span></span>

<span data-ttu-id="5a7ad-128">此工作需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-128">This work takes time.</span></span> <span data-ttu-id="5a7ad-129">讓我們從策略開始，將您的程式庫或應用程式設為可為 null 感知，同時平衡其他需求和交付專案。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-129">Let's start with strategies to make your library or application nullable-aware, while balancing other requirements and deliverables.</span></span> <span data-ttu-id="5a7ad-130">您將瞭解如何平衡進行中的開發，並啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-130">You'll see how to balance ongoing development enabling nullable reference types.</span></span> <span data-ttu-id="5a7ad-131">您將會學到泛型型別定義的挑戰。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-131">You'll learn challenges for generic type definitions.</span></span> <span data-ttu-id="5a7ad-132">您將瞭解如何套用屬性，以描述個別 Api 的前置和後置條件。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-132">You'll learn to apply attributes to describe pre- and post-conditions on individual APIs.</span></span>

## <a name="choose-a-nullable-strategy"></a><span data-ttu-id="5a7ad-133">選擇可為 null 的策略</span><span class="sxs-lookup"><span data-stu-id="5a7ad-133">Choose a nullable strategy</span></span>

<span data-ttu-id="5a7ad-134">第一個選擇是可為 null 的參考型別是否預設為開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-134">The first choice is whether nullable reference types should be on or off by default.</span></span> <span data-ttu-id="5a7ad-135">您有兩種策略：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-135">You have two strategies:</span></span>

- <span data-ttu-id="5a7ad-136">為整個專案啟用可為 null 的參考型別，並在未就緒的程式碼中停用它。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-136">Enable nullable reference types for the entire project, and disable it in code that's not ready.</span></span>
- <span data-ttu-id="5a7ad-137">僅針對已針對可為 null 的參考型別標注的程式碼，啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-137">Only enable nullable reference types for code that's been annotated for nullable reference types.</span></span>

<span data-ttu-id="5a7ad-138">當您將其他功能新增至程式庫時，第一個策略的效果最佳，是針對可為 null 的參考型別進行更新。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-138">The first strategy works best when you're adding other features to the library as you update it for nullable reference types.</span></span> <span data-ttu-id="5a7ad-139">所有新的開發都是可為 null 的感知。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-139">All new development is nullable aware.</span></span> <span data-ttu-id="5a7ad-140">當您更新現有程式碼時，您可以在這些類別中啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-140">As you update existing code, you enable nullable reference types in those classes.</span></span>

<span data-ttu-id="5a7ad-141">遵循第一個策略，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-141">Following this first strategy, you do the following:</span></span>

1. <span data-ttu-id="5a7ad-142">藉由將 `<Nullable>enable</Nullable>` 專案新增至您的 *.csproj*檔案，為整個專案啟用可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-142">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span> 
1. <span data-ttu-id="5a7ad-143">將 `#nullable disable` pragma 新增至專案中的每個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-143">Add the `#nullable disable` pragma to every source file in your project.</span></span> 
1. <span data-ttu-id="5a7ad-144">當您處理每個檔案時，請移除 pragma 並解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-144">As you work on each file, remove the pragma and address any warnings.</span></span>

<span data-ttu-id="5a7ad-145">第一個策略有更多的最新工作，可以將 pragma 新增至每個檔案。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-145">This first strategy has more up-front work to add the pragma to every file.</span></span> <span data-ttu-id="5a7ad-146">優點是每個新增至專案的新程式碼檔案都可為 null 啟用。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-146">The advantage is that every new code file added to the project will be nullable enabled.</span></span> <span data-ttu-id="5a7ad-147">任何新工作都可為 null 感知;僅必須更新現有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-147">Any new work will be nullable aware; only existing code must be updated.</span></span>

<span data-ttu-id="5a7ad-148">如果程式庫通常穩定，第二個策略的效果更好，而開發的主要重點是採用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-148">The second strategy works better if the library is generally stable, and the main focus of the development is to adopt nullable reference types.</span></span> <span data-ttu-id="5a7ad-149">當您標注 Api 時，您會開啟可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-149">You turn on nullable reference types as you annotate APIs.</span></span> <span data-ttu-id="5a7ad-150">當您完成時，您可以為整個專案啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-150">When you've finished, you enable nullable reference types for the entire project.</span></span>

<span data-ttu-id="5a7ad-151">遵循第二個策略，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-151">Following this second strategy you do the following:</span></span>

1. <span data-ttu-id="5a7ad-152">將 `#nullable enable` pragma 新增至您要讓可為 null 感知的檔案。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-152">Add the `#nullable enable` pragma to the file you want to make nullable aware.</span></span>
1. <span data-ttu-id="5a7ad-153">解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-153">Address any warnings.</span></span>
1. <span data-ttu-id="5a7ad-154">繼續執行前兩個步驟，直到您將整個程式庫設為可為 null 為止。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-154">Continue these first two steps until you've made the entire library nullable aware.</span></span>
1. <span data-ttu-id="5a7ad-155">藉由將 `<Nullable>enable</Nullable>` 專案新增至您的 *.csproj*檔案，為整個專案啟用可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-155">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span> 
1. <span data-ttu-id="5a7ad-156">移除 `#nullable enable` pragma，因為不再需要它們。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-156">Remove the `#nullable enable` pragmas, as they're no longer needed.</span></span>

<span data-ttu-id="5a7ad-157">第二個策略的處理時間較少。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-157">This second strategy has less work up-front.</span></span> <span data-ttu-id="5a7ad-158">缺點是，當您建立新檔案時，第一項工作是新增 pragma 並讓它成為可為 null 的感知。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-158">The tradeoff is that the first task when you create a new file is to add the pragma and make it nullable aware.</span></span> <span data-ttu-id="5a7ad-159">如果您小組中的任何開發人員忘記，新的程式碼現在已在工作待處理專案中，使所有程式碼可為 null 感知。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-159">If any developers on your team forget, that new code is now in the backlog of work to make all code nullable aware.</span></span>

<span data-ttu-id="5a7ad-160">您挑選的其中一個策略，取決於您的專案中有多少使用中的開發。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-160">Which of these strategies you pick depends on how much active development is taking place in your project.</span></span> <span data-ttu-id="5a7ad-161">您的專案越成熟且穩定，第二個策略就越好。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-161">The more mature and stable your project, the better the second strategy.</span></span> <span data-ttu-id="5a7ad-162">開發的功能越多，第一個策略就越好。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-162">The more features being developed, the better the first strategy.</span></span>

## <a name="should-nullable-warnings-introduce-breaking-changes"></a><span data-ttu-id="5a7ad-163">可為 null 的警告是否會引進重大變更？</span><span class="sxs-lookup"><span data-stu-id="5a7ad-163">Should nullable warnings introduce breaking changes?</span></span>

<span data-ttu-id="5a7ad-164">啟用可為 null 的參考型別之前，變數會被視為*可為 null 的遺忘式*。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-164">Before you enable nullable reference types, variables are considered *nullable oblivious*.</span></span> <span data-ttu-id="5a7ad-165">啟用可為 null 的參考型別後，所有這些變數都*不可為 null*。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-165">Once you enable nullable reference types, all those variables are *non-nullable*.</span></span> <span data-ttu-id="5a7ad-166">如果未將這些變數初始化為非 null 值，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-166">The compiler will issue warnings if those variables aren't initialized to non-null values.</span></span>

<span data-ttu-id="5a7ad-167">另一個可能的警告來源是值未初始化時的傳回值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-167">Another likely source of warnings is return values when the value hasn't been initialized.</span></span>

<span data-ttu-id="5a7ad-168">解決編譯器警告的第一個步驟，是在參數和傳回型別上使用 `?` 注釋，以指出引數或傳回值是否可以是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-168">The first step in addressing the compiler warnings is to use `?` annotations on parameter and return types to indicate when arguments or return values may be null.</span></span> <span data-ttu-id="5a7ad-169">當參考變數不得為 null 時，原始宣告是正確的。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-169">When reference variables must not be null, the original declaration is correct.</span></span> <span data-ttu-id="5a7ad-170">當您這麼做時，您的目標不是要修正警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-170">As you do this, your goal isn't just to fix warnings.</span></span> <span data-ttu-id="5a7ad-171">較重要的目標是讓編譯器瞭解潛在 null 值的意圖。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-171">The more important goal is to make the compiler understand your intent for potential null values.</span></span> <span data-ttu-id="5a7ad-172">當您檢查這些警告時，您會到達程式庫的下一個主要決策。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-172">As you examine the warnings, you reach your next major decision for your library.</span></span> <span data-ttu-id="5a7ad-173">您是否想要考慮修改 API 簽章，以更清楚地傳達您的設計意圖？</span><span class="sxs-lookup"><span data-stu-id="5a7ad-173">Do you want to consider modifying API signatures to more clearly communicate your design intent?</span></span> <span data-ttu-id="5a7ad-174">更好的 API 簽章適用于先前檢查的 `TryGetMessage` 方法，可能是：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-174">A better API signature for the `TryGetMessage` method examined earlier could be:</span></span>

```csharp
string? TryGetMessage(string key);
```

<span data-ttu-id="5a7ad-175">傳回值表示成功或失敗，如果找到值，則會攜帶值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-175">The return value indicates success or failure, and carries the value if the value was found.</span></span> <span data-ttu-id="5a7ad-176">在許多情況下，變更 API 簽章可以改善它們傳達 null 值的方式。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-176">In many cases, changing API signatures can improve how they communicate null values.</span></span>

<span data-ttu-id="5a7ad-177">不過，對於公用程式庫或具有大型使用者群的程式庫，您可能不會想要引入任何 API 簽章變更。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-177">However, for public libraries, or libraries with large user bases, you may prefer not introducing any API signature changes.</span></span> <span data-ttu-id="5a7ad-178">針對這些案例和其他常見的模式，您可以套用屬性，以更清楚地定義何時可以 `null`引數或傳回值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-178">For those cases, and other common patterns, you can apply attributes to more clearly define when an argument or return value may be `null`.</span></span> <span data-ttu-id="5a7ad-179">不論您是否考慮變更 API 的介面，您可能會發現單獨的類型注釋不足以描述引數或傳回值的 `null` 值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-179">Whether or not you consider changing the surface of your API, you'll likely find that type annotations alone aren't sufficient for describing `null` values for arguments or return values.</span></span> <span data-ttu-id="5a7ad-180">在這些情況下，您可以套用屬性，以更清楚地描述 API。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-180">In those instances, you can apply attributes to more clearly describe an API.</span></span> 

## <a name="attributes-extend-type-annotations"></a><span data-ttu-id="5a7ad-181">屬性擴充類型注釋</span><span class="sxs-lookup"><span data-stu-id="5a7ad-181">Attributes extend type annotations</span></span>

<span data-ttu-id="5a7ad-182">已經加入數個屬性，以表達變數的 null 狀態的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-182">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="5a7ad-183">您在8之前C#撰寫的所有程式碼，都是 null 的參考型別*遺忘式*。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-183">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="5a7ad-184">這表示任何參考型別變數都可以是 null，但不需要 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-184">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="5a7ad-185">一旦您的程式碼*可為 null 感知*，這些規則就會變更。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-185">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="5a7ad-186">參考型別絕對不應為 `null` 值，而且在取值前，必須先針對 `null` 檢查可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-186">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="5a7ad-187">您的 Api 規則可能會更複雜，如同您在 `TryGetValue` API 案例中所見。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-187">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="5a7ad-188">當變數可以或無法 `null`時，許多 Api 都有更複雜的規則。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-188">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="5a7ad-189">在這些情況下，您將使用下列其中一個屬性來表示這些規則：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-189">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="5a7ad-190">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-190">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="5a7ad-191">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數絕對不應為 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-191">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="5a7ad-192">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可以是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-192">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="5a7ad-193">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-193">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="5a7ad-194">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的 `bool` 值時，不可為 null 的輸入引數可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-194">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5a7ad-195">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的 `bool` 值時，可為 null 的輸入引數將不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-195">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5a7ad-196">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定之參數的引數不是 null，則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-196">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>

<span data-ttu-id="5a7ad-197">上述描述是每個屬性的快速參考。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-197">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="5a7ad-198">下一節將詳細說明行為和意義。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-198">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="5a7ad-199">新增這些屬性可讓編譯器詳細說明您 API 的規則。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-199">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="5a7ad-200">在可為 null 的已啟用內容中編譯呼叫程式碼時，編譯器會在呼叫端違反這些規則時發出警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-200">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="5a7ad-201">這些屬性不會在您的執行上啟用額外的檢查。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-201">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="5a7ad-202">指定前置條件： `AllowNull` 和 `DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="5a7ad-202">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="5a7ad-203">請考慮永遠不會傳回 `null` 的讀取/寫入屬性，因為它有合理的預設值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-203">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="5a7ad-204">設定為預設值時，呼叫端會將 `null` 傳遞給 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-204">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="5a7ad-205">例如，假設有一個訊息系統會要求聊天室中的螢幕名稱。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-205">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="5a7ad-206">如果未提供，系統會產生隨機名稱：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-206">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

<span data-ttu-id="5a7ad-207">當您在可為 null 的遺忘式內容中編譯上述程式碼時，一切都沒問題。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-207">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="5a7ad-208">啟用可為 null 的參考型別後，`ScreenName` 屬性會變成不可為 null 的參考。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-208">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="5a7ad-209">這對於 `get` 存取子而言是正確的：它絕對不會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-209">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="5a7ad-210">呼叫端不需要檢查傳回的屬性以進行 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-210">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="5a7ad-211">但現在將屬性設定為 `null` 會產生警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-211">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="5a7ad-212">為了繼續支援這種類型的程式碼，您可以將 <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> 屬性加入至屬性，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-212">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span> 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

<span data-ttu-id="5a7ad-213">您可能需要加入 <xref:System.Diagnostics.CodeAnalysis> 的 `using` 指示詞，以使用此文章和本文中討論的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-213">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="5a7ad-214">屬性會套用至屬性，而不是 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-214">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="5a7ad-215">`AllowNull` 屬性會指定*前置條件*，而且只適用于輸入。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-215">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="5a7ad-216">`get` 存取子具有傳回值，但沒有輸入引數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-216">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="5a7ad-217">因此，`AllowNull` 屬性僅適用于 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-217">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="5a7ad-218">上述範例示範在引數上加入 `AllowNull` 屬性時要尋找的事項：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-218">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="5a7ad-219">該變數的一般合約是不應該 `null`，因此您需要不可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-219">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="5a7ad-220">在某些情況下，會 `null`輸入變數，雖然它們不是最常見的使用方式。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-220">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="5a7ad-221">通常您需要屬性的這個屬性，或 `in`、`out`和 `ref` 引數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-221">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="5a7ad-222">當變數通常不是 null 時，`AllowNull` 屬性是最佳選擇，但您必須允許 `null` 做為前置條件。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-222">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="5a7ad-223">相較之下，使用 `DisallowNull`的案例：您可以使用這個屬性來指定可為 null 類型的輸入變數不應 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-223">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable type shouldn't be `null`.</span></span> <span data-ttu-id="5a7ad-224">假設有一個屬性，其中 `null` 是預設值，但是用戶端只能將它設定為非 null 值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-224">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="5a7ad-225">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-225">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="5a7ad-226">上述程式碼是表達設計的最佳方式，可 `null``ReviewComment`，但不能設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-226">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="5a7ad-227">一旦這段程式碼可為 null，您就可以更清楚地表達此概念給使用 <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>的呼叫端：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-227">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="5a7ad-228">在可為 null 的內容中，`ReviewComment` `get` 存取子可能會傳回 `null`的預設值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-228">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="5a7ad-229">編譯器會警告您必須在存取之前先檢查它。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-229">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="5a7ad-230">此外，它會警告呼叫端，即使它可以 `null`，呼叫端也不應該明確地將它設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-230">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="5a7ad-231">`DisallowNull` 屬性也會指定*前置條件*，而不會影響 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-231">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="5a7ad-232">當您觀察下列有關的特性時，應該選擇使用 `DisallowNull` 屬性：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-232">You should choose to use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="5a7ad-233">變數可以在核心案例中 `null`，通常是在第一次具現化時。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-233">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="5a7ad-234">變數不應明確設定為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-234">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="5a7ad-235">這些情況在原本是*null 遺忘式*的程式碼中很常見。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-235">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="5a7ad-236">這可能是在兩個不同的初始化作業中設定物件屬性。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-236">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="5a7ad-237">這可能是某些屬性只有在一些非同步工作完成後才會設定。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-237">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="5a7ad-238">`AllowNull` 和 `DisallowNull` 屬性可讓您指定變數上的前置條件可能不符合那些變數上的可為 null 注釋。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-238">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="5a7ad-239">這些會提供 API 特性的更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-239">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="5a7ad-240">此額外資訊可協助呼叫者正確地使用您的 API。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-240">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="5a7ad-241">請記住，您可以使用下列屬性來指定前置條件：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-241">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="5a7ad-242">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-242">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="5a7ad-243">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數絕對不應為 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-243">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="5a7ad-244">指定後置條件： `MaybeNull` 和 `NotNull`</span><span class="sxs-lookup"><span data-stu-id="5a7ad-244">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="5a7ad-245">假設您有一個具有下列簽章的方法：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-245">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="5a7ad-246">當找不到所尋找的名稱時，您可能會撰寫如下所示的方法，以傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-246">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="5a7ad-247">`null` 清楚地指出找不到記錄。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-247">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="5a7ad-248">在此範例中，您可能會將傳回型別從 `Customer` 變更為 `Customer?`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-248">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="5a7ad-249">將傳回值宣告為可為 null 的參考型別，可以清楚地指定這個 API 的意圖。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-249">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span> 

<span data-ttu-id="5a7ad-250">基於[泛型定義和 null](#generic-definitions-and-nullability)屬性所涵蓋的原因，這項技術無法與泛型方法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-250">For reasons covered under [Generic definitions and nullability](#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="5a7ad-251">您的泛型方法可能會遵循類似的模式：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-251">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="5a7ad-252">您無法指定傳回值為 `T?`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-252">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="5a7ad-253">當找不到搜尋的專案時，方法會傳回 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-253">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="5a7ad-254">由於您無法宣告 `T?` 傳回型別，因此，您可以將 `MaybeNull` 注釋新增至方法傳回：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-254">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="5a7ad-255">上述程式碼會通知呼叫者，合約隱含了不可為 null 的型別，但傳回值實際上*可能*是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-255">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="5a7ad-256">當您的 API 應該是不可為 null 的型別（通常是泛型型別參數）時，請使用 `MaybeNull` 屬性，但可能會傳回 `null` 的實例。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-256">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="5a7ad-257">您也可以指定傳回值或 `out` 或 `ref` 引數不是 null，即使該類型是可為 null 的類型也一樣。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-257">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable type.</span></span> <span data-ttu-id="5a7ad-258">假設有一個方法可確保陣列夠大，足以容納多個元素。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-258">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="5a7ad-259">如果輸入引數沒有容量，常式會配置新的陣列，並將所有現有的元素複製到其中。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-259">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="5a7ad-260">如果 `null`輸入引數，則常式會配置新的儲存體。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-260">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="5a7ad-261">如果有足夠的容量，常式不會執行任何動作：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-261">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="5a7ad-262">您可以呼叫此常式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-262">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="5a7ad-263">啟用 null 參考型別之後，您想要確保先前的程式碼會編譯而不會出現警告。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-263">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="5a7ad-264">當此方法傳回時，會保證 `storage` 引數不是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-264">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="5a7ad-265">不過，使用 null 參考呼叫 `EnsureCapacity` 是可接受的。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-265">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="5a7ad-266">您可以讓 `storage` 可為 null 的參考型別，並將 `NotNull` 後置條件新增至參數宣告：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-266">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

<span data-ttu-id="5a7ad-267">上述程式碼非常清楚地表示現有的合約：呼叫端可以傳遞具有 `null` 值的變數，但傳回值保證永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-267">The preceding code expresses the existing contract very clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="5a7ad-268">`NotNull` 屬性最適用于 `ref` 和 `out` 引數，其中 `null` 可能會當做引數傳遞，但當方法傳回時，該引數保證不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-268">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="5a7ad-269">您可以使用下列屬性來指定無條件的後置條件：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-269">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="5a7ad-270">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可以是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-270">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="5a7ad-271">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-271">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="5a7ad-272">指定條件式後置條件： `NotNullWhen`、`MaybeNullWhen`和 `NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="5a7ad-272">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="5a7ad-273">您很可能已熟悉 <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>的 `string` 方法。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-273">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="5a7ad-274">當引數為 null 或空字串時，這個方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-274">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="5a7ad-275">這是一種 null 檢查形式：如果方法傳回 `false`，則呼叫端不需要 null 檢查引數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-275">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="5a7ad-276">若要讓方法類似于可為 null 的感知，您可以將引數設定為可為 null 的型別，並加入 `NotNullWhen` 屬性：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-276">To make a method like this nullable aware, you'd set the argument to a nullable type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

<span data-ttu-id="5a7ad-277">這會通知編譯器，傳回值 `false` 的任何程式碼都不需要為 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-277">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="5a7ad-278">新增屬性會通知編譯器的靜態分析 `IsNullOrEmpty` 執行必要的 null 檢查：當它傳回 `false`時，不會 `null`輸入引數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-278">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="5a7ad-279">針對 .NET Core 3.0，<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> 方法將標注為如上所示。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-279">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="5a7ad-280">您的程式碼基底中可能會有類似的方法，可檢查物件的狀態是否為 null 值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-280">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="5a7ad-281">編譯器不會辨識自訂的 null 檢查方法，您必須自行新增批註。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-281">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="5a7ad-282">當您新增屬性時，編譯器的靜態分析會知道已檢查過測試的變數何時已進行 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-282">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="5a7ad-283">這些屬性的另一個用法是 `Try*` 模式。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-283">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="5a7ad-284">`ref` 和 `out` 變數的後置條件會透過傳回值進行通訊。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-284">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="5a7ad-285">請考慮稍早所示的這個方法：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-285">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="5a7ad-286">上述方法會遵循典型的 .NET 用法：傳回值會指出 `message` 是否設定為找到的值，或者，如果找不到任何訊息，則為預設值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-286">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="5a7ad-287">如果方法傳回 `true`，`message` 的值不能是 null;否則，方法會將 `message` 設定為 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-287">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="5a7ad-288">您可以使用 `NotNullWhen` 屬性來傳達該用法。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-288">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="5a7ad-289">當您更新可為 null 之參考型別的簽章時，請 `message` `string?` 並加入屬性：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-289">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="5a7ad-290">在上述範例中，當 `TryGetMessage` 傳回 `true`時，`message` 的值已知為 not null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-290">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="5a7ad-291">您應該以相同的方式，在程式碼基底中標注類似的方法：可以 `null`引數，而當方法傳回 `true`時，已知為 not null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-291">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="5a7ad-292">還有一個您可能也需要的最終屬性。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-292">There's one final attribute you may also need.</span></span> <span data-ttu-id="5a7ad-293">有時傳回值的 null 狀態會視一或多個輸入引數的 null 狀態而定。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-293">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="5a7ad-294">每當不 `null`特定輸入引數時，這些方法將會傳回非 null 值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-294">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="5a7ad-295">若要正確地為這些方法加上批註，您可以使用 `NotNullIfNotNull` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-295">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="5a7ad-296">請考慮下列方法：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-296">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="5a7ad-297">如果 `url` 引數不是 null，則不會 `null`輸出。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-297">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="5a7ad-298">啟用可為 null 的參考後，如果您的 API 永遠不接受 null 輸入，則該簽章會正常運作。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-298">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="5a7ad-299">不過，如果輸入可以是 null，則傳回值也可以是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-299">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="5a7ad-300">因此，您可以將簽章變更為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-300">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="5a7ad-301">這也可行，但是通常會強制呼叫者執行額外的 `null` 檢查。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-301">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="5a7ad-302">合約是只有在 `null`輸入引數 `url` 時，才會 `null` 傳回值。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-302">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="5a7ad-303">若要表達該合約，您可以標注此方法，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-303">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="5a7ad-304">傳回值和引數都已使用 `?` 批註，表示可以 `null`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-304">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="5a7ad-305">屬性會進一步說明當 `url` 引數不 `null`時，傳回值不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-305">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="5a7ad-306">您可以使用下列屬性來指定條件性後置條件：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-306">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="5a7ad-307">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的 `bool` 值時，不可為 null 的輸入引數可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-307">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5a7ad-308">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的 `bool` 值時，可為 null 的輸入引數將不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-308">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5a7ad-309">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的輸入引數不是 null，則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-309">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="generic-definitions-and-nullability"></a><span data-ttu-id="5a7ad-310">泛型定義和 null 屬性</span><span class="sxs-lookup"><span data-stu-id="5a7ad-310">Generic definitions and nullability</span></span>

<span data-ttu-id="5a7ad-311">正確地傳達泛型型別和泛型方法的 null 狀態需要特別小心。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-311">Correctly communicating the null state of generic types and generic methods requires special care.</span></span> <span data-ttu-id="5a7ad-312">這源自于可為 null 的實值型別和可為 null 的參考型別，基本上是不同的事實。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-312">This stems from the fact that a nullable value type and a nullable reference type are fundamentally different.</span></span> <span data-ttu-id="5a7ad-313">`int?` 是 `Nullable<int>`的同義字，而 `string?` 則是由編譯器新增的屬性所 `string`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-313">An `int?` is a synonym for `Nullable<int>`, whereas `string?` is `string` with an attribute added by the compiler.</span></span> <span data-ttu-id="5a7ad-314">結果是編譯器無法產生 `T?` 的正確程式碼，而不知道 `T` 是 `class` 還是 `struct`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-314">The result is that the compiler can't generate correct code for `T?` without knowing if `T` is a `class` or a `struct`.</span></span> 

<span data-ttu-id="5a7ad-315">這並不表示您無法使用可為 null 的類型（實數值型別或參考型別）做為封閉式泛型型別的類型引數。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-315">This doesn't mean you can't use a nullable type (either value type or reference type) as the type argument for a closed generic type.</span></span> <span data-ttu-id="5a7ad-316">`List<string?>` 和 `List<int?>` 都是 `List<T>`的有效具現化。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-316">Both `List<string?>` and `List<int?>` are valid instantiations of `List<T>`.</span></span> 

<span data-ttu-id="5a7ad-317">這表示您不能在泛型類別或方法宣告中使用 `T?`，而不會有條件約束。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-317">What it does mean is that you can't use `T?` in a generic class or method declaration without constraints.</span></span> <span data-ttu-id="5a7ad-318">例如，<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> 不會變更為傳回 `T?`。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-318">For example, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> won't be changed to return `T?`.</span></span> <span data-ttu-id="5a7ad-319">您可以藉由加入 `struct` 或 `class` 條件約束來克服這項限制。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-319">You can overcome this limitation by adding either the `struct` or `class` constraint.</span></span> <span data-ttu-id="5a7ad-320">透過上述任一條件約束，編譯器知道如何產生 `T` 和 `T?`的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-320">With either of those constraints, the compiler knows how to generate code for both `T` and `T?`.</span></span>

<span data-ttu-id="5a7ad-321">您可能想要將泛型型別引數所使用的類型限制為不可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-321">You may want to restrict the types used for a generic type argument to be non-nullable types.</span></span> <span data-ttu-id="5a7ad-322">若要這麼做，您可以在該型別引數上加入 `notnull` 條件約束。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-322">You can do that by adding the `notnull` constraint on that type argument.</span></span> <span data-ttu-id="5a7ad-323">套用該條件約束時，類型引數不能是可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-323">When that constraint is applied, the type argument must not be a nullable type.</span></span>

## <a name="conclusions"></a><span data-ttu-id="5a7ad-324">結論</span><span class="sxs-lookup"><span data-stu-id="5a7ad-324">Conclusions</span></span>

<span data-ttu-id="5a7ad-325">加入可為 null 的參考型別會提供初始詞彙，以描述您的 Api 對可能 `null`之變數的預期。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-325">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="5a7ad-326">其他屬性會提供更豐富的詞彙，將變數的 null 狀態原因為前置條件和後置條件。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-326">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="5a7ad-327">這些屬性會更清楚地描述您的期望，並為使用您 Api 的開發人員提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-327">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="5a7ad-328">當您更新可為 null 內容的程式庫時，請新增這些屬性以引導 Api 的使用者使用正確的用法。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-328">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="5a7ad-329">這些屬性可協助您完整描述輸入引數和傳回值的 null 狀態：</span><span class="sxs-lookup"><span data-stu-id="5a7ad-329">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="5a7ad-330">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-330">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="5a7ad-331">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數絕對不應為 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-331">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="5a7ad-332">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可以是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-332">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="5a7ad-333">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-333">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="5a7ad-334">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的 `bool` 值時，不可為 null 的輸入引數可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-334">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5a7ad-335">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的 `bool` 值時，可為 null 的輸入引數將不會是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-335">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="5a7ad-336">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的輸入引數不是 null，則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="5a7ad-336">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
