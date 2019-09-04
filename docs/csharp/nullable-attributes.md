---
title: 升級具有屬性的 Api 以定義 null 預期
description: 本文說明加入描述性屬性的動機和技術, 以描述引數的 null 狀態和 Api 的傳回值
ms.date: 07/31/2019
ms.openlocfilehash: eebd3d190b8c93833de6e1c1f1594c1c1f56e14e
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "70234672"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a><span data-ttu-id="b0955-103">更新程式庫以使用可為 null 的參考型別, 並將可為 null 的規則與呼叫端</span><span class="sxs-lookup"><span data-stu-id="b0955-103">Update libraries to use nullable reference types and communicate nullable rules to callers.</span></span>

<span data-ttu-id="b0955-104">加入[可為 null 的參考型別](nullable-references.md)表示您可以宣告每個變數`null`是否允許或預期值。</span><span class="sxs-lookup"><span data-stu-id="b0955-104">The addition of [nullable reference types](nullable-references.md) means you can declare whether or not a `null` value is allowed or expected for every variable.</span></span> <span data-ttu-id="b0955-105">這會在您撰寫程式碼時提供絕佳的體驗。</span><span class="sxs-lookup"><span data-stu-id="b0955-105">That provides a great experience as you write code.</span></span> <span data-ttu-id="b0955-106">如果不可為 null 的變數可能設定為`null`, 則會收到警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-106">You get warnings if a non-nullable variable might be set to `null`.</span></span> <span data-ttu-id="b0955-107">如果可為 null 的變數不是 null, 則您會收到警告, 然後再對其進行取值。</span><span class="sxs-lookup"><span data-stu-id="b0955-107">You get warnings if a nullable variable isn't null-checked before you dereference it.</span></span> <span data-ttu-id="b0955-108">更新您的程式庫可能需要一些時間, 但回報值得一提。</span><span class="sxs-lookup"><span data-stu-id="b0955-108">Updating your libraries can take time, but the payoffs are worth it.</span></span> <span data-ttu-id="b0955-109">*當*允許或禁止某個`null`值時, 您提供給編譯器的資訊越多, API 的使用者就會得到更好的警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-109">The more information you provide to the compiler about *when* a `null` value is allowed or prohibited, the better warnings users of your API will get.</span></span> <span data-ttu-id="b0955-110">讓我們從熟悉的範例開始。</span><span class="sxs-lookup"><span data-stu-id="b0955-110">Let's start with a familiar example.</span></span> <span data-ttu-id="b0955-111">假設您的程式庫具有下列 API 來抓取資源字串:</span><span class="sxs-lookup"><span data-stu-id="b0955-111">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="b0955-112">上述範例會遵循 .net 中`Try*`熟悉的模式。</span><span class="sxs-lookup"><span data-stu-id="b0955-112">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="b0955-113">此 API 有兩個參考引數: `key` `message`和參數。</span><span class="sxs-lookup"><span data-stu-id="b0955-113">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="b0955-114">此 API 具有下列與這些引數的 null 相關的規則:</span><span class="sxs-lookup"><span data-stu-id="b0955-114">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="b0955-115">呼叫端不`null`應傳遞做為`key`的引數。</span><span class="sxs-lookup"><span data-stu-id="b0955-115">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="b0955-116">呼叫端可以傳遞一個變數, 其`null`值會當做的`message`引數。</span><span class="sxs-lookup"><span data-stu-id="b0955-116">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="b0955-117">`TryGetMessage`如果`message`方法傳回`true`, 則的值不是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-117">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="b0955-118">如果傳回值是`false,` `message` (和其 null 狀態) 的值, 則為 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-118">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="b0955-119">的規則`key`可以完全以變數類型表示: `key`應該是不可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="b0955-119">The rule for `key` can be completely expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="b0955-120">`message`參數較複雜。</span><span class="sxs-lookup"><span data-stu-id="b0955-120">The `message` parameter is more complex.</span></span> <span data-ttu-id="b0955-121">它允許`null`做為引數, 但可保證在成功時, `out`該引數不是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-121">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="b0955-122">在這些情況下, 您需要更豐富的詞彙來描述預期。</span><span class="sxs-lookup"><span data-stu-id="b0955-122">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="b0955-123">針對可為 null 的參考更新您的連結`?`庫, 在某些變數和類型名稱上不需要隨處揮灑 threadpool.queueuserworkitem。</span><span class="sxs-lookup"><span data-stu-id="b0955-123">Updating your library for nullable references requires more than sprinkling `?` on some of the variables and type names.</span></span> <span data-ttu-id="b0955-124">上述範例顯示您需要檢查您的 Api, 並考慮每個輸入引數的預期。</span><span class="sxs-lookup"><span data-stu-id="b0955-124">The preceding example shows that you need to examine your APIs and consider your expectations for each input argument.</span></span> <span data-ttu-id="b0955-125">請考慮傳回值的保證, 以及方法傳回`out`時`ref`的任何或引數。</span><span class="sxs-lookup"><span data-stu-id="b0955-125">Consider the guarantees for the return value, and any `out` or `ref` arguments upon the method's return.</span></span> <span data-ttu-id="b0955-126">然後將這些規則傳達給編譯器, 而編譯器會在呼叫者不遵守這些規則時提供警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-126">Then communicate those rules to the compiler, and the compiler will provide warnings when callers don't abide by those rules.</span></span>

