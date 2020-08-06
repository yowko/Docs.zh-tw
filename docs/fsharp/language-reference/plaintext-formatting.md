---
title: 純文字格式
description: '瞭解如何在 F # 應用程式和腳本中使用 printf 和其他純文字格式。'
ms.date: 07/22/2020
ms.openlocfilehash: a0f2c52431be894c4f74dd2940345a518f620589
ms.sourcegitcommit: 09bad6ec0cbf18be7cd7f62e77286d305a18b607
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/05/2020
ms.locfileid: "87795743"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="5d44e-103">純文字格式</span><span class="sxs-lookup"><span data-stu-id="5d44e-103">Plain text formatting</span></span>

<span data-ttu-id="5d44e-104">F # 使用 `printf` 、 `printfn` 、和相關函式，支援純文字的類型檢查格式 `sprintf` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="5d44e-105">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="5d44e-106">提供輸出</span><span class="sxs-lookup"><span data-stu-id="5d44e-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="5d44e-107">F # 也允許將結構化值格式化為純文字。</span><span class="sxs-lookup"><span data-stu-id="5d44e-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="5d44e-108">例如，請考慮下列範例，其會將輸出格式化為類似矩陣的元組顯示。</span><span class="sxs-lookup"><span data-stu-id="5d44e-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="5d44e-109">當您 `%A` 在格式化字串中使用格式時，會啟用結構化純文字格式 `printf` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="5d44e-110">它也會在 F # interactive 中格式化值的輸出時啟用，其中輸出會包含額外的資訊，而且還可自訂。</span><span class="sxs-lookup"><span data-stu-id="5d44e-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="5d44e-111">純文字格式也可透過任何對 `x.ToString()` F # union 和記錄值的呼叫來觀察，包括在偵錯工具、記錄和其他工具中隱含發生的。</span><span class="sxs-lookup"><span data-stu-id="5d44e-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="5d44e-112">檢查 `printf` 格式字串</span><span class="sxs-lookup"><span data-stu-id="5d44e-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="5d44e-113">如果 `printf` 使用格式函數搭配的引數與格式字串中的 printf 格式規範不相符，就會回報編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d44e-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="5d44e-114">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="5d44e-115">提供輸出</span><span class="sxs-lookup"><span data-stu-id="5d44e-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="5d44e-116">技術上而言，當使用 `printf` 和其他相關函式時，F # 編譯器中的特殊規則會檢查當做格式字串傳遞的字串常值，確保後續套用的引數是正確的類型，以符合所使用的格式規範。</span><span class="sxs-lookup"><span data-stu-id="5d44e-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="5d44e-117">的格式規範`printf`</span><span class="sxs-lookup"><span data-stu-id="5d44e-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="5d44e-118">格式規格 `printf` 是具有 `%` 標記的字串，表示格式。</span><span class="sxs-lookup"><span data-stu-id="5d44e-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="5d44e-119">格式預留位置是由類型的解讀方式所組成 `%[flags][width][.precision][type]` ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d44e-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="5d44e-120">格式規範</span><span class="sxs-lookup"><span data-stu-id="5d44e-120">Format specifier</span></span>   | <span data-ttu-id="5d44e-121">輸入 (s) </span><span class="sxs-lookup"><span data-stu-id="5d44e-121">Type(s)</span></span>        | <span data-ttu-id="5d44e-122">備註</span><span class="sxs-lookup"><span data-stu-id="5d44e-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="5d44e-123">bool</span><span class="sxs-lookup"><span data-stu-id="5d44e-123">bool</span></span>      | <span data-ttu-id="5d44e-124">格式化為 `true` 或`false`</span><span class="sxs-lookup"><span data-stu-id="5d44e-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="5d44e-125">字串</span><span class="sxs-lookup"><span data-stu-id="5d44e-125">string</span></span>    | <span data-ttu-id="5d44e-126">格式化為其非的非格式內容</span><span class="sxs-lookup"><span data-stu-id="5d44e-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="5d44e-127">char</span><span class="sxs-lookup"><span data-stu-id="5d44e-127">char</span></span>      | <span data-ttu-id="5d44e-128">格式化為字元常值</span><span class="sxs-lookup"><span data-stu-id="5d44e-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="5d44e-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="5d44e-129">`%d`, `%i`</span></span>         | <span data-ttu-id="5d44e-130">基本整數類型</span><span class="sxs-lookup"><span data-stu-id="5d44e-130">a basic integer type</span></span> | <span data-ttu-id="5d44e-131">格式化為十進位整數，如果基本整數類型已簽署，則為帶正負號</span><span class="sxs-lookup"><span data-stu-id="5d44e-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="5d44e-132">基本整數類型</span><span class="sxs-lookup"><span data-stu-id="5d44e-132">a basic integer type</span></span> | <span data-ttu-id="5d44e-133">格式化為不帶正負號的十進位整數</span><span class="sxs-lookup"><span data-stu-id="5d44e-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="5d44e-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="5d44e-134">`%x`, `%X`</span></span>         | <span data-ttu-id="5d44e-135">基本整數類型</span><span class="sxs-lookup"><span data-stu-id="5d44e-135">a basic integer type</span></span> | <span data-ttu-id="5d44e-136">已格式化為不帶正負號的十六進位數位 (-f 或-F 分別用於十六進位數位) </span><span class="sxs-lookup"><span data-stu-id="5d44e-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="5d44e-137">基本整數類型</span><span class="sxs-lookup"><span data-stu-id="5d44e-137">a basic integer type</span></span> | <span data-ttu-id="5d44e-138">格式化為不帶正負號的八進位數位</span><span class="sxs-lookup"><span data-stu-id="5d44e-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="5d44e-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="5d44e-139">`%e`, `%E`</span></span>         | <span data-ttu-id="5d44e-140">基本浮點類型</span><span class="sxs-lookup"><span data-stu-id="5d44e-140">a basic floating point type</span></span> | <span data-ttu-id="5d44e-141">格式化為具有格式的帶正負號值 `[-]d.dddde[sign]ddd` ，其中 d 是單一十進位數，dddd 是一或多個十進位數，ddd 只是三個小數位數，而 sign 是 `+` 或`-`</span><span class="sxs-lookup"><span data-stu-id="5d44e-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="5d44e-142">基本浮點類型</span><span class="sxs-lookup"><span data-stu-id="5d44e-142">a basic floating point type</span></span> | <span data-ttu-id="5d44e-143">格式化為具有格式的帶正負號值 `[-]dddd.dddd` ，其中 `dddd` 是一或多個十進位數。</span><span class="sxs-lookup"><span data-stu-id="5d44e-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="5d44e-144">小數點前面的位數取決於數字的大小，小數點後面的位數則取決於要求的精確度。</span><span class="sxs-lookup"><span data-stu-id="5d44e-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="5d44e-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="5d44e-145">`%g`, `%G`</span></span> | <span data-ttu-id="5d44e-146">基本浮點類型</span><span class="sxs-lookup"><span data-stu-id="5d44e-146">a basic floating point type</span></span> |  <span data-ttu-id="5d44e-147">使用當做以或格式列印的帶正負號值進行格式化，以較 `%f` `%e` 精簡的指定值和有效位數為准。</span><span class="sxs-lookup"><span data-stu-id="5d44e-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="5d44e-148">`System.Decimal`值</span><span class="sxs-lookup"><span data-stu-id="5d44e-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="5d44e-149">使用的 `"G"` 格式標準格式化`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="5d44e-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="5d44e-150">任何值</span><span class="sxs-lookup"><span data-stu-id="5d44e-150">any value</span></span>  |   <span data-ttu-id="5d44e-151">藉由將物件裝箱並 valling 其方法來進行格式化 `System.Object.ToString()`</span><span class="sxs-lookup"><span data-stu-id="5d44e-151">Formatted by boxing the object and valling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="5d44e-152">任何值</span><span class="sxs-lookup"><span data-stu-id="5d44e-152">any value</span></span>  |   <span data-ttu-id="5d44e-153">使用預設版面配置設定，以[結構化純文字格式](plaintext-formatting.md)格式化</span><span class="sxs-lookup"><span data-stu-id="5d44e-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="5d44e-154">任何值</span><span class="sxs-lookup"><span data-stu-id="5d44e-154">any value</span></span>  |   <span data-ttu-id="5d44e-155">需要兩個引數-格式函數接受內容參數和值，以及要列印的特定值</span><span class="sxs-lookup"><span data-stu-id="5d44e-155">Requires two arguments - a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="5d44e-156">任何值</span><span class="sxs-lookup"><span data-stu-id="5d44e-156">any value</span></span>  |   <span data-ttu-id="5d44e-157">需要一個引數，格式函式會接受內容參數，以輸出或傳回適當的文字。</span><span class="sxs-lookup"><span data-stu-id="5d44e-157">Requires one argument, a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |

