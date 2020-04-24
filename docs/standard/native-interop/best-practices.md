---
title: 原生互通性最佳做法 - .NET
description: 了解在 .NET 中與原生元件建立介面的最佳做法。
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391217"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="d2330-103">原生互通性最佳做法</span><span class="sxs-lookup"><span data-stu-id="d2330-103">Native interoperability best practices</span></span>

<span data-ttu-id="d2330-104">.NET 提供您各種自訂原生互通性程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="d2330-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="d2330-105">本文包含 Microsoft 的 .NET 小組在原生互通性上遵循的指導方針。</span><span class="sxs-lookup"><span data-stu-id="d2330-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="d2330-106">一般方針</span><span class="sxs-lookup"><span data-stu-id="d2330-106">General guidance</span></span>

<span data-ttu-id="d2330-107">本節中的指導方針適用於所有互通案例。</span><span class="sxs-lookup"><span data-stu-id="d2330-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="d2330-108">✔️ 請這樣做 為您的方法和參數使用與要呼叫之原生方法相同的命名和大小寫。</span><span class="sxs-lookup"><span data-stu-id="d2330-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="d2330-109">✔️ 請考慮 為常數值使用相同的命名和大小寫。</span><span class="sxs-lookup"><span data-stu-id="d2330-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="d2330-110">✔️ 請這樣做 使用與原生類型對應相近的 .NET 類型。</span><span class="sxs-lookup"><span data-stu-id="d2330-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="d2330-111">例如在 C# 中，當原生類型是 `unsigned int` 時就使用 `uint`。</span><span class="sxs-lookup"><span data-stu-id="d2330-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="d2330-112">✔️ 請這樣做 當您想要的行為與預設行為不同時，才使用 `[In]` 和 `[Out]` 屬性。</span><span class="sxs-lookup"><span data-stu-id="d2330-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="d2330-113">✔️ 請考慮 使用 <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> 來建立您的原生陣列緩衝區集區。</span><span class="sxs-lookup"><span data-stu-id="d2330-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="d2330-114">✔️ 請考慮 將您的 P/Invoke 委派包裝在與您的原生程式庫有相同名稱和大小寫的類型中。</span><span class="sxs-lookup"><span data-stu-id="d2330-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="d2330-115">這樣可讓您的 `[DllImport]` 屬性使用 C# `nameof` 語言功能來傳入原生程式庫名稱，並確保您不會拼錯原生程式庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2330-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="d2330-116">DllImport 屬性設定</span><span class="sxs-lookup"><span data-stu-id="d2330-116">DllImport attribute settings</span></span>

| <span data-ttu-id="d2330-117">設定</span><span class="sxs-lookup"><span data-stu-id="d2330-117">Setting</span></span> | <span data-ttu-id="d2330-118">Default</span><span class="sxs-lookup"><span data-stu-id="d2330-118">Default</span></span> | <span data-ttu-id="d2330-119">建議</span><span class="sxs-lookup"><span data-stu-id="d2330-119">Recommendation</span></span> | <span data-ttu-id="d2330-120">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d2330-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="d2330-121">保留預設值</span><span class="sxs-lookup"><span data-stu-id="d2330-121">keep default</span></span>  | <span data-ttu-id="d2330-122">當此項目明確設為 False 時，失敗的 HRESULT 傳回值會轉換成例外狀況 (結果為定義中的傳回值會變成 Null)。</span><span class="sxs-lookup"><span data-stu-id="d2330-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="d2330-123">取決於 API</span><span class="sxs-lookup"><span data-stu-id="d2330-123">depends on the API</span></span>  | <span data-ttu-id="d2330-124">如果 API 使用 GetLastError 並使用 Marshal.GetLastWin32Error 來取得值，請將此項目設為 True。</span><span class="sxs-lookup"><span data-stu-id="d2330-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="d2330-125">如果 API 設定的條件指出有錯誤，請先取得該錯誤再進行其他呼叫，以避免不小心複寫它。</span><span class="sxs-lookup"><span data-stu-id="d2330-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="d2330-126">`CharSet.None`，會退而使用 `CharSet.Ansi` 行為</span><span class="sxs-lookup"><span data-stu-id="d2330-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="d2330-127">當定義中出現字串或字元時，請明確地使用 `CharSet.Unicode` 或 `CharSet.Ansi`</span><span class="sxs-lookup"><span data-stu-id="d2330-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="d2330-128">此項目指定值為 `false` 時，字串的封送處理行為及 `ExactSpelling` 的作用。</span><span class="sxs-lookup"><span data-stu-id="d2330-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="d2330-129">請留意到，`CharSet.Ansi` 在 Unix 上實際是 UTF8。</span><span class="sxs-lookup"><span data-stu-id="d2330-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="d2330-130">Windows「多數」__ 時候是使用 Unicode，而 Unix 是使用 UTF8。</span><span class="sxs-lookup"><span data-stu-id="d2330-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="d2330-131">請在[字元集相關文件](./charset.md)查看詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d2330-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="d2330-132">將此項目設為 True 可獲得些微效能好處，因為執行階段不會根據 `CharSet` 的設定，查看名稱尾碼是 "A" 或 "W" 的替代函式 ("A" 是 `CharSet.Ansi` 而 "W" 是 `CharSet.Unicode`)。</span><span class="sxs-lookup"><span data-stu-id="d2330-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="d2330-133">字串參數</span><span class="sxs-lookup"><span data-stu-id="d2330-133">String parameters</span></span>