<span data-ttu-id="b0955-127">此工作需要一些時間。</span><span class="sxs-lookup"><span data-stu-id="b0955-127">This work takes time.</span></span> <span data-ttu-id="b0955-128">讓我們從策略開始, 將您的程式庫或應用程式設為可為 null 感知, 同時平衡其他需求和交付專案。</span><span class="sxs-lookup"><span data-stu-id="b0955-128">Let's start with strategies to make your library or application nullable-aware, while balancing other requirements and deliverables.</span></span> <span data-ttu-id="b0955-129">您將瞭解如何平衡進行中的開發, 並啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="b0955-129">You'll see how to balance ongoing development enabling nullable reference types.</span></span> <span data-ttu-id="b0955-130">您將會學到泛型型別定義的挑戰。</span><span class="sxs-lookup"><span data-stu-id="b0955-130">You'll learn challenges for generic type definitions.</span></span> <span data-ttu-id="b0955-131">您將瞭解如何套用屬性, 以描述個別 Api 的前置和後置條件。</span><span class="sxs-lookup"><span data-stu-id="b0955-131">You'll learn to apply attributes to describe pre- and post-conditions on individual APIs.</span></span>

## <a name="choose-a-nullable-strategy"></a><span data-ttu-id="b0955-132">選擇可為 null 的策略</span><span class="sxs-lookup"><span data-stu-id="b0955-132">Choose a nullable strategy</span></span>

<span data-ttu-id="b0955-133">第一個選擇是可為 null 的參考型別是否預設為開啟或關閉。</span><span class="sxs-lookup"><span data-stu-id="b0955-133">The first choice is whether nullable reference types should be on or off by default.</span></span> <span data-ttu-id="b0955-134">您有兩種策略:</span><span class="sxs-lookup"><span data-stu-id="b0955-134">You have two strategies:</span></span>

- <span data-ttu-id="b0955-135">為整個專案啟用可為 null 的參考型別, 並在未就緒的程式碼中停用它。</span><span class="sxs-lookup"><span data-stu-id="b0955-135">Enable nullable reference types for the entire project, and disable it in code that's not ready.</span></span>
- <span data-ttu-id="b0955-136">僅針對已針對可為 null 的參考型別標注的程式碼, 啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="b0955-136">Only enable nullable reference types for code that's been annotated for nullable reference types.</span></span>

<span data-ttu-id="b0955-137">當您將其他功能新增至程式庫時, 第一個策略的效果最佳, 是針對可為 null 的參考型別進行更新。</span><span class="sxs-lookup"><span data-stu-id="b0955-137">The first strategy works best when you're adding other features to the library as you update it for nullable reference types.</span></span> <span data-ttu-id="b0955-138">所有新的開發都是可為 null 的感知。</span><span class="sxs-lookup"><span data-stu-id="b0955-138">All new development is nullable aware.</span></span> <span data-ttu-id="b0955-139">當您更新現有程式碼時, 您可以在這些類別中啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="b0955-139">As you update existing code, you enable nullable reference types in those classes.</span></span>

<span data-ttu-id="b0955-140">遵循第一個策略, 您可以執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="b0955-140">Following this first strategy, you do the following:</span></span>

1. <span data-ttu-id="b0955-141">將`<Nullable>enable</Nullable>`元素新增至您的 *.csproj*檔案, 為整個專案啟用可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="b0955-141">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span> 
1. <span data-ttu-id="b0955-142">`#nullable disable`將 pragma 新增至專案中的每個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="b0955-142">Add the `#nullable disable` pragma to every source file in your project.</span></span> 
1. <span data-ttu-id="b0955-143">當您處理每個檔案時, 請移除 pragma 並解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-143">As you work on each file, remove the pragma and address any warnings.</span></span>

<span data-ttu-id="b0955-144">第一個策略有更多的最新工作, 可以將 pragma 新增至每個檔案。</span><span class="sxs-lookup"><span data-stu-id="b0955-144">This first strategy has more up-front work to add the pragma to every file.</span></span> <span data-ttu-id="b0955-145">優點是每個新增至專案的新程式碼檔案都可為 null 啟用。</span><span class="sxs-lookup"><span data-stu-id="b0955-145">The advantage is that every new code file added to the project will be nullable enabled.</span></span> <span data-ttu-id="b0955-146">任何新工作都可為 null 感知;僅必須更新現有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0955-146">Any new work will be nullable aware; only existing code must be updated.</span></span>

<span data-ttu-id="b0955-147">如果程式庫通常穩定, 第二個策略的效果更好, 而開發的主要重點是採用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="b0955-147">The second strategy works better if the library is generally stable, and the main focus of the development is to adopt nullable reference types.</span></span> <span data-ttu-id="b0955-148">當您標注 Api 時, 您會開啟可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="b0955-148">You turn on nullable reference types as you annotate APIs.</span></span> <span data-ttu-id="b0955-149">當您完成時, 您可以為整個專案啟用可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="b0955-149">When you've finished, you enable nullable reference types for the entire project.</span></span>

<span data-ttu-id="b0955-150">遵循第二個策略, 您可以執行下列動作:</span><span class="sxs-lookup"><span data-stu-id="b0955-150">Following this second strategy you do the following:</span></span>

