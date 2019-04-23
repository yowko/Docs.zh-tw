---
title: 原生互通性最佳做法 - .NET
description: 了解在 .NET 中與原生元件建立介面的最佳做法。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 6702d469abf317b3b1f545ce79b980e8581ab5f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196654"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="1615b-103">原生互通性最佳做法</span><span class="sxs-lookup"><span data-stu-id="1615b-103">Native interoperability best practices</span></span>

<span data-ttu-id="1615b-104">.NET 提供您各種自訂原生互通性程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="1615b-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="1615b-105">本文包含 Microsoft 的 .NET 小組在原生互通性上遵循的指導方針。</span><span class="sxs-lookup"><span data-stu-id="1615b-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="1615b-106">一般指引</span><span class="sxs-lookup"><span data-stu-id="1615b-106">General guidance</span></span>

<span data-ttu-id="1615b-107">本節中的指導方針適用於所有互通案例。</span><span class="sxs-lookup"><span data-stu-id="1615b-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="1615b-108">**✔️ 請這樣做** 為您的方法和參數使用與要呼叫之原生方法相同的命名和大小寫。</span><span class="sxs-lookup"><span data-stu-id="1615b-108">**✔️ DO** use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="1615b-109">**✔️ 請考慮** 為常數值使用相同的命名和大小寫。</span><span class="sxs-lookup"><span data-stu-id="1615b-109">**✔️ CONSIDER** using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="1615b-110">**✔️ 請這樣做** 使用與原生類型對應相近的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="1615b-110">**✔️ DO** use .NET types that map closest to the native type.</span></span> <span data-ttu-id="1615b-111">例如在 C# 中，當原生類型是 `unsigned int` 時就使用 `uint`。</span><span class="sxs-lookup"><span data-stu-id="1615b-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="1615b-112">**✔️ 請這樣做** 當您想要的行為與預設行為不同時，才使用 `[In]` 和 `[Out]` 屬性。</span><span class="sxs-lookup"><span data-stu-id="1615b-112">**✔️ DO** only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="1615b-113">**✔️ 請考慮** 使用 <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> 來建立您的原生陣列緩衝區集區。</span><span class="sxs-lookup"><span data-stu-id="1615b-113">**✔️ CONSIDER** using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="1615b-114">**✔️ 請考慮** 將您的 P/Invoke 委派包裝在與您的原生程式庫有相同名稱和大小寫的類型中。</span><span class="sxs-lookup"><span data-stu-id="1615b-114">**✔️ CONSIDER** wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="1615b-115">這樣可讓您的 `[DllImport]` 屬性使用 C# `nameof` 語言功能來傳入原生程式庫名稱，並確保您不會拼錯原生程式庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="1615b-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="1615b-116">DllImport 屬性設定</span><span class="sxs-lookup"><span data-stu-id="1615b-116">DllImport attribute settings</span></span>

