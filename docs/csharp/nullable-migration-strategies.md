---
title: 更新您的程式碼基底以使用可為 null 的參考型別
description: 選擇升級程式碼基底的最佳策略，以使用可為 null 的參考型別。
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: ab0970247c7e3f3c20d7fdb40ef035c4ba1d8b01
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099323"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a><span data-ttu-id="9158e-103">更新程式庫以使用可為 null 的參考型別，並將可為 null 的規則傳達給</span><span class="sxs-lookup"><span data-stu-id="9158e-103">Update libraries to use nullable reference types and communicate nullable rules to callers</span></span>

<span data-ttu-id="9158e-104">加入 [可為 null 的參考](nullable-references.md) 型別，表示您可以宣告 `null` 每個變數的值是允許或預期的。</span><span class="sxs-lookup"><span data-stu-id="9158e-104">The addition of [nullable reference types](nullable-references.md) means you can declare whether or not a `null` value is allowed or expected for every variable.</span></span> <span data-ttu-id="9158e-105">此外，您可以套用數個屬性： `AllowNull` 、 `DisallowNull` 、 `MaybeNull` 、、、 `NotNull` `NotNullWhen` 和， `MaybeNullWhen` `NotNullIfNotNull` 以完整描述引數和傳回值的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="9158e-105">In addition, you can apply a number of attributes: `AllowNull`, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull` to completely describe the null states of argument and return values.</span></span> <span data-ttu-id="9158e-106">這可在您撰寫程式碼時提供絕佳的體驗。</span><span class="sxs-lookup"><span data-stu-id="9158e-106">That provides a great experience as you write code.</span></span> <span data-ttu-id="9158e-107">如果不可為 null 的變數可能設定為，就會收到警告 `null` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-107">You get warnings if a non-nullable variable might be set to `null`.</span></span> <span data-ttu-id="9158e-108">如果可為 null 的變數在進行取值之前，不是以 null 檢查，您會收到警告。</span><span class="sxs-lookup"><span data-stu-id="9158e-108">You get warnings if a nullable variable isn't null-checked before you dereference it.</span></span> <span data-ttu-id="9158e-109">更新您的程式庫可能需要一些時間，但回報值得一提。</span><span class="sxs-lookup"><span data-stu-id="9158e-109">Updating your libraries can take time, but the payoffs are worth it.</span></span> <span data-ttu-id="9158e-110">您提供給編譯器的詳細資訊是在 *when* `null` 允許或禁止某個值時，您的 API 使用者將會得到更好的警告。</span><span class="sxs-lookup"><span data-stu-id="9158e-110">The more information you provide to the compiler about *when* a `null` value is allowed or prohibited, the better warnings users of your API will get.</span></span> <span data-ttu-id="9158e-111">讓我們從熟悉的範例開始。</span><span class="sxs-lookup"><span data-stu-id="9158e-111">Let's start with a familiar example.</span></span> <span data-ttu-id="9158e-112">假設您的程式庫有下列 API 可取得資源字串：</span><span class="sxs-lookup"><span data-stu-id="9158e-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="9158e-113">上述範例會遵循 `Try*` .net 中熟悉的模式。</span><span class="sxs-lookup"><span data-stu-id="9158e-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="9158e-114">此 API 有兩個參考引數： `key` 和 `message` 參數。</span><span class="sxs-lookup"><span data-stu-id="9158e-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="9158e-115">此 API 具有下列與這些引數 null f.23 相關的規則：</span><span class="sxs-lookup"><span data-stu-id="9158e-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="9158e-116">呼叫端不應該傳遞 `null` 做為的引數 `key` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="9158e-117">呼叫端可以傳遞變數，其值為 `null` 的引數 `message` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="9158e-118">如果 `TryGetMessage` 方法傳回 `true` ，的值 `message` 不是 null。</span><span class="sxs-lookup"><span data-stu-id="9158e-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="9158e-119">如果傳回值是 `false,` (的值 `message` ，且其 null 狀態) 為 null。</span><span class="sxs-lookup"><span data-stu-id="9158e-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="9158e-120">的規則 `key` 可以完全以變數類型表示： `key` 應為不可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="9158e-120">The rule for `key` can be completely expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="9158e-121">`message`參數較為複雜。</span><span class="sxs-lookup"><span data-stu-id="9158e-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="9158e-122">它可 `null` 做為引數，但保證在成功時，該 `out` 引數不是 null。</span><span class="sxs-lookup"><span data-stu-id="9158e-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="9158e-123">在這些情況下，您需要更豐富的詞彙來描述期望。</span><span class="sxs-lookup"><span data-stu-id="9158e-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="9158e-124">針對可為 null 的參考更新您的程式庫， `?` 在某些變數和類型名稱上需要隨處揮灑 threadpool.queueuserworkitem 以上的部分。</span><span class="sxs-lookup"><span data-stu-id="9158e-124">Updating your library for nullable references requires more than sprinkling `?` on some of the variables and type names.</span></span> <span data-ttu-id="9158e-125">上述範例顯示您需要檢查您的 Api，並考慮每個輸入引數的預期。</span><span class="sxs-lookup"><span data-stu-id="9158e-125">The preceding example shows that you need to examine your APIs and consider your expectations for each input argument.</span></span> <span data-ttu-id="9158e-126">請考慮傳回值的保證，以及方法傳回 `out` 時的任何或 `ref` 引數。</span><span class="sxs-lookup"><span data-stu-id="9158e-126">Consider the guarantees for the return value, and any `out` or `ref` arguments upon the method's return.</span></span> <span data-ttu-id="9158e-127">然後，將這些規則傳達給編譯器，而當呼叫端不遵守這些規則時，編譯器將會提供警告。</span><span class="sxs-lookup"><span data-stu-id="9158e-127">Then communicate those rules to the compiler, and the compiler will provide warnings when callers don't abide by those rules.</span></span>

<span data-ttu-id="9158e-128">此工作需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="9158e-128">This work takes time.</span></span> <span data-ttu-id="9158e-129">讓我們從策略開始，讓您的程式庫或應用程式成為可為 null 感知，同時平衡其他需求。</span><span class="sxs-lookup"><span data-stu-id="9158e-129">Let's start with strategies to make your library or application nullable-aware, while balancing other requirements.</span></span> <span data-ttu-id="9158e-130">您將瞭解如何平衡進行中的開發啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="9158e-130">You'll see how to balance ongoing development enabling nullable reference types.</span></span> <span data-ttu-id="9158e-131">您將瞭解泛型型別定義的挑戰。</span><span class="sxs-lookup"><span data-stu-id="9158e-131">You'll learn challenges for generic type definitions.</span></span> <span data-ttu-id="9158e-132">您將瞭解如何套用屬性來描述個別 Api 的前置和後置條件。</span><span class="sxs-lookup"><span data-stu-id="9158e-132">You'll learn to apply attributes to describe pre- and post-conditions on individual APIs.</span></span>

## <a name="choose-a-strategy-for-nullable-reference-types"></a><span data-ttu-id="9158e-133">選擇可為 null 的參考型別策略</span><span class="sxs-lookup"><span data-stu-id="9158e-133">Choose a strategy for nullable reference types</span></span>

<span data-ttu-id="9158e-134">第一個選擇是可為 null 的參考型別預設為開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="9158e-134">The first choice is whether nullable reference types should be on or off by default.</span></span> <span data-ttu-id="9158e-135">您有兩個策略：</span><span class="sxs-lookup"><span data-stu-id="9158e-135">You have two strategies:</span></span>

- <span data-ttu-id="9158e-136">針對整個專案啟用可為 null 的參考型別，並在尚未就緒的程式碼中加以停用。</span><span class="sxs-lookup"><span data-stu-id="9158e-136">Enable nullable reference types for the entire project, and disable it in code that's not ready.</span></span>
- <span data-ttu-id="9158e-137">針對已針對可為 null 的參考型別進行批註的程式碼，只啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="9158e-137">Only enable nullable reference types for code that's been annotated for nullable reference types.</span></span>

<span data-ttu-id="9158e-138">當您針對可為 null 的參考型別更新時，第一種策略的效果最好是將其他功能新增至程式庫。</span><span class="sxs-lookup"><span data-stu-id="9158e-138">The first strategy works best when you're adding other features to the library as you update it for nullable reference types.</span></span> <span data-ttu-id="9158e-139">所有新的開發都可為 null 感知。</span><span class="sxs-lookup"><span data-stu-id="9158e-139">All new development is nullable aware.</span></span> <span data-ttu-id="9158e-140">當您更新現有的程式碼時，會在這些類別中啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="9158e-140">As you update existing code, you enable nullable reference types in those classes.</span></span>

<span data-ttu-id="9158e-141">遵循第一個策略之後，您可以執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9158e-141">Following this first strategy, you do the following steps:</span></span>

1. <span data-ttu-id="9158e-142">將專案新增至 .csproj 檔案，以啟用整個專案的可為 null 參考型別 `<Nullable>enable</Nullable>` 。 *csproj*</span><span class="sxs-lookup"><span data-stu-id="9158e-142">Enable nullable reference types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="9158e-143">將 `#nullable disable` pragma 新增至專案中的每個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="9158e-143">Add the `#nullable disable` pragma to every source file in your project.</span></span>
1. <span data-ttu-id="9158e-144">當您處理每個檔案時，請移除 pragma 並解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="9158e-144">As you work on each file, remove the pragma and address any warnings.</span></span>