1. <span data-ttu-id="b0955-151">`#nullable enable`將 pragma 新增到您想要使其成為可為 null 的檔案。</span><span class="sxs-lookup"><span data-stu-id="b0955-151">Add the `#nullable enable` pragma to the file you want to make nullable aware.</span></span>
1. <span data-ttu-id="b0955-152">解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-152">Address any warnings.</span></span>
1. <span data-ttu-id="b0955-153">繼續執行前兩個步驟, 直到您將整個程式庫設為可為 null 為止。</span><span class="sxs-lookup"><span data-stu-id="b0955-153">Continue these first two steps until you've made the entire library nullable aware.</span></span>
1. <span data-ttu-id="b0955-154">將`<Nullable>enable</Nullable>`元素新增至您的 *.csproj*檔案, 為整個專案啟用可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="b0955-154">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span> 
1. <span data-ttu-id="b0955-155">`#nullable enable`移除 pragma, 因為已不再需要它。</span><span class="sxs-lookup"><span data-stu-id="b0955-155">Remove the `#nullable enable` pragmas, as they're no longer needed.</span></span>

<span data-ttu-id="b0955-156">第二個策略的處理時間較少。</span><span class="sxs-lookup"><span data-stu-id="b0955-156">This second strategy has less work up-front.</span></span> <span data-ttu-id="b0955-157">缺點是, 當您建立新檔案時, 第一項工作是新增 pragma 並讓它成為可為 null 的感知。</span><span class="sxs-lookup"><span data-stu-id="b0955-157">The tradeoff is that the first task when you create a new file is to add the pragma and make it nullable aware.</span></span> <span data-ttu-id="b0955-158">如果您小組中的任何開發人員忘記, 新的程式碼現在已在工作待處理專案中, 使所有程式碼可為 null 感知。</span><span class="sxs-lookup"><span data-stu-id="b0955-158">If any developers on your team forget, that new code is now in the backlog of work to make all code nullable aware.</span></span>

<span data-ttu-id="b0955-159">您挑選的其中一個策略, 取決於您的專案中有多少使用中的開發。</span><span class="sxs-lookup"><span data-stu-id="b0955-159">Which of these strategies you pick depends on how much active development is taking place in your project.</span></span> <span data-ttu-id="b0955-160">您的專案越成熟且穩定, 第二個策略就越好。</span><span class="sxs-lookup"><span data-stu-id="b0955-160">The more mature and stable your project, the better the second strategy.</span></span> <span data-ttu-id="b0955-161">開發的功能越多, 第一個策略就越好。</span><span class="sxs-lookup"><span data-stu-id="b0955-161">The more features being developed, the better the first strategy.</span></span>

## <a name="should-nullable-warnings-introduce-breaking-changes"></a><span data-ttu-id="b0955-162">可為 null 的警告是否會引進重大變更？</span><span class="sxs-lookup"><span data-stu-id="b0955-162">Should nullable warnings introduce breaking changes?</span></span>

<span data-ttu-id="b0955-163">啟用可為 null 的參考型別之前, 變數會被視為*可為 null 的遺忘式*。</span><span class="sxs-lookup"><span data-stu-id="b0955-163">Before you enable nullable reference types, variables are considered *nullable oblivious*.</span></span> <span data-ttu-id="b0955-164">啟用可為 null 的參考型別後, 所有這些變數都*不可為 null*。</span><span class="sxs-lookup"><span data-stu-id="b0955-164">Once you enable nullable reference types, all those variables are *non-nullable*.</span></span> <span data-ttu-id="b0955-165">如果未將這些變數初始化為非 null 值, 編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-165">The compiler will issue warnings if those variables aren't initialized to non-null values.</span></span>

<span data-ttu-id="b0955-166">另一個可能的警告來源是值未初始化時的傳回值。</span><span class="sxs-lookup"><span data-stu-id="b0955-166">Another likely source of warnings is return values when the value hasn't been initialized.</span></span>

<span data-ttu-id="b0955-167">解決編譯器警告的第一個步驟是在參數和`?`傳回型別上使用注釋, 以指示引數或傳回值是否可以是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-167">The first step in addressing the compiler warnings is to use `?` annotations on parameter and return types to indicate when arguments or return values may be null.</span></span> <span data-ttu-id="b0955-168">當參考變數不得為 null 時, 原始宣告是正確的。</span><span class="sxs-lookup"><span data-stu-id="b0955-168">When reference variables must not be null, the original declaration is correct.</span></span> <span data-ttu-id="b0955-169">當您這麼做時, 您的目標不是要修正警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-169">As you do this, your goal isn't just to fix warnings.</span></span> <span data-ttu-id="b0955-170">較重要的目標是讓編譯器瞭解潛在 null 值的意圖。</span><span class="sxs-lookup"><span data-stu-id="b0955-170">The more important goal is to make the compiler understand your intent for potential null values.</span></span> <span data-ttu-id="b0955-171">當您檢查這些警告時, 您會到達程式庫的下一個主要決策。</span><span class="sxs-lookup"><span data-stu-id="b0955-171">As you examine the warnings, you reach your next major decision for your library.</span></span> <span data-ttu-id="b0955-172">您是否想要考慮修改 API 簽章, 以更清楚地傳達您的設計意圖？</span><span class="sxs-lookup"><span data-stu-id="b0955-172">Do you want to consider modifying API signatures to more clearly communicate your design intent?</span></span> <span data-ttu-id="b0955-173">更好的 API 簽章`TryGetMessage`適用于先前檢查的方法, 可能是:</span><span class="sxs-lookup"><span data-stu-id="b0955-173">A better API signature for the `TryGetMessage` method examined earlier could be:</span></span>

```csharp
string? TryGetMessage(string key);
```

<span data-ttu-id="b0955-174">傳回值表示成功或失敗, 如果找到值, 則會攜帶值。</span><span class="sxs-lookup"><span data-stu-id="b0955-174">The return value indicates success or failure, and carries the value if the value was found.</span></span> <span data-ttu-id="b0955-175">在許多情況下, 變更 API 簽章可以改善它們傳達 null 值的方式。</span><span class="sxs-lookup"><span data-stu-id="b0955-175">In many cases, changing API signatures can improve how they communicate null values.</span></span>