<span data-ttu-id="5d44e-158">基本整數類型 `byte` (`System.Byte`) 、 `sbyte` (`System.SByte`) 、 `int16` (`System.Int16`) 、 `uint16` (`System.UInt16`) 、 `int32` (`System.Int32`) 、 `uint32` (`System.UInt32`) 、 `int64` (`System.Int64`) 、 `uint64` (`System.UInt64`) 、 `nativeint` (`System.IntPtr`) 和 () `unativeint` `System.UIntPtr` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-158">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="5d44e-159">基本浮點類型 `float` (`System.Double`) 和 `float32` (`System.Single`) 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-159">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="5d44e-160">選擇性寬度是一個整數，表示結果的最小寬度。</span><span class="sxs-lookup"><span data-stu-id="5d44e-160">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="5d44e-161">例如， `%6d` 會列印一個整數，並在前面加上空格，以填補至少6個字元。</span><span class="sxs-lookup"><span data-stu-id="5d44e-161">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least 6 characters.</span></span> <span data-ttu-id="5d44e-162">如果 width 為 `*` ，則會採用額外的整數引數來指定對應的寬度。</span><span class="sxs-lookup"><span data-stu-id="5d44e-162">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="5d44e-163">有效的旗標如下：</span><span class="sxs-lookup"><span data-stu-id="5d44e-163">Valid flags are:</span></span>

