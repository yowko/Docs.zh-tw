---
title: 更新您的程式碼基底以使用可為 null 的參考型別
description: 選擇最佳的策略來升級程式碼基底，以使用可為 null 的參考型別。
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5909eb9ffe1f5398fc2eb74848b82f8fe9516548
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975330"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a><span data-ttu-id="f2351-103">更新程式庫以使用可為 null 的參考型別，並將可為 null 的規則與呼叫</span><span class="sxs-lookup"><span data-stu-id="f2351-103">Update libraries to use nullable reference types and communicate nullable rules to callers</span></span>

<span data-ttu-id="f2351-104">加入[可為 null 的參考型別](nullable-references.md)表示您可以宣告每個變數`null`是否允許或預期值。</span><span class="sxs-lookup"><span data-stu-id="f2351-104">The addition of [nullable reference types](nullable-references.md) means you can declare whether or not a `null` value is allowed or expected for every variable.</span></span> <span data-ttu-id="f2351-105">此外，您可以套用`AllowNull`一些屬性：、 `DisallowNull`、 `MaybeNull`、 `NotNull`、 `NotNullWhen` `MaybeNullWhen`、和`NotNullIfNotNull` ，以完整描述引數和傳回值的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="f2351-105">In addition, you can apply a number of attributes: `AllowNull`, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull` to completely describe the null states of argument and return values.</span></span> <span data-ttu-id="f2351-106">這會在您撰寫程式碼時提供絕佳的體驗。</span><span class="sxs-lookup"><span data-stu-id="f2351-106">That provides a great experience as you write code.</span></span> <span data-ttu-id="f2351-107">如果不可為 null 的變數可能設定為`null`，則會收到警告。</span><span class="sxs-lookup"><span data-stu-id="f2351-107">You get warnings if a non-nullable variable might be set to `null`.</span></span> <span data-ttu-id="f2351-108">如果可為 null 的變數不是 null，則您會收到警告，然後再對其進行取值。</span><span class="sxs-lookup"><span data-stu-id="f2351-108">You get warnings if a nullable variable isn't null-checked before you dereference it.</span></span> <span data-ttu-id="f2351-109">更新您的程式庫可能需要一些時間，但回報值得一提。</span><span class="sxs-lookup"><span data-stu-id="f2351-109">Updating your libraries can take time, but the payoffs are worth it.</span></span> <span data-ttu-id="f2351-110">*當*允許或禁止某個`null`值時，您提供給編譯器的資訊越多，API 的使用者就會得到更好的警告。</span><span class="sxs-lookup"><span data-stu-id="f2351-110">The more information you provide to the compiler about *when* a `null` value is allowed or prohibited, the better warnings users of your API will get.</span></span> <span data-ttu-id="f2351-111">讓我們從熟悉的範例開始。</span><span class="sxs-lookup"><span data-stu-id="f2351-111">Let's start with a familiar example.</span></span> <span data-ttu-id="f2351-112">假設您的程式庫具有下列 API 來抓取資源字串：</span><span class="sxs-lookup"><span data-stu-id="f2351-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="f2351-113">上述範例會遵循 .NET 中`Try*`熟悉的模式。</span><span class="sxs-lookup"><span data-stu-id="f2351-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="f2351-114">此 API 有兩個參考引數： `key`和`message`參數。</span><span class="sxs-lookup"><span data-stu-id="f2351-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="f2351-115">此 API 具有下列與這些引數的 null 相關的規則：</span><span class="sxs-lookup"><span data-stu-id="f2351-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="f2351-116">呼叫端不`null`應傳遞做為`key`的引數。</span><span class="sxs-lookup"><span data-stu-id="f2351-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="f2351-117">呼叫端可以傳遞一個變數，其`null`值會當做的`message`引數。</span><span class="sxs-lookup"><span data-stu-id="f2351-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="f2351-118">如果`TryGetMessage`方法傳回`true`，則的值`message`不是 null。</span><span class="sxs-lookup"><span data-stu-id="f2351-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="f2351-119">如果傳回值是`false,` `message` （和其 null 狀態）的值，則為 null。</span><span class="sxs-lookup"><span data-stu-id="f2351-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="f2351-120">的規則`key`可以完全以變數類型表示： `key`應該是不可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="f2351-120">The rule for `key` can be completely expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="f2351-121">`message`參數較複雜。</span><span class="sxs-lookup"><span data-stu-id="f2351-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="f2351-122">它允許`null`做為引數，但可保證在成功時， `out`該引數不是 null。</span><span class="sxs-lookup"><span data-stu-id="f2351-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="f2351-123">在這些情況下，您需要更豐富的詞彙來描述預期。</span><span class="sxs-lookup"><span data-stu-id="f2351-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="f2351-124">針對可為 null 的參考更新您的連結`?`庫，在某些變數和類型名稱上不需要隨處揮灑 threadpool.queueuserworkitem。</span><span class="sxs-lookup"><span data-stu-id="f2351-124">Updating your library for nullable references requires more than sprinkling `?` on some of the variables and type names.</span></span> <span data-ttu-id="f2351-125">上述範例顯示您需要檢查您的 Api，並考慮每個輸入引數的預期。</span><span class="sxs-lookup"><span data-stu-id="f2351-125">The preceding example shows that you need to examine your APIs and consider your expectations for each input argument.</span></span> <span data-ttu-id="f2351-126">請考慮傳回值的保證，以及方法傳回`out`時`ref`的任何或引數。</span><span class="sxs-lookup"><span data-stu-id="f2351-126">Consider the guarantees for the return value, and any `out` or `ref` arguments upon the method's return.</span></span> <span data-ttu-id="f2351-127">然後將這些規則傳達給編譯器，而編譯器會在呼叫者不遵守這些規則時提供警告。</span><span class="sxs-lookup"><span data-stu-id="f2351-127">Then communicate those rules to the compiler, and the compiler will provide warnings when callers don't abide by those rules.</span></span>

<span data-ttu-id="f2351-128">此工作需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="f2351-128">This work takes time.</span></span> <span data-ttu-id="f2351-129">讓我們從策略開始，將您的程式庫或應用程式設為可為 null 感知，同時平衡其他需求和交付專案。</span><span class="sxs-lookup"><span data-stu-id="f2351-129">Let's start with strategies to make your library or application nullable-aware, while balancing other requirements and deliverables.</span></span> <span data-ttu-id="f2351-130">您將瞭解如何平衡進行中的開發，並啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="f2351-130">You'll see how to balance ongoing development enabling nullable reference types.</span></span> <span data-ttu-id="f2351-131">您將會學到泛型型別定義的挑戰。</span><span class="sxs-lookup"><span data-stu-id="f2351-131">You'll learn challenges for generic type definitions.</span></span> <span data-ttu-id="f2351-132">您將瞭解如何套用屬性，以描述個別 Api 的前置和後置條件。</span><span class="sxs-lookup"><span data-stu-id="f2351-132">You'll learn to apply attributes to describe pre- and post-conditions on individual APIs.</span></span>

## <a name="choose-a-strategy-for-nullable-reference-types"></a><span data-ttu-id="f2351-133">選擇可為 null 之參考型別的策略</span><span class="sxs-lookup"><span data-stu-id="f2351-133">Choose a strategy for nullable reference types</span></span>

<span data-ttu-id="f2351-134">第一個選擇是可為 null 的參考型別是否預設為開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="f2351-134">The first choice is whether nullable reference types should be on or off by default.</span></span> <span data-ttu-id="f2351-135">您有兩種策略：</span><span class="sxs-lookup"><span data-stu-id="f2351-135">You have two strategies:</span></span>

- <span data-ttu-id="f2351-136">為整個專案啟用可為 null 的參考型別，並在未就緒的程式碼中停用它。</span><span class="sxs-lookup"><span data-stu-id="f2351-136">Enable nullable reference types for the entire project, and disable it in code that's not ready.</span></span>
- <span data-ttu-id="f2351-137">僅針對已針對可為 null 的參考型別標注的程式碼，啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="f2351-137">Only enable nullable reference types for code that's been annotated for nullable reference types.</span></span>

<span data-ttu-id="f2351-138">當您將其他功能新增至程式庫時，第一個策略的效果最佳，是針對可為 null 的參考型別進行更新。</span><span class="sxs-lookup"><span data-stu-id="f2351-138">The first strategy works best when you're adding other features to the library as you update it for nullable reference types.</span></span> <span data-ttu-id="f2351-139">所有新的開發都是可為 null 的感知。</span><span class="sxs-lookup"><span data-stu-id="f2351-139">All new development is nullable aware.</span></span> <span data-ttu-id="f2351-140">當您更新現有程式碼時，您可以在這些類別中啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="f2351-140">As you update existing code, you enable nullable reference types in those classes.</span></span>

<span data-ttu-id="f2351-141">遵循第一個策略，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f2351-141">Following this first strategy, you do the following:</span></span>

1. <span data-ttu-id="f2351-142">藉由將`<Nullable>enable</Nullable>`元素新增至您的 *.csproj*檔案，為整個專案啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="f2351-142">Enable nullable reference types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="f2351-143">將`#nullable disable` pragma 新增至專案中的每個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="f2351-143">Add the `#nullable disable` pragma to every source file in your project.</span></span>
1. <span data-ttu-id="f2351-144">當您處理每個檔案時，請移除 pragma 並解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="f2351-144">As you work on each file, remove the pragma and address any warnings.</span></span>