<span data-ttu-id="b0955-176">不過, 對於公用程式庫或具有大型使用者群的程式庫, 您可能不會想要引入任何 API 簽章變更。</span><span class="sxs-lookup"><span data-stu-id="b0955-176">However, for public libraries, or libraries with large user bases, you may prefer not introducing any API signature changes.</span></span> <span data-ttu-id="b0955-177">針對這些案例和其他常見的模式, 您可以套用屬性, 以更清楚地定義引數或傳回值可能`null`的時機。</span><span class="sxs-lookup"><span data-stu-id="b0955-177">For those cases, and other common patterns, you can apply attributes to more clearly define when an argument or return value may be `null`.</span></span> <span data-ttu-id="b0955-178">無論您是否考慮變更 API 的介面, 您可能會發現單獨的類型注釋並不足以描述`null`引數或傳回值的值。</span><span class="sxs-lookup"><span data-stu-id="b0955-178">Whether or not you consider changing the surface of your API, you'll likely find that type annotations alone aren't sufficient for describing `null` values for arguments or return values.</span></span> <span data-ttu-id="b0955-179">在這些情況下, 您可以套用屬性, 以更清楚地描述 API。</span><span class="sxs-lookup"><span data-stu-id="b0955-179">In those instances, you can apply attributes to more clearly describe an API.</span></span> 

## <a name="attributes-extend-type-annotations"></a><span data-ttu-id="b0955-180">屬性擴充類型注釋</span><span class="sxs-lookup"><span data-stu-id="b0955-180">Attributes extend type annotations</span></span>

<span data-ttu-id="b0955-181">已經加入數個屬性, 以表達變數的 null 狀態的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b0955-181">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="b0955-182">您在8之前C#撰寫的所有程式碼, 都是 null 的參考型別*遺忘式*。</span><span class="sxs-lookup"><span data-stu-id="b0955-182">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="b0955-183">這表示任何參考型別變數都可以是 null, 但不需要 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="b0955-183">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="b0955-184">一旦您的程式碼*可為 null 感知*, 這些規則就會變更。</span><span class="sxs-lookup"><span data-stu-id="b0955-184">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="b0955-185">參考型別應該永遠不`null`會是值, 而且必須`null`先檢查可為 null 的參考型別, 然後再進行引用。</span><span class="sxs-lookup"><span data-stu-id="b0955-185">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="b0955-186">您的 api 規則可能會更複雜, 如您在`TryGetValue` API 案例中所見。</span><span class="sxs-lookup"><span data-stu-id="b0955-186">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="b0955-187">許多 Api 在變數可以或不是`null`時, 會有更複雜的規則。</span><span class="sxs-lookup"><span data-stu-id="b0955-187">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="b0955-188">在這些情況下, 您將使用下列其中一個屬性來表示這些規則:</span><span class="sxs-lookup"><span data-stu-id="b0955-188">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="b0955-189">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute):不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-189">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="b0955-190">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可為 null 的輸入引數絕對不應為 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-190">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="b0955-191">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute):不可為 null 的傳回值可以是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-191">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="b0955-192">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute):可為 null 的傳回值永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-192">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="b0955-193">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute):當傳回值符合`out`條件`ref`時, 不可為 null 或引數可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-193">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable `out` or `ref` argument may be null when the return value satisfies a condition.</span></span>
- <span data-ttu-id="b0955-194">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當傳回`out`值`ref`符合條件時, 可為 null 或引數不可以是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-194">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable `out` or `ref` argument may not be null when the return value satisfies a condition.</span></span>
- <span data-ttu-id="b0955-195">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入引數不是 null, 則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-195">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

<span data-ttu-id="b0955-196">上述描述是每個屬性的快速參考。</span><span class="sxs-lookup"><span data-stu-id="b0955-196">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="b0955-197">下一節將詳細說明行為和意義。</span><span class="sxs-lookup"><span data-stu-id="b0955-197">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="b0955-198">新增這些屬性可讓編譯器詳細說明您 API 的規則。</span><span class="sxs-lookup"><span data-stu-id="b0955-198">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="b0955-199">在可為 null 的已啟用內容中編譯呼叫程式碼時, 編譯器會在呼叫端違反這些規則時發出警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-199">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="b0955-200">這些屬性不會在您的執行上啟用額外的檢查。</span><span class="sxs-lookup"><span data-stu-id="b0955-200">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="b0955-201">指定前置條件`AllowNull` : 和`DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="b0955-201">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="b0955-202">請考慮永遠不會`null`傳回的讀取/寫入屬性, 因為它有合理的預設值。</span><span class="sxs-lookup"><span data-stu-id="b0955-202">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="b0955-203">當呼叫`null`端將它設定為預設值時, 會傳遞至 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="b0955-203">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="b0955-204">例如, 假設有一個訊息系統會要求聊天室中的螢幕名稱。</span><span class="sxs-lookup"><span data-stu-id="b0955-204">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="b0955-205">如果未提供, 系統會產生隨機名稱:</span><span class="sxs-lookup"><span data-stu-id="b0955-205">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

