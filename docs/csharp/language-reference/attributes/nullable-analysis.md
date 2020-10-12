---
title: 'C # 保留屬性：可為 Null 的靜態分析'
ms.date: 04/14/2020
description: 編譯器會解讀這些屬性，以提供可為 null 且不可為 null 的參考型別的更佳靜態分析。
ms.openlocfilehash: 6678cd21de23d4ed391eff089e33939b5adff0fa
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955599"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a><span data-ttu-id="a9ee4-103">保留的屬性有助於編譯器的 null 狀態靜態分析</span><span class="sxs-lookup"><span data-stu-id="a9ee4-103">Reserved attributes contribute to the compiler's null state static analysis</span></span>

<span data-ttu-id="a9ee4-104">在可為 null 的內容中，編譯器會執行程式碼的靜態分析，以判斷所有參考型別變數的 null 狀態：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-104">In a nullable context, the compiler performs static analysis of code to determine the null state of all reference type variables:</span></span>

- <span data-ttu-id="a9ee4-105">*not null*：靜態分析會判斷變數是否已指派非 null 值。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-105">*not null*: Static analysis determines that a variable is assigned a non-null value.</span></span>
- <span data-ttu-id="a9ee4-106">*可能是 null*：靜態分析無法判斷變數是否已指派非 null 值。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-106">*maybe null*: Static analysis cannot determine that a variable is assigned a non-null value.</span></span>

<span data-ttu-id="a9ee4-107">您可以套用多個屬性，以提供有關 Api 之語義的資訊給編譯器。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-107">You can apply a number of attributes that provide information to the compiler about the semantics of your APIs.</span></span> <span data-ttu-id="a9ee4-108">這項資訊可協助編譯器執行靜態分析，並判斷變數是否為 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-108">That information helps the compiler perform static analysis and determine when a variable is not null.</span></span> <span data-ttu-id="a9ee4-109">本文提供每個屬性的簡短描述，以及如何使用這些屬性。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-109">This article provides a brief description of each of those attributes and how to use them.</span></span> <span data-ttu-id="a9ee4-110">所有範例都採用 c # 8.0 或更新版本，且程式碼位於可為 null 的內容中。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-110">All the examples assume C# 8.0 or newer, and the code is in a nullable context.</span></span>

<span data-ttu-id="a9ee4-111">讓我們從熟悉的範例開始。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-111">Let's start with a familiar example.</span></span> <span data-ttu-id="a9ee4-112">假設您的程式庫有下列 API 可取得資源字串：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="a9ee4-113">上述範例會遵循 `Try*` .net 中熟悉的模式。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="a9ee4-114">此 API 有兩個參考引數： `key` 和 `message` 參數。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="a9ee4-115">此 API 具有下列與這些引數 null f.23 相關的規則：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="a9ee4-116">呼叫端不應該傳遞 `null` 做為的引數 `key` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="a9ee4-117">呼叫端可以傳遞變數，其值為 `null` 的引數 `message` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="a9ee4-118">如果 `TryGetMessage` 方法傳回 `true` ，的值 `message` 不是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="a9ee4-119">如果傳回值是 `false,` (的值 `message` ，且其 null 狀態) 為 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="a9ee4-120">的規則 `key` 可以用變數型別表示： `key` 應為不可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-120">The rule for `key` can be expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="a9ee4-121">`message`參數較為複雜。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="a9ee4-122">它可 `null` 做為引數，但保證在成功時，該 `out` 引數不是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="a9ee4-123">在這些情況下，您需要更豐富的詞彙來描述期望。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="a9ee4-124">已加入數個屬性，以表達變數 null 狀態的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-124">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="a9ee4-125">您在 c # 8 之前撰寫的所有程式碼都是 null 的參考型別 *無警示*。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-125">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="a9ee4-126">這表示任何參考型別變數可能是 null，但不需要 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-126">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="a9ee4-127">當您的程式碼 *可為 null 感知*時，這些規則就會變更。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-127">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="a9ee4-128">參考型別絕對不應該是 `null` 值，而且必須先檢查可為 null 的參考型別， `null` 再進行取值。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-128">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="a9ee4-129">您的 Api 規則可能更複雜，如您在 API 案例中所見 `TryGetValue` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-129">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="a9ee4-130">許多 Api 都有更複雜的規則，可供變數或無法使用 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-130">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="a9ee4-131">在這些情況下，您將使用下列其中一個屬性來表示這些規則：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-131">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="a9ee4-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="a9ee4-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數永遠不應為 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="a9ee4-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可能是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="a9ee4-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值絕對不會是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="a9ee4-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的值時，不可為 null 的輸入引數可能是 null `bool` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="a9ee4-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的值時，可為 null 的輸入引數不會是 null `bool` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="a9ee4-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的引數不是 null，則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="a9ee4-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute)：方法永遠不會傳回。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="a9ee4-140">換句話說，它一律會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-140">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="a9ee4-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute)：如果相關聯的 `bool` 參數具有指定的值，則不會傳回這個方法。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>