<span data-ttu-id="9158e-145">第一個策略是將 pragma 新增到每個檔案的前幾個工作。</span><span class="sxs-lookup"><span data-stu-id="9158e-145">This first strategy has more up-front work to add the pragma to every file.</span></span> <span data-ttu-id="9158e-146">優點是每個新增至專案的新程式碼檔案都可為 null 啟用。</span><span class="sxs-lookup"><span data-stu-id="9158e-146">The advantage is that every new code file added to the project will be nullable enabled.</span></span> <span data-ttu-id="9158e-147">任何新工作都可為 null 感知;只有現有的程式碼必須更新。</span><span class="sxs-lookup"><span data-stu-id="9158e-147">Any new work will be nullable aware; only existing code must be updated.</span></span>

<span data-ttu-id="9158e-148">如果程式庫是穩定的，第二個策略的運作效果最好，而開發的主要重點是採用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="9158e-148">The second strategy works better if the library is stable, and the main focus of the development is to adopt nullable reference types.</span></span> <span data-ttu-id="9158e-149">當您標注 Api 時，會開啟可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="9158e-149">You turn on nullable reference types as you annotate APIs.</span></span> <span data-ttu-id="9158e-150">當您完成時，您會為整個專案啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="9158e-150">When you've finished, you enable nullable reference types for the entire project.</span></span>

