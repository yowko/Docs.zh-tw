---
title: C# 保留屬性:可無靜態分析
ms.date: 04/14/2020
description: 這些屬性由編譯器解釋,以便為可無和不可取消的引用類型提供更好的靜態分析。
ms.openlocfilehash: 33521133a6a01196e6e1ab9c3cdc191a24f1ecf3
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102706"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a><span data-ttu-id="e2f5a-103">保留屬性有助於編譯器的空狀態靜態分析</span><span class="sxs-lookup"><span data-stu-id="e2f5a-103">Reserved attributes contribute to the compiler's null state static analysis</span></span>

<span data-ttu-id="e2f5a-104">在可無的上下文中,編譯器執行代碼的靜態分析,以確定所有引用類型變數的 null 狀態:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-104">In a nullable context, the compiler performs static analysis of code to determine the null state of all reference type variables:</span></span>

- <span data-ttu-id="e2f5a-105">*非空*:靜態分析確定變數已分配給非空值。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-105">*not null*: Static analysis determined that the variable is assigned to a non-null value.</span></span>
- <span data-ttu-id="e2f5a-106">*可能為空*:靜態分析無法確定變數已分配非空值。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-106">*maybe null*: Static analysis cannot determine that a variable is assigned a non-null value.</span></span>

<span data-ttu-id="e2f5a-107">可以應用許多屬性,這些屬性向編譯器提供有關 API 語義的資訊。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-107">You can apply a number of attributes that provide information to the compiler about the semantics of your APIs.</span></span> <span data-ttu-id="e2f5a-108">此資訊可幫助編譯器執行靜態分析並確定變數何時不是空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-108">That information helps the compiler perform static analysis and determine when a variable is not null.</span></span> <span data-ttu-id="e2f5a-109">本文簡要描述了每個屬性以及如何使用它們。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-109">This article provides a brief description of each of those attributes and how to use them.</span></span> <span data-ttu-id="e2f5a-110">所有示例都假定 C# 8.0 或更新,並且代碼位於可空上下文中。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-110">All the examples assume C# 8.0 or newer, and the code is in a nullable context.</span></span>