<span data-ttu-id="a9ee4-142">上述描述可快速參考每個屬性的用途。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-142">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="a9ee4-143">下一節會更詳盡地說明行為和意義。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-143">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="a9ee4-144">新增這些屬性可讓編譯器更詳細地瞭解您的 API 規則。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-144">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="a9ee4-145">在可為 null 的已啟用內容中編譯呼叫程式碼時，編譯器會在違反這些規則時警告呼叫端。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-145">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="a9ee4-146">這些屬性不會在您的執行上啟用其他檢查。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-146">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="a9ee4-147">指定前置條件： `AllowNull` 和 `DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="a9ee4-147">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="a9ee4-148">請考慮永遠不會傳回的讀取/寫入屬性， `null` 因為它具有合理的預設值。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-148">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="a9ee4-149">將呼叫端 `null` 設定為預設值時，呼叫端會傳遞至 set 存取子。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-149">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="a9ee4-150">例如，假設有一個訊息系統要求您在聊天室中提供螢幕名稱。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-150">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="a9ee4-151">如果沒有提供，系統會產生隨機名稱：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-151">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName;
```

<span data-ttu-id="a9ee4-152">當您在可為 null 的無警示內容中編譯上述程式碼時，一切都沒問題。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-152">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="a9ee4-153">啟用可為 null 的參考型別之後， `ScreenName` 屬性會變成不可為 null 的參考。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-153">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="a9ee4-154">這對存取子而言是正確的 `get` ：它永遠不會傳回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-154">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="a9ee4-155">呼叫端不需要檢查傳回的屬性 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-155">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="a9ee4-156">但現在設定屬性以 `null` 產生警告。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-156">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="a9ee4-157">為了繼續支援這種類型的程式碼，您可以將 <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> 屬性加入至屬性中，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-157">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName = GenerateRandomScreenName();
```