| <span data-ttu-id="5d44e-164">旗標</span><span class="sxs-lookup"><span data-stu-id="5d44e-164">Flag</span></span>   | <span data-ttu-id="5d44e-165">效果</span><span class="sxs-lookup"><span data-stu-id="5d44e-165">Effect</span></span>        | <span data-ttu-id="5d44e-166">備註</span><span class="sxs-lookup"><span data-stu-id="5d44e-166">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="5d44e-167">新增零（而不是空格）來組成所需的寬度</span><span class="sxs-lookup"><span data-stu-id="5d44e-167">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="5d44e-168">靠左對齊指定寬度內的結果</span><span class="sxs-lookup"><span data-stu-id="5d44e-168">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="5d44e-169">`+`如果數位是正數 (以符合否定的正負號，請新增一個字元 `-`) </span><span class="sxs-lookup"><span data-stu-id="5d44e-169">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="5d44e-170">空白字元</span><span class="sxs-lookup"><span data-stu-id="5d44e-170">space character</span></span> | <span data-ttu-id="5d44e-171">如果數位是正數 (以符合否定的 '-' 正負號，請新增額外的空間) </span><span class="sxs-lookup"><span data-stu-id="5d44e-171">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="5d44e-172">Printf `#` 旗標無效，如果使用，將會回報編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d44e-172">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="5d44e-173">值是使用不因文化特性而異的格式。</span><span class="sxs-lookup"><span data-stu-id="5d44e-173">Values are formatted using invariant culture.</span></span> <span data-ttu-id="5d44e-174">文化特性設定與格式無關， `printf` 不同之處在于它們會影響 `%O` 和格式化的結果 `%A` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-174">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="5d44e-175">如需詳細資訊，請參閱[結構化純文字格式](plaintext-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="5d44e-175">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="5d44e-176">`%A`樣式</span><span class="sxs-lookup"><span data-stu-id="5d44e-176">`%A` formatting</span></span>

<span data-ttu-id="5d44e-177">`%A`格式規範是用來以人類看得懂的方式來格式化值，也適用于報告診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="5d44e-177">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="5d44e-178">基本值</span><span class="sxs-lookup"><span data-stu-id="5d44e-178">Primitive values</span></span>

<span data-ttu-id="5d44e-179">使用規範來格式化純文字時 `%A` ，F # 數值會使用其後綴和不因文化特性而異。</span><span class="sxs-lookup"><span data-stu-id="5d44e-179">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="5d44e-180">使用浮點精確度的10個位置來格式化浮點值。</span><span class="sxs-lookup"><span data-stu-id="5d44e-180">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="5d44e-181">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-181">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="5d44e-182">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-182">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="5d44e-183">使用規範時 `%A` ，字串會使用引號來格式化。</span><span class="sxs-lookup"><span data-stu-id="5d44e-183">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="5d44e-184">不會新增轉義碼，而是會列印原始字元。</span><span class="sxs-lookup"><span data-stu-id="5d44e-184">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="5d44e-185">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-185">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="5d44e-186">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-186">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="5d44e-187">.NET 值</span><span class="sxs-lookup"><span data-stu-id="5d44e-187">.NET values</span></span>

<span data-ttu-id="5d44e-188">使用規範來格式化純文字時 `%A` ，非 F # .net 物件是使用 `x.ToString()` 和所指定的 .net 預設設定來格式化 `System.Globalization.CultureInfo.CurrentCulture` `System.Globalization.CultureInfo.CurrentUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-188">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="5d44e-189">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-189">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="5d44e-190">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-190">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="5d44e-191">結構化值</span><span class="sxs-lookup"><span data-stu-id="5d44e-191">Structured values</span></span>

<span data-ttu-id="5d44e-192">使用規範來格式化純文字時 `%A` ，區塊縮排會用於 F # 清單和元組。</span><span class="sxs-lookup"><span data-stu-id="5d44e-192">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="5d44e-193">如上一個範例所示。</span><span class="sxs-lookup"><span data-stu-id="5d44e-193">The is shown in the previous example.</span></span>
<span data-ttu-id="5d44e-194">陣列的結構也會使用，包括多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="5d44e-194">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="5d44e-195">一維陣列會以語法顯示 `[| ... |]` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-195">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="5d44e-196">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-196">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="5d44e-197">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-197">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="5d44e-198">預設列印寬度為80。</span><span class="sxs-lookup"><span data-stu-id="5d44e-198">The default print width is 80.</span></span>  <span data-ttu-id="5d44e-199">您可以使用格式規範中的列印寬度來自訂此寬度。</span><span class="sxs-lookup"><span data-stu-id="5d44e-199">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="5d44e-200">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-200">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="5d44e-201">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-201">produces</span></span>

```console
[|(1, 1);
  (2, 4);
  (3, 9);
  (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4);
  (3, 9); (4, 16);
  (5, 25)|]
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
```

<span data-ttu-id="5d44e-202">將列印寬度指定為0會導致不使用列印寬度。</span><span class="sxs-lookup"><span data-stu-id="5d44e-202">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="5d44e-203">會產生單行文字，但輸出中的內嵌字串本身會包含分行符號。</span><span class="sxs-lookup"><span data-stu-id="5d44e-203">A single line of text will result, except where embedded strings in the output themselves contain linebreaks.</span></span>  <span data-ttu-id="5d44e-204">例如：</span><span class="sxs-lookup"><span data-stu-id="5d44e-204">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef |]
```

<span data-ttu-id="5d44e-205">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-205">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="5d44e-206">深度限制4用於順序 (`IEnumerable`) 值，這會顯示為 `seq { ...}` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-206">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="5d44e-207">[深度限制] 100 用於清單和陣列值。</span><span class="sxs-lookup"><span data-stu-id="5d44e-207">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="5d44e-208">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-208">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="5d44e-209">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-209">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="5d44e-210">區塊縮排也會用於公用記錄和聯集值的結構。</span><span class="sxs-lookup"><span data-stu-id="5d44e-210">Block indentation is also used for the the structure of public record and union values.</span></span> <span data-ttu-id="5d44e-211">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-211">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="5d44e-212">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-212">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="5d44e-213">如果 `%+A` 使用了，則也會使用反映來顯示記錄和等位的私用結構。</span><span class="sxs-lookup"><span data-stu-id="5d44e-213">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="5d44e-214">例如：</span><span class="sxs-lookup"><span data-stu-id="5d44e-214">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="5d44e-215">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-215">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="5d44e-216">大型、迴圈或深層的嵌套值</span><span class="sxs-lookup"><span data-stu-id="5d44e-216">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="5d44e-217">大型結構化的值會格式化為最大整體物件節點計數10000。</span><span class="sxs-lookup"><span data-stu-id="5d44e-217">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="5d44e-218">深層的嵌套值會格式化為深度100。</span><span class="sxs-lookup"><span data-stu-id="5d44e-218">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="5d44e-219">在這兩種情況下 `...` ，都是用來省略部分輸出。</span><span class="sxs-lookup"><span data-stu-id="5d44e-219">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="5d44e-220">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-220">For example,</span></span>

```fsharp
type Tree =
    | Tip
    | Node of Tree * Tree