<span data-ttu-id="9158e-151">遵循第二個策略，您可以執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9158e-151">Following this second strategy you do the following steps:</span></span>

1. <span data-ttu-id="9158e-152">將 `#nullable enable` pragma 新增至您想要成為可為 null 感知的檔案。</span><span class="sxs-lookup"><span data-stu-id="9158e-152">Add the `#nullable enable` pragma to the file you want to make nullable aware.</span></span>
1. <span data-ttu-id="9158e-153">解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="9158e-153">Address any warnings.</span></span>
1. <span data-ttu-id="9158e-154">繼續執行前兩個步驟，直到整個程式庫都可供 null 感知。</span><span class="sxs-lookup"><span data-stu-id="9158e-154">Continue these first two steps until you've made the entire library nullable aware.</span></span>
1. <span data-ttu-id="9158e-155">將專案新增至 .csproj 檔案，以啟用整個專案的可為 null 類型 `<Nullable>enable</Nullable>` 。 *csproj*</span><span class="sxs-lookup"><span data-stu-id="9158e-155">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="9158e-156">移除 `#nullable enable` pragma，因為它們已經不再需要。</span><span class="sxs-lookup"><span data-stu-id="9158e-156">Remove the `#nullable enable` pragmas, as they're no longer needed.</span></span>

<span data-ttu-id="9158e-157">第二個策略的工作量較低。</span><span class="sxs-lookup"><span data-stu-id="9158e-157">This second strategy has less work up-front.</span></span> <span data-ttu-id="9158e-158">缺點是，當您建立新檔案時，第一個工作是新增 pragma 並讓它成為可為 null 的感知。</span><span class="sxs-lookup"><span data-stu-id="9158e-158">The tradeoff is that the first task when you create a new file is to add the pragma and make it nullable aware.</span></span> <span data-ttu-id="9158e-159">如果您的小組有任何開發人員忘記，則新的程式碼現在會在工作待處理專案中，讓所有程式碼都可為 null 感知。</span><span class="sxs-lookup"><span data-stu-id="9158e-159">If any developers on your team forget, that new code is now in the backlog of work to make all code nullable aware.</span></span>

