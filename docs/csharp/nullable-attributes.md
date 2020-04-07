---
title: 使用定義對空值的預期的屬性升級可空引用類型的 API
description: 瞭解如何使用描述性屬性「允許無效」、可能無效、無虛無等來完全描述 API 的空狀態。
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5d7a864ba1b66ad6b4ae7b0391d170a29147c537
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805840"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a><span data-ttu-id="4788e-103">更新函式庫以使用空引言類型,並將無效規則傳達給呼叫者</span><span class="sxs-lookup"><span data-stu-id="4788e-103">Update libraries to use nullable reference types and communicate nullable rules to callers</span></span>

<span data-ttu-id="4788e-104">新增[可取消的引用類型](nullable-references.md)意味著您`null`可以聲明 是否允許或預期每個變數的值。</span><span class="sxs-lookup"><span data-stu-id="4788e-104">The addition of [nullable reference types](nullable-references.md) means you can declare whether or not a `null` value is allowed or expected for every variable.</span></span> <span data-ttu-id="4788e-105">此外`AllowNull`,還可以應用許多屬性: `DisallowNull` `MaybeNull`、 `NotNull` `NotNullWhen`、 `MaybeNullWhen` `NotNullIfNotNull` 、 、 、 、 、 、 、 、 、 、 、 和, 並完全描述參數和返回值的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="4788e-105">In addition, you can apply a number of attributes: `AllowNull`, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull` to completely describe the null states of argument and return values.</span></span> <span data-ttu-id="4788e-106">在編寫代碼時,這提供了很好的體驗。</span><span class="sxs-lookup"><span data-stu-id="4788e-106">That provides a great experience as you write code.</span></span> <span data-ttu-id="4788e-107">如果非空變數可能設置為`null`,則會收到警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-107">You get warnings if a non-nullable variable might be set to `null`.</span></span> <span data-ttu-id="4788e-108">如果在取消引用之前未選中空變數,則會收到警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-108">You get warnings if a nullable variable isn't null-checked before you dereference it.</span></span> <span data-ttu-id="4788e-109">更新庫可能需要一些時間,但回報是值得的。</span><span class="sxs-lookup"><span data-stu-id="4788e-109">Updating your libraries can take time, but the payoffs are worth it.</span></span> <span data-ttu-id="4788e-110">您向編譯器提供的關於*何時*允許`null`或禁止 值的資訊越多,API 使用者得到的更好警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-110">The more information you provide to the compiler about *when* a `null` value is allowed or prohibited, the better warnings users of your API will get.</span></span> <span data-ttu-id="4788e-111">讓我們從一個熟悉的例子開始。</span><span class="sxs-lookup"><span data-stu-id="4788e-111">Let's start with a familiar example.</span></span> <span data-ttu-id="4788e-112">假設您的函式庫有以下 API 來檢索資源字串:</span><span class="sxs-lookup"><span data-stu-id="4788e-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="4788e-113">前面的範例遵循 .NET`Try*`中熟悉的模式。</span><span class="sxs-lookup"><span data-stu-id="4788e-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="4788e-114">此 API 有兩個引用`key`參數:`message`與 參數 。</span><span class="sxs-lookup"><span data-stu-id="4788e-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="4788e-115">此 API 有以下與這些參數的不合法的規則:</span><span class="sxs-lookup"><span data-stu-id="4788e-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="4788e-116">調用方不應作為`null``key`的參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="4788e-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="4788e-117">調用方可以傳遞其值為`null``message`的變數作為 的 參數。</span><span class="sxs-lookup"><span data-stu-id="4788e-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="4788e-118">如果`TryGetMessage`方法`true`返回`message`,則 的值不為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="4788e-119">如果傳回值`false,``message`為 (及其 null 狀態) 的值為 null。</span><span class="sxs-lookup"><span data-stu-id="4788e-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="4788e-120">的規則`key`可以通過變數類型完全表示`key`: 應該是一個不可空的引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-120">The rule for `key` can be completely expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="4788e-121">參數`message`更為複雜。</span><span class="sxs-lookup"><span data-stu-id="4788e-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="4788e-122">它允許`null`作為參數,但保證,在成功時,`out`該 參數不為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="4788e-123">對於這些方案,您需要更豐富的詞彙來描述期望值。</span><span class="sxs-lookup"><span data-stu-id="4788e-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="4788e-124">更新庫以進行空引用需要的不僅僅是灑`?`灑某些變數和類型名稱。</span><span class="sxs-lookup"><span data-stu-id="4788e-124">Updating your library for nullable references requires more than sprinkling `?` on some of the variables and type names.</span></span> <span data-ttu-id="4788e-125">前面的範例表明,您需要檢查 API 並考慮您對每個輸入參數的期望。</span><span class="sxs-lookup"><span data-stu-id="4788e-125">The preceding example shows that you need to examine your APIs and consider your expectations for each input argument.</span></span> <span data-ttu-id="4788e-126">考慮返回值的保證,以及方法返回時`out`的`ref`任何 或參數。</span><span class="sxs-lookup"><span data-stu-id="4788e-126">Consider the guarantees for the return value, and any `out` or `ref` arguments upon the method's return.</span></span> <span data-ttu-id="4788e-127">然後,將這些規則傳達給編譯器,當調用方不遵守這些規則時,編譯器將提供警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-127">Then communicate those rules to the compiler, and the compiler will provide warnings when callers don't abide by those rules.</span></span>

<span data-ttu-id="4788e-128">這項工作需要時間。</span><span class="sxs-lookup"><span data-stu-id="4788e-128">This work takes time.</span></span> <span data-ttu-id="4788e-129">讓我們從使庫或應用程式具有空感知性的策略開始,同時平衡其他要求和可交付成果。</span><span class="sxs-lookup"><span data-stu-id="4788e-129">Let's start with strategies to make your library or application nullable-aware, while balancing other requirements and deliverables.</span></span> <span data-ttu-id="4788e-130">您將看到如何平衡支援空引用類型的持續開發。</span><span class="sxs-lookup"><span data-stu-id="4788e-130">You'll see how to balance ongoing development enabling nullable reference types.</span></span> <span data-ttu-id="4788e-131">您將瞭解泛型類型定義的挑戰。</span><span class="sxs-lookup"><span data-stu-id="4788e-131">You'll learn challenges for generic type definitions.</span></span> <span data-ttu-id="4788e-132">您將學習應用屬性來描述單個 API 的預置和後置條件。</span><span class="sxs-lookup"><span data-stu-id="4788e-132">You'll learn to apply attributes to describe pre- and post-conditions on individual APIs.</span></span>

## <a name="choose-a-strategy-for-nullable-reference-types"></a><span data-ttu-id="4788e-133">選擇空白的引言型態</span><span class="sxs-lookup"><span data-stu-id="4788e-133">Choose a strategy for nullable reference types</span></span>

<span data-ttu-id="4788e-134">第一種選擇是預設是可空引用類型應打開還是關閉。</span><span class="sxs-lookup"><span data-stu-id="4788e-134">The first choice is whether nullable reference types should be on or off by default.</span></span> <span data-ttu-id="4788e-135">您有兩種策略:</span><span class="sxs-lookup"><span data-stu-id="4788e-135">You have two strategies:</span></span>

- <span data-ttu-id="4788e-136">為整個項目啟用空引用類型,並在未準備好的代碼中禁用它。</span><span class="sxs-lookup"><span data-stu-id="4788e-136">Enable nullable reference types for the entire project, and disable it in code that's not ready.</span></span>
- <span data-ttu-id="4788e-137">僅為已為空引用類型提供已註明的代碼的可啟用引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-137">Only enable nullable reference types for code that's been annotated for nullable reference types.</span></span>

<span data-ttu-id="4788e-138">當您為庫更新其他要素以進行空引用類型更新時,第一個策略效果最佳。</span><span class="sxs-lookup"><span data-stu-id="4788e-138">The first strategy works best when you're adding other features to the library as you update it for nullable reference types.</span></span> <span data-ttu-id="4788e-139">所有新開發都是空意識的。</span><span class="sxs-lookup"><span data-stu-id="4788e-139">All new development is nullable aware.</span></span> <span data-ttu-id="4788e-140">更新現有代碼時,在這些類中啟用空引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-140">As you update existing code, you enable nullable reference types in those classes.</span></span>

<span data-ttu-id="4788e-141">遵循第一個策略,執行以下操作:</span><span class="sxs-lookup"><span data-stu-id="4788e-141">Following this first strategy, you do the following:</span></span>

1. <span data-ttu-id="4788e-142">通過將元素添加到`<Nullable>enable</Nullable>`*csproj*檔,為整個項目啟用可無效的引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-142">Enable nullable reference types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="4788e-143">將`#nullable disable`實用方案添加到專案中的每個源檔。</span><span class="sxs-lookup"><span data-stu-id="4788e-143">Add the `#nullable disable` pragma to every source file in your project.</span></span>
1. <span data-ttu-id="4788e-144">處理每個檔時,請刪除雜注並解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-144">As you work on each file, remove the pragma and address any warnings.</span></span>