<span data-ttu-id="f2351-145">第一個策略有更多的最新工作，可以將 pragma 新增至每個檔案。</span><span class="sxs-lookup"><span data-stu-id="f2351-145">This first strategy has more up-front work to add the pragma to every file.</span></span> <span data-ttu-id="f2351-146">優點是每個新增至專案的新程式碼檔案都可為 null 啟用。</span><span class="sxs-lookup"><span data-stu-id="f2351-146">The advantage is that every new code file added to the project will be nullable enabled.</span></span> <span data-ttu-id="f2351-147">任何新工作都可為 null 感知;僅必須更新現有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2351-147">Any new work will be nullable aware; only existing code must be updated.</span></span>

<span data-ttu-id="f2351-148">如果程式庫通常穩定，第二個策略的效果更好，而開發的主要重點是採用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="f2351-148">The second strategy works better if the library is generally stable, and the main focus of the development is to adopt nullable reference types.</span></span> <span data-ttu-id="f2351-149">當您標注 Api 時，您會開啟可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="f2351-149">You turn on nullable reference types as you annotate APIs.</span></span> <span data-ttu-id="f2351-150">當您完成時，您可以為整個專案啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="f2351-150">When you've finished, you enable nullable reference types for the entire project.</span></span>

<span data-ttu-id="f2351-151">遵循第二個策略，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f2351-151">Following this second strategy you do the following:</span></span>