| <span data-ttu-id="1615b-117">設定</span><span class="sxs-lookup"><span data-stu-id="1615b-117">Setting</span></span> | <span data-ttu-id="1615b-118">預設</span><span class="sxs-lookup"><span data-stu-id="1615b-118">Default</span></span> | <span data-ttu-id="1615b-119">建議</span><span class="sxs-lookup"><span data-stu-id="1615b-119">Recommendation</span></span> | <span data-ttu-id="1615b-120">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1615b-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="1615b-121">保留預設值</span><span class="sxs-lookup"><span data-stu-id="1615b-121">keep default</span></span>  | <span data-ttu-id="1615b-122">當此項目明確設為 False 時，失敗的 HRESULT 傳回值會轉換成例外狀況 (結果為定義中的傳回值會變成 Null)。</span><span class="sxs-lookup"><span data-stu-id="1615b-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="1615b-123">取決於 API</span><span class="sxs-lookup"><span data-stu-id="1615b-123">depends on the API</span></span>  | <span data-ttu-id="1615b-124">如果 API 使用 GetLastError 並使用 Marshal.GetLastWin32Error 來取得值，請將此項目設為 True。</span><span class="sxs-lookup"><span data-stu-id="1615b-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="1615b-125">如果 API 設定的條件指出有錯誤，請先取得該錯誤再進行其他呼叫，以避免不小心複寫它。</span><span class="sxs-lookup"><span data-stu-id="1615b-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`<span data-ttu-id="1615b-126">，其會退而使用 `CharSet.Ansi` 行為</span><span class="sxs-lookup"><span data-stu-id="1615b-126">, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="1615b-127">當定義中出現字串或字元時，請明確地使用 `CharSet.Unicode` 或 `CharSet.Ansi`</span><span class="sxs-lookup"><span data-stu-id="1615b-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="1615b-128">此項目指定值為 `false` 時，字串的封送行為及 `ExactSpelling` 的作用。</span><span class="sxs-lookup"><span data-stu-id="1615b-128">This specifies marshalling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="1615b-129">請留意到，`CharSet.Ansi` 在 Unix 上實際是 UTF8。</span><span class="sxs-lookup"><span data-stu-id="1615b-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="1615b-130">Windows「多數」時候是使用 Unicode，而 Unix 是使用 UTF8。</span><span class="sxs-lookup"><span data-stu-id="1615b-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="1615b-131">請在[字元集相關文件](./charset.md)查看詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1615b-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="1615b-132">將此項目設為 True 可獲得些微效能好處，因為執行階段不會根據 `CharSet` 的設定，查看名稱尾碼是 "A" 或 "W" 的替代函式 ("A" 是 `CharSet.Ansi` 而 "W" 是 `CharSet.Unicode`)。</span><span class="sxs-lookup"><span data-stu-id="1615b-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="1615b-133">字串參數</span><span class="sxs-lookup"><span data-stu-id="1615b-133">String parameters</span></span>

<span data-ttu-id="1615b-134">當 CharSet 是 Unicode 時或引數明確標示為 `[MarshalAs(UnmanagedType.LPWSTR)]`「且」該字串是以傳值方式傳遞時 (不是 `ref` 或 `out`)，則該字串會被固定並由機器碼直接使用 (而不是複製)。</span><span class="sxs-lookup"><span data-stu-id="1615b-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="1615b-135">請記得將 `[DllImport]` 標示為 `Charset.Unicode`，除非您明確地想要對字串進行 ANSI 處理。</span><span class="sxs-lookup"><span data-stu-id="1615b-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="1615b-136">**❌ 請勿** 使用 `[Out] string` 參數。</span><span class="sxs-lookup"><span data-stu-id="1615b-136">**❌ DO NOT** use `[Out] string` parameters.</span></span> <span data-ttu-id="1615b-137">使用 `[Out]` 屬性以傳值方式傳遞的字串參數，可能會使執行階段不穩定 (如果該字串是暫留字串)。</span><span class="sxs-lookup"><span data-stu-id="1615b-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="1615b-138">請在 <xref:System.String.Intern%2A?displayProperty=nameWithType> 的文件中查看字串暫留的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1615b-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1615b-139">**❌ 請避免** `StringBuilder` 參數。</span><span class="sxs-lookup"><span data-stu-id="1615b-139">**❌ AVOID** `StringBuilder` parameters.</span></span> `StringBuilder` <span data-ttu-id="1615b-140">封送「一律」會建立原生緩衝區複本。</span><span class="sxs-lookup"><span data-stu-id="1615b-140">marshalling *always* creates a native buffer copy.</span></span> <span data-ttu-id="1615b-141">因此，這麼做可能非常沒有效率。</span><span class="sxs-lookup"><span data-stu-id="1615b-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="1615b-142">請考慮呼叫接受字串之 Windows API 的典型案例：</span><span class="sxs-lookup"><span data-stu-id="1615b-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="1615b-143">建立所需容量的 SB (配置受控容量) **{1}**</span><span class="sxs-lookup"><span data-stu-id="1615b-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="1615b-144">叫用</span><span class="sxs-lookup"><span data-stu-id="1615b-144">Invoke</span></span>
   1. <span data-ttu-id="1615b-145">配置原生緩衝區 **{2}**</span><span class="sxs-lookup"><span data-stu-id="1615b-145">Allocates a native buffer **{2}**</span></span>  
   2. <span data-ttu-id="1615b-146">若為 `[In]`，則複製內容 (`StringBuilder` 參數的預設值)</span><span class="sxs-lookup"><span data-stu-id="1615b-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>  
   3. <span data-ttu-id="1615b-147">若為 `[Out]`，則將原生緩衝區複製到新配置的受控陣列中 **{3}** (也是 `StringBuilder` 的預設值)</span><span class="sxs-lookup"><span data-stu-id="1615b-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>  