<span data-ttu-id="4788e-145">第一個策略具有更多的前期工作,以將實用處理添加到每個檔。</span><span class="sxs-lookup"><span data-stu-id="4788e-145">This first strategy has more up-front work to add the pragma to every file.</span></span> <span data-ttu-id="4788e-146">優點是,添加到專案的每個新代碼檔都將為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-146">The advantage is that every new code file added to the project will be nullable enabled.</span></span> <span data-ttu-id="4788e-147">任何新工作都將是可撤銷的;只能更新現有代碼。</span><span class="sxs-lookup"><span data-stu-id="4788e-147">Any new work will be nullable aware; only existing code must be updated.</span></span>

<span data-ttu-id="4788e-148">如果庫總體穩定,第二種策略效果更好,開發的重點是採用可無引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-148">The second strategy works better if the library is generally stable, and the main focus of the development is to adopt nullable reference types.</span></span> <span data-ttu-id="4788e-149">在對 API 進行編號時,打開可取消的引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-149">You turn on nullable reference types as you annotate APIs.</span></span> <span data-ttu-id="4788e-150">完成後,將對整個項目啟用空引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-150">When you've finished, you enable nullable reference types for the entire project.</span></span>

<span data-ttu-id="4788e-151">遵循第二個策略,您可以執行以下操作:</span><span class="sxs-lookup"><span data-stu-id="4788e-151">Following this second strategy you do the following:</span></span>