<span data-ttu-id="b0955-206">當您在可為 null 的遺忘式內容中編譯上述程式碼時, 一切都沒問題。</span><span class="sxs-lookup"><span data-stu-id="b0955-206">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="b0955-207">啟用可為 null 的`ScreenName`參考型別後, 屬性會變成不可為 null 的參考。</span><span class="sxs-lookup"><span data-stu-id="b0955-207">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="b0955-208">這對`get`存取子而言是正確的: `null`永遠不會傳回。</span><span class="sxs-lookup"><span data-stu-id="b0955-208">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="b0955-209">呼叫端不需要檢查傳回的屬性`null`。</span><span class="sxs-lookup"><span data-stu-id="b0955-209">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="b0955-210">但現在將屬性設定為`null`會產生警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-210">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="b0955-211">為了繼續支援這種類型的程式碼, 您可以將<xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType>屬性新增至屬性, 如下列程式碼所示:</span><span class="sxs-lookup"><span data-stu-id="b0955-211">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span> 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

<span data-ttu-id="b0955-212">您可能需要新增的`using` <xref:System.Diagnostics.CodeAnalysis>指示詞, 才能使用此和本文中討論的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="b0955-212">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="b0955-213">屬性會套用至屬性, 而不`set`是存取子。</span><span class="sxs-lookup"><span data-stu-id="b0955-213">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="b0955-214">屬性會指定*前置條件*, 而且只會套用至輸入。 `AllowNull`</span><span class="sxs-lookup"><span data-stu-id="b0955-214">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="b0955-215">`get`存取子具有傳回值, 但沒有輸入引數。</span><span class="sxs-lookup"><span data-stu-id="b0955-215">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="b0955-216">因此, `AllowNull`屬性只適用`set`于存取子。</span><span class="sxs-lookup"><span data-stu-id="b0955-216">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="b0955-217">上述範例示範在引數上加入`AllowNull`屬性時要尋找的內容:</span><span class="sxs-lookup"><span data-stu-id="b0955-217">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="b0955-218">該變數的一般合約是它不應該是`null`, 因此您需要不可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="b0955-218">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="b0955-219">雖然輸入變數`null`不是最常見的使用方式, 但還是有一些案例。</span><span class="sxs-lookup"><span data-stu-id="b0955-219">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="b0955-220">通常您需要屬性、 `in` `out`、和`ref`引數的這個屬性。</span><span class="sxs-lookup"><span data-stu-id="b0955-220">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="b0955-221">當變數通常不是 null 時, `null` 屬性是最佳選擇,但您必須允許做為前置條件。`AllowNull`</span><span class="sxs-lookup"><span data-stu-id="b0955-221">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="b0955-222">相較之下, 使用`DisallowNull`的案例如下:您可以使用這個屬性來指定可為 null 類型的輸入變數不應`null`為。</span><span class="sxs-lookup"><span data-stu-id="b0955-222">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable type shouldn't be `null`.</span></span> <span data-ttu-id="b0955-223">假設有一個屬性`null` , 其中是預設值, 但是用戶端只能將它設定為非 null 值。</span><span class="sxs-lookup"><span data-stu-id="b0955-223">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="b0955-224">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b0955-224">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="b0955-225">上述程式碼是表達設計`ReviewComment`的最佳方式, 可以是`null`, 但不能設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="b0955-225">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="b0955-226">一旦這段程式碼可為 null, 您就可以更清楚地將此概念<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>表達給呼叫者, 使用:</span><span class="sxs-lookup"><span data-stu-id="b0955-226">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="b0955-227">在可為 null 的內容`ReviewComment`中, `get`存取子可能會傳回`null`的預設值。</span><span class="sxs-lookup"><span data-stu-id="b0955-227">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="b0955-228">編譯器會警告您必須在存取之前先檢查它。</span><span class="sxs-lookup"><span data-stu-id="b0955-228">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="b0955-229">此外, 它也會警告呼叫端, 雖然呼叫端`null`不應該明確地將它設定`null`為。</span><span class="sxs-lookup"><span data-stu-id="b0955-229">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="b0955-230">屬性也會指定*前置條件*, 而不會影響`get`存取子。 `DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="b0955-230">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="b0955-231">當您觀察下列有關的`DisallowNull`特性時, 應該選擇使用屬性:</span><span class="sxs-lookup"><span data-stu-id="b0955-231">You should choose to use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="b0955-232">變數可能在核心`null`案例中, 通常是在第一次具現化時。</span><span class="sxs-lookup"><span data-stu-id="b0955-232">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="b0955-233">變數不應明確設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="b0955-233">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="b0955-234">這些情況在原本是*null 遺忘式*的程式碼中很常見。</span><span class="sxs-lookup"><span data-stu-id="b0955-234">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="b0955-235">這可能是在兩個不同的初始化作業中設定物件屬性。</span><span class="sxs-lookup"><span data-stu-id="b0955-235">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="b0955-236">這可能是某些屬性只有在一些非同步工作完成後才會設定。</span><span class="sxs-lookup"><span data-stu-id="b0955-236">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="b0955-237">`AllowNull` 和`DisallowNull`屬性可讓您指定變數上的前置條件可能不符合那些變數上的可為 null 注釋。</span><span class="sxs-lookup"><span data-stu-id="b0955-237">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="b0955-238">這些會提供 API 特性的更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b0955-238">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="b0955-239">此額外資訊可協助呼叫者正確地使用您的 API。</span><span class="sxs-lookup"><span data-stu-id="b0955-239">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="b0955-240">請記住, 您可以使用下列屬性來指定前置條件:</span><span class="sxs-lookup"><span data-stu-id="b0955-240">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="b0955-241">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute):不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-241">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="b0955-242">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可為 null 的輸入引數絕對不應為 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-242">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="b0955-243">指定後置條件: `MaybeNull`和`NotNull`</span><span class="sxs-lookup"><span data-stu-id="b0955-243">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="b0955-244">假設您有一個具有下列簽章的方法:</span><span class="sxs-lookup"><span data-stu-id="b0955-244">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="b0955-245">在找不到所尋找的名稱`null`時, 您可能會撰寫如下所示的方法來傳回。</span><span class="sxs-lookup"><span data-stu-id="b0955-245">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="b0955-246">`null`顯然會指出找不到記錄。</span><span class="sxs-lookup"><span data-stu-id="b0955-246">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="b0955-247">在此範例中, 您可能會將傳回型別`Customer`從`Customer?`變更為。</span><span class="sxs-lookup"><span data-stu-id="b0955-247">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="b0955-248">將傳回值宣告為可為 null 的參考型別, 可以清楚地指定這個 API 的意圖。</span><span class="sxs-lookup"><span data-stu-id="b0955-248">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span> 