<span data-ttu-id="a9ee4-158">您可能需要加入的指示詞， `using` <xref:System.Diagnostics.CodeAnalysis> 才能使用此程式和本文中討論的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-158">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="a9ee4-159">屬性（attribute）會套用至屬性（property），而不是 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-159">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="a9ee4-160">`AllowNull`屬性會指定*前置條件*，而且只會套用至輸入。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-160">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="a9ee4-161">`get`存取子有傳回值，但沒有輸入引數。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-161">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="a9ee4-162">因此， `AllowNull` 屬性只會套用至 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-162">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="a9ee4-163">上述範例示範在引數上加入屬性時要尋找的內容 `AllowNull` ：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-163">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="a9ee4-164">該變數的一般合約是它不應該是 `null` ，因此您想要使用不可為 null 的參考型別。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-164">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="a9ee4-165">雖然輸入變數不是 `null` 最常見的使用方式，但仍有一些案例。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-165">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="a9ee4-166">大部分情況下，您都需要屬性、、 `in` `out` 和引數的這個屬性 `ref` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-166">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="a9ee4-167">`AllowNull`當變數通常為非 null 時，屬性是最佳選擇，但您必須允許 `null` 前置條件。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-167">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="a9ee4-168">相較之下，使用的案例 `DisallowNull` ：您可以使用這個屬性來指定可為 null 的參考型別的輸入變數不應該是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-168">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="a9ee4-169">請考慮屬性 `null` ，其中是預設值，但用戶端只能將它設定為非 null 值。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-169">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="a9ee4-170">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-170">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="a9ee4-171">上述程式碼是表達您設計的最佳方式 `ReviewComment` `null` ，但無法設定為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-171">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="a9ee4-172">一旦這段程式碼可成為可為 null 的可感知，您就可以更清楚地向呼叫者表達這個概念 <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-172">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="a9ee4-173">在可為 null 的內容中， `ReviewComment` `get` 存取子可能會傳回的預設值 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-173">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="a9ee4-174">編譯器會警告您必須在存取之前檢查它。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-174">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="a9ee4-175">此外，它也會警告呼叫端（即使可能的話 `null` ），呼叫端不應該將它明確設定為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-175">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="a9ee4-176">`DisallowNull`屬性也會指定*前置條件*，而不會影響 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-176">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="a9ee4-177">`DisallowNull`當您觀察這些特性時，請使用屬性：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-177">You use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="a9ee4-178">變數可能 `null` 在核心案例中，通常是在第一次具現化時。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-178">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="a9ee4-179">變數不應明確設定為 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-179">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="a9ee4-180">這些情況在原本是 *null 無警示*的程式碼中很常見。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-180">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="a9ee4-181">可能是物件屬性是在兩個不同的初始化作業中所設定。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-181">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="a9ee4-182">可能是某些屬性只有在某些非同步工作完成後才會設定。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-182">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="a9ee4-183">`AllowNull`和 `DisallowNull` 屬性可讓您指定變數上的前置條件可能不符合這些變數上的可為 null 注釋。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-183">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="a9ee4-184">這些會提供 API 特性的更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-184">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="a9ee4-185">此額外資訊可協助呼叫端正確地使用您的 API。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-185">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="a9ee4-186">請記住，您可以使用下列屬性來指定前置條件：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-186">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="a9ee4-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="a9ee4-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數永遠不應為 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="a9ee4-189">指定後置條件： `MaybeNull` 和 `NotNull`</span><span class="sxs-lookup"><span data-stu-id="a9ee4-189">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="a9ee4-190">假設您有一個具有下列簽章的方法：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-190">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="a9ee4-191">您可能會撰寫如下所示的方法，以在找不到找不到 `null` 的名稱時傳回。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-191">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="a9ee4-192">`null`顯然會指出找不到記錄。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-192">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="a9ee4-193">在此範例中，您可能會將傳回類型從變更 `Customer` 為 `Customer?` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-193">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="a9ee4-194">將傳回值宣告為可為 null 的參考型別，可明確指定此 API 的意圖。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-194">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="a9ee4-195">基於泛型定義下所涵蓋的原因 [，以及](../../nullable-migration-strategies.md#generic-definitions-and-nullability) 此技術無法使用泛型方法的 null 屬性。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-195">For reasons covered under [Generic definitions and nullability](../../nullable-migration-strategies.md#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="a9ee4-196">您可能會有遵循類似模式的泛型方法：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-196">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

<span data-ttu-id="a9ee4-197">您無法指定傳回值為 `T?` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-197">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="a9ee4-198">`null`找不到搜尋的專案時，方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-198">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="a9ee4-199">由於您無法宣告傳回 `T?` 型別，因此您會將 `MaybeNull` 批註加入至方法傳回：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-199">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

<span data-ttu-id="a9ee4-200">上述程式碼會通知呼叫者，合約意指不可為 null 的型別，但是傳回值實際上 *可能* 是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-200">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="a9ee4-201">`MaybeNull`當您的 API 應為不可為 null 的類型（通常是泛型型別參數）時，請使用屬性，但可能會有可能會傳回的實例 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-201">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="a9ee4-202">`out`即使型別是可為 null 的參考型別，您也可以指定傳回值或或 `ref` 引數不是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-202">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="a9ee4-203">假設有一個方法可確保陣列夠大，足以容納一些元素。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-203">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="a9ee4-204">如果輸入引數沒有容量，則常式會配置新的陣列，並將所有現有的元素複製到其中。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-204">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="a9ee4-205">如果輸入引數是 `null` ，則常式會配置新的儲存區。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-205">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="a9ee4-206">如果有足夠的容量，常式不會執行任何動作：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-206">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="a9ee4-207">您可以呼叫此常式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-207">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="a9ee4-208">啟用 null 參考型別之後，您想要確保先前的程式碼會進行編譯而不發出警告。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-208">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="a9ee4-209">當方法傳回時， `storage` 引數保證不是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-209">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="a9ee4-210">不過，您可以 `EnsureCapacity` 使用 null 參考來呼叫。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-210">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="a9ee4-211">您可以建立 `storage` 可為 null 的參考型別，並將 `NotNull` 後置條件新增至參數宣告：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-211">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull] ref T[]? storage, int size)
```

<span data-ttu-id="a9ee4-212">上述程式碼清楚地表示現有的合約：呼叫端可以傳遞具有值的變數 `null` ，但傳回值保證永遠不會是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-212">The preceding code expresses the existing contract clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="a9ee4-213">`NotNull`屬性最適用于 `ref` 和 `out` 引數 `null` ，可傳遞做為引數，但在方法傳回時，該引數保證不是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-213">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="a9ee4-214">您可以使用下列屬性來指定無條件後置條件：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-214">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="a9ee4-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可能是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="a9ee4-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值絕對不會是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="a9ee4-217">指定條件式後置條件： `NotNullWhen` 、 `MaybeNullWhen` 和 `NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="a9ee4-217">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="a9ee4-218">您可能很熟悉該 `string` 方法 <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-218">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="a9ee4-219">`true`當引數為 null 或空字串時，這個方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-219">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="a9ee4-220">這是一種 null 檢查形式：呼叫端不需要 null-如果方法傳回，則檢查引數 `false` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-220">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="a9ee4-221">若要讓此方法成為可為 null 的感知，您要將引數設定為可為 null 的參考型別，並新增 `NotNullWhen` 屬性：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-221">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)] string? value);
```

<span data-ttu-id="a9ee4-222">這會通知編譯器，傳回值不 `false` 需要是 null 檢查的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-222">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="a9ee4-223">加入屬性會通知編譯器 `IsNullOrEmpty` 執行必要 null 檢查的靜態分析：傳回時 `false` ，輸入引數不是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-223">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="a9ee4-224">此 <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> 方法會針對 .Net Core 3.0 標注為如上所示。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-224">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="a9ee4-225">您的程式碼基底中可能會有類似的方法，可檢查物件的狀態是否有 null 值。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-225">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="a9ee4-226">編譯器無法辨識自訂 null 檢查方法，您必須自行新增批註。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-226">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="a9ee4-227">當您加入屬性時，編譯器的靜態分析會知道測試的變數是否已核取為 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-227">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="a9ee4-228">這些屬性的另一個用法是 `Try*` 模式。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-228">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="a9ee4-229">`ref`和變數的後置條件 `out` 會透過傳回值進行通訊。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-229">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="a9ee4-230">請考慮稍早所示的這個方法：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-230">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="a9ee4-231">上述方法會遵循一般的 .NET 用法：傳回值會指出是否 `message` 已將設定為找到的值，如果找不到任何訊息，則為預設值。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-231">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="a9ee4-232">如果方法傳回 `true` ，的值 `message` 不是 null; 否則，方法會將設定 `message` 為 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-232">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="a9ee4-233">您可以使用屬性來傳達該用法 `NotNullWhen` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-233">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="a9ee4-234">當您針對可為 null 的參考型別更新簽章時，請建立 `message` `string?` 並新增屬性：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-234">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="a9ee4-235">在上述範例中，當傳回時，的值 `message` 已知為非 null `TryGetMessage` `true` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-235">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="a9ee4-236">您應以相同方式在程式碼基底中標注類似的方法：引數可能是 `null` ，而且當方法傳回時，已知為非 null `true` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-236">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="a9ee4-237">您可能還需要的最後一個屬性。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-237">There's one final attribute you may also need.</span></span> <span data-ttu-id="a9ee4-238">有時，傳回值的 null 狀態取決於一或多個輸入引數的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-238">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="a9ee4-239">當特定輸入引數不是時，這些方法會傳回非 null 的值 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-239">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="a9ee4-240">若要正確地批註這些方法，請使用 `NotNullIfNotNull` 屬性。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-240">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="a9ee4-241">請考慮下列方法：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-241">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="a9ee4-242">如果 `url` 引數不是 null，則輸出不是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-242">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="a9ee4-243">啟用可為 null 的參考之後，如果您的 API 永遠不接受 null 輸入，則該簽章會正確運作。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-243">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="a9ee4-244">但是，如果輸入可以是 null，則傳回值也可以是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-244">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="a9ee4-245">因此，您可以將簽章變更為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-245">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="a9ee4-246">這也可以運作，但通常會強制呼叫者執行額外的 `null` 檢查。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-246">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="a9ee4-247">合約是 `null` 只有當輸入引數為時，傳回值才會 `url` 是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-247">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="a9ee4-248">若要表達該合約，您可以標注此方法，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-248">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="a9ee4-249">傳回值和引數都已加上批註， `?` 指出可能是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-249">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="a9ee4-250">屬性會進一步說明當引數不是時，傳回值不會是 null `url` `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-250">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="a9ee4-251">您可以使用下列屬性來指定條件式後置條件：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-251">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="a9ee4-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的值時，不可為 null 的輸入引數可能是 null `bool` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="a9ee4-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的值時，可為 null 的輸入引數不會是 null `bool` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="a9ee4-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的輸入引數不是 null，則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="verify-unreachable-code"></a><span data-ttu-id="a9ee4-255">驗證無法連線的程式碼</span><span class="sxs-lookup"><span data-stu-id="a9ee4-255">Verify unreachable code</span></span>