1. <span data-ttu-id="4788e-152">將`#nullable enable`雜注添加到要使空感知的檔中。</span><span class="sxs-lookup"><span data-stu-id="4788e-152">Add the `#nullable enable` pragma to the file you want to make nullable aware.</span></span>
1. <span data-ttu-id="4788e-153">解決任何警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-153">Address any warnings.</span></span>
1. <span data-ttu-id="4788e-154">繼續前兩個步驟,直到使整個庫都為空所知。</span><span class="sxs-lookup"><span data-stu-id="4788e-154">Continue these first two steps until you've made the entire library nullable aware.</span></span>
1. <span data-ttu-id="4788e-155">通過將元素添加到`<Nullable>enable</Nullable>`*csproj*檔,為整個項目啟用可無效的類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-155">Enable nullable types for the entire project by adding the `<Nullable>enable</Nullable>` element to your *csproj* files.</span></span>
1. <span data-ttu-id="4788e-156">刪除`#nullable enable`雜注,因為它們不再需要。</span><span class="sxs-lookup"><span data-stu-id="4788e-156">Remove the `#nullable enable` pragmas, as they're no longer needed.</span></span>

<span data-ttu-id="4788e-157">第二種戰略前期工作較少。</span><span class="sxs-lookup"><span data-stu-id="4788e-157">This second strategy has less work up-front.</span></span> <span data-ttu-id="4788e-158">權衡是,創建新檔時的第一個任務是添加雜注並使之無效。</span><span class="sxs-lookup"><span data-stu-id="4788e-158">The tradeoff is that the first task when you create a new file is to add the pragma and make it nullable aware.</span></span> <span data-ttu-id="4788e-159">如果團隊中的任何開發人員忘記了該新代碼,則新代碼現在處於工作積壓中,以使所有代碼都為空所知。</span><span class="sxs-lookup"><span data-stu-id="4788e-159">If any developers on your team forget, that new code is now in the backlog of work to make all code nullable aware.</span></span>

<span data-ttu-id="4788e-160">您選擇哪些策略取決於專案中正在進行多少主動開發。</span><span class="sxs-lookup"><span data-stu-id="4788e-160">Which of these strategies you pick depends on how much active development is taking place in your project.</span></span> <span data-ttu-id="4788e-161">專案越成熟、越穩定,第二個策略越好。</span><span class="sxs-lookup"><span data-stu-id="4788e-161">The more mature and stable your project, the better the second strategy.</span></span> <span data-ttu-id="4788e-162">正在開發的功能越多,第一個策略越好。</span><span class="sxs-lookup"><span data-stu-id="4788e-162">The more features being developed, the better the first strategy.</span></span>

## <a name="should-nullable-warnings-introduce-breaking-changes"></a><span data-ttu-id="4788e-163">不合法警告是否應引入重大更改?</span><span class="sxs-lookup"><span data-stu-id="4788e-163">Should nullable warnings introduce breaking changes?</span></span>

<span data-ttu-id="4788e-164">開啟可取消參考型態之前,變數被被被被被*被被被被被被被被被被被被被被被被被被被被被被被被被被被被被被*</span><span class="sxs-lookup"><span data-stu-id="4788e-164">Before you enable nullable reference types, variables are considered *nullable oblivious*.</span></span> <span data-ttu-id="4788e-165">開啟空引引型態後,所有這些變數都是*非空的*。</span><span class="sxs-lookup"><span data-stu-id="4788e-165">Once you enable nullable reference types, all those variables are *non-nullable*.</span></span> <span data-ttu-id="4788e-166">如果這些變數未初始化為非空值,編譯器將發出警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-166">The compiler will issue warnings if those variables aren't initialized to non-null values.</span></span>

<span data-ttu-id="4788e-167">另一個可能的警告來源是在尚未初始化該值時返回值。</span><span class="sxs-lookup"><span data-stu-id="4788e-167">Another likely source of warnings is return values when the value hasn't been initialized.</span></span>

<span data-ttu-id="4788e-168">解決編譯器警告的第一步是對參數和返回類型`?`使用註釋來指示參數或返回值何時可能為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-168">The first step in addressing the compiler warnings is to use `?` annotations on parameter and return types to indicate when arguments or return values may be null.</span></span> <span data-ttu-id="4788e-169">當引用變數不能為空時,原始聲明是正確的。</span><span class="sxs-lookup"><span data-stu-id="4788e-169">When reference variables must not be null, the original declaration is correct.</span></span> <span data-ttu-id="4788e-170">執行此操作時,您的目標不僅僅是修復警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-170">As you do this, your goal isn't just to fix warnings.</span></span> <span data-ttu-id="4788e-171">更重要的目標是使編譯器瞭解您對於潛在空值的意圖。</span><span class="sxs-lookup"><span data-stu-id="4788e-171">The more important goal is to make the compiler understand your intent for potential null values.</span></span> <span data-ttu-id="4788e-172">在檢查警告時,您將得出庫的下一個重大決策。</span><span class="sxs-lookup"><span data-stu-id="4788e-172">As you examine the warnings, you reach your next major decision for your library.</span></span> <span data-ttu-id="4788e-173">是否要考慮修改 API 簽名以更清楚地傳達您的設計意圖?</span><span class="sxs-lookup"><span data-stu-id="4788e-173">Do you want to consider modifying API signatures to more clearly communicate your design intent?</span></span> <span data-ttu-id="4788e-174">前面檢查`TryGetMessage`的方法更好的 API 簽章可以是:</span><span class="sxs-lookup"><span data-stu-id="4788e-174">A better API signature for the `TryGetMessage` method examined earlier could be:</span></span>