1. <span data-ttu-id="f2351-152">將`#nullable enable` pragma 新增到您想要使其成為可為 null 的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2351-152">Add the `#nullable enable` pragma to the file you want to make nullable aware.</span></span>
1. <span data-ttu-id="f2351-153">解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="f2351-153">Address any warnings.</span></span>
1. <span data-ttu-id="f2351-154">繼續執行前兩個步驟，直到您將整個程式庫設為可為 null 為止。</span><span class="sxs-lookup"><span data-stu-id="f2351-154">Continue these first two steps until you've made the entire library nullable aware.</span></span>
1. <span data-ttu-id="f2351-155">將`<Nullable>enable</Nullable>`元素新增至您的 *.csproj*檔案，為整個專案啟用可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="f2351-155">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="f2351-156">移除`#nullable enable` pragma，因為已不再需要它。</span><span class="sxs-lookup"><span data-stu-id="f2351-156">Remove the `#nullable enable` pragmas, as they're no longer needed.</span></span>

<span data-ttu-id="f2351-157">第二個策略的處理時間較少。</span><span class="sxs-lookup"><span data-stu-id="f2351-157">This second strategy has less work up-front.</span></span> <span data-ttu-id="f2351-158">缺點是，當您建立新檔案時，第一項工作是新增 pragma 並讓它成為可為 null 的感知。</span><span class="sxs-lookup"><span data-stu-id="f2351-158">The tradeoff is that the first task when you create a new file is to add the pragma and make it nullable aware.</span></span> <span data-ttu-id="f2351-159">如果您小組中的任何開發人員忘記，新的程式碼現在已在工作待處理專案中，使所有程式碼可為 null 感知。</span><span class="sxs-lookup"><span data-stu-id="f2351-159">If any developers on your team forget, that new code is now in the backlog of work to make all code nullable aware.</span></span>