<span data-ttu-id="9158e-160">您選擇哪一種策略，取決於您的專案中正在進行的開發中活動量。</span><span class="sxs-lookup"><span data-stu-id="9158e-160">Which of these strategies you pick depends on how much active development is taking place in your project.</span></span> <span data-ttu-id="9158e-161">更成熟且穩定的專案，第二個策略愈好。</span><span class="sxs-lookup"><span data-stu-id="9158e-161">The more mature and stable your project, the better the second strategy.</span></span> <span data-ttu-id="9158e-162">開發的功能愈多，第一種策略就越好。</span><span class="sxs-lookup"><span data-stu-id="9158e-162">The more features being developed, the better the first strategy.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9158e-163">全域可為 null 的內容不適用於產生的程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="9158e-163">The global nullable context does not apply for generated code files.</span></span> <span data-ttu-id="9158e-164">在任一策略下，任何標示為已產生的原始程式檔都會 *停用* 可為 null 的內容。</span><span class="sxs-lookup"><span data-stu-id="9158e-164">Under either strategy, the nullable context is *disabled* for any source file marked as generated.</span></span> <span data-ttu-id="9158e-165">這表示產生的檔案中的任何 Api 都不會加上批註。</span><span class="sxs-lookup"><span data-stu-id="9158e-165">This means any APIs in generated files are not annotated.</span></span> <span data-ttu-id="9158e-166">有四種方式可將檔案標示為已產生：</span><span class="sxs-lookup"><span data-stu-id="9158e-166">There are four ways a file is marked as generated:</span></span>
>
> 1. <span data-ttu-id="9158e-167">在 editorconfig 中，指定 `generated_code = true` 套用至該檔案的區段。</span><span class="sxs-lookup"><span data-stu-id="9158e-167">In the .editorconfig, specify `generated_code = true` in a section that applies to that file.</span></span>
> 1. <span data-ttu-id="9158e-168">在 `<auto-generated>` 檔案 `<auto-generated/>` 頂端的批註中放入或。</span><span class="sxs-lookup"><span data-stu-id="9158e-168">Put `<auto-generated>` or `<auto-generated/>` in a comment at the top of the file.</span></span> <span data-ttu-id="9158e-169">它可以位於批註中的任何一行，但批註區塊必須是檔案中的第一個元素。</span><span class="sxs-lookup"><span data-stu-id="9158e-169">It can be on any line in that comment, but the comment block must be the first element in the file.</span></span>
> 1. <span data-ttu-id="9158e-170">使用 *TemporaryGeneratedFile_* 開始檔案名</span><span class="sxs-lookup"><span data-stu-id="9158e-170">Start the file name with *TemporaryGeneratedFile_*</span></span>
> 1. <span data-ttu-id="9158e-171">以 *. designer.cs*、 *. generated.cs*、 *. g.cs* 或 *g.i.cs* 的檔案名結尾。</span><span class="sxs-lookup"><span data-stu-id="9158e-171">End the file name with *.designer.cs*, *.generated.cs*, *.g.cs*, or *.g.i.cs*.</span></span>
>
> <span data-ttu-id="9158e-172">產生器可以使用預處理器指示詞來加入宣告 [`#nullable`](language-reference/preprocessor-directives/preprocessor-nullable.md) 。</span><span class="sxs-lookup"><span data-stu-id="9158e-172">Generators can opt-in using the [`#nullable`](language-reference/preprocessor-directives/preprocessor-nullable.md) preprocessor directive.</span></span>

## <a name="should-nullable-warnings-introduce-breaking-changes"></a><span data-ttu-id="9158e-173">是否應該有可為 null 的警告會導致中斷性變更？</span><span class="sxs-lookup"><span data-stu-id="9158e-173">Should nullable warnings introduce breaking changes?</span></span>

<span data-ttu-id="9158e-174">在您啟用可為 null 的參考型別之前，變數會被視為 *可為 null 的無警示*。</span><span class="sxs-lookup"><span data-stu-id="9158e-174">Before you enable nullable reference types, variables are considered *nullable oblivious*.</span></span> <span data-ttu-id="9158e-175">一旦您啟用可為 null 的參考型別，這些變數都不能 *為 null*。</span><span class="sxs-lookup"><span data-stu-id="9158e-175">Once you enable nullable reference types, all those variables are *non-nullable*.</span></span> <span data-ttu-id="9158e-176">如果這些變數未初始化為非 null 值，則編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="9158e-176">The compiler will issue warnings if those variables aren't initialized to non-null values.</span></span>

<span data-ttu-id="9158e-177">另一個可能的警告來源是值未初始化時的傳回值。</span><span class="sxs-lookup"><span data-stu-id="9158e-177">Another likely source of warnings is return values when the value hasn't been initialized.</span></span>