<span data-ttu-id="a9ee4-256">某些方法（通常是例外狀況協助程式或其他公用程式方法）一律會擲回例外狀況來結束。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-256">Some methods, typically exception helpers or other utility methods, always exit by throwing an exception.</span></span> <span data-ttu-id="a9ee4-257">或者，helper 可能會根據布林值引數的值來擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-257">Or, a helper may throw an exception based on the value of a Boolean argument.</span></span>

<span data-ttu-id="a9ee4-258">在第一種情況下，您可以將 `DoesNotReturn` 屬性加入至方法宣告。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-258">In the first case, you can add the `DoesNotReturn` attribute to the method declaration.</span></span> <span data-ttu-id="a9ee4-259">編譯器以三種方式協助您。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-259">The compiler helps you in three ways.</span></span> <span data-ttu-id="a9ee4-260">首先，如果沒有擲回例外狀況的方法可以結束，則編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-260">First, the compiler issues a warning if there is a path where the method can exit without throwing an exception.</span></span> <span data-ttu-id="a9ee4-261">其次，編譯器會在呼叫該方法之後，將任何程式碼標示為 *無法*存取，直到遇到適當的 `catch` 子句為止。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-261">Second, the compiler marks any code after a call to that method as *unreachable*, until an appropriate `catch` clause is encountered.</span></span> <span data-ttu-id="a9ee4-262">第三，無法連線的程式碼將不會影響任何 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-262">Third, the unreachable code won't affect any null states.</span></span> <span data-ttu-id="a9ee4-263">請參考下列方法：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-263">Consider this method:</span></span>