```csharp
string? TryGetMessage(string key);
```

<span data-ttu-id="4788e-175">返回值指示成功或失敗,如果找到該值,則攜帶該值。</span><span class="sxs-lookup"><span data-stu-id="4788e-175">The return value indicates success or failure, and carries the value if the value was found.</span></span> <span data-ttu-id="4788e-176">在許多情況下,更改 API 簽名可以改進它們傳達空值的方式。</span><span class="sxs-lookup"><span data-stu-id="4788e-176">In many cases, changing API signatures can improve how they communicate null values.</span></span>

<span data-ttu-id="4788e-177">但是,對於公共圖書館或具有大型使用者群的庫,您可能不希望引入任何 API 簽名更改。</span><span class="sxs-lookup"><span data-stu-id="4788e-177">However, for public libraries, or libraries with large user bases, you may prefer not introducing any API signature changes.</span></span> <span data-ttu-id="4788e-178">對於這些情況和其他常見模式,可以將屬性應用於更明確地定義參數或返回值何時可能是`null`。</span><span class="sxs-lookup"><span data-stu-id="4788e-178">For those cases, and other common patterns, you can apply attributes to more clearly define when an argument or return value may be `null`.</span></span> <span data-ttu-id="4788e-179">無論您是否考慮更改 API 的表面,您都可能會發現,僅類型註釋`null`不足以描述 參數或返回值的值。</span><span class="sxs-lookup"><span data-stu-id="4788e-179">Whether or not you consider changing the surface of your API, you'll likely find that type annotations alone aren't sufficient for describing `null` values for arguments or return values.</span></span> <span data-ttu-id="4788e-180">在這些情況下,可以將屬性應用於更清晰地描述 API。</span><span class="sxs-lookup"><span data-stu-id="4788e-180">In those instances, you can apply attributes to more clearly describe an API.</span></span>

## <a name="attributes-extend-type-annotations"></a><span data-ttu-id="4788e-181">屬性延伸型態</span><span class="sxs-lookup"><span data-stu-id="4788e-181">Attributes extend type annotations</span></span>

<span data-ttu-id="4788e-182">添加了多個屬性以表示有關變數的 null 狀態的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="4788e-182">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="4788e-183">在 C# 8 引入可無引用類型之前編寫的所有代碼都是*無效的。*</span><span class="sxs-lookup"><span data-stu-id="4788e-183">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="4788e-184">這意味著任何引用類型變數可能為空,但不需要 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="4788e-184">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="4788e-185">一旦代碼*是空的,* 這些規則就會改變。</span><span class="sxs-lookup"><span data-stu-id="4788e-185">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="4788e-186">引用類型絕不應為`null`值,並且在取消引用之前必須`null`針對 選中可消除的引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-186">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="4788e-187">API 的規則可能更為複雜,正如您在 API 方案中所`TryGetValue`看到的那樣 。</span><span class="sxs-lookup"><span data-stu-id="4788e-187">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="4788e-188">許多 API 對於變數可以或不能`null`是 時,都有更複雜的規則。</span><span class="sxs-lookup"><span data-stu-id="4788e-188">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="4788e-189">在這些情況下,您將使用以下屬性之一來表示這些規則:</span><span class="sxs-lookup"><span data-stu-id="4788e-189">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="4788e-190">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-190">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="4788e-191">[禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-191">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="4788e-192">[可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。</span><span class="sxs-lookup"><span data-stu-id="4788e-192">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="4788e-193">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-193">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="4788e-194">[當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-194">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="4788e-195">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-195">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="4788e-196">[NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的參數不是 null,則返回值不為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-196">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>