<span data-ttu-id="b0955-249">基於[泛型定義和 null](#generic-definitions-and-nullability)屬性所涵蓋的原因, 這項技術無法與泛型方法搭配使用。</span><span class="sxs-lookup"><span data-stu-id="b0955-249">For reasons covered under [Generic definitions and nullability](#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="b0955-250">您的泛型方法可能會遵循類似的模式:</span><span class="sxs-lookup"><span data-stu-id="b0955-250">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="b0955-251">您無法指定傳回值為`T?`。</span><span class="sxs-lookup"><span data-stu-id="b0955-251">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="b0955-252">找不到`null`尋找的專案時, 方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="b0955-252">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="b0955-253">因為您無法`T?`宣告傳回型別, 所以您會`MaybeNull`將注釋加入至方法傳回:</span><span class="sxs-lookup"><span data-stu-id="b0955-253">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="b0955-254">上述程式碼會通知呼叫者, 合約隱含了不可為 null 的型別, 但傳回值實際上*可能*是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-254">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="b0955-255">當您的 API 應該是不可為 null 的型別 (通常是泛型型別參數) 時, 請使用`null` 屬性,但可能會傳回實例。`MaybeNull`</span><span class="sxs-lookup"><span data-stu-id="b0955-255">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="b0955-256">您也可以指定傳回值或`out`或`ref`引數不是 null, 即使該類型是可為 null 的類型也一樣。</span><span class="sxs-lookup"><span data-stu-id="b0955-256">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable type.</span></span> <span data-ttu-id="b0955-257">假設有一個方法可確保陣列夠大, 足以容納多個元素。</span><span class="sxs-lookup"><span data-stu-id="b0955-257">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="b0955-258">如果輸入引數沒有容量, 常式會配置新的陣列, 並將所有現有的元素複製到其中。</span><span class="sxs-lookup"><span data-stu-id="b0955-258">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="b0955-259">如果輸入引數為`null`, 則常式會配置新的儲存區。</span><span class="sxs-lookup"><span data-stu-id="b0955-259">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="b0955-260">如果有足夠的容量, 常式不會執行任何動作:</span><span class="sxs-lookup"><span data-stu-id="b0955-260">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="b0955-261">您可以呼叫此常式, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="b0955-261">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="b0955-262">啟用 null 參考型別之後, 您想要確保先前的程式碼會編譯而不會出現警告。</span><span class="sxs-lookup"><span data-stu-id="b0955-262">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="b0955-263">當此方法傳回時, `storage`會保證引數不是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-263">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="b0955-264">不過, 您可以使用 null 參考`EnsureCapacity`來呼叫。</span><span class="sxs-lookup"><span data-stu-id="b0955-264">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="b0955-265">您可以建立`storage`可為 null 的參考型別, `NotNull`並將後續條件新增至參數宣告:</span><span class="sxs-lookup"><span data-stu-id="b0955-265">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

<span data-ttu-id="b0955-266">上述程式碼非常清楚地表示現有的合約:呼叫端可以傳遞`null`值為的變數, 但傳回值保證永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-266">The preceding code expresses the existing contract very clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="b0955-267">屬性最適用于`ref`和`out`引數, 其中`null`可當做引數傳遞, 但當方法傳回時, 該引數保證不會是 null。 `NotNull`</span><span class="sxs-lookup"><span data-stu-id="b0955-267">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="b0955-268">您可以使用下列屬性來指定無條件的後置條件:</span><span class="sxs-lookup"><span data-stu-id="b0955-268">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="b0955-269">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute):不可為 null 的傳回值可以是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-269">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="b0955-270">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute):可為 null 的傳回值永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-270">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-and-maybenullwhen"></a><span data-ttu-id="b0955-271">指定條件式後置條件`NotNullWhen` : 和`MaybeNullWhen`</span><span class="sxs-lookup"><span data-stu-id="b0955-271">Specify conditional post-conditions: `NotNullWhen` and `MaybeNullWhen`</span></span>

<span data-ttu-id="b0955-272">您很可能已經熟悉`string`方法。 <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b0955-272">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="b0955-273">`true`當引數不是 null, 而不是空字串時, 這個方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="b0955-273">This method returns `true` when the argument isn't null, and not the empty string.</span></span> <span data-ttu-id="b0955-274">這是一種 null 檢查的形式:如果方法`false`傳回, 則呼叫端不需要 null 檢查引數。</span><span class="sxs-lookup"><span data-stu-id="b0955-274">It is a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="b0955-275">若要讓方法類似于可為 null 的感知, 您可以將引數設定為可為 null `NotNullWhen`的型別, 並新增屬性:</span><span class="sxs-lookup"><span data-stu-id="b0955-275">To make a method like this nullable aware, you'd set the argument to a nullable type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