<span data-ttu-id="9158e-178">解決編譯器警告的第一步，是在參數和傳回型別 `?` 上使用注釋，指出引數或傳回值可能是 null。</span><span class="sxs-lookup"><span data-stu-id="9158e-178">The first step in addressing the compiler warnings is to use `?` annotations on parameter and return types to indicate when arguments or return values may be null.</span></span> <span data-ttu-id="9158e-179">當參考變數不可以是 null 時，原始宣告是正確的。</span><span class="sxs-lookup"><span data-stu-id="9158e-179">When reference variables must not be null, the original declaration is correct.</span></span> <span data-ttu-id="9158e-180">當您進行這項工作時，您的目標並不只是為了修正警告。</span><span class="sxs-lookup"><span data-stu-id="9158e-180">As you do this task, your goal isn't just to fix warnings.</span></span> <span data-ttu-id="9158e-181">更重要的目標是讓編譯器瞭解潛在 null 值的意圖。</span><span class="sxs-lookup"><span data-stu-id="9158e-181">The more important goal is to make the compiler understand your intent for potential null values.</span></span> <span data-ttu-id="9158e-182">當您檢查警告時，就會到達您的程式庫的下一個主要決策。</span><span class="sxs-lookup"><span data-stu-id="9158e-182">As you examine the warnings, you reach your next major decision for your library.</span></span> <span data-ttu-id="9158e-183">您是否要考慮修改 API 簽章，以更清楚地傳達您的設計意圖？</span><span class="sxs-lookup"><span data-stu-id="9158e-183">Do you want to consider modifying API signatures to more clearly communicate your design intent?</span></span> <span data-ttu-id="9158e-184">稍早檢查過的方法的 API 簽章 `TryGetMessage` 可能是：</span><span class="sxs-lookup"><span data-stu-id="9158e-184">A better API signature for the `TryGetMessage` method examined earlier could be:</span></span>

```csharp
string? TryGetMessage(string key);
```

<span data-ttu-id="9158e-185">傳回值表示成功或失敗，如果找到值，則會攜帶值。</span><span class="sxs-lookup"><span data-stu-id="9158e-185">The return value indicates success or failure, and carries the value if the value was found.</span></span> <span data-ttu-id="9158e-186">在許多情況下，變更 API 簽章可以改善它們傳達 null 值的方式。</span><span class="sxs-lookup"><span data-stu-id="9158e-186">In many cases, changing API signatures can improve how they communicate null values.</span></span>

<span data-ttu-id="9158e-187">不過，對於公用程式庫或具有大型使用者群的程式庫，您可能不會想要引入任何 API 簽章變更。</span><span class="sxs-lookup"><span data-stu-id="9158e-187">However, for public libraries, or libraries with large user bases, you may prefer not introducing any API signature changes.</span></span> <span data-ttu-id="9158e-188">針對這些案例和其他常見的模式，您可以套用屬性，以便在引數或傳回值可能時更清楚地定義 `null` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-188">For those cases, and other common patterns, you can apply attributes to more clearly define when an argument or return value may be `null`.</span></span> <span data-ttu-id="9158e-189">無論您是否考慮變更您的 API 介面，您可能會發現單獨的型別批註無法用來描述 `null` 引數或傳回值的值。</span><span class="sxs-lookup"><span data-stu-id="9158e-189">Whether or not you consider changing the surface of your API, you'll likely find that type annotations alone aren't sufficient for describing `null` values for arguments or return values.</span></span> <span data-ttu-id="9158e-190">在這些情況下，您可以套用屬性來更清楚地描述 API。</span><span class="sxs-lookup"><span data-stu-id="9158e-190">In those instances, you can apply attributes to more clearly describe an API.</span></span>

## <a name="attributes-extend-type-annotations"></a><span data-ttu-id="9158e-191">屬性延伸類型注釋</span><span class="sxs-lookup"><span data-stu-id="9158e-191">Attributes extend type annotations</span></span>