<span data-ttu-id="4788e-197">前面的說明是每個屬性執行功能的快速引用。</span><span class="sxs-lookup"><span data-stu-id="4788e-197">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="4788e-198">以下各節更全面地描述行為和含義。</span><span class="sxs-lookup"><span data-stu-id="4788e-198">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="4788e-199">添加這些屬性為編譯器提供有關 API 規則的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4788e-199">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="4788e-200">在啟用空的上下文中編譯調用代碼時,編譯器將在調用方違反這些規則時發出警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-200">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="4788e-201">這些屬性無法對實現啟用其他檢查。</span><span class="sxs-lookup"><span data-stu-id="4788e-201">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="4788e-202">指定先決條件:`AllowNull`與`DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="4788e-202">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="4788e-203">請考慮從不返回`null`的讀/寫屬性,因為它具有合理的默認值。</span><span class="sxs-lookup"><span data-stu-id="4788e-203">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="4788e-204">將調用方`null`設置為該預設值時,將傳遞給集訪問器。</span><span class="sxs-lookup"><span data-stu-id="4788e-204">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="4788e-205">例如,考慮在聊天室中要求顯示螢幕名稱的郵件系統。</span><span class="sxs-lookup"><span data-stu-id="4788e-205">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="4788e-206">如果未提供,系統將產生隨機名稱:</span><span class="sxs-lookup"><span data-stu-id="4788e-206">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

<span data-ttu-id="4788e-207">當您在一個無效的遺忘上下文中編譯前面的代碼時,一切都很好。</span><span class="sxs-lookup"><span data-stu-id="4788e-207">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="4788e-208">啟用空引用類型後,該`ScreenName`屬性將成為不可取消的引用。</span><span class="sxs-lookup"><span data-stu-id="4788e-208">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="4788e-209">這對`get`存取者是正確的:它永遠不會`null`返回 。</span><span class="sxs-lookup"><span data-stu-id="4788e-209">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="4788e-210">調用方不需要檢查 返回的屬性`null`。</span><span class="sxs-lookup"><span data-stu-id="4788e-210">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="4788e-211">但現在將屬性設置為`null`生成警告。</span><span class="sxs-lookup"><span data-stu-id="4788e-211">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="4788e-212">為了繼續支援這種類型的代碼,將<xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType>屬性添加到屬性,如以下代碼所示:</span><span class="sxs-lookup"><span data-stu-id="4788e-212">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

<span data-ttu-id="4788e-213">您可能需要添加一個`using`指令,<xref:System.Diagnostics.CodeAnalysis>以便使用此屬性和本文中討論的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="4788e-213">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="4788e-214">該屬性應用於屬性,而不是`set`訪問器。</span><span class="sxs-lookup"><span data-stu-id="4788e-214">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="4788e-215">屬性`AllowNull`指定*先決條件*,並且僅適用於輸入。</span><span class="sxs-lookup"><span data-stu-id="4788e-215">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="4788e-216">`get`訪問器具有返回值,但沒有輸入參數。</span><span class="sxs-lookup"><span data-stu-id="4788e-216">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="4788e-217">因此,該`AllowNull`屬性僅適用於`set`訪問器。</span><span class="sxs-lookup"><span data-stu-id="4788e-217">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="4788e-218">前面的範例展示在參數上新增`AllowNull`屬性時要尋找的內容:</span><span class="sxs-lookup"><span data-stu-id="4788e-218">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="4788e-219">該變數的一般協定是,它不應該是`null`,因此您需要一個不可取消的引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-219">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="4788e-220">輸入變數有一些方案,`null`儘管它們不是最常見的用法。</span><span class="sxs-lookup"><span data-stu-id="4788e-220">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="4788e-221">通常,屬性或`in`或或`out`.`ref`和參數需要此屬性。</span><span class="sxs-lookup"><span data-stu-id="4788e-221">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="4788e-222">當`AllowNull`變數通常是非空的,但您需要作為先決條件允許`null`時,該屬性是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="4788e-222">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="4788e-223">與使用`DisallowNull`: 的機制相比,使用此屬性指定 null 引用類型的輸入變數`null`不應為 。</span><span class="sxs-lookup"><span data-stu-id="4788e-223">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="4788e-224">請考慮一個屬性`null`,其中是預設值,但用戶端只能將其設置為非 null 值。</span><span class="sxs-lookup"><span data-stu-id="4788e-224">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="4788e-225">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4788e-225">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="4788e-226">前面的代碼是表示設計的最佳方式,`ReviewComment`可以`null`是 ,但不能`null`設定為 。</span><span class="sxs-lookup"><span data-stu-id="4788e-226">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="4788e-227">一旦此代碼是空的,您可以使用 更清楚地向呼叫方表達這<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>一 概念:</span><span class="sxs-lookup"><span data-stu-id="4788e-227">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="4788e-228">在空中,`ReviewComment``get`存取器可以傳回`null`預設值 。</span><span class="sxs-lookup"><span data-stu-id="4788e-228">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="4788e-229">編譯器警告必須在訪問之前檢查它。</span><span class="sxs-lookup"><span data-stu-id="4788e-229">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="4788e-230">此外,它警告呼叫方,即使它可能是`null`,呼叫方也不應顯式將其設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="4788e-230">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="4788e-231">該`DisallowNull`屬性還指定*一個先決條件*,它`get`不會影響 訪問器。</span><span class="sxs-lookup"><span data-stu-id="4788e-231">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="4788e-232">當您觀察以下特徵時,`DisallowNull`應選擇使用該屬性:</span><span class="sxs-lookup"><span data-stu-id="4788e-232">You should choose to use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="4788e-233">變數可能`null`位於核心方案中,通常是在第一次實例化時。</span><span class="sxs-lookup"><span data-stu-id="4788e-233">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="4788e-234">變數不應顯示式設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="4788e-234">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="4788e-235">這些情況在最初*為空遺忘*的代碼中很常見。</span><span class="sxs-lookup"><span data-stu-id="4788e-235">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="4788e-236">可能是對象屬性設置在兩個不同的初始化操作中。</span><span class="sxs-lookup"><span data-stu-id="4788e-236">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="4788e-237">可能某些屬性僅在某些非同步工作完成後進行設置。</span><span class="sxs-lookup"><span data-stu-id="4788e-237">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="4788e-238">`AllowNull`和`DisallowNull`屬性使您能夠指定變數的先決條件可能與這些變數上的空註釋不匹配。</span><span class="sxs-lookup"><span data-stu-id="4788e-238">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="4788e-239">這些提供了有關 API 特徵的更多詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4788e-239">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="4788e-240">此附加資訊可幫助呼叫方正確使用API。</span><span class="sxs-lookup"><span data-stu-id="4788e-240">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="4788e-241">請記住,您使用以下屬性指定先決條件:</span><span class="sxs-lookup"><span data-stu-id="4788e-241">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="4788e-242">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-242">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="4788e-243">[禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-243">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="4788e-244">指定後條件:`MaybeNull`與`NotNull`</span><span class="sxs-lookup"><span data-stu-id="4788e-244">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="4788e-245">假設您有一個具有以下簽名的方法:</span><span class="sxs-lookup"><span data-stu-id="4788e-245">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="4788e-246">您可能已經編寫了這樣的方法,在未找到要`null`找的名稱時返回。</span><span class="sxs-lookup"><span data-stu-id="4788e-246">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="4788e-247">清楚地`null`指示找不到記錄。</span><span class="sxs-lookup"><span data-stu-id="4788e-247">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="4788e-248">這個選項, 可能會傳回類型從`Customer`變更為`Customer?`。</span><span class="sxs-lookup"><span data-stu-id="4788e-248">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="4788e-249">將返回值聲明為空引用類型明確指定此 API 的意圖。</span><span class="sxs-lookup"><span data-stu-id="4788e-249">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="4788e-250">由於[泛型定義和無效性](#generic-definitions-and-nullability)所涵蓋的原因,該技術不適用於泛型方法。</span><span class="sxs-lookup"><span data-stu-id="4788e-250">For reasons covered under [Generic definitions and nullability](#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="4788e-251">您可能有一個遵循類似模式的泛型方法:</span><span class="sxs-lookup"><span data-stu-id="4788e-251">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="4788e-252">無法指定傳回值`T?`為 。</span><span class="sxs-lookup"><span data-stu-id="4788e-252">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="4788e-253">當未找到`null`已請求的項時,該方法將返回。</span><span class="sxs-lookup"><span data-stu-id="4788e-253">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="4788e-254">由於無法聲明`T?`傳回類型,`MaybeNull`因此將註釋添加到方法傳回:</span><span class="sxs-lookup"><span data-stu-id="4788e-254">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="4788e-255">前面的代碼通知調用方協定意味著一種不可空的類型,但返回值*實際上可能*為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-255">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="4788e-256">當`MaybeNull`API 應為非空類型(通常是泛型類型參數),但可能存在`null`返回的 實例時,請使用該屬性。</span><span class="sxs-lookup"><span data-stu-id="4788e-256">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="4788e-257">還可以指定返回值或`out`或`ref`或參數 不為空,即使類型為空引用類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-257">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="4788e-258">考慮一種確保數組足夠大以容納多個元素的方法。</span><span class="sxs-lookup"><span data-stu-id="4788e-258">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="4788e-259">如果輸入參數沒有容量,例程將分配一個新陣組並將所有現有元素複製到其中。</span><span class="sxs-lookup"><span data-stu-id="4788e-259">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="4788e-260">如果輸入參數為`null`,例程將分配新的存儲。</span><span class="sxs-lookup"><span data-stu-id="4788e-260">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="4788e-261">如果容量充足,例程將不執行任何操作:</span><span class="sxs-lookup"><span data-stu-id="4788e-261">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="4788e-262">您可以按照以下方式呼叫此例程式:</span><span class="sxs-lookup"><span data-stu-id="4788e-262">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="4788e-263">開啟空引用類型後,您希望確保前面的代碼在無警告的情況下編譯。</span><span class="sxs-lookup"><span data-stu-id="4788e-263">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="4788e-264">當方法返回時,`storage`參數保證不為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-264">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="4788e-265">但是,使用空引用進行調用`EnsureCapacity`是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="4788e-265">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="4788e-266">您可以建立`storage`空白參考類型,並將`NotNull`後條件加入參數的聲明:</span><span class="sxs-lookup"><span data-stu-id="4788e-266">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

<span data-ttu-id="4788e-267">前面的代碼非常清楚地表示現有協定:調用方可以傳遞具有該值的`null`變數,但返回值保證永遠不會為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-267">The preceding code expresses the existing contract very clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="4788e-268">該`NotNull`屬性`ref`對於`out`和 參數`null`最有用, 其中可以作為參數傳遞,但當方法返回時,該參數保證不為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-268">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="4788e-269">使用以下屬性指定無條件的後情況:</span><span class="sxs-lookup"><span data-stu-id="4788e-269">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="4788e-270">[可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。</span><span class="sxs-lookup"><span data-stu-id="4788e-270">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="4788e-271">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-271">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="4788e-272">指定條件後條件: `NotNullWhen``MaybeNullWhen`、 與`NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="4788e-272">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="4788e-273">您可能熟悉這種方法`string`<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4788e-273">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="4788e-274">當參數為`true`空字串或空字串時,此方法將返回。</span><span class="sxs-lookup"><span data-stu-id="4788e-274">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="4788e-275">它是一種 null 檢查形式:如果`false`方法返回 ,調用方不需要對參數進行空檢查。</span><span class="sxs-lookup"><span data-stu-id="4788e-275">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="4788e-276">要使此類方法具有 null 感知,您需要將參數設定為可 null 引用類型`NotNullWhen`,並新增屬性 :</span><span class="sxs-lookup"><span data-stu-id="4788e-276">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