let rec make n =
    if n = 0 then
        Tip
    else
        Node(Tip, make (n-1))

printfn "%A" (make 1000)
```

<span data-ttu-id="5d44e-221">會產生具有部分省略的大型輸出：</span><span class="sxs-lookup"><span data-stu-id="5d44e-221">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="5d44e-222">迴圈會在物件圖形中偵測到，並在偵測 `...` 到迴圈的位置使用。</span><span class="sxs-lookup"><span data-stu-id="5d44e-222">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="5d44e-223">例如：</span><span class="sxs-lookup"><span data-stu-id="5d44e-223">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="5d44e-224">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-224">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="5d44e-225">Lazy、null 和 function 值</span><span class="sxs-lookup"><span data-stu-id="5d44e-225">Lazy, null, and function values</span></span>

<span data-ttu-id="5d44e-226">當尚未評估值時，延遲值會列印成 `Value is not created` 或對等的文字。</span><span class="sxs-lookup"><span data-stu-id="5d44e-226">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="5d44e-227">Null 值會列印成， `null` 除非將值的靜態類型判斷為可允許表示的聯集類型 `null` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-227">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted represenation.</span></span>

<span data-ttu-id="5d44e-228">F # 函式值會列印為其內部產生的關閉名稱，例如 `<fun:it@43-7>` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-228">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="5d44e-229">使用自訂純文字格式`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="5d44e-229">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="5d44e-230">使用規範時 `%A` ， `StructuredFormatDisplay` 會遵守類型宣告上的屬性是否存在。</span><span class="sxs-lookup"><span data-stu-id="5d44e-230">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="5d44e-231">這可用來指定用來顯示值的代理文字和屬性。</span><span class="sxs-lookup"><span data-stu-id="5d44e-231">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="5d44e-232">例如：</span><span class="sxs-lookup"><span data-stu-id="5d44e-232">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="5d44e-233">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-233">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="5d44e-234">藉由覆寫自訂純文字格式`ToString`</span><span class="sxs-lookup"><span data-stu-id="5d44e-234">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="5d44e-235">的預設執行 `ToString` 在 F # 程式設計中是可觀察的。</span><span class="sxs-lookup"><span data-stu-id="5d44e-235">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="5d44e-236">通常，預設結果不適合在程式設計人員面向的資訊顯示或使用者輸出中使用，因此，通常會覆寫預設的執行。</span><span class="sxs-lookup"><span data-stu-id="5d44e-236">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="5d44e-237">根據預設，F # 記錄和聯集類型會以使用的執行來覆寫的執行 `ToString` `sprintf "%+A"` 。</span><span class="sxs-lookup"><span data-stu-id="5d44e-237">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="5d44e-238">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-238">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="5d44e-239">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-239">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="5d44e-240">針對類別類型，不會提供的預設實作為， `ToString` 而且會使用 .net 預設值，這會報告類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="5d44e-240">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="5d44e-241">例如</span><span class="sxs-lookup"><span data-stu-id="5d44e-241">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="5d44e-242">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-242">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="5d44e-243">新增的覆寫 `ToString` 可以提供更好的格式。</span><span class="sxs-lookup"><span data-stu-id="5d44e-243">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="5d44e-244">塊</span><span class="sxs-lookup"><span data-stu-id="5d44e-244">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="5d44e-245">F # 互動式結構化列印</span><span class="sxs-lookup"><span data-stu-id="5d44e-245">F# Interactive structured printing</span></span>