<span data-ttu-id="e2f5a-111">讓我們從一個熟悉的例子開始。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-111">Let's start with a familiar example.</span></span> <span data-ttu-id="e2f5a-112">假設您的函式庫有以下 API 來檢索資源字串:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="e2f5a-113">前面的範例遵循 .NET`Try*`中熟悉的模式。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="e2f5a-114">此 API 有兩個引用`key`參數:`message`與 參數 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="e2f5a-115">此 API 有以下與這些參數的不合法的規則:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="e2f5a-116">調用方不應作為`null``key`的參數傳遞。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="e2f5a-117">調用方可以傳遞其值為`null``message`的變數作為 的 參數。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="e2f5a-118">如果`TryGetMessage`方法`true`返回`message`,則 的值不為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="e2f5a-119">如果傳回值`false,``message`為 (及其 null 狀態) 的值為 null。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="e2f5a-120">的規則`key`可以通過變數類型表示`key`: 應為不可消除的引用類型。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-120">The rule for `key` can be expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="e2f5a-121">參數`message`更為複雜。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="e2f5a-122">它允許`null`作為參數,但保證,在成功時,`out`該 參數不為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="e2f5a-123">對於這些方案,您需要更豐富的詞彙來描述期望值。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="e2f5a-124">添加了多個屬性以表示有關變數的 null 狀態的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-124">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="e2f5a-125">在 C# 8 引入可無引用類型之前編寫的所有代碼都是*無效的。*</span><span class="sxs-lookup"><span data-stu-id="e2f5a-125">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="e2f5a-126">這意味著任何引用類型變數可能為空,但不需要 null 檢查。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-126">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="e2f5a-127">一旦代碼*是空的,* 這些規則就會改變。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-127">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="e2f5a-128">引用類型絕不應為`null`值,並且在取消引用之前必須`null`針對 選中可消除的引用類型。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-128">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="e2f5a-129">API 的規則可能更為複雜,正如您在 API 方案中所`TryGetValue`看到的那樣 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-129">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="e2f5a-130">許多 API 對於變數可以或不能`null`是 時,都有更複雜的規則。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-130">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="e2f5a-131">在這些情況下,您將使用以下屬性之一來表示這些規則:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-131">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="e2f5a-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="e2f5a-133">[禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="e2f5a-134">[可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="e2f5a-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="e2f5a-136">[當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="e2f5a-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="e2f5a-138">[NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的參數不是 null,則返回值不為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="e2f5a-139">[不返回](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute):方法永遠不會返回。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="e2f5a-140">換句話說,它總是引發異常。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-140">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="e2f5a-141">[不返回If](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute):如果關聯`bool`的 參數具有指定的值,則此方法永遠不會返回。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>

<span data-ttu-id="e2f5a-142">前面的說明是每個屬性執行功能的快速引用。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-142">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="e2f5a-143">以下各節更全面地描述行為和含義。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-143">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="e2f5a-144">添加這些屬性為編譯器提供有關 API 規則的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-144">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="e2f5a-145">在啟用空的上下文中編譯調用代碼時,編譯器將在調用方違反這些規則時發出警告。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-145">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="e2f5a-146">這些屬性無法對實現啟用其他檢查。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-146">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="e2f5a-147">指定先決條件:`AllowNull`與`DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="e2f5a-147">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="e2f5a-148">請考慮從不返回`null`的讀/寫屬性,因為它具有合理的默認值。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-148">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="e2f5a-149">將調用方`null`設置為該預設值時,將傳遞給集訪問器。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-149">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="e2f5a-150">例如,考慮在聊天室中要求顯示螢幕名稱的郵件系統。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-150">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="e2f5a-151">如果未提供,系統將產生隨機名稱:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-151">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

<span data-ttu-id="e2f5a-152">當您在一個無效的遺忘上下文中編譯前面的代碼時,一切都很好。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-152">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="e2f5a-153">啟用空引用類型後,該`ScreenName`屬性將成為不可取消的引用。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-153">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="e2f5a-154">這對`get`存取者是正確的:它永遠不會`null`返回 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-154">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="e2f5a-155">調用方不需要檢查 返回的屬性`null`。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-155">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="e2f5a-156">但現在將屬性設置為`null`生成警告。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-156">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="e2f5a-157">為了繼續支援這種類型的代碼,將<xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType>屬性添加到屬性,如以下代碼所示:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-157">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

<span data-ttu-id="e2f5a-158">您可能需要添加一個`using`指令,<xref:System.Diagnostics.CodeAnalysis>以便使用此屬性和本文中討論的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-158">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="e2f5a-159">該屬性應用於屬性,而不是`set`訪問器。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-159">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="e2f5a-160">屬性`AllowNull`指定*先決條件*,並且僅適用於輸入。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-160">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="e2f5a-161">`get`訪問器具有返回值,但沒有輸入參數。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-161">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="e2f5a-162">因此,該`AllowNull`屬性僅適用於`set`訪問器。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-162">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="e2f5a-163">前面的範例展示在參數上新增`AllowNull`屬性時要尋找的內容:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-163">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="e2f5a-164">該變數的一般協定是,它不應該是`null`,因此您需要一個不可取消的引用類型。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-164">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="e2f5a-165">輸入變數有一些方案,`null`儘管它們不是最常見的用法。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-165">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="e2f5a-166">通常,屬性或`in`或或`out`.`ref`和參數需要此屬性。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-166">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="e2f5a-167">當`AllowNull`變數通常是非空的,但您需要作為先決條件允許`null`時,該屬性是最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-167">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="e2f5a-168">與使用`DisallowNull`: 的機制相比,使用此屬性指定 null 引用類型的輸入變數`null`不應為 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-168">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="e2f5a-169">請考慮一個屬性`null`,其中是預設值,但用戶端只能將其設置為非 null 值。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-169">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="e2f5a-170">請考慮下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e2f5a-170">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="e2f5a-171">前面的代碼是表示設計的最佳方式,`ReviewComment`可以`null`是 ,但不能`null`設定為 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-171">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="e2f5a-172">一旦此代碼是空的,您可以使用 更清楚地向呼叫方表達這<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>一 概念:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-172">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="e2f5a-173">在空中,`ReviewComment``get`存取器可以傳回`null`預設值 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-173">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="e2f5a-174">編譯器警告必須在訪問之前檢查它。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-174">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="e2f5a-175">此外,它警告呼叫方,即使它可能是`null`,呼叫方也不應顯式將其設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-175">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="e2f5a-176">該`DisallowNull`屬性還指定*一個先決條件*,它`get`不會影響 訪問器。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-176">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="e2f5a-177">當您觀察以下`DisallowNull`特徵時,可以使用該屬性:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-177">You use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="e2f5a-178">變數可能`null`位於核心方案中,通常是在第一次實例化時。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-178">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="e2f5a-179">變數不應顯示式設定為`null`。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-179">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="e2f5a-180">這些情況在最初*為空遺忘*的代碼中很常見。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-180">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="e2f5a-181">可能是對象屬性設置在兩個不同的初始化操作中。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-181">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="e2f5a-182">可能某些屬性僅在某些非同步工作完成後進行設置。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-182">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="e2f5a-183">`AllowNull`和`DisallowNull`屬性使您能夠指定變數的先決條件可能與這些變數上的空註釋不匹配。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-183">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="e2f5a-184">這些提供了有關 API 特徵的更多詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-184">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="e2f5a-185">此附加資訊可幫助呼叫方正確使用API。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-185">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="e2f5a-186">請記住,您使用以下屬性指定先決條件:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-186">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="e2f5a-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="e2f5a-188">[禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="e2f5a-189">指定後條件:`MaybeNull`與`NotNull`</span><span class="sxs-lookup"><span data-stu-id="e2f5a-189">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="e2f5a-190">假設您有一個具有以下簽名的方法:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-190">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="e2f5a-191">您可能已經編寫了這樣的方法,在未找到要`null`找的名稱時返回。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-191">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="e2f5a-192">清楚地`null`指示找不到記錄。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-192">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="e2f5a-193">這個選項, 可能會傳回類型從`Customer`變更為`Customer?`。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-193">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="e2f5a-194">將返回值聲明為空引用類型明確指定此 API 的意圖。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-194">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="e2f5a-195">由於[泛型定義和無效性](../../nullable-migration-strategies.md#generic-definitions-and-nullability)所涵蓋的原因,該技術不適用於泛型方法。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-195">For reasons covered under [Generic definitions and nullability](../../nullable-migration-strategies.md#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="e2f5a-196">您可能有一個遵循類似模式的泛型方法:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-196">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="e2f5a-197">無法指定傳回值`T?`為 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-197">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="e2f5a-198">當未找到`null`已請求的項時,該方法將返回。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-198">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="e2f5a-199">由於無法聲明`T?`傳回類型,`MaybeNull`因此將註釋添加到方法傳回:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-199">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="e2f5a-200">前面的代碼通知調用方協定意味著一種不可空的類型,但返回值*實際上可能*為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-200">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="e2f5a-201">當`MaybeNull`API 應為非空類型(通常是泛型類型參數),但可能存在`null`返回的 實例時,請使用該屬性。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-201">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="e2f5a-202">還可以指定返回值或`out`或`ref`或參數 不為空,即使類型為空引用類型。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-202">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="e2f5a-203">考慮一種確保數組足夠大以容納多個元素的方法。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-203">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="e2f5a-204">如果輸入參數沒有容量,例程將分配一個新陣組並將所有現有元素複製到其中。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-204">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="e2f5a-205">如果輸入參數為`null`,例程將分配新的存儲。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-205">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="e2f5a-206">如果容量充足,例程將不執行任何操作:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-206">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="e2f5a-207">您可以按照以下方式呼叫此例程式:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-207">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="e2f5a-208">開啟空引用類型後,您希望確保前面的代碼在無警告的情況下編譯。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-208">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="e2f5a-209">當方法返回時,`storage`參數保證不為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-209">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="e2f5a-210">但是,使用空引用進行調用`EnsureCapacity`是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-210">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="e2f5a-211">您可以建立`storage`空白參考類型,並將`NotNull`後條件加入參數的聲明:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-211">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

<span data-ttu-id="e2f5a-212">前面的代碼清楚地表達了現有協定:調用方可以傳遞具有該值的`null`變數,但返回值保證永遠不會為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-212">The preceding code expresses the existing contract clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="e2f5a-213">該`NotNull`屬性`ref`對於`out`和 參數`null`最有用, 其中可以作為參數傳遞,但當方法返回時,該參數保證不為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-213">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="e2f5a-214">使用以下屬性指定無條件的後情況:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-214">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="e2f5a-215">[可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="e2f5a-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="e2f5a-217">指定條件後條件: `NotNullWhen``MaybeNullWhen`、 與`NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="e2f5a-217">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="e2f5a-218">您可能熟悉這種方法`string`<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-218">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="e2f5a-219">當參數為`true`空字串或空字串時,此方法將返回。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-219">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="e2f5a-220">它是一種 null 檢查形式:如果`false`方法返回 ,調用方不需要對參數進行空檢查。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-220">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="e2f5a-221">要使此類方法具有 null 感知,您需要將參數設定為可 null 引用類型`NotNullWhen`,並新增屬性 :</span><span class="sxs-lookup"><span data-stu-id="e2f5a-221">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

<span data-ttu-id="e2f5a-222">這通知編譯器不需要對返回值`false`的任何代碼進行空檢查。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-222">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="e2f5a-223">屬性的新增通知編譯器的靜態分析,該`IsNullOrEmpty`分析執行必要的 null 檢查:`false`當它傳回`null`時,輸入參數不是 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-223">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="e2f5a-224">該方法<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>將如上所述.NET Core 3.0的用點子。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-224">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="e2f5a-225">代碼庫中可能也有類似的方法,用於檢查物件的狀態為 null 值。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-225">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="e2f5a-226">編譯器不會識別自定義 null 檢查方法,您需要自己添加註釋。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-226">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="e2f5a-227">添加屬性時,編譯器的靜態分析知道測試變數何時被空檢查。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-227">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="e2f5a-228">這些屬性的另一個用途是`Try*`模式。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-228">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="e2f5a-229">和`out`變數的`ref`后情況通過返回值進行通信。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-229">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="e2f5a-230">請考慮前面顯示的方法:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-230">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="e2f5a-231">前面的方法遵循典型的 .NET 習慣用法:返回`message`值指示 是否設置為找到的值,或者如果沒有找到消息,則指示默認值。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-231">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="e2f5a-232">如果方法返回`true`,則`message`的值 不為 null;如果 方法傳回 ,則值為 null。否則,該方法將設置`message`為null。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-232">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="e2f5a-233">您可以使用`NotNullWhen`屬性來傳達該習慣用法。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-233">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="e2f5a-234">更新可空引言型態的簽名時,`message``string?`請建立並新增屬性:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-234">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="e2f5a-235">在前面的範例中,`message`當`TryGetMessage``true`傳回時,值已知不為 null。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-235">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="e2f5a-236">應在代碼庫中以相同的方式對類似的方法進行編帶:當方法返回`null``true`時,參數可以是 ,並且已知為不為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-236">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="e2f5a-237">還有一個最終屬性,您可能還需要。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-237">There's one final attribute you may also need.</span></span> <span data-ttu-id="e2f5a-238">有時,返回值的 null 狀態取決於一個或多個輸入參數的 null 狀態。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-238">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="e2f5a-239">當某些輸入參數不是`null`時,這些方法將返回一個非空值。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-239">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="e2f5a-240">要正確對這些方法進行給上用,請使用`NotNullIfNotNull`屬性 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-240">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="e2f5a-241">請考慮以下方法:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-241">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="e2f5a-242">如果`url`參數不為空,則輸出`null`不是 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-242">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="e2f5a-243">啟用了可無效引用後,該簽名將正常工作,前提是 API 永遠不會接受空輸入。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-243">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="e2f5a-244">但是,如果輸入可以為空,則返回值也可以為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-244">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="e2f5a-245">因此,您可以將簽名更改為以下代碼:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-245">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="e2f5a-246">這也行得通,但通常會強制調用方實施額外的`null`檢查。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-246">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="e2f5a-247">協定是返回值僅在輸入參數`null``url``null`為 時才。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-247">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="e2f5a-248">要表示該協定,您需要對此方法進行編號,如以下代碼所示:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-248">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="e2f5a-249">傳回值和參數都帶`?`有 指示,指示任一`null`可以是 。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-249">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="e2f5a-250">該屬性進一步闡明,當參數不是`url``null`時,返回值不會為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-250">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="e2f5a-251">使用這些屬性指定條件後條件:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-251">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="e2f5a-252">[當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="e2f5a-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="e2f5a-254">[NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入參數不是 null,則返回值不為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="verify-unreachable-code"></a><span data-ttu-id="e2f5a-255">驗證無法存取的代碼</span><span class="sxs-lookup"><span data-stu-id="e2f5a-255">Verify unreachable code</span></span>

<span data-ttu-id="e2f5a-256">某些方法(通常是異常説明器或其他實用程式方法)總是通過引發異常退出。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-256">Some methods, typically exception helpers or other utility methods, always exit by throwing an exception.</span></span> <span data-ttu-id="e2f5a-257">或者,説明程式可能會根據布爾參數的值引發異常。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-257">Or, a helper may throw an exception based on the value of a Boolean argument.</span></span>

<span data-ttu-id="e2f5a-258">在第一種情況下,可以將`DoesNotReturn`屬性添加到方法聲明。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-258">In the first case, you can add the `DoesNotReturn` attribute to the method declaration.</span></span> <span data-ttu-id="e2f5a-259">編譯器在三個方面為您提供説明。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-259">The compiler helps you in three ways.</span></span> <span data-ttu-id="e2f5a-260">首先,如果有一個路徑可以退出而不引發異常,編譯器會發出警告。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-260">First, the compiler issues a warning if there is a path where the method can exit without throwing an exception.</span></span> <span data-ttu-id="e2f5a-261">其次,編譯器在調用該方法后將任何代碼標記為*不可訪問*,直到遇到`catch`適當的 子句。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-261">Second, the compiler marks any code after a call to that method as *unreachable*, until an appropriate `catch` clause is encountered.</span></span> <span data-ttu-id="e2f5a-262">第三,無法訪問的代碼不會影響任何空狀態。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-262">Third, the unreachable code won't affect any null states.</span></span> <span data-ttu-id="e2f5a-263">請參考下列方法：</span><span class="sxs-lookup"><span data-stu-id="e2f5a-263">Consider this method:</span></span>

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

<span data-ttu-id="e2f5a-264">在第二種情況下,您將`DoesNotReturnIf`屬性添加到方法的布爾參數。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-264">In the second case, you add the `DoesNotReturnIf` attribute to a Boolean parameter of the method.</span></span> <span data-ttu-id="e2f5a-265">您可以修改前面的範例,如下所示:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-265">You can modify the previous example as follows:</span></span>

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a><span data-ttu-id="e2f5a-266">摘要</span><span class="sxs-lookup"><span data-stu-id="e2f5a-266">Summary</span></span>

<span data-ttu-id="e2f5a-267">添加可取消的引用類型提供了一個初始詞彙表來描述 API 對`null`可能為的變數的期望。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-267">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="e2f5a-268">附加屬性提供了更豐富的詞彙,將變數的 null 狀態描述為先決條件和後條件。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-268">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="e2f5a-269">這些屬性更清楚地描述了您的期望,並為使用 API 的開發人員提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-269">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="e2f5a-270">更新可無效上下文的庫時,請添加這些屬性以引導 API 的使用者使用正確的方法。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-270">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="e2f5a-271">這些屬性可説明您完全描述輸入參數和傳回值的 null 狀態:</span><span class="sxs-lookup"><span data-stu-id="e2f5a-271">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="e2f5a-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): 不可無效的輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="e2f5a-273">[禁止無效](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute):可空輸入參數絕不應為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="e2f5a-274">[可能 Null](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): 無法取消的傳回值可能為 null。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="e2f5a-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): 空返回值永遠不會為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="e2f5a-276">[當](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)方法返回指定`bool`的 值時,可能 Null 時:非空輸入參數可能為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="e2f5a-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute):當方法返回指定`bool`的 值時,可 null 的輸入參數不會為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="e2f5a-278">[NotNullIf NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute):如果指定參數的輸入參數不是 null,則返回值不為空。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="e2f5a-279">[不返回](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute):方法永遠不會返回。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="e2f5a-280">換句話說,它總是引發異常。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-280">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="e2f5a-281">[不返回If](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute):如果關聯`bool`的 參數具有指定的值,則此方法永遠不會返回。</span><span class="sxs-lookup"><span data-stu-id="e2f5a-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>