<span data-ttu-id="4788e-277">這通知編譯器不需要對返回值`false`的任何代碼進行空檢查。</span><span class="sxs-lookup"><span data-stu-id="4788e-277">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="4788e-278">屬性的新增通知編譯器的靜態分析,該`IsNullOrEmpty`分析執行必要的 null 檢查:`false`當它傳回`null`時,輸入參數不是 。</span><span class="sxs-lookup"><span data-stu-id="4788e-278">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="4788e-279">該方法<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>將如上所述.NET Core 3.0的用點子。</span><span class="sxs-lookup"><span data-stu-id="4788e-279">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="4788e-280">代碼庫中可能也有類似的方法,用於檢查物件的狀態為 null 值。</span><span class="sxs-lookup"><span data-stu-id="4788e-280">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="4788e-281">編譯器不會識別自定義 null 檢查方法,您需要自己添加註釋。</span><span class="sxs-lookup"><span data-stu-id="4788e-281">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="4788e-282">添加屬性時,編譯器的靜態分析知道測試變數何時被空檢查。</span><span class="sxs-lookup"><span data-stu-id="4788e-282">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="4788e-283">這些屬性的另一個用途是`Try*`模式。</span><span class="sxs-lookup"><span data-stu-id="4788e-283">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="4788e-284">和`out`變數的`ref`后情況通過返回值進行通信。</span><span class="sxs-lookup"><span data-stu-id="4788e-284">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="4788e-285">請考慮前面顯示的方法:</span><span class="sxs-lookup"><span data-stu-id="4788e-285">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="4788e-286">前面的方法遵循典型的 .NET 習慣用法:返回`message`值指示 是否設置為找到的值,或者如果沒有找到消息,則指示默認值。</span><span class="sxs-lookup"><span data-stu-id="4788e-286">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="4788e-287">如果方法返回`true`,則`message`的值 不為 null;如果 方法傳回 ,則值為 null。否則,該方法將設置`message`為null。</span><span class="sxs-lookup"><span data-stu-id="4788e-287">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="4788e-288">您可以使用`NotNullWhen`屬性來傳達該習慣用法。</span><span class="sxs-lookup"><span data-stu-id="4788e-288">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="4788e-289">更新可空引言型態的簽名時,`message``string?`請建立並新增屬性:</span><span class="sxs-lookup"><span data-stu-id="4788e-289">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="4788e-290">在前面的範例中,`message`當`TryGetMessage``true`傳回時,值已知不為 null。</span><span class="sxs-lookup"><span data-stu-id="4788e-290">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="4788e-291">應在代碼庫中以相同的方式對類似的方法進行編帶:當方法返回`null``true`時,參數可以是 ,並且已知為不為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-291">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="4788e-292">還有一個最終屬性,您可能還需要。</span><span class="sxs-lookup"><span data-stu-id="4788e-292">There's one final attribute you may also need.</span></span> <span data-ttu-id="4788e-293">有時,返回值的 null 狀態取決於一個或多個輸入參數的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="4788e-293">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="4788e-294">當某些輸入參數不是`null`時,這些方法將返回一個非空值。</span><span class="sxs-lookup"><span data-stu-id="4788e-294">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="4788e-295">要正確對這些方法進行給上用,請使用`NotNullIfNotNull`屬性 。</span><span class="sxs-lookup"><span data-stu-id="4788e-295">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="4788e-296">請考慮以下方法:</span><span class="sxs-lookup"><span data-stu-id="4788e-296">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="4788e-297">如果`url`參數不為空,則輸出`null`不是 。</span><span class="sxs-lookup"><span data-stu-id="4788e-297">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="4788e-298">啟用了可無效引用後,該簽名將正常工作,前提是 API 永遠不會接受空輸入。</span><span class="sxs-lookup"><span data-stu-id="4788e-298">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="4788e-299">但是,如果輸入可以為空,則返回值也可以為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-299">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="4788e-300">因此,您可以將簽名更改為以下代碼:</span><span class="sxs-lookup"><span data-stu-id="4788e-300">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="4788e-301">這也行得通,但通常會強制調用方實施額外的`null`檢查。</span><span class="sxs-lookup"><span data-stu-id="4788e-301">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="4788e-302">協定是返回值僅在輸入參數`null``url``null`為 時才。</span><span class="sxs-lookup"><span data-stu-id="4788e-302">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="4788e-303">要表示該協定,您需要對此方法進行編號,如以下代碼所示:</span><span class="sxs-lookup"><span data-stu-id="4788e-303">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="4788e-304">傳回值和參數都帶`?`有 指示,指示任一`null`可以是 。</span><span class="sxs-lookup"><span data-stu-id="4788e-304">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="4788e-305">該屬性進一步闡明,當參數不是`url``null`時,返回值不會為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-305">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="4788e-306">使用這些屬性指定條件後條件:</span><span class="sxs-lookup"><span data-stu-id="4788e-306">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="4788e-307">[當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-307">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="4788e-308">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-308">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="4788e-309">[NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入參數不是 null,則返回值不為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-309">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="generic-definitions-and-nullability"></a><span data-ttu-id="4788e-310">一般定義與空值</span><span class="sxs-lookup"><span data-stu-id="4788e-310">Generic definitions and nullability</span></span>