<span data-ttu-id="b0955-276">這會通知編譯器, 傳回值所`false`需的任何程式碼都不能以 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="b0955-276">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="b0955-277">新增屬性會通知編譯器`IsNullOrEmpty`執行必要 null 檢查的靜態分析: 傳回時`false`, 輸入引數不`null`是。</span><span class="sxs-lookup"><span data-stu-id="b0955-277">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="b0955-278"><xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>方法將會針對 .net Core 3.0 標注為如上所示。</span><span class="sxs-lookup"><span data-stu-id="b0955-278">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="b0955-279">您的程式碼基底中可能會有類似的方法, 可檢查物件的狀態是否為 null 值。</span><span class="sxs-lookup"><span data-stu-id="b0955-279">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="b0955-280">編譯器不會辨識自訂的 null 檢查方法, 您必須自行新增批註。</span><span class="sxs-lookup"><span data-stu-id="b0955-280">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="b0955-281">當您新增屬性時, 編譯器的靜態分析會知道已檢查過測試的變數何時已進行 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-281">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="b0955-282">這些屬性的另一個用法是`Try*`模式。</span><span class="sxs-lookup"><span data-stu-id="b0955-282">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="b0955-283">`ref` 和`out`變數的後置條件會透過傳回值進行通訊。</span><span class="sxs-lookup"><span data-stu-id="b0955-283">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="b0955-284">請考慮稍早所示的這個方法:</span><span class="sxs-lookup"><span data-stu-id="b0955-284">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="b0955-285">上述方法會遵循一般的 .net 用法: 傳回值會指出`message`是否設定為找到的值, 或如果找不到任何訊息, 則為預設值。</span><span class="sxs-lookup"><span data-stu-id="b0955-285">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="b0955-286">如果方法`true`傳回, 的`message`值不是 null, 否則, 方法會將設定`message`為 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-286">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="b0955-287">您可以使用`NotNullWhen`屬性來傳達該用法。</span><span class="sxs-lookup"><span data-stu-id="b0955-287">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="b0955-288">當您更新可為 null 之參考型別的簽`message`章`string?`時, 請建立並加入屬性:</span><span class="sxs-lookup"><span data-stu-id="b0955-288">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="b0955-289">在上述範例中, `message` `true`當傳回時`TryGetMessage` , 的值已知為 not null。</span><span class="sxs-lookup"><span data-stu-id="b0955-289">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="b0955-290">您應該以相同的方式, 在程式碼基底中標注類似的方法`null`: 引數可能是, 而`true`方法傳回時已知為 not null。</span><span class="sxs-lookup"><span data-stu-id="b0955-290">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="b0955-291">還有一個您可能也需要的最終屬性。</span><span class="sxs-lookup"><span data-stu-id="b0955-291">There's one final attribute you may also need.</span></span> <span data-ttu-id="b0955-292">有時傳回值的 null 狀態會視一或多個輸入引數的 null 狀態而定。</span><span class="sxs-lookup"><span data-stu-id="b0955-292">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="b0955-293">每當特定輸入引數不是`null`時, 這些方法會傳回非 null 值。</span><span class="sxs-lookup"><span data-stu-id="b0955-293">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="b0955-294">若要正確地為這些方法加上`NotNullIfNotNull`批註, 您可以使用屬性。</span><span class="sxs-lookup"><span data-stu-id="b0955-294">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="b0955-295">請考慮下列方法:</span><span class="sxs-lookup"><span data-stu-id="b0955-295">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="b0955-296">如果引數不是 null, 輸出就`null`不會。 `url`</span><span class="sxs-lookup"><span data-stu-id="b0955-296">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="b0955-297">啟用可為 null 的參考後, 如果您的 API 永遠不接受 null 輸入, 則該簽章會正常運作。</span><span class="sxs-lookup"><span data-stu-id="b0955-297">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="b0955-298">不過, 如果輸入可以是 null, 則傳回值也可以是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-298">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="b0955-299">因此, 您可以將簽章變更為下列程式碼:</span><span class="sxs-lookup"><span data-stu-id="b0955-299">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="b0955-300">這也可行, 但是通常會強制呼叫者執行額外`null`的檢查。</span><span class="sxs-lookup"><span data-stu-id="b0955-300">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="b0955-301">合約是`null`只有當輸入引數`url`為`null`時, 傳回值才會是。</span><span class="sxs-lookup"><span data-stu-id="b0955-301">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="b0955-302">若要表達該合約, 您可以標注此方法, 如下列程式碼所示:</span><span class="sxs-lookup"><span data-stu-id="b0955-302">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="b0955-303">傳回值和引數都已使用`?`標注, 表示可能是。 `null`</span><span class="sxs-lookup"><span data-stu-id="b0955-303">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="b0955-304">屬性會進一步說明當`url`引數不`null`是時, 傳回值不會是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-304">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="b0955-305">您可以使用下列屬性來指定條件性後置條件:</span><span class="sxs-lookup"><span data-stu-id="b0955-305">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="b0955-306">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute):當傳回值符合`out`條件`ref`時, 不可為 null 或引數可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-306">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable `out` or `ref` argument may be null when the return value satisfies a condition.</span></span>
- <span data-ttu-id="b0955-307">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當傳回`out`值`ref`符合條件時, 可為 null 或引數不可以是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-307">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable `out` or `ref` argument may not be null when the return value satisfies a condition.</span></span>
- <span data-ttu-id="b0955-308">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入引數不是 null, 則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-308">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="generic-definitions-and-nullability"></a><span data-ttu-id="b0955-309">泛型定義和 null 屬性</span><span class="sxs-lookup"><span data-stu-id="b0955-309">Generic definitions and nullability</span></span>