<span data-ttu-id="d2330-134">當 CharSet 是 Unicode 時或引數明確標示為 「且」`[MarshalAs(UnmanagedType.LPWSTR)]` __ 該字串是以傳值方式傳遞時 (不是 `ref` 或 `out`)，則該字串會被固定並由機器碼直接使用 (而不是複製)。</span><span class="sxs-lookup"><span data-stu-id="d2330-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="d2330-135">請記得將 `[DllImport]` 標示為 `Charset.Unicode`，除非您明確地想要對字串進行 ANSI 處理。</span><span class="sxs-lookup"><span data-stu-id="d2330-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="d2330-136">❌請勿使用`[Out] string`參數。</span><span class="sxs-lookup"><span data-stu-id="d2330-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="d2330-137">使用 `[Out]` 屬性以傳值方式傳遞的字串參數，可能會使執行階段不穩定 (如果該字串是暫留字串)。</span><span class="sxs-lookup"><span data-stu-id="d2330-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="d2330-138">請在 <xref:System.String.Intern%2A?displayProperty=nameWithType> 的文件中查看字串暫留的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d2330-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d2330-139">❌避免`StringBuilder`參數。</span><span class="sxs-lookup"><span data-stu-id="d2330-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="d2330-140">`StringBuilder` 封送處理「一律」\*\* 會建立原生緩衝區複本。</span><span class="sxs-lookup"><span data-stu-id="d2330-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="d2330-141">因此，這麼做可能非常沒有效率。</span><span class="sxs-lookup"><span data-stu-id="d2330-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="d2330-142">請考慮呼叫接受字串之 Windows API 的典型案例：</span><span class="sxs-lookup"><span data-stu-id="d2330-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="d2330-143">建立所需容量的 SB （配置受控容量）**{1}**</span><span class="sxs-lookup"><span data-stu-id="d2330-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="d2330-144">叫用</span><span class="sxs-lookup"><span data-stu-id="d2330-144">Invoke</span></span>
   1. <span data-ttu-id="d2330-145">配置原生緩衝區**{2}**</span><span class="sxs-lookup"><span data-stu-id="d2330-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="d2330-146">若為 ，則複製內容 (`StringBuilder` 參數的預設值)`[In]` __</span><span class="sxs-lookup"><span data-stu-id="d2330-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="d2330-147">若為 `[Out]` **，則將原生緩衝區複製到新配置的受控陣列中 {3} (也是 `StringBuilder` 的預設值)** __</span><span class="sxs-lookup"><span data-stu-id="d2330-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="d2330-148">`ToString()`配置另一個受控陣列**{4}**</span><span class="sxs-lookup"><span data-stu-id="d2330-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="d2330-149">這是*{4}* 從原生程式碼取得字串的配置。</span><span class="sxs-lookup"><span data-stu-id="d2330-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="d2330-150">要限制此情況最好的方式是在其他呼叫中重複使用 `StringBuilder`，但這樣仍然只儲存 *1* 配置。</span><span class="sxs-lookup"><span data-stu-id="d2330-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="d2330-151">這樣比較好使用及從 `ArrayPool` 快取字元緩衝區，而且在後續的呼叫您可以直接取得 `ToString()` 的配置。</span><span class="sxs-lookup"><span data-stu-id="d2330-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="d2330-152">`StringBuilder` 的另一個問題是它一律會將傳回緩衝區備份複製到第一個 Null。</span><span class="sxs-lookup"><span data-stu-id="d2330-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="d2330-153">如果傳回的字串沒有中止，或者它是雙重 Null 結尾的字串，則您 P/Invoke 最佳的狀態會是不正確。</span><span class="sxs-lookup"><span data-stu-id="d2330-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="d2330-154">如果您「確實」\*\* 使用 `StringBuilder`，最後一個陷阱是該容量**不**包含隱藏的 Null (封送一律會計算)。</span><span class="sxs-lookup"><span data-stu-id="d2330-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="d2330-155">這經常被誤解，因為大部分 API 都想要緩衝區「包含」\*\* Null。</span><span class="sxs-lookup"><span data-stu-id="d2330-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="d2330-156">這會導致浪費/不必要的配置。</span><span class="sxs-lookup"><span data-stu-id="d2330-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="d2330-157">此外，此陷阱會防止執行階段最佳化 `StringBuilder` 封送處理以減少複本。</span><span class="sxs-lookup"><span data-stu-id="d2330-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="d2330-158">✔️ 請考慮 使用來自 `ArrayPool`的 `char[]`。</span><span class="sxs-lookup"><span data-stu-id="d2330-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="d2330-159">如需字串封送處理的詳細資訊，請參閱[字串的預設封送處理](../../framework/interop/default-marshaling-for-strings.md)和[自訂字串封送處理](customize-parameter-marshaling.md#customizing-string-parameters)。</span><span class="sxs-lookup"><span data-stu-id="d2330-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="d2330-160">__Windows 特定__針對`[Out]`字串，CLR 預設會`CoTaskMemFree`使用來釋放字串或`SysStringFree`標示為`UnmanagedType.BSTR`的字串。</span><span class="sxs-lookup"><span data-stu-id="d2330-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="d2330-161">**針對具有輸出字串緩衝區的大部分 api：** 傳入的字元計數必須包含 null。</span><span class="sxs-lookup"><span data-stu-id="d2330-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="d2330-162">如果傳回值小於呼叫接收的傳入字元計數，則該值是「不含」\*\* 尾端 Null 的字元數目。</span><span class="sxs-lookup"><span data-stu-id="d2330-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="d2330-163">否則，該計數為緩衝區「包含」\*\* Null 字元所需的大小。</span><span class="sxs-lookup"><span data-stu-id="d2330-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="d2330-164">傳入5，取得4：字串長度為4個字元，結尾為 null。</span><span class="sxs-lookup"><span data-stu-id="d2330-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="d2330-165">傳入5，get 6：字串長度為5個字元，需要6個字元的緩衝區來保存 null。</span><span class="sxs-lookup"><span data-stu-id="d2330-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="d2330-166">字串的 Windows 資料類型</span><span class="sxs-lookup"><span data-stu-id="d2330-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="d2330-167">布林值參數和欄位</span><span class="sxs-lookup"><span data-stu-id="d2330-167">Boolean parameters and fields</span></span>

<span data-ttu-id="d2330-168">布林值很容易弄錯。</span><span class="sxs-lookup"><span data-stu-id="d2330-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="d2330-169">根據預設，.NET `bool` 會封送到 Windows `BOOL` (4 個位元組的值)。</span><span class="sxs-lookup"><span data-stu-id="d2330-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="d2330-170">不過，C 和 C++ 中的 `_Bool` 和 `bool` 是「單一」\*\* 位元組。</span><span class="sxs-lookup"><span data-stu-id="d2330-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="d2330-171">這可能導致難以追蹤的錯誤 (bug)，因為傳回值會有一半被捨棄，這有可能「潛在地」\*\* 變更結果。</span><span class="sxs-lookup"><span data-stu-id="d2330-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="d2330-172">如需將 .NET `bool` 值封送至 C 或 C++ `bool` 類型的詳細資訊，請參閱[自訂布林欄位封送處理](customize-struct-marshaling.md#customizing-boolean-field-marshaling)文件。</span><span class="sxs-lookup"><span data-stu-id="d2330-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="d2330-173">GUID</span><span class="sxs-lookup"><span data-stu-id="d2330-173">GUIDs</span></span>

<span data-ttu-id="d2330-174">GUID 可直接在特徵標記中使用。</span><span class="sxs-lookup"><span data-stu-id="d2330-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="d2330-175">許多 Windows API 都接受 `GUID&` 類型的別名，如 `REFIID`。</span><span class="sxs-lookup"><span data-stu-id="d2330-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="d2330-176">當以傳址方式傳遞時，可以透過 `ref` 或 `[MarshalAs(UnmanagedType.LPStruct)]` 屬性來傳遞它們。</span><span class="sxs-lookup"><span data-stu-id="d2330-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="d2330-177">GUID</span><span class="sxs-lookup"><span data-stu-id="d2330-177">GUID</span></span> | <span data-ttu-id="d2330-178">傳址 GUID</span><span class="sxs-lookup"><span data-stu-id="d2330-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="d2330-179">❌請勿針對`ref` GUID `[MarshalAs(UnmanagedType.LPStruct)]`參數以外的任何專案使用。</span><span class="sxs-lookup"><span data-stu-id="d2330-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="d2330-180">Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="d2330-180">Blittable types</span></span>

<span data-ttu-id="d2330-181">Blittable 類型是受控碼和機器碼有相同位元層級表示的類型。</span><span class="sxs-lookup"><span data-stu-id="d2330-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="d2330-182">由於它們不需要為了從機器碼來回封送而轉換成其他格式，因此它們可以改善效能，建議您使用它們。</span><span class="sxs-lookup"><span data-stu-id="d2330-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="d2330-183">**Blittable 類型：**</span><span class="sxs-lookup"><span data-stu-id="d2330-183">**Blittable types:**</span></span>

- <span data-ttu-id="d2330-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="d2330-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="d2330-185">非巢狀的一維 Blittable 類型陣列 (例如，`int[]`)</span><span class="sxs-lookup"><span data-stu-id="d2330-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="d2330-186">有固定配置的結構和類別的執行個體欄位只有 Blittable 值類型</span><span class="sxs-lookup"><span data-stu-id="d2330-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="d2330-187">固定配置需要 `[StructLayout(LayoutKind.Sequential)]` 或 `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="d2330-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="d2330-188">結構預設為 `LayoutKind.Sequential`，類別為 `LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="d2330-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="d2330-189">**非 Blittable：**</span><span class="sxs-lookup"><span data-stu-id="d2330-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="d2330-190">**有時 Blittable：**</span><span class="sxs-lookup"><span data-stu-id="d2330-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="d2330-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="d2330-191">`char`, `string`</span></span>

<span data-ttu-id="d2330-192">以傳址方式傳遞 Blittable 類型時，封送處理器會將它們固定，而不會複製到中繼緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d2330-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="d2330-193">(類別會以傳址的方式繼承地傳遞，結構搭配使用 `ref` 或 `out` 時，會以傳址的方式傳遞。)</span><span class="sxs-lookup"><span data-stu-id="d2330-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="d2330-194">當 `char` 在一維陣列中時，**或**當它所屬的類型明確地以 `CharSet = CharSet.Unicode` 標示為 `[StructLayout]` 時，它是 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="d2330-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="d2330-195">當 `string` 不是包含在其他類型中，且它是當作引數傳遞並標示 `[MarshalAs(UnmanagedType.LPWStr)]` 或已設定`CharSet = CharSet.Unicode`的 `[DllImport]`。</span><span class="sxs-lookup"><span data-stu-id="d2330-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="d2330-196">您可以藉由嘗試建立固定的 `GCHandle`，以查看某個類型是否為 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="d2330-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="d2330-197">如果該類型不是字串或被視為 Blittable，則 `GCHandle.Alloc` 會擲回 `ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="d2330-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="d2330-198">✔️ 請這樣做 盡可能讓您的結構是 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="d2330-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="d2330-199">如需詳細資訊，請參閱：</span><span class="sxs-lookup"><span data-stu-id="d2330-199">For more information, see:</span></span>

- [<span data-ttu-id="d2330-200">Blittable 和非 Blittable 類型</span><span class="sxs-lookup"><span data-stu-id="d2330-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="d2330-201">類型封送處理</span><span class="sxs-lookup"><span data-stu-id="d2330-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="d2330-202">讓受控物件保持運作</span><span class="sxs-lookup"><span data-stu-id="d2330-202">Keeping managed objects alive</span></span>

<span data-ttu-id="d2330-203">`GC.KeepAlive()` 會確保物件在範圍保持運作，直到叫用 KeepAlive 方法。</span><span class="sxs-lookup"><span data-stu-id="d2330-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="d2330-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)允許封送處理器在 P/Invoke 期間讓物件維持運作狀態。</span><span class="sxs-lookup"><span data-stu-id="d2330-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="d2330-205">可以使用它，而不使用方法特徵標記中的 `IntPtr`。</span><span class="sxs-lookup"><span data-stu-id="d2330-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="d2330-206">應改為使用 `SafeHandle`，它可有效地取代此類別。</span><span class="sxs-lookup"><span data-stu-id="d2330-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="d2330-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)允許釘選 managed 物件，並取得其原生指標。</span><span class="sxs-lookup"><span data-stu-id="d2330-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="d2330-208">基本模式為：</span><span class="sxs-lookup"><span data-stu-id="d2330-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="d2330-209">固定不是 `GCHandle` 的預設值。</span><span class="sxs-lookup"><span data-stu-id="d2330-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="d2330-210">其他主要模式是透過機器碼將參考傳遞至受控物件，然後再回到受控碼 (通常是使用回呼)。</span><span class="sxs-lookup"><span data-stu-id="d2330-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="d2330-211">以下是模式：</span><span class="sxs-lookup"><span data-stu-id="d2330-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="d2330-212">請注意，必須明確釋放 `GCHandle`，以避免記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="d2330-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="d2330-213">常見的 Windows 資料類型</span><span class="sxs-lookup"><span data-stu-id="d2330-213">Common Windows data types</span></span>

<span data-ttu-id="d2330-214">以下是常用於 Windows API 中的資料類型清單，以及在呼叫至 Windows 程式碼內時要使用的 C# 類型。</span><span class="sxs-lookup"><span data-stu-id="d2330-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="d2330-215">下列類型在 32 位元和 64 位元 Windows 上的大小相同 (除了其名稱)。</span><span class="sxs-lookup"><span data-stu-id="d2330-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="d2330-216">寬度</span><span class="sxs-lookup"><span data-stu-id="d2330-216">Width</span></span> | <span data-ttu-id="d2330-217">Windows</span><span class="sxs-lookup"><span data-stu-id="d2330-217">Windows</span></span>          | <span data-ttu-id="d2330-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="d2330-218">C (Windows)</span></span>          | <span data-ttu-id="d2330-219">C#</span><span class="sxs-lookup"><span data-stu-id="d2330-219">C#</span></span>       | <span data-ttu-id="d2330-220">替代函式</span><span class="sxs-lookup"><span data-stu-id="d2330-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="d2330-221">32</span><span class="sxs-lookup"><span data-stu-id="d2330-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="d2330-222">8</span><span class="sxs-lookup"><span data-stu-id="d2330-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="d2330-223">8</span><span class="sxs-lookup"><span data-stu-id="d2330-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="d2330-224">8</span><span class="sxs-lookup"><span data-stu-id="d2330-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="d2330-225">8</span><span class="sxs-lookup"><span data-stu-id="d2330-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="d2330-226">16</span><span class="sxs-lookup"><span data-stu-id="d2330-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="d2330-227">16</span><span class="sxs-lookup"><span data-stu-id="d2330-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="d2330-228">16</span><span class="sxs-lookup"><span data-stu-id="d2330-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="d2330-229">16</span><span class="sxs-lookup"><span data-stu-id="d2330-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="d2330-230">16</span><span class="sxs-lookup"><span data-stu-id="d2330-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="d2330-231">32</span><span class="sxs-lookup"><span data-stu-id="d2330-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="d2330-232">32</span><span class="sxs-lookup"><span data-stu-id="d2330-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="d2330-233">32</span><span class="sxs-lookup"><span data-stu-id="d2330-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="d2330-234">32</span><span class="sxs-lookup"><span data-stu-id="d2330-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="d2330-235">64</span><span class="sxs-lookup"><span data-stu-id="d2330-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="d2330-236">64</span><span class="sxs-lookup"><span data-stu-id="d2330-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="d2330-237">64</span><span class="sxs-lookup"><span data-stu-id="d2330-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="d2330-238">64</span><span class="sxs-lookup"><span data-stu-id="d2330-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="d2330-239">64</span><span class="sxs-lookup"><span data-stu-id="d2330-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="d2330-240">32</span><span class="sxs-lookup"><span data-stu-id="d2330-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="d2330-241">32</span><span class="sxs-lookup"><span data-stu-id="d2330-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="d2330-242">下列類型 (為指標) 確實按照平台的寬度。</span><span class="sxs-lookup"><span data-stu-id="d2330-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="d2330-243">將 `IntPtr`/`UIntPtr` 用於這些。</span><span class="sxs-lookup"><span data-stu-id="d2330-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="d2330-244">帶正負號指標類型 (使用 `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="d2330-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="d2330-245">不帶正負號指標類型 (使用 `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="d2330-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="d2330-246">Windows `PVOID` 是 C `void*`，可以作為 `IntPtr` 或 `UIntPtr` 來封送，但建議盡可能使用 `void*`。</span><span class="sxs-lookup"><span data-stu-id="d2330-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="d2330-247">Windows 資料類型</span><span class="sxs-lookup"><span data-stu-id="d2330-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="d2330-248">資料類型範圍</span><span class="sxs-lookup"><span data-stu-id="d2330-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="d2330-249">結構</span><span class="sxs-lookup"><span data-stu-id="d2330-249">Structs</span></span>

<span data-ttu-id="d2330-250">受控結構是在堆疊上建立的，直到方法傳回才會將它移除。</span><span class="sxs-lookup"><span data-stu-id="d2330-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="d2330-251">根據定義，他們是「固定的」(不會被 GC 移除)。</span><span class="sxs-lookup"><span data-stu-id="d2330-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="d2330-252">如果機器碼不使用目前方法結尾所傳遞的指標，您也可以直接接受不安全程式碼區塊中的位址。</span><span class="sxs-lookup"><span data-stu-id="d2330-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="d2330-253">Blittable 結構效能更好，因為封送處理層可以直接使用它們。</span><span class="sxs-lookup"><span data-stu-id="d2330-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="d2330-254">請嘗試讓結構是 Blittable 的 (例如，避免`bool`)。</span><span class="sxs-lookup"><span data-stu-id="d2330-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="d2330-255">如需詳細資訊，請參閱 [Blittable 類型](#blittable-types)一節。</span><span class="sxs-lookup"><span data-stu-id="d2330-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="d2330-256">「如果」\*\* 結構是 Blittable 的，為了獲得更好的效能，請使用 `sizeof()` 而不使用 `Marshal.SizeOf<MyStruct>()`。</span><span class="sxs-lookup"><span data-stu-id="d2330-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="d2330-257">如先前所述，您可以藉由嘗試建立固定的 `GCHandle`，以驗證類型是否為 Blittable 的。</span><span class="sxs-lookup"><span data-stu-id="d2330-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="d2330-258">如果該類型不是字串或被視為 Blittable，則 `GCHandle.Alloc` 會擲回 `ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="d2330-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="d2330-259">在定義中，結構的指標必須以 `ref` 傳遞，或者使用 `unsafe` 和 `*`。</span><span class="sxs-lookup"><span data-stu-id="d2330-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="d2330-260">✔️ 請這樣做 盡可能近似地對應受控結構與官方平台文件或標頭中所使用的圖形和名稱。</span><span class="sxs-lookup"><span data-stu-id="d2330-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="d2330-261">✔️ 請這樣做 針對 Blittable 結構使用 C# `sizeof()`，而不使用 `Marshal.SizeOf<MyStruct>()`，以改善效能。</span><span class="sxs-lookup"><span data-stu-id="d2330-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="d2330-262">❌避免使用`System.Delegate`或`System.MulticastDelegate`欄位來表示結構中的函式指標欄位。</span><span class="sxs-lookup"><span data-stu-id="d2330-262">❌ AVOID using `System.Delegate` or `System.MulticastDelegate` fields to represent function pointer fields in structures.</span></span>

<span data-ttu-id="d2330-263">由於<xref:System.Delegate?displayProperty=fullName>和<xref:System.MulticastDelegate?displayProperty=fullName>沒有所需的簽章，因此不保證傳入的委派會符合原生程式碼所預期的簽章。</span><span class="sxs-lookup"><span data-stu-id="d2330-263">Since <xref:System.Delegate?displayProperty=fullName> and <xref:System.MulticastDelegate?displayProperty=fullName> don't have a required signature, they don't guarantee that the delegate passed in will match the signature the native code expects.</span></span> <span data-ttu-id="d2330-264">此外，在 .NET Framework 和 .NET Core 中，如果原生表示`System.Delegate`法`System.MulticastDelegate`中的欄位值不是包裝 managed 委派的函式指標，則將包含或其原生標記法的結構封送處理至 managed 物件可能會使執行時間不穩定。</span><span class="sxs-lookup"><span data-stu-id="d2330-264">Additionally, in .NET Framework and .NET Core, marshaling a struct containing a `System.Delegate` or `System.MulticastDelegate` from its native representation to a managed object can destabilize the runtime if the value of the field in the native representation isn't a function pointer that wraps a managed delegate.</span></span> <span data-ttu-id="d2330-265">在 .NET 5 和更新版本中，不`System.Delegate`支援`System.MulticastDelegate`將或欄位從原生表示封送處理至 managed 物件。</span><span class="sxs-lookup"><span data-stu-id="d2330-265">In .NET 5 and later versions, marshaling a `System.Delegate` or `System.MulticastDelegate` field from a native representation to a managed object is not supported.</span></span> <span data-ttu-id="d2330-266">請使用特定的委派類型， `System.Delegate`而`System.MulticastDelegate`不是或。</span><span class="sxs-lookup"><span data-stu-id="d2330-266">Use a specific delegate type instead of `System.Delegate` or `System.MulticastDelegate`.</span></span>

### <a name="fixed-buffers"></a><span data-ttu-id="d2330-267">固定緩衝區</span><span class="sxs-lookup"><span data-stu-id="d2330-267">Fixed Buffers</span></span>

<span data-ttu-id="d2330-268">`INT_PTR Reserved1[2]` 之類的陣列必須封送至兩個 `IntPtr` 欄位：`Reserved1a` 和 `Reserved1b`。</span><span class="sxs-lookup"><span data-stu-id="d2330-268">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="d2330-269">當原生陣列是基本類型時，我們可以使用 `fixed` 關鍵字來將它撰寫得更簡潔一點。</span><span class="sxs-lookup"><span data-stu-id="d2330-269">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="d2330-270">例如，在原生標頭中 `SYSTEM_PROCESS_INFORMATION` 看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="d2330-270">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="d2330-271">在 C# 中，我們可以將它撰寫像這樣：</span><span class="sxs-lookup"><span data-stu-id="d2330-271">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="d2330-272">不過，固定的緩衝區有一些陷阱。</span><span class="sxs-lookup"><span data-stu-id="d2330-272">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="d2330-273">非 Blittable 類型的固定緩衝區不會正確地進行封送，因此需要將就地陣列展開成多個個別欄位。</span><span class="sxs-lookup"><span data-stu-id="d2330-273">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="d2330-274">此外，在 .NET Framework 和 .NET Core 3.0 之前，如果包含固定緩衝區欄位的結構是呈巢狀包含在非 Blittable 結構中，則該固定緩衝區欄位不會正確地封送至機器碼。</span><span class="sxs-lookup"><span data-stu-id="d2330-274">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