<span data-ttu-id="4788e-311">正確傳達泛型類型和泛型方法的 null 狀態需要特別注意。</span><span class="sxs-lookup"><span data-stu-id="4788e-311">Correctly communicating the null state of generic types and generic methods requires special care.</span></span> <span data-ttu-id="4788e-312">這是因為可 null 值類型和空引用類型根本不同。</span><span class="sxs-lookup"><span data-stu-id="4788e-312">This stems from the fact that a nullable value type and a nullable reference type are fundamentally different.</span></span> <span data-ttu-id="4788e-313">是 的`Nullable<int>`同 義詞`string?`,而與編譯`string`器添加 的屬性`int?`一起。</span><span class="sxs-lookup"><span data-stu-id="4788e-313">An `int?` is a synonym for `Nullable<int>`, whereas `string?` is `string` with an attribute added by the compiler.</span></span> <span data-ttu-id="4788e-314">`T?`結果是,如果不知道是`T``class`. 或 , 編譯器無法`struct`生成正確的代碼。</span><span class="sxs-lookup"><span data-stu-id="4788e-314">The result is that the compiler can't generate correct code for `T?` without knowing if `T` is a `class` or a `struct`.</span></span>

<span data-ttu-id="4788e-315">這並不意味著不能使用空類型(值類型或引用類型)作為閉合泛型的類型參數。</span><span class="sxs-lookup"><span data-stu-id="4788e-315">This doesn't mean you can't use a nullable type (either value type or reference type) as the type argument for a closed generic type.</span></span> <span data-ttu-id="4788e-316">和`List<string?>``List<int?>`都是`List<T>`的有效實例化。</span><span class="sxs-lookup"><span data-stu-id="4788e-316">Both `List<string?>` and `List<int?>` are valid instantiations of `List<T>`.</span></span>