```csharp
[DoesNotReturn]
private void FailFast()
{
    throw new InvalidOperationException();
}

public void SetState(object containedField)
{
    if (!isInitialized)
    {
        FailFast();
    }

    // unreachable code:
    _field = containedField;
}
```

<span data-ttu-id="a9ee4-264">在第二個案例中，您會將 `DoesNotReturnIf` 屬性加入至方法的布林值參數。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-264">In the second case, you add the `DoesNotReturnIf` attribute to a Boolean parameter of the method.</span></span> <span data-ttu-id="a9ee4-265">您可以修改先前的範例，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-265">You can modify the previous example as follows:</span></span>

```csharp
private void FailFast([DoesNotReturnIf(false)] bool isValid)
{
    if (!isValid)
    {
        throw new InvalidOperationException();
    }
}

public void SetState(object containedField)
{
    FailFast(isInitialized);

    // unreachable code when "isInitialized" is false:
    _field = containedField;
}
```

## <a name="summary"></a><span data-ttu-id="a9ee4-266">總結</span><span class="sxs-lookup"><span data-stu-id="a9ee4-266">Summary</span></span>

[!INCLUDE [C# version alert](../../includes/csharp-version-alert.md)]

<span data-ttu-id="a9ee4-267">加入可為 null 的參考型別會提供初始詞彙，以描述您的 Api 對可能的變數的期望 `null` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-267">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="a9ee4-268">額外的屬性會提供更豐富的詞彙，以將變數的 null 狀態原因為前置條件與後置條件。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-268">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="a9ee4-269">這些屬性更清楚地描述您的期望，並為使用您 Api 的開發人員提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-269">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="a9ee4-270">當您更新可為 null 內容的程式庫時，請新增這些屬性，以引導您的 Api 使用者使用正確的使用方式。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-270">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="a9ee4-271">這些屬性可協助您完整描述輸入引數和傳回值的 null 狀態：</span><span class="sxs-lookup"><span data-stu-id="a9ee4-271">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="a9ee4-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute)：不可為 null 的輸入引數可能是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="a9ee4-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)：可為 null 的輸入引數永遠不應為 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="a9ee4-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute)：不可為 null 的傳回值可能是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="a9ee4-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)：可為 null 的傳回值絕對不會是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="a9ee4-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)：當方法傳回指定的值時，不可為 null 的輸入引數可能是 null `bool` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="a9ee4-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute)：當方法傳回指定的值時，可為 null 的輸入引數不會是 null `bool` 。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="a9ee4-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)：如果指定參數的輸入引數不是 null，則傳回值不是 null。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="a9ee4-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute)：方法永遠不會傳回。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="a9ee4-280">換句話說，它一律會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-280">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="a9ee4-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute)：如果相關聯的 `bool` 參數具有指定的值，則不會傳回這個方法。</span><span class="sxs-lookup"><span data-stu-id="a9ee4-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>