3. `ToString()` <span data-ttu-id="1615b-148">會配置另一個受控陣列 **{4}**</span><span class="sxs-lookup"><span data-stu-id="1615b-148">allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="1615b-149">這樣是由 *{4}* 配置從機器碼取得字串。</span><span class="sxs-lookup"><span data-stu-id="1615b-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="1615b-150">要限制此情況最好的方式是在其他呼叫中重複使用 `StringBuilder`，但這樣仍然只儲存 *1* 配置。</span><span class="sxs-lookup"><span data-stu-id="1615b-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="1615b-151">這樣比較好使用及從 `ArrayPool` 快取字元緩衝區，而且在後續的呼叫您可以直接取得 `ToString()` 的配置。</span><span class="sxs-lookup"><span data-stu-id="1615b-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="1615b-152">`StringBuilder` 的另一個問題是它一律會將傳回緩衝區備份複製到第一個 Null。</span><span class="sxs-lookup"><span data-stu-id="1615b-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="1615b-153">如果傳回的字串沒有中止，或者它是雙重 Null 結尾的字串，則您 P/Invoke 最佳的狀態會是不正確。</span><span class="sxs-lookup"><span data-stu-id="1615b-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="1615b-154">如果您「確實」使用 `StringBuilder`，最後一個陷阱是該容量**不**包含隱藏的 Null (封送一律會計算)。</span><span class="sxs-lookup"><span data-stu-id="1615b-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="1615b-155">這經常被誤解，因為大部分 API 都想要緩衝區「包含」Null。</span><span class="sxs-lookup"><span data-stu-id="1615b-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="1615b-156">這會導致浪費/不必要的配置。</span><span class="sxs-lookup"><span data-stu-id="1615b-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="1615b-157">此外，此陷阱會防止執行階段最佳化 `StringBuilder` 封送以減少複本。</span><span class="sxs-lookup"><span data-stu-id="1615b-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshalling to minimize copies.</span></span>