<span data-ttu-id="4788e-317">它的意思是,在泛型類或方法聲明中,`T?`沒有約束,不能使用。</span><span class="sxs-lookup"><span data-stu-id="4788e-317">What it does mean is that you can't use `T?` in a generic class or method declaration without constraints.</span></span> <span data-ttu-id="4788e-318">例如,<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType>不會變更為`T?`傳回 。</span><span class="sxs-lookup"><span data-stu-id="4788e-318">For example, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> won't be changed to return `T?`.</span></span> <span data-ttu-id="4788e-319">您可以通過添加`struct``class`或約束來克服此限制。</span><span class="sxs-lookup"><span data-stu-id="4788e-319">You can overcome this limitation by adding either the `struct` or `class` constraint.</span></span> <span data-ttu-id="4788e-320">對於其中任一約束,編譯器知道如何為和`T``T?`生成代碼。</span><span class="sxs-lookup"><span data-stu-id="4788e-320">With either of those constraints, the compiler knows how to generate code for both `T` and `T?`.</span></span>

<span data-ttu-id="4788e-321">您可能希望將泛型類型參數使用的類型限制為非空類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-321">You may want to restrict the types used for a generic type argument to be non-nullable types.</span></span> <span data-ttu-id="4788e-322">可以通過添加該類型參數的`notnull`約束 來執行此操作。</span><span class="sxs-lookup"><span data-stu-id="4788e-322">You can do that by adding the `notnull` constraint on that type argument.</span></span> <span data-ttu-id="4788e-323">應用該約束時,類型參數不能為空類型。</span><span class="sxs-lookup"><span data-stu-id="4788e-323">When that constraint is applied, the type argument must not be a nullable type.</span></span>

## <a name="conclusions"></a><span data-ttu-id="4788e-324">結論</span><span class="sxs-lookup"><span data-stu-id="4788e-324">Conclusions</span></span>

<span data-ttu-id="4788e-325">添加可取消的引用類型提供了一個初始詞彙表來描述 API 對`null`可能為的變數的期望。</span><span class="sxs-lookup"><span data-stu-id="4788e-325">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="4788e-326">附加屬性提供了更豐富的詞彙,將變數的 null 狀態描述為先決條件和後條件。</span><span class="sxs-lookup"><span data-stu-id="4788e-326">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="4788e-327">這些屬性更清楚地描述了您的期望,並為使用 API 的開發人員提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="4788e-327">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="4788e-328">更新可無效上下文的庫時,請添加這些屬性以引導 API 的使用者使用正確的方法。</span><span class="sxs-lookup"><span data-stu-id="4788e-328">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="4788e-329">這些屬性可説明您完全描述輸入參數和傳回值的 null 狀態:</span><span class="sxs-lookup"><span data-stu-id="4788e-329">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="4788e-330">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-330">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="4788e-331">[禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-331">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="4788e-332">[可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。</span><span class="sxs-lookup"><span data-stu-id="4788e-332">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="4788e-333">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-333">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="4788e-334">[當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-334">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="4788e-335">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-335">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="4788e-336">[NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入參數不是 null,則返回值不為空。</span><span class="sxs-lookup"><span data-stu-id="4788e-336">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