<span data-ttu-id="f2351-160">您挑選的其中一個策略，取決於您的專案中有多少使用中的開發。</span><span class="sxs-lookup"><span data-stu-id="f2351-160">Which of these strategies you pick depends on how much active development is taking place in your project.</span></span> <span data-ttu-id="f2351-161">您的專案越成熟且穩定，第二個策略就越好。</span><span class="sxs-lookup"><span data-stu-id="f2351-161">The more mature and stable your project, the better the second strategy.</span></span> <span data-ttu-id="f2351-162">開發的功能越多，第一個策略就越好。</span><span class="sxs-lookup"><span data-stu-id="f2351-162">The more features being developed, the better the first strategy.</span></span>

## <a name="should-nullable-warnings-introduce-breaking-changes"></a><span data-ttu-id="f2351-163">可為 null 的警告是否會引進重大變更？</span><span class="sxs-lookup"><span data-stu-id="f2351-163">Should nullable warnings introduce breaking changes?</span></span>

<span data-ttu-id="f2351-164">啟用可為 null 的參考型別之前，變數會被視為*可為 null 的遺忘式*。</span><span class="sxs-lookup"><span data-stu-id="f2351-164">Before you enable nullable reference types, variables are considered *nullable oblivious*.</span></span> <span data-ttu-id="f2351-165">啟用可為 null 的參考型別後，所有這些變數都*不可為 null*。</span><span class="sxs-lookup"><span data-stu-id="f2351-165">Once you enable nullable reference types, all those variables are *non-nullable*.</span></span> <span data-ttu-id="f2351-166">如果未將這些變數初始化為非 null 值，編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="f2351-166">The compiler will issue warnings if those variables aren't initialized to non-null values.</span></span>

<span data-ttu-id="f2351-167">另一個可能的警告來源是值未初始化時的傳回值。</span><span class="sxs-lookup"><span data-stu-id="f2351-167">Another likely source of warnings is return values when the value hasn't been initialized.</span></span>

<span data-ttu-id="f2351-168">解決編譯器警告的第一個步驟是在參數和`?`傳回型別上使用注釋，以指示引數或傳回值是否可以是 null。</span><span class="sxs-lookup"><span data-stu-id="f2351-168">The first step in addressing the compiler warnings is to use `?` annotations on parameter and return types to indicate when arguments or return values may be null.</span></span> <span data-ttu-id="f2351-169">當參考變數不得為 null 時，原始宣告是正確的。</span><span class="sxs-lookup"><span data-stu-id="f2351-169">When reference variables must not be null, the original declaration is correct.</span></span> <span data-ttu-id="f2351-170">當您這麼做時，您的目標不是要修正警告。</span><span class="sxs-lookup"><span data-stu-id="f2351-170">As you do this, your goal isn't just to fix warnings.</span></span> <span data-ttu-id="f2351-171">較重要的目標是讓編譯器瞭解潛在 null 值的意圖。</span><span class="sxs-lookup"><span data-stu-id="f2351-171">The more important goal is to make the compiler understand your intent for potential null values.</span></span> <span data-ttu-id="f2351-172">當您檢查這些警告時，您會到達程式庫的下一個主要決策。</span><span class="sxs-lookup"><span data-stu-id="f2351-172">As you examine the warnings, you reach your next major decision for your library.</span></span> <span data-ttu-id="f2351-173">您是否想要考慮修改 API 簽章，以更清楚地傳達您的設計意圖？</span><span class="sxs-lookup"><span data-stu-id="f2351-173">Do you want to consider modifying API signatures to more clearly communicate your design intent?</span></span> <span data-ttu-id="f2351-174">更好的 API 簽章`TryGetMessage`適用于先前檢查的方法，可能是：</span><span class="sxs-lookup"><span data-stu-id="f2351-174">A better API signature for the `TryGetMessage` method examined earlier could be:</span></span>