<span data-ttu-id="5d44e-246">F # Interactive (`dotnet fsi`) 會使用延伸版本的結構化純文字格式來報告值，並允許其他自訂能力。</span><span class="sxs-lookup"><span data-stu-id="5d44e-246">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="5d44e-247">如需詳細資訊，請參閱[F # Interactive](fsharp-interactive-options.md)。</span><span class="sxs-lookup"><span data-stu-id="5d44e-247">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="5d44e-248">自訂 debug 顯示</span><span class="sxs-lookup"><span data-stu-id="5d44e-248">Customize debug displays</span></span>

<span data-ttu-id="5d44e-249">適用于 .NET 的偵錯工具會使用和之類的屬性 `DebuggerDisplay` `DebuggerTypeProxy` ，而且這些屬性會影響偵錯工具檢查視窗中物件的結構化顯示。</span><span class="sxs-lookup"><span data-stu-id="5d44e-249">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="5d44e-250">F # 編譯器會針對區分聯集和記錄類型自動產生這些屬性，但不會針對類別、介面或結構類型來產生。</span><span class="sxs-lookup"><span data-stu-id="5d44e-250">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="5d44e-251">F # 純文字格式會忽略這些屬性，但在進行 F # 型別的調試時，執行這些方法以改善顯示會很有用。</span><span class="sxs-lookup"><span data-stu-id="5d44e-251">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d44e-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d44e-252">See also</span></span>

- [<span data-ttu-id="5d44e-253">字串</span><span class="sxs-lookup"><span data-stu-id="5d44e-253">Strings</span></span>](strings.md)
- [<span data-ttu-id="5d44e-254">記錄</span><span class="sxs-lookup"><span data-stu-id="5d44e-254">Records</span></span>](records.md)
- [<span data-ttu-id="5d44e-255">差別聯集</span><span class="sxs-lookup"><span data-stu-id="5d44e-255">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="5d44e-256">F# 互動</span><span class="sxs-lookup"><span data-stu-id="5d44e-256">F# Interactive</span></span>](fsharp-interactive-options.md)