<span data-ttu-id="9158e-192">已加入數個屬性，以表達變數 null 狀態的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9158e-192">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="9158e-193">您在 c # 8 之前撰寫的所有程式碼都是 null 的參考型別 *無警示*。</span><span class="sxs-lookup"><span data-stu-id="9158e-193">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="9158e-194">這表示任何參考型別變數可能是 null，但不需要 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="9158e-194">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="9158e-195">當您的程式碼 *可為 null 感知* 時，這些規則就會變更。</span><span class="sxs-lookup"><span data-stu-id="9158e-195">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="9158e-196">參考型別絕對不應該是 `null` 值，而且必須先檢查可為 null 的參考型別， `null` 再進行取值。</span><span class="sxs-lookup"><span data-stu-id="9158e-196">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="9158e-197">您的 Api 規則可能更複雜，如您在 API 案例中所見 `TryGetValue` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-197">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="9158e-198">許多 Api 都有更複雜的規則，可供變數或無法使用 `null` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-198">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="9158e-199">在這些情況下，您將使用屬性來表示這些規則。</span><span class="sxs-lookup"><span data-stu-id="9158e-199">In these cases, you'll use attributes to express those rules.</span></span> <span data-ttu-id="9158e-200">描述 API 語義的屬性可在文章中找到 [影響可為 null 分析的屬性](./language-reference/attributes/nullable-analysis.md)。</span><span class="sxs-lookup"><span data-stu-id="9158e-200">The attributes that describe the semantics of your API are found in the article on [Attributes that impact nullable analysis](./language-reference/attributes/nullable-analysis.md).</span></span>

## <a name="generic-definitions-and-nullability"></a><span data-ttu-id="9158e-201">泛型定義和 null 屬性</span><span class="sxs-lookup"><span data-stu-id="9158e-201">Generic definitions and nullability</span></span>

<span data-ttu-id="9158e-202">正確地傳達泛型型別和泛型方法的 null 狀態，需要特別注意。</span><span class="sxs-lookup"><span data-stu-id="9158e-202">Correctly communicating the null state of generic types and generic methods requires special care.</span></span> <span data-ttu-id="9158e-203">從可為 null 的實值型別與可為 null 的參考型別，到本質上是不同的。</span><span class="sxs-lookup"><span data-stu-id="9158e-203">The extra care stems from the fact that a nullable value type and a nullable reference type are fundamentally different.</span></span> <span data-ttu-id="9158e-204">`int?`是的同義字 `Nullable<int>` ，而 `string?` 是 `string` 由編譯器所加入的屬性。</span><span class="sxs-lookup"><span data-stu-id="9158e-204">An `int?` is a synonym for `Nullable<int>`, whereas `string?` is `string` with an attribute added by the compiler.</span></span> <span data-ttu-id="9158e-205">結果是，編譯器無法產生正確的程式碼， `T?` 而不知道是否 `T` 為 `class` 或 `struct` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-205">The result is that the compiler can't generate correct code for `T?` without knowing if `T` is a `class` or a `struct`.</span></span>

<span data-ttu-id="9158e-206">這種事實並不表示您無法使用可為 null 的型別 (實值型別或參考型別) 做為封閉式泛型型別的型別引數。</span><span class="sxs-lookup"><span data-stu-id="9158e-206">This fact doesn't mean you can't use a nullable type (either value type or reference type) as the type argument for a closed generic type.</span></span> <span data-ttu-id="9158e-207">`List<string?>`和 `List<int?>` 都是的有效具現化 `List<T>` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-207">Both `List<string?>` and `List<int?>` are valid instantiations of `List<T>`.</span></span>

<span data-ttu-id="9158e-208">它的意思是，您不能 `T?` 在沒有條件約束的泛型類別或方法宣告中使用。</span><span class="sxs-lookup"><span data-stu-id="9158e-208">What it does mean is that you can't use `T?` in a generic class or method declaration without constraints.</span></span> <span data-ttu-id="9158e-209">例如， <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> 不會變更為 return `T?` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-209">For example, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> won't be changed to return `T?`.</span></span> <span data-ttu-id="9158e-210">您可以藉由新增 `struct` 或條件約束來克服這項限制 `class` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-210">You can overcome this limitation by adding either the `struct` or `class` constraint.</span></span> <span data-ttu-id="9158e-211">使用上述任一條件約束時，編譯器就知道如何為和產生程式 `T` 代碼 `T?` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-211">With either of those constraints, the compiler knows how to generate code for both `T` and `T?`.</span></span>

<span data-ttu-id="9158e-212">您可能會想要將用於泛型型別引數的類型限制為不可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="9158e-212">You may want to restrict the types used for a generic type argument to be non-nullable types.</span></span> <span data-ttu-id="9158e-213">您可以藉由在 `notnull` 該型別引數加入條件約束來這麼做。</span><span class="sxs-lookup"><span data-stu-id="9158e-213">You can do that by adding the `notnull` constraint on that type argument.</span></span> <span data-ttu-id="9158e-214">套用該條件約束時，型別引數不能是可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="9158e-214">When that constraint is applied, the type argument must not be a nullable type.</span></span>

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a><span data-ttu-id="9158e-215">延遲初始化的屬性、資料傳輸物件和 null 屬性</span><span class="sxs-lookup"><span data-stu-id="9158e-215">Late-initialized properties, Data Transfer Objects, and nullability</span></span>