```csharp
string? TryGetMessage(string key);
```

<span data-ttu-id="f2351-175">傳回值表示成功或失敗，如果找到值，則會攜帶值。</span><span class="sxs-lookup"><span data-stu-id="f2351-175">The return value indicates success or failure, and carries the value if the value was found.</span></span> <span data-ttu-id="f2351-176">在許多情況下，變更 API 簽章可以改善它們傳達 null 值的方式。</span><span class="sxs-lookup"><span data-stu-id="f2351-176">In many cases, changing API signatures can improve how they communicate null values.</span></span>

<span data-ttu-id="f2351-177">不過，對於公用程式庫或具有大型使用者群的程式庫，您可能不會想要引入任何 API 簽章變更。</span><span class="sxs-lookup"><span data-stu-id="f2351-177">However, for public libraries, or libraries with large user bases, you may prefer not introducing any API signature changes.</span></span> <span data-ttu-id="f2351-178">針對這些案例和其他常見的模式，您可以套用屬性，以更清楚地定義引數或傳回值可能`null`的時機。</span><span class="sxs-lookup"><span data-stu-id="f2351-178">For those cases, and other common patterns, you can apply attributes to more clearly define when an argument or return value may be `null`.</span></span> <span data-ttu-id="f2351-179">無論您是否考慮變更 API 的介面，您可能會發現單獨的類型注釋並不足以描述`null`引數或傳回值的值。</span><span class="sxs-lookup"><span data-stu-id="f2351-179">Whether or not you consider changing the surface of your API, you'll likely find that type annotations alone aren't sufficient for describing `null` values for arguments or return values.</span></span> <span data-ttu-id="f2351-180">在這些情況下，您可以套用屬性，以更清楚地描述 API。</span><span class="sxs-lookup"><span data-stu-id="f2351-180">In those instances, you can apply attributes to more clearly describe an API.</span></span>

## <a name="attributes-extend-type-annotations"></a><span data-ttu-id="f2351-181">屬性擴充類型注釋</span><span class="sxs-lookup"><span data-stu-id="f2351-181">Attributes extend type annotations</span></span>

<span data-ttu-id="f2351-182">已經加入數個屬性，以表達變數的 null 狀態的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f2351-182">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="f2351-183">您在 c # 8 之前撰寫的所有程式碼引進了可為 null 的參考型別，*遺忘式*。</span><span class="sxs-lookup"><span data-stu-id="f2351-183">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="f2351-184">這表示任何參考型別變數都可以是 null，但不需要 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="f2351-184">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="f2351-185">一旦您的程式碼*可為 null 感知*，這些規則就會變更。</span><span class="sxs-lookup"><span data-stu-id="f2351-185">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="f2351-186">參考型別應該永遠不`null`會是值，而且必須`null`先檢查可為 null 的參考型別，然後再進行引用。</span><span class="sxs-lookup"><span data-stu-id="f2351-186">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="f2351-187">您的 Api 規則可能會更複雜，如您在`TryGetValue` API 案例中所見。</span><span class="sxs-lookup"><span data-stu-id="f2351-187">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="f2351-188">許多 Api 在變數可以或不是`null`時，會有更複雜的規則。</span><span class="sxs-lookup"><span data-stu-id="f2351-188">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="f2351-189">在這些情況下，您將使用屬性來表示這些規則。</span><span class="sxs-lookup"><span data-stu-id="f2351-189">In these cases, you'll use attributes to express those rules.</span></span> <span data-ttu-id="f2351-190">描述 API 的語義的屬性可在[影響可為 null 分析的屬性](./language-reference/attributes/nullable-analysis.md)一文中找到。</span><span class="sxs-lookup"><span data-stu-id="f2351-190">The attributes that describe the semantics of your API are found in the article on [Attributes that impact nullable analysis](./language-reference/attributes/nullable-analysis.md).</span></span>

## <a name="generic-definitions-and-nullability"></a><span data-ttu-id="f2351-191">泛型定義和 null 屬性</span><span class="sxs-lookup"><span data-stu-id="f2351-191">Generic definitions and nullability</span></span>