<span data-ttu-id="1615b-158">**✔️ 請考慮** 使用來自 `ArrayPool`的 `char[]`。</span><span class="sxs-lookup"><span data-stu-id="1615b-158">**✔️ CONSIDER** using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="1615b-159">如需字串封送的詳細資訊，請參閱[預設的字串封送](../../framework/interop/default-marshaling-for-strings.md)和[自訂字串封送](customize-parameter-marshalling.md#customizing-string-parameters)。</span><span class="sxs-lookup"><span data-stu-id="1615b-159">For more information on string marshalling, see [Default Marshalling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshalling](customize-parameter-marshalling.md#customizing-string-parameters).</span></span>

> __<span data-ttu-id="1615b-160">Windows 特定</span><span class="sxs-lookup"><span data-stu-id="1615b-160">Windows Specific</span></span>__  
> <span data-ttu-id="1615b-161">針對 `[Out]` 字串，CLR 預設會使用 `CoTaskMemFree` 來釋放字串，或是針對標示為 `UnmanagedType.BSTR` 的字串使用 `SysStringFree`。</span><span class="sxs-lookup"><span data-stu-id="1615b-161">For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>  
**<span data-ttu-id="1615b-162">針對具有輸出字串緩衝區的大部分 API：</span><span class="sxs-lookup"><span data-stu-id="1615b-162">For most APIs with an output string buffer:</span></span>**  
> <span data-ttu-id="1615b-163">傳入的字元計數必須包含 Null。</span><span class="sxs-lookup"><span data-stu-id="1615b-163">The passed in character count must include the null.</span></span> <span data-ttu-id="1615b-164">如果傳回值小於呼叫接收的傳入字元計數，則該值是「不含」尾端 Null 的字元數目。</span><span class="sxs-lookup"><span data-stu-id="1615b-164">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="1615b-165">否則，該計數為緩衝區「包含」Null 字元所需的大小。</span><span class="sxs-lookup"><span data-stu-id="1615b-165">Otherwise the count is the required size of the buffer *including* the null character.</span></span>  
> - <span data-ttu-id="1615b-166">傳入 5，取得 4：該字串為 4 個字元與一個尾端 Null。</span><span class="sxs-lookup"><span data-stu-id="1615b-166">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="1615b-167">傳入 6，取得 5：該字串為 5 個字元長，需要 6 個字元的緩衝區以保存 Null。</span><span class="sxs-lookup"><span data-stu-id="1615b-167">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>  
> [<span data-ttu-id="1615b-168">適用於字串的 Windows 資料類型</span><span class="sxs-lookup"><span data-stu-id="1615b-168">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="1615b-169">布林值參數和欄位</span><span class="sxs-lookup"><span data-stu-id="1615b-169">Boolean parameters and fields</span></span>

<span data-ttu-id="1615b-170">布林值很容易弄錯。</span><span class="sxs-lookup"><span data-stu-id="1615b-170">Booleans are easy to mess up.</span></span> <span data-ttu-id="1615b-171">根據預設，.NET `bool` 會封送到 Windows `BOOL` (4 個位元組的值)。</span><span class="sxs-lookup"><span data-stu-id="1615b-171">By default, a .NET `bool` is marshalled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="1615b-172">不過，C 和 C++ 中的 `_Bool` 和 `bool` 是「單一」位元組。</span><span class="sxs-lookup"><span data-stu-id="1615b-172">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="1615b-173">這可能導致難以追蹤的錯誤 (bug)，因為傳回值會有一半被捨棄，這有可能「潛在地」變更結果。</span><span class="sxs-lookup"><span data-stu-id="1615b-173">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="1615b-174">如需 .NET `bool` 值封送至 C 或 C++ `bool` 型別的詳細資訊，請參閱[自訂布林欄位封送](customize-struct-marshalling.md#customizing-boolean-field-marshalling)文件。</span><span class="sxs-lookup"><span data-stu-id="1615b-174">For more for information on marshalling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshalling](customize-struct-marshalling.md#customizing-boolean-field-marshalling).</span></span>

## <a name="guids"></a><span data-ttu-id="1615b-175">GUID</span><span class="sxs-lookup"><span data-stu-id="1615b-175">GUIDs</span></span>

<span data-ttu-id="1615b-176">GUID 可直接在特徵標記中使用。</span><span class="sxs-lookup"><span data-stu-id="1615b-176">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="1615b-177">許多 Windows API 都接受 `GUID&` 類型的別名，如 `REFIID`。</span><span class="sxs-lookup"><span data-stu-id="1615b-177">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="1615b-178">當以傳址方式傳遞時，可以透過 `ref` 或 `[MarshalAs(UnmanagedType.LPStruct)]` 屬性來傳遞它們。</span><span class="sxs-lookup"><span data-stu-id="1615b-178">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="1615b-179">GUID</span><span class="sxs-lookup"><span data-stu-id="1615b-179">GUID</span></span> | <span data-ttu-id="1615b-180">傳址 GUID</span><span class="sxs-lookup"><span data-stu-id="1615b-180">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="1615b-181">**❌ 請勿** 將 `[MarshalAs(UnmanagedType.LPStruct)]` 用於 `ref` GUID 參數以外的任何項目。</span><span class="sxs-lookup"><span data-stu-id="1615b-181">**❌ DO NOT** Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="1615b-182">Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="1615b-182">Blittable types</span></span>

<span data-ttu-id="1615b-183">Blittable 類型是受控碼和機器碼有相同位元層級表示的類型。</span><span class="sxs-lookup"><span data-stu-id="1615b-183">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="1615b-184">因此它們不需要為了從機器碼封送而傳換成其他格式，而這樣可以改善為它們所偏好的效能。</span><span class="sxs-lookup"><span data-stu-id="1615b-184">As such they do not need to be converted to another format to be marshalled to and from native code, and as this improves performance they should be preferred.</span></span>

**<span data-ttu-id="1615b-185">Blittable 類型：</span><span class="sxs-lookup"><span data-stu-id="1615b-185">Blittable types:</span></span>**

- `byte`<span data-ttu-id="1615b-186">、`sbyte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`single`、</span><span class="sxs-lookup"><span data-stu-id="1615b-186">, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`,</span></span> `double`
- <span data-ttu-id="1615b-187">非巢狀的一維 Blittable 類型陣列 (例如，`int[]`)</span><span class="sxs-lookup"><span data-stu-id="1615b-187">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="1615b-188">有固定配置的結構和類別的執行個體欄位只有 Blittable 值類型</span><span class="sxs-lookup"><span data-stu-id="1615b-188">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="1615b-189">固定配置需要 `[StructLayout(LayoutKind.Sequential)]` 或</span><span class="sxs-lookup"><span data-stu-id="1615b-189">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or</span></span> `[StructLayout(LayoutKind.Explicit)]`
  - <span data-ttu-id="1615b-190">結構預設為 `LayoutKind.Sequential`，類別為</span><span class="sxs-lookup"><span data-stu-id="1615b-190">structs are `LayoutKind.Sequential` by default, classes are</span></span> `LayoutKind.Auto`

**<span data-ttu-id="1615b-191">非 Blittable：</span><span class="sxs-lookup"><span data-stu-id="1615b-191">NOT blittable:</span></span>**

- `bool`

**<span data-ttu-id="1615b-192">有時 Blittable：</span><span class="sxs-lookup"><span data-stu-id="1615b-192">SOMETIMES blittable:</span></span>**

- `char`<span data-ttu-id="1615b-193">,</span><span class="sxs-lookup"><span data-stu-id="1615b-193">,</span></span> `string`

<span data-ttu-id="1615b-194">以傳址方式傳遞 Blittable 類型時，封送處理器會將它們固定，而不會複製到中繼緩衝區。</span><span class="sxs-lookup"><span data-stu-id="1615b-194">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="1615b-195">(類別會以傳址的方式繼承地傳遞，結構搭配使用 `ref` 或 `out` 時，會以傳址的方式傳遞。)</span><span class="sxs-lookup"><span data-stu-id="1615b-195">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

`char` <span data-ttu-id="1615b-196">在一維陣列中時，**或**當它所屬的類型明確地以 `CharSet = CharSet.Unicode` 標示為 `[StructLayout]` 時，它是 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="1615b-196">is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

`string` <span data-ttu-id="1615b-197">不是包含在其他類型中，且是作為引數傳遞並標示為 `[MarshalAs(UnmanagedType.LPWStr)]` 或 `[DllImport]` 已設定 `CharSet = CharSet.Unicode` 時，它是 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="1615b-197">is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="1615b-198">您可以藉由嘗試建立固定的 `GCHandle`，以查看某個類型是否為 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="1615b-198">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="1615b-199">如果該類型不是字串或被視為 Blittable，則 `GCHandle.Alloc` 會擲回 `ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="1615b-199">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="1615b-200">**✔️ 請這樣做** 盡可能讓您的結構是 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="1615b-200">**✔️ DO** make your structures blittable when possible.</span></span>

<span data-ttu-id="1615b-201">如需詳細資訊，請參閱:</span><span class="sxs-lookup"><span data-stu-id="1615b-201">For more information, see:</span></span>

- [<span data-ttu-id="1615b-202">Blittable 和非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="1615b-202">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)  
- [<span data-ttu-id="1615b-203">類型封送處理</span><span class="sxs-lookup"><span data-stu-id="1615b-203">Type Marshalling</span></span>](type-marshalling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="1615b-204">讓受控物件保持運作</span><span class="sxs-lookup"><span data-stu-id="1615b-204">Keeping managed objects alive</span></span>

`GC.KeepAlive()` <span data-ttu-id="1615b-205">會確保物件在範圍保持運作，直到叫用 KeepAlive 方法。</span><span class="sxs-lookup"><span data-stu-id="1615b-205">will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="1615b-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) 可讓封送處理器使物件在 P/Invoke 期間保持運作。</span><span class="sxs-lookup"><span data-stu-id="1615b-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="1615b-207">可以使用它，而不使用方法特徵標記中的 `IntPtr`。</span><span class="sxs-lookup"><span data-stu-id="1615b-207">It can be used instead of `IntPtr` in method signatures.</span></span> `SafeHandle` <span data-ttu-id="1615b-208">可有效地取代此類別，且應改為使用它。</span><span class="sxs-lookup"><span data-stu-id="1615b-208">effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="1615b-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) 允許固定受控物件，並取得指向它的原生指標。</span><span class="sxs-lookup"><span data-stu-id="1615b-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="1615b-210">基本模式為：</span><span class="sxs-lookup"><span data-stu-id="1615b-210">The basic pattern is:</span></span>  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="1615b-211">固定不是 `GCHandle` 的預設值。</span><span class="sxs-lookup"><span data-stu-id="1615b-211">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="1615b-212">其他主要模式是透過機器碼將參考傳遞至受控物件，然後再回到受控碼 (通常是使用回呼)。</span><span class="sxs-lookup"><span data-stu-id="1615b-212">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="1615b-213">以下是模式：</span><span class="sxs-lookup"><span data-stu-id="1615b-213">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="1615b-214">請注意，必須明確釋放 `GCHandle`，以避免記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="1615b-214">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="1615b-215">常見的 Windows 資料類型</span><span class="sxs-lookup"><span data-stu-id="1615b-215">Common Windows data types</span></span>

<span data-ttu-id="1615b-216">以下是常用於 Windows API 中的資料類型清單，以及在呼叫至 Windows 程式碼內時要使用的 C# 類型。</span><span class="sxs-lookup"><span data-stu-id="1615b-216">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="1615b-217">下列類型在 32 位元和 64 位元 Windows 上的大小相同 (除了其名稱)。</span><span class="sxs-lookup"><span data-stu-id="1615b-217">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="1615b-218">寬度</span><span class="sxs-lookup"><span data-stu-id="1615b-218">Width</span></span> | <span data-ttu-id="1615b-219">Windows</span><span class="sxs-lookup"><span data-stu-id="1615b-219">Windows</span></span>          | <span data-ttu-id="1615b-220">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="1615b-220">C (Windows)</span></span>          | <span data-ttu-id="1615b-221">C#</span><span class="sxs-lookup"><span data-stu-id="1615b-221">C#</span></span>       | <span data-ttu-id="1615b-222">替代函式</span><span class="sxs-lookup"><span data-stu-id="1615b-222">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="1615b-223">32</span><span class="sxs-lookup"><span data-stu-id="1615b-223">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="1615b-224">8</span><span class="sxs-lookup"><span data-stu-id="1615b-224">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="1615b-225">8</span><span class="sxs-lookup"><span data-stu-id="1615b-225">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="1615b-226">8</span><span class="sxs-lookup"><span data-stu-id="1615b-226">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="1615b-227">8</span><span class="sxs-lookup"><span data-stu-id="1615b-227">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="1615b-228">16</span><span class="sxs-lookup"><span data-stu-id="1615b-228">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="1615b-229">16</span><span class="sxs-lookup"><span data-stu-id="1615b-229">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="1615b-230">16</span><span class="sxs-lookup"><span data-stu-id="1615b-230">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="1615b-231">16</span><span class="sxs-lookup"><span data-stu-id="1615b-231">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="1615b-232">16</span><span class="sxs-lookup"><span data-stu-id="1615b-232">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="1615b-233">32</span><span class="sxs-lookup"><span data-stu-id="1615b-233">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="1615b-234">32</span><span class="sxs-lookup"><span data-stu-id="1615b-234">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="1615b-235">32</span><span class="sxs-lookup"><span data-stu-id="1615b-235">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="1615b-236">32</span><span class="sxs-lookup"><span data-stu-id="1615b-236">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="1615b-237">64</span><span class="sxs-lookup"><span data-stu-id="1615b-237">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="1615b-238">64</span><span class="sxs-lookup"><span data-stu-id="1615b-238">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="1615b-239">64</span><span class="sxs-lookup"><span data-stu-id="1615b-239">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="1615b-240">64</span><span class="sxs-lookup"><span data-stu-id="1615b-240">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="1615b-241">64</span><span class="sxs-lookup"><span data-stu-id="1615b-241">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="1615b-242">32</span><span class="sxs-lookup"><span data-stu-id="1615b-242">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="1615b-243">32</span><span class="sxs-lookup"><span data-stu-id="1615b-243">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="1615b-244">下列類型 (為指標) 確實按照平台的寬度。</span><span class="sxs-lookup"><span data-stu-id="1615b-244">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="1615b-245">將 `IntPtr`/`UIntPtr` 用於這些。</span><span class="sxs-lookup"><span data-stu-id="1615b-245">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="1615b-246">帶正負號指標類型 (使用 `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="1615b-246">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="1615b-247">不帶正負號指標類型 (使用 `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="1615b-247">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="1615b-248">Windows `PVOID` 是 C `void*`，可以作為 `IntPtr` 或 `UIntPtr` 來封送，但建議盡可能使用 `void*`。</span><span class="sxs-lookup"><span data-stu-id="1615b-248">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="1615b-249">Windows 資料類型</span><span class="sxs-lookup"><span data-stu-id="1615b-249">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="1615b-250">資料類型範圍</span><span class="sxs-lookup"><span data-stu-id="1615b-250">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="1615b-251">結構</span><span class="sxs-lookup"><span data-stu-id="1615b-251">Structs</span></span>

<span data-ttu-id="1615b-252">受控結構是在堆疊上建立的，直到方法傳回才會將它移除。</span><span class="sxs-lookup"><span data-stu-id="1615b-252">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="1615b-253">根據定義，他們是「固定的」(不會被 GC 移除)。</span><span class="sxs-lookup"><span data-stu-id="1615b-253">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="1615b-254">如果機器碼不使用目前方法結尾所傳遞的指標，您也可以直接接受不安全程式碼區塊中的位址。</span><span class="sxs-lookup"><span data-stu-id="1615b-254">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="1615b-255">Blittable 的結構效能更好，因為封送層可以直接使用它們。</span><span class="sxs-lookup"><span data-stu-id="1615b-255">Blittable structs are much more performant as they can simply be used directly by the marshalling layer.</span></span> <span data-ttu-id="1615b-256">請嘗試讓結構是 Blittable 的 (例如，避免`bool`)。</span><span class="sxs-lookup"><span data-stu-id="1615b-256">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="1615b-257">如需詳細資訊，請參閱 [Blittable 類型](#blittable-types)一節。</span><span class="sxs-lookup"><span data-stu-id="1615b-257">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="1615b-258">「如果」結構是 Blittable 的，為了獲得更好的效能，請使用 `sizeof()` 而不使用 `Marshal.SizeOf<MyStruct>()`。</span><span class="sxs-lookup"><span data-stu-id="1615b-258">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="1615b-259">如先前所述，您可以藉由嘗試建立固定的 `GCHandle`，以驗證類型是否為 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="1615b-259">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="1615b-260">如果該類型不是字串或被視為 Blittable，則 `GCHandle.Alloc` 會擲回 `ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="1615b-260">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="1615b-261">在定義中，結構的指標必須以 `ref` 傳遞，或者使用 `unsafe` 和 `*`。</span><span class="sxs-lookup"><span data-stu-id="1615b-261">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="1615b-262">**✔️ 請這樣做** 盡可能近似地對應受控結構與官方平台文件或標頭中所使用的圖形和名稱。</span><span class="sxs-lookup"><span data-stu-id="1615b-262">**✔️ DO** match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="1615b-263">**✔️ 請這樣做** 針對 Blittable 結構使用 C# `sizeof()`，而不使用 `Marshal.SizeOf<MyStruct>()`，以改善效能。</span><span class="sxs-lookup"><span data-stu-id="1615b-263">**✔️ DO** use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="1615b-264">`INT_PTR Reserved1[2]` 之類的陣列必須封送至兩個 `IntPtr` 欄位：`Reserved1a` 和 `Reserved1b`。</span><span class="sxs-lookup"><span data-stu-id="1615b-264">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="1615b-265">當原生陣列是基本類型時，我們可以使用 `fixed` 關鍵字來將它撰寫得更簡潔一點。</span><span class="sxs-lookup"><span data-stu-id="1615b-265">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="1615b-266">例如，在原生標頭中 `SYSTEM_PROCESS_INFORMATION` 看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="1615b-266">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="1615b-267">在 C# 中，我們可以將它撰寫像這樣：</span><span class="sxs-lookup"><span data-stu-id="1615b-267">In C#, we can write it like this:</span></span>

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

<span data-ttu-id="1615b-268">不過，固定的緩衝區有一些陷阱。</span><span class="sxs-lookup"><span data-stu-id="1615b-268">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="1615b-269">非 Blittable 類型的固定緩衝區不會正確地被封送，因此需要將原陣列展開成多個個別欄位。</span><span class="sxs-lookup"><span data-stu-id="1615b-269">Fixed buffers of non-blittable types won't be correctly marshalled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="1615b-270">此外，在 .NET Framework 和 .NET Core 3.0 之前，如果結構包含的固定緩衝區欄位是巢狀地包含在非 Blittable 結構中，則該固定緩衝區欄位不會正確地封送至機器碼。</span><span class="sxs-lookup"><span data-stu-id="1615b-270">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshalled to native code.</span></span>