<span data-ttu-id="b0955-310">正確地傳達泛型型別和泛型方法的 null 狀態需要特別小心。</span><span class="sxs-lookup"><span data-stu-id="b0955-310">Correctly communicating the null state of generic types and generic methods requires special care.</span></span> <span data-ttu-id="b0955-311">這源自于可為 null 的實值型別和可為 null 的參考型別, 基本上是不同的事實。</span><span class="sxs-lookup"><span data-stu-id="b0955-311">This stems from the fact that a nullable value type and a nullable reference type are fundamentally different.</span></span> <span data-ttu-id="b0955-312">是的`string?`同義字, 而則是`string`由編譯器新增的屬性。 `Nullable<int>` `int?`</span><span class="sxs-lookup"><span data-stu-id="b0955-312">An `int?` is a synonym for `Nullable<int>`, whereas `string?` is `string` with an attribute added by the compiler.</span></span> <span data-ttu-id="b0955-313">結果是, 編譯器無法產生的正確`T?`程式碼, 而不`T`知道是`class`或`struct`。</span><span class="sxs-lookup"><span data-stu-id="b0955-313">The result is that the compiler can't generate correct code for `T?` without knowing if `T` is a `class` or a `struct`.</span></span> 

<span data-ttu-id="b0955-314">這並不表示您無法使用可為 null 的類型 (實數值型別或參考型別) 做為封閉式泛型型別的類型引數。</span><span class="sxs-lookup"><span data-stu-id="b0955-314">This doesn't mean you can't use a nullable type (either value type or reference type) as the type argument for a closed generic type.</span></span> <span data-ttu-id="b0955-315">和都是的`List<T>`有效具現化。 `List<int?>` `List<string?>`</span><span class="sxs-lookup"><span data-stu-id="b0955-315">Both `List<string?>` and `List<int?>` are valid instantiations of `List<T>`.</span></span> 

<span data-ttu-id="b0955-316">它的意思是, 您無法在沒有`T?`條件約束的泛型類別或方法宣告中使用。</span><span class="sxs-lookup"><span data-stu-id="b0955-316">What it does mean is that you can't use `T?` in a generic class or method declaration without constraints.</span></span> <span data-ttu-id="b0955-317">例如, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType>不會變更`T?`為傳回。</span><span class="sxs-lookup"><span data-stu-id="b0955-317">For example, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> won't be changed to return `T?`.</span></span> <span data-ttu-id="b0955-318">您可以藉由新增`struct`或`class`條件約束來克服這項限制。</span><span class="sxs-lookup"><span data-stu-id="b0955-318">You can overcome this limitation by adding either the `struct` or `class` constraint.</span></span> <span data-ttu-id="b0955-319">使用上述任一條件約束時, 編譯器會知道如何為`T`和`T?`產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0955-319">With either of those constraints, the compiler knows how to generate code for both `T` and `T?`.</span></span>

<span data-ttu-id="b0955-320">您可能想要將泛型型別引數所使用的類型限制為不可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="b0955-320">You may want to restrict the types used for a generic type argument to be non-nullable types.</span></span> <span data-ttu-id="b0955-321">您可以在該型別自`notnull`變數上加入條件約束來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="b0955-321">You can do that by adding the `notnull` constraint on that type argument.</span></span> <span data-ttu-id="b0955-322">套用該條件約束時, 類型引數不能是可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="b0955-322">When that constraint is applied, the type argument must not be a nullable type.</span></span>

## <a name="conclusions"></a><span data-ttu-id="b0955-323">結論</span><span class="sxs-lookup"><span data-stu-id="b0955-323">Conclusions</span></span>

<span data-ttu-id="b0955-324">加入可為 null 的參考型別會`null`提供初始詞彙, 以描述您的 api 對可能的變數的期望。</span><span class="sxs-lookup"><span data-stu-id="b0955-324">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="b0955-325">其他屬性會提供更豐富的詞彙, 將變數的 null 狀態原因為前置條件和後置條件。</span><span class="sxs-lookup"><span data-stu-id="b0955-325">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="b0955-326">這些屬性會更清楚地描述您的期望, 並為使用您 Api 的開發人員提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="b0955-326">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="b0955-327">當您更新可為 null 內容的程式庫時, 請新增這些屬性以引導 Api 的使用者使用正確的用法。</span><span class="sxs-lookup"><span data-stu-id="b0955-327">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="b0955-328">這些屬性可協助您完整描述輸入引數和傳回值的 null 狀態:</span><span class="sxs-lookup"><span data-stu-id="b0955-328">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="b0955-329">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute):不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-329">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="b0955-330">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可為 null 的輸入引數絕對不應為 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-330">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="b0955-331">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute):不可為 null 的傳回值可以是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-331">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="b0955-332">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute):可為 null 的傳回值永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-332">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="b0955-333">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute):當傳回值符合`out`條件`ref`時, 不可為 null 或引數可能會是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-333">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable `out` or `ref` argument may be null when the return value satisfies a condition.</span></span>
- <span data-ttu-id="b0955-334">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當傳回`out`值`ref`符合條件時, 可為 null 或引數不可以是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-334">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable `out` or `ref` argument may not be null when the return value satisfies a condition.</span></span>
- <span data-ttu-id="b0955-335">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入引數不是 null, 則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="b0955-335">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