<span data-ttu-id="f2351-192">正確地傳達泛型型別和泛型方法的 null 狀態需要特別小心。</span><span class="sxs-lookup"><span data-stu-id="f2351-192">Correctly communicating the null state of generic types and generic methods requires special care.</span></span> <span data-ttu-id="f2351-193">這源自于可為 null 的實值型別和可為 null 的參考型別，基本上是不同的事實。</span><span class="sxs-lookup"><span data-stu-id="f2351-193">This stems from the fact that a nullable value type and a nullable reference type are fundamentally different.</span></span> <span data-ttu-id="f2351-194">`int?`是的同義字`Nullable<int>`，而`string?`則是`string`由編譯器新增的屬性。</span><span class="sxs-lookup"><span data-stu-id="f2351-194">An `int?` is a synonym for `Nullable<int>`, whereas `string?` is `string` with an attribute added by the compiler.</span></span> <span data-ttu-id="f2351-195">結果是`T?` ，編譯器無法產生的正確程式碼，而不知道`T`是`class`或。 `struct`</span><span class="sxs-lookup"><span data-stu-id="f2351-195">The result is that the compiler can't generate correct code for `T?` without knowing if `T` is a `class` or a `struct`.</span></span>

<span data-ttu-id="f2351-196">這並不表示您無法使用可為 null 的類型（實數值型別或參考型別）做為封閉式泛型型別的類型引數。</span><span class="sxs-lookup"><span data-stu-id="f2351-196">This doesn't mean you can't use a nullable type (either value type or reference type) as the type argument for a closed generic type.</span></span> <span data-ttu-id="f2351-197">`List<string?>`和`List<int?>`都是的`List<T>`有效具現化。</span><span class="sxs-lookup"><span data-stu-id="f2351-197">Both `List<string?>` and `List<int?>` are valid instantiations of `List<T>`.</span></span>

<span data-ttu-id="f2351-198">它的意思是，您無法在沒有`T?`條件約束的泛型類別或方法宣告中使用。</span><span class="sxs-lookup"><span data-stu-id="f2351-198">What it does mean is that you can't use `T?` in a generic class or method declaration without constraints.</span></span> <span data-ttu-id="f2351-199">例如， <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType>不會變更為傳回`T?`。</span><span class="sxs-lookup"><span data-stu-id="f2351-199">For example, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> won't be changed to return `T?`.</span></span> <span data-ttu-id="f2351-200">您可以藉由新增`struct`或`class`條件約束來克服這項限制。</span><span class="sxs-lookup"><span data-stu-id="f2351-200">You can overcome this limitation by adding either the `struct` or `class` constraint.</span></span> <span data-ttu-id="f2351-201">使用上述任一條件約束時，編譯器會知道如何為`T`和`T?`產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="f2351-201">With either of those constraints, the compiler knows how to generate code for both `T` and `T?`.</span></span>

<span data-ttu-id="f2351-202">您可能想要將泛型型別引數所使用的類型限制為不可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="f2351-202">You may want to restrict the types used for a generic type argument to be non-nullable types.</span></span> <span data-ttu-id="f2351-203">您可以在該型別自`notnull`變數上加入條件約束來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="f2351-203">You can do that by adding the `notnull` constraint on that type argument.</span></span> <span data-ttu-id="f2351-204">套用該條件約束時，類型引數不能是可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="f2351-204">When that constraint is applied, the type argument must not be a nullable type.</span></span>

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a><span data-ttu-id="f2351-205">晚期初始化的屬性、資料傳輸物件和可為 null</span><span class="sxs-lookup"><span data-stu-id="f2351-205">Late-initialized properties, Data Transfer Objects and nullability</span></span>

<span data-ttu-id="f2351-206">指出已延遲初始化之屬性的 null 屬性（亦即在結構之後設定）可能需要特別考慮，以確保您的類別會繼續正確地表達原始的設計意圖。</span><span class="sxs-lookup"><span data-stu-id="f2351-206">Indicating the nullability of properties that are late-initialized, meaning set after construction, may require special consideration to ensure that your class continues to correctly express the original design intent.</span></span>