<span data-ttu-id="9158e-216">指出已延遲初始化之屬性的可 null 性（表示在結構化之後設定），可能需要特別考慮，以確保您的類別會繼續正確表達原始設計意圖。</span><span class="sxs-lookup"><span data-stu-id="9158e-216">Indicating the nullability of properties that are late-initialized, meaning set after construction, may require special consideration to ensure that your class continues to correctly express the original design intent.</span></span>

<span data-ttu-id="9158e-217">包含晚期初始化屬性的類型（例如 (Dto) 的資料傳輸物件）通常是由外部程式庫具現化，例如資料庫 ORM (物件關聯式對應程式) 、還原序列化程式，或從另一個來源自動填入屬性的其他元件。</span><span class="sxs-lookup"><span data-stu-id="9158e-217">Types that contain late-initialized properties, such as Data Transfer Objects (DTOs), are often instantiated by an external library, like a database ORM (Object Relational Mapper), a deserializer, or some other component that automatically populates properties from another source.</span></span>

<span data-ttu-id="9158e-218">在啟用可為 null 的參考型別之前，請先考慮下列 DTO 類別，以代表學生：</span><span class="sxs-lookup"><span data-stu-id="9158e-218">Consider the following DTO class, prior to enabling nullable reference types, that represents a student:</span></span>

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string VehicleRegistration { get; set; }
}
```

<span data-ttu-id="9158e-219">設計意圖 (在此案例中以屬性工作表示 `Required`) 建議在此系統中， `FirstName` 和 `LastName` 屬性是 **強制性** 的，因此不是 null。</span><span class="sxs-lookup"><span data-stu-id="9158e-219">The design intent (indicated in this case by the `Required` attribute) suggests that in this system, the `FirstName` and `LastName` properties are **mandatory**, and therefore not null.</span></span>

<span data-ttu-id="9158e-220">`VehicleRegistration`屬性不是 **強制性** 的，因此可能是 null。</span><span class="sxs-lookup"><span data-stu-id="9158e-220">The `VehicleRegistration` property is **not mandatory**, so may be null.</span></span>

<span data-ttu-id="9158e-221">當您啟用可為 null 的參考型別時，您想要指出您的 DTO 上的哪些屬性可以是可為 null，與原始意圖一致：</span><span class="sxs-lookup"><span data-stu-id="9158e-221">When you enable nullable reference types, you want to indicate which properties on your DTO may be nullable, consistent with your original intent:</span></span>

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

<span data-ttu-id="9158e-222">針對此 DTO，唯一可為 null 的屬性為 ``VehicleRegistration`` 。</span><span class="sxs-lookup"><span data-stu-id="9158e-222">For this DTO, the only property that may be null is ``VehicleRegistration``.</span></span>

<span data-ttu-id="9158e-223">不過，編譯器 `CS8618` 會針對和引發警告 `FirstName` `LastName` ，指出不可為 null 的屬性未初始化。</span><span class="sxs-lookup"><span data-stu-id="9158e-223">However, the compiler raises `CS8618` warnings for both `FirstName` and `LastName`, indicating the non-nullable properties are uninitialized.</span></span>

<span data-ttu-id="9158e-224">有三個選項可供您解決編譯器警告，方法是維護原始意圖。</span><span class="sxs-lookup"><span data-stu-id="9158e-224">There are three options available to you that resolve the compiler warnings in a way that maintains the original intent.</span></span> <span data-ttu-id="9158e-225">任何這些選項都是有效的;您應該選擇最適合您的程式碼樣式和設計需求的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9158e-225">Any of these options are valid; you should choose the one that best suits your coding style and design requirements.</span></span>

### <a name="initialize-in-the-constructor"></a><span data-ttu-id="9158e-226">在函式中初始化</span><span class="sxs-lookup"><span data-stu-id="9158e-226">Initialize in the constructor</span></span>

<span data-ttu-id="9158e-227">解決未初始化之警告的理想方式，就是初始化函式中的屬性：</span><span class="sxs-lookup"><span data-stu-id="9158e-227">The ideal way to resolve the uninitialized warnings is to initialize the properties in the constructor:</span></span>

```csharp
class Student
{
    public Student(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }

    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

<span data-ttu-id="9158e-228">只有當您用來具現化類別的程式庫支援在函式中傳遞參數時，此方法才適用。</span><span class="sxs-lookup"><span data-stu-id="9158e-228">This approach only works if the library that you use to instantiate the class supports passing parameters in the constructor.</span></span>

<span data-ttu-id="9158e-229">程式庫可能支援在函式中傳遞 *某些* 屬性，但並非全部。</span><span class="sxs-lookup"><span data-stu-id="9158e-229">A library may support passing *some* properties in the constructor, but not all.</span></span> <span data-ttu-id="9158e-230">例如，EF Core 支援一般資料行屬性的 [函數](/ef/core/modeling/constructors) 系結，但不支援導覽屬性。</span><span class="sxs-lookup"><span data-stu-id="9158e-230">For example, EF Core supports [constructor binding](/ef/core/modeling/constructors) for normal column properties, but not navigation properties.</span></span>

<span data-ttu-id="9158e-231">請查看可具現化類別之程式庫的檔，以瞭解它支援的函式系結範圍。</span><span class="sxs-lookup"><span data-stu-id="9158e-231">Check the documentation on the library that instantiates your class, to understand the extent to which it supports constructor binding.</span></span>

### <a name="property-with-nullable-backing-field"></a><span data-ttu-id="9158e-232">具有可為 null 之支援欄位的屬性</span><span class="sxs-lookup"><span data-stu-id="9158e-232">Property with nullable backing field</span></span>

<span data-ttu-id="9158e-233">如果您無法使用函式系結，則處理此問題的其中一種方式是讓不可為 null 的屬性具有可為 null 的支援欄位：</span><span class="sxs-lookup"><span data-stu-id="9158e-233">If constructor binding won't work for you, one way to deal with this problem is to have a non-nullable property with a nullable backing field:</span></span>

```csharp
private string? _firstName;

[Required]
public string FirstName
{
    set => _firstName = value;
    get => _firstName
           ?? throw new InvalidOperationException("Uninitialized " + nameof(FirstName))
}
```

<span data-ttu-id="9158e-234">在此案例中，如果在 `FirstName` 初始化之前存取屬性，則程式碼會擲回 `InvalidOperationException` ，因為 API 合約的使用方式不正確。</span><span class="sxs-lookup"><span data-stu-id="9158e-234">In this scenario, if the `FirstName` property is accessed before it has been initialized, then the code throws an `InvalidOperationException`, because the API contract has been used incorrectly.</span></span>

<span data-ttu-id="9158e-235">請考慮在使用支援欄位時，某些程式庫可能會有特殊的考慮。</span><span class="sxs-lookup"><span data-stu-id="9158e-235">Consider that some libraries may have special considerations when using backing fields.</span></span> <span data-ttu-id="9158e-236">例如，可能需要將 EF Core 設定為正確使用 [支援欄位](/ef/core/modeling/backing-field) 。</span><span class="sxs-lookup"><span data-stu-id="9158e-236">For example, EF Core may need to be configured to use [backing fields](/ef/core/modeling/backing-field) correctly.</span></span>

### <a name="initialize-the-property-to-null"></a><span data-ttu-id="9158e-237">將屬性初始化為 null</span><span class="sxs-lookup"><span data-stu-id="9158e-237">Initialize the property to null</span></span>

<span data-ttu-id="9158e-238">作為使用可為 null 之支援欄位的 terser 替代方案，或者如果具現化類別的程式庫與該方法不相容，您可以 `null` 使用容許運算子的說明 () 來直接初始化屬性 `!` ：</span><span class="sxs-lookup"><span data-stu-id="9158e-238">As a terser alternative to using a nullable backing field, or if the library that instantiates your class isn't compatible with that approach, you can initialize the property to `null` directly, with the help of the null-forgiving operator (`!`):</span></span>

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

<span data-ttu-id="9158e-239">您永遠不會在執行時間觀察到實際的 null 值，因為程式設計錯誤的結果是在正確初始化之前存取屬性。</span><span class="sxs-lookup"><span data-stu-id="9158e-239">You'll never observe an actual null value at runtime except as a result of a programming bug, by accessing the property before it has been properly initialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="9158e-240">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9158e-240">See also</span></span>

- [<span data-ttu-id="9158e-241">將現有的程式碼基底遷移至可為 Null 參考</span><span class="sxs-lookup"><span data-stu-id="9158e-241">Migrate an existing codebase to nullable references</span></span>](tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="9158e-242">在 EF Core 中使用可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="9158e-242">Working with Nullable Reference Types in EF Core</span></span>](/ef/core/miscellaneous/nullable-reference-types)