<span data-ttu-id="f2351-207">包含晚期初始化屬性的型別（如資料傳輸物件（Dto））通常是由外部程式庫（例如資料庫 ORM （物件關聯式對應程式）、還原序列化程式，或是自動從另一個來源填入屬性的其他元件）所具現化。</span><span class="sxs-lookup"><span data-stu-id="f2351-207">Types that contain late-initialized properties, such as Data Transfer Objects (DTOs), are often instantiated by an external library, like a database ORM (Object Relational Mapper), a deserializer, or some other component that automatically populates properties from another source.</span></span>

<span data-ttu-id="f2351-208">在啟用可為 null 的參考型別（代表學生）之前，請先考慮下列 DTO 類別：</span><span class="sxs-lookup"><span data-stu-id="f2351-208">Consider the following DTO class, prior to enabling nullable reference types, that represents a student:</span></span>

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

<span data-ttu-id="f2351-209">設計意圖（在此案例中是`Required`由屬性所表示）表示在此系統中， `FirstName`和`LastName`屬性是**強制性**的，因此不是 null。</span><span class="sxs-lookup"><span data-stu-id="f2351-209">The design intent (indicated in this case by the `Required` attribute) suggests that in this system, the `FirstName` and `LastName` properties are **mandatory**, and therefore not null.</span></span>

<span data-ttu-id="f2351-210">屬性`VehicleRegistration`不是**強制性**的，因此可能是 null。</span><span class="sxs-lookup"><span data-stu-id="f2351-210">The `VehicleRegistration` property is **not mandatory**, so may be null.</span></span>

<span data-ttu-id="f2351-211">當您啟用可為 null 的參考型別時，您會想要在 DTO 上指出哪些屬性可為 null，與您的原始意圖一致：</span><span class="sxs-lookup"><span data-stu-id="f2351-211">When you enable nullable reference types, you want to indicate on our DTO which of the properties may be nullable, consistent with your original intent:</span></span>

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

<span data-ttu-id="f2351-212">對於此 DTO，唯一可為 null 的屬性是``VehicleRegistration``。</span><span class="sxs-lookup"><span data-stu-id="f2351-212">For this DTO, the only property that may be null is ``VehicleRegistration``.</span></span>

<span data-ttu-id="f2351-213">不過，編譯器會同時`CS8618` `FirstName`引發和`LastName`的警告，表示不可為 null 的屬性未初始化。</span><span class="sxs-lookup"><span data-stu-id="f2351-213">However, the compiler raises `CS8618` warnings for both `FirstName` and `LastName`, indicating the non-nullable properties are uninitialized.</span></span>

<span data-ttu-id="f2351-214">有三個選項可供您使用，以維護原始意圖的方式解決編譯器警告。</span><span class="sxs-lookup"><span data-stu-id="f2351-214">There are three options available to you that resolve the compiler warnings in a way that maintains the original intent.</span></span> <span data-ttu-id="f2351-215">任何這些選項都是有效的;您應該選擇最適合您程式碼樣式和設計需求的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f2351-215">Any of these options are valid; you should choose the one that best suits your coding style and design requirements.</span></span>

### <a name="initialize-in-the-constructor"></a><span data-ttu-id="f2351-216">在函式中初始化</span><span class="sxs-lookup"><span data-stu-id="f2351-216">Initialize in the constructor</span></span>

<span data-ttu-id="f2351-217">解決未初始化警告的理想方式，是初始化此函式中的屬性：</span><span class="sxs-lookup"><span data-stu-id="f2351-217">The ideal way to resolve the uninitialized warnings is to initialize the properties in the constructor:</span></span>

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

<span data-ttu-id="f2351-218">只有當您用來具現化類別的程式庫支援在此函式中傳遞參數時，這個方法才有效。</span><span class="sxs-lookup"><span data-stu-id="f2351-218">This approach only works if the library that you use to instantiate the class supports passing parameters in the constructor.</span></span>

<span data-ttu-id="f2351-219">此外，程式庫可能支援在函式中傳遞*某些*屬性，但並非全部。</span><span class="sxs-lookup"><span data-stu-id="f2351-219">In addition, a library may support passing *some* properties in the constructor, but not all.</span></span>
<span data-ttu-id="f2351-220">例如， [EF Core 支援一般](/ef/core/modeling/constructors)資料行屬性的「函式系結」，而非「導覽屬性」。</span><span class="sxs-lookup"><span data-stu-id="f2351-220">For example, EF Core supports [constructor binding](/ef/core/modeling/constructors) for normal column properties, but not navigation properties.</span></span>

<span data-ttu-id="f2351-221">請查看具現化類別之程式庫上的檔，以瞭解它支援的函式系結程度。</span><span class="sxs-lookup"><span data-stu-id="f2351-221">Check the documentation on the library that instantiates your class, to understand the extent to which it supports constructor binding.</span></span>

### <a name="property-with-nullable-backing-field"></a><span data-ttu-id="f2351-222">具有可為 null 支援欄位的屬性</span><span class="sxs-lookup"><span data-stu-id="f2351-222">Property with nullable backing field</span></span>

<span data-ttu-id="f2351-223">如果函式系結無法供您使用，則解決此問題的其中一種方法是將不可為 null 的屬性與可為 null 的支援欄位搭配使用：</span><span class="sxs-lookup"><span data-stu-id="f2351-223">If constructor binding won't work for you, one way to deal with this problem is to have a non-nullable property with a nullable backing field:</span></span>

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

<span data-ttu-id="f2351-224">在此案例中，如果`FirstName`在初始化之前存取屬性，則程式`InvalidOperationException`代碼會擲回，因為 API 合約的使用不正確。</span><span class="sxs-lookup"><span data-stu-id="f2351-224">In this scenario, if the `FirstName` property is accessed before it has been initialized, then the code throws an `InvalidOperationException`, because the API contract has been used incorrectly.</span></span>

<span data-ttu-id="f2351-225">使用支援欄位時，您應該考慮某些程式庫可能會有特殊的考慮。</span><span class="sxs-lookup"><span data-stu-id="f2351-225">You should consider that some libraries may have special considerations when using backing fields.</span></span> <span data-ttu-id="f2351-226">例如，EF Core 可能需要設定為正確使用[支援欄位](/ef/core/modeling/backing-field)。</span><span class="sxs-lookup"><span data-stu-id="f2351-226">For example, EF Core may need to be configured to use [backing fields](/ef/core/modeling/backing-field) correctly.</span></span>

### <a name="initialize-the-property-to-null"></a><span data-ttu-id="f2351-227">將屬性初始化為 null</span><span class="sxs-lookup"><span data-stu-id="f2351-227">Initialize the property to null</span></span>

<span data-ttu-id="f2351-228">做為使用可為 null 之支援欄位的 terser 替代方案，或如果具現化類別的程式庫與該方法不相容，您可以直接將`null`屬性初始化為，並搭配 null-容許運算子（`!`）的協助：</span><span class="sxs-lookup"><span data-stu-id="f2351-228">As a terser alternative to using a nullable backing field, or if the library that instantiates your class is not compatible with that approach, you can simply initialize the property to `null` directly, with the help of the null-forgiving operator (`!`):</span></span>

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

<span data-ttu-id="f2351-229">您永遠不會在執行時間看到實際的 null 值，但由於程式設計錯誤的結果，會先存取屬性，再進行正確的初始化。</span><span class="sxs-lookup"><span data-stu-id="f2351-229">You will never observe an actual null value at runtime except as a result of a programming bug, by accessing the property before it has been properly initialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2351-230">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2351-230">See also</span></span>

- [<span data-ttu-id="f2351-231">將現有的程式碼基底遷移至可為 Null 參考</span><span class="sxs-lookup"><span data-stu-id="f2351-231">Migrate an existing codebase to nullable references</span></span>](tutorials/upgrade-to-nullable-references.md)
- [<span data-ttu-id="f2351-232">在 EF Core 中使用可為 Null 的參考型別</span><span class="sxs-lookup"><span data-stu-id="f2351-232">Working with Nullable Reference Types in EF Core</span></span>](/ef/core/miscellaneous/nullable-reference-types)
