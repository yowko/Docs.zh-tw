---
title: 純文字格式
description: '瞭解如何在 F # 應用程式和腳本中使用 printf 和其他純文字格式。'
ms.date: 07/22/2020
ms.openlocfilehash: 90a861736dae69dfbc199a19e24f587c42404737
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063779"
---
# <a name="plain-text-formatting"></a><span data-ttu-id="c3068-103">純文字格式</span><span class="sxs-lookup"><span data-stu-id="c3068-103">Plain text formatting</span></span>

<span data-ttu-id="c3068-104">F # 使用 `printf` 、 `printfn` 、和相關函式，支援純文字的類型檢查格式 `sprintf` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-104">F# supports type-checked formatting of plain text using `printf`, `printfn`, `sprintf`, and related functions.</span></span>
<span data-ttu-id="c3068-105">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-105">For example,</span></span>

```console
dotnet fsi

> printfn "Hello %s, %d + %d is %d" "world" 2 2 (2+2);;
```

<span data-ttu-id="c3068-106">提供輸出</span><span class="sxs-lookup"><span data-stu-id="c3068-106">gives the output</span></span>

```fsharp
Hello world, 2 + 2 is 4
```

<span data-ttu-id="c3068-107">F # 也允許將結構化值格式化為純文字。</span><span class="sxs-lookup"><span data-stu-id="c3068-107">F# also allows structured values to be formatted as plain text.</span></span>
<span data-ttu-id="c3068-108">例如，請考慮下列範例，其會將輸出格式化為類似矩陣的元組顯示。</span><span class="sxs-lookup"><span data-stu-id="c3068-108">For example, consider the following example that formats the output as a matrix-like display of tuples.</span></span>

```console
dotnet fsi

> printfn "%A" [ for i in 1 .. 5 -> [ for j in 1 .. 5 -> (i, j) ] ];;

[[(1, 1); (1, 2); (1, 3); (1, 4); (1, 5)];
 [(2, 1); (2, 2); (2, 3); (2, 4); (2, 5)];
 [(3, 1); (3, 2); (3, 3); (3, 4); (3, 5)];
 [(4, 1); (4, 2); (4, 3); (4, 4); (4, 5)];
 [(5, 1); (5, 2); (5, 3); (5, 4); (5, 5)]]
```

<span data-ttu-id="c3068-109">當您 `%A` 在格式化字串中使用格式時，會啟用結構化純文字格式 `printf` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-109">Structured plain text formatting is activated when you use the `%A` format in `printf` formatting strings.</span></span>
<span data-ttu-id="c3068-110">它也會在 F # interactive 中格式化值的輸出時啟用，其中輸出會包含額外的資訊，而且還可自訂。</span><span class="sxs-lookup"><span data-stu-id="c3068-110">It's also activated when formatting the output of values in F# interactive, where the output includes extra information and is additionally customizable.</span></span>
<span data-ttu-id="c3068-111">純文字格式也可透過任何對 `x.ToString()` F # union 和記錄值的呼叫來觀察，包括在偵錯工具、記錄和其他工具中隱含發生的。</span><span class="sxs-lookup"><span data-stu-id="c3068-111">Plain text formatting is also observable through any calls to `x.ToString()` on F# union and record values, including those that occur implicitly in debugging, logging, and other tooling.</span></span>

## <a name="checking-of-printf-format-strings"></a><span data-ttu-id="c3068-112">檢查 `printf` 格式字串</span><span class="sxs-lookup"><span data-stu-id="c3068-112">Checking of `printf`-format strings</span></span>

<span data-ttu-id="c3068-113">如果 `printf` 使用格式函數搭配的引數與格式字串中的 printf 格式規範不相符，就會回報編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3068-113">A compile-time error will be reported if a `printf` formatting function is used with an argument that doesn't match the printf format specifiers in the format string.</span></span>  <span data-ttu-id="c3068-114">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-114">For example,</span></span>

```fsharp
sprintf "Hello %s" (2+2)
```

<span data-ttu-id="c3068-115">提供輸出</span><span class="sxs-lookup"><span data-stu-id="c3068-115">gives the output</span></span>

```console
  sprintf "Hello %s" (2+2)
  ----------------------^

stdin(3,25): error FS0001: The type 'string' does not match the type 'int'
```

<span data-ttu-id="c3068-116">技術上而言，當使用 `printf` 和其他相關函式時，F # 編譯器中的特殊規則會檢查當做格式字串傳遞的字串常值，確保後續套用的引數是正確的類型，以符合所使用的格式規範。</span><span class="sxs-lookup"><span data-stu-id="c3068-116">Technically speaking, when using `printf` and other related functions, a special rule in the F# compiler checks the string literal passed as the format string, ensuring the subsequent arguments applied are of the correct type to match the format specifiers used.</span></span>

## <a name="format-specifiers-for-printf"></a><span data-ttu-id="c3068-117">的格式規範`printf`</span><span class="sxs-lookup"><span data-stu-id="c3068-117">Format specifiers for `printf`</span></span>

<span data-ttu-id="c3068-118">格式規格 `printf` 是具有 `%` 標記的字串，表示格式。</span><span class="sxs-lookup"><span data-stu-id="c3068-118">Format specifications for `printf` formats are strings with `%` markers that indicate format.</span></span> <span data-ttu-id="c3068-119">格式預留位置是由類型的解讀方式所組成 `%[flags][width][.precision][type]` ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c3068-119">Format placeholders consist of `%[flags][width][.precision][type]` where the type is interpreted as follows:</span></span>

| <span data-ttu-id="c3068-120">格式規範</span><span class="sxs-lookup"><span data-stu-id="c3068-120">Format specifier</span></span>   | <span data-ttu-id="c3068-121">輸入 (s) </span><span class="sxs-lookup"><span data-stu-id="c3068-121">Type(s)</span></span>        | <span data-ttu-id="c3068-122">備註</span><span class="sxs-lookup"><span data-stu-id="c3068-122">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `%b`               | <span data-ttu-id="c3068-123">bool</span><span class="sxs-lookup"><span data-stu-id="c3068-123">bool</span></span>      | <span data-ttu-id="c3068-124">格式化為 `true` 或`false`</span><span class="sxs-lookup"><span data-stu-id="c3068-124">Formatted as `true` or `false`</span></span>                |
| `%s`               | <span data-ttu-id="c3068-125">字串</span><span class="sxs-lookup"><span data-stu-id="c3068-125">string</span></span>    | <span data-ttu-id="c3068-126">格式化為其非的非格式內容</span><span class="sxs-lookup"><span data-stu-id="c3068-126">Formatted as its unescaped contents</span></span>         |
| `%c`               | <span data-ttu-id="c3068-127">char</span><span class="sxs-lookup"><span data-stu-id="c3068-127">char</span></span>      | <span data-ttu-id="c3068-128">格式化為字元常值</span><span class="sxs-lookup"><span data-stu-id="c3068-128">Formatted as the character literal</span></span>  |
| <span data-ttu-id="c3068-129">`%d`, `%i`</span><span class="sxs-lookup"><span data-stu-id="c3068-129">`%d`, `%i`</span></span>         | <span data-ttu-id="c3068-130">基本整數類型</span><span class="sxs-lookup"><span data-stu-id="c3068-130">a basic integer type</span></span> | <span data-ttu-id="c3068-131">格式化為十進位整數，如果基本整數類型已簽署，則為帶正負號</span><span class="sxs-lookup"><span data-stu-id="c3068-131">Formatted as a decimal integer, signed if the basic integer type is signed</span></span> |
| `%u`               | <span data-ttu-id="c3068-132">基本整數類型</span><span class="sxs-lookup"><span data-stu-id="c3068-132">a basic integer type</span></span> | <span data-ttu-id="c3068-133">格式化為不帶正負號的十進位整數</span><span class="sxs-lookup"><span data-stu-id="c3068-133">Formatted as an unsigned decimal integer</span></span>   |
| <span data-ttu-id="c3068-134">`%x`, `%X`</span><span class="sxs-lookup"><span data-stu-id="c3068-134">`%x`, `%X`</span></span>         | <span data-ttu-id="c3068-135">基本整數類型</span><span class="sxs-lookup"><span data-stu-id="c3068-135">a basic integer type</span></span> | <span data-ttu-id="c3068-136">已格式化為不帶正負號的十六進位數位 (-f 或-F 分別用於十六進位數位) </span><span class="sxs-lookup"><span data-stu-id="c3068-136">Formatted as an unsigned hexadecimal number (a-f or A-F for hex digits respectively)</span></span>  |
|  `%o`              | <span data-ttu-id="c3068-137">基本整數類型</span><span class="sxs-lookup"><span data-stu-id="c3068-137">a basic integer type</span></span> | <span data-ttu-id="c3068-138">格式化為不帶正負號的八進位數位</span><span class="sxs-lookup"><span data-stu-id="c3068-138">Formatted as an unsigned octal number</span></span> |
| <span data-ttu-id="c3068-139">`%e`, `%E`</span><span class="sxs-lookup"><span data-stu-id="c3068-139">`%e`, `%E`</span></span>         | <span data-ttu-id="c3068-140">基本浮點類型</span><span class="sxs-lookup"><span data-stu-id="c3068-140">a basic floating point type</span></span> | <span data-ttu-id="c3068-141">格式化為具有格式的帶正負號值 `[-]d.dddde[sign]ddd` ，其中 d 是單一十進位數，dddd 是一或多個十進位數，ddd 只是三個小數位數，而 sign 是 `+` 或`-`</span><span class="sxs-lookup"><span data-stu-id="c3068-141">Formatted as a signed value having the form `[-]d.dddde[sign]ddd` where d is a single decimal digit, dddd is one or more decimal digits, ddd is exactly three decimal digits, and sign is `+` or `-`</span></span> |
| `%f`               | <span data-ttu-id="c3068-142">基本浮點類型</span><span class="sxs-lookup"><span data-stu-id="c3068-142">a basic floating point type</span></span> | <span data-ttu-id="c3068-143">格式化為具有格式的帶正負號值 `[-]dddd.dddd` ，其中 `dddd` 是一或多個十進位數。</span><span class="sxs-lookup"><span data-stu-id="c3068-143">Formatted as a signed value having the form `[-]dddd.dddd`, where `dddd` is one or more decimal digits.</span></span> <span data-ttu-id="c3068-144">小數點前面的位數取決於數字的大小，小數點後面的位數則取決於要求的精確度。</span><span class="sxs-lookup"><span data-stu-id="c3068-144">The number of digits before the decimal point depends on the magnitude of the number, and the number of digits after the decimal point depends on the requested precision.</span></span> |
| <span data-ttu-id="c3068-145">`%g`, `%G`</span><span class="sxs-lookup"><span data-stu-id="c3068-145">`%g`, `%G`</span></span> | <span data-ttu-id="c3068-146">基本浮點類型</span><span class="sxs-lookup"><span data-stu-id="c3068-146">a basic floating point type</span></span> |  <span data-ttu-id="c3068-147">使用當做以或格式列印的帶正負號值進行格式化，以較 `%f` `%e` 精簡的指定值和有效位數為准。</span><span class="sxs-lookup"><span data-stu-id="c3068-147">Formatted using as a signed value printed in `%f` or `%e` format, whichever is more compact for the given value and precision.</span></span> |
| `%M` | <span data-ttu-id="c3068-148">`System.Decimal`值</span><span class="sxs-lookup"><span data-stu-id="c3068-148">a `System.Decimal` value</span></span>  |    <span data-ttu-id="c3068-149">使用的 `"G"` 格式標準格式化`System.Decimal.ToString(format)`</span><span class="sxs-lookup"><span data-stu-id="c3068-149">Formatted using the `"G"` format specifier for `System.Decimal.ToString(format)`</span></span> |
| `%O` | <span data-ttu-id="c3068-150">任何值</span><span class="sxs-lookup"><span data-stu-id="c3068-150">any value</span></span>  |   <span data-ttu-id="c3068-151">藉由將物件裝箱並呼叫其方法來進行格式化 `System.Object.ToString()`</span><span class="sxs-lookup"><span data-stu-id="c3068-151">Formatted by boxing the object and calling its `System.Object.ToString()` method</span></span> |
| `%A` | <span data-ttu-id="c3068-152">任何值</span><span class="sxs-lookup"><span data-stu-id="c3068-152">any value</span></span>  |   <span data-ttu-id="c3068-153">使用預設版面配置設定，以[結構化純文字格式](plaintext-formatting.md)格式化</span><span class="sxs-lookup"><span data-stu-id="c3068-153">Formatted using [structured plain text formatting](plaintext-formatting.md) with the default layout settings</span></span> |
| `%a` | <span data-ttu-id="c3068-154">任何值</span><span class="sxs-lookup"><span data-stu-id="c3068-154">any value</span></span>  |   <span data-ttu-id="c3068-155">需要兩個引數：格式函數接受內容參數和值，以及要列印的特定值</span><span class="sxs-lookup"><span data-stu-id="c3068-155">Requires two arguments: a formatting function accepting a context parameter and the value, and the particular value to print</span></span> |
| `%t` | <span data-ttu-id="c3068-156">任何值</span><span class="sxs-lookup"><span data-stu-id="c3068-156">any value</span></span>  |   <span data-ttu-id="c3068-157">需要一個引數：格式化函數接受內容參數，以輸出或傳回適當的文字</span><span class="sxs-lookup"><span data-stu-id="c3068-157">Requires one argument: a formatting function accepting a context parameter that either outputs or returns the appropriate text</span></span> |
| `%%` | <span data-ttu-id="c3068-158">(無)</span><span class="sxs-lookup"><span data-stu-id="c3068-158">(none)</span></span>  |   <span data-ttu-id="c3068-159">不需要任何引數，而且會列印純量的字元：`%`</span><span class="sxs-lookup"><span data-stu-id="c3068-159">Requires no arguments and prints a plain percent sign: `%`</span></span> |

<span data-ttu-id="c3068-160">基本整數類型 `byte` (`System.Byte`) 、 `sbyte` (`System.SByte`) 、 `int16` (`System.Int16`) 、 `uint16` (`System.UInt16`) 、 `int32` (`System.Int32`) 、 `uint32` (`System.UInt32`) 、 `int64` (`System.Int64`) 、 `uint64` (`System.UInt64`) 、 `nativeint` (`System.IntPtr`) 和 () `unativeint` `System.UIntPtr` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-160">Basic integer types are `byte` (`System.Byte`), `sbyte` (`System.SByte`), `int16` (`System.Int16`), `uint16` (`System.UInt16`), `int32` (`System.Int32`), `uint32` (`System.UInt32`), `int64` (`System.Int64`), `uint64` (`System.UInt64`), `nativeint`  (`System.IntPtr`), and `unativeint`  (`System.UIntPtr`).</span></span>
<span data-ttu-id="c3068-161">基本浮點類型 `float` (`System.Double`) 和 `float32` (`System.Single`) 。</span><span class="sxs-lookup"><span data-stu-id="c3068-161">Basic floating point types are `float` (`System.Double`) and `float32` (`System.Single`).</span></span>

<span data-ttu-id="c3068-162">選擇性寬度是一個整數，表示結果的最小寬度。</span><span class="sxs-lookup"><span data-stu-id="c3068-162">The optional width is an integer indicating the minimal width of the result.</span></span> <span data-ttu-id="c3068-163">例如， `%6d` 會列印一個整數，並在前面加上空格，以填滿至少六個字元。</span><span class="sxs-lookup"><span data-stu-id="c3068-163">For instance, `%6d` prints an integer, prefixing it with spaces to fill at least six characters.</span></span> <span data-ttu-id="c3068-164">如果 width 為 `*` ，則會採用額外的整數引數來指定對應的寬度。</span><span class="sxs-lookup"><span data-stu-id="c3068-164">If width is `*`, then an extra integer  argument is taken to specify the corresponding width.</span></span>

<span data-ttu-id="c3068-165">有效的旗標如下：</span><span class="sxs-lookup"><span data-stu-id="c3068-165">Valid flags are:</span></span>

| <span data-ttu-id="c3068-166">旗標</span><span class="sxs-lookup"><span data-stu-id="c3068-166">Flag</span></span>   | <span data-ttu-id="c3068-167">效果</span><span class="sxs-lookup"><span data-stu-id="c3068-167">Effect</span></span>        | <span data-ttu-id="c3068-168">備註</span><span class="sxs-lookup"><span data-stu-id="c3068-168">Remarks</span></span>                      |
|:-------------------|:---------------|:-----------------------------|
| `0`  | <span data-ttu-id="c3068-169">新增零（而不是空格）來組成所需的寬度</span><span class="sxs-lookup"><span data-stu-id="c3068-169">Add zeros instead of spaces to make up the required width</span></span> |    |
| `-` |  <span data-ttu-id="c3068-170">靠左對齊指定寬度內的結果</span><span class="sxs-lookup"><span data-stu-id="c3068-170">Left justify the result within the specified width</span></span> |   |
| `+`  | <span data-ttu-id="c3068-171">`+`如果數位是正數 (以符合否定的正負號，請新增一個字元 `-`) </span><span class="sxs-lookup"><span data-stu-id="c3068-171">Add a `+` character if the number is positive (to match a `-` sign for negatives)</span></span> |   |
| <span data-ttu-id="c3068-172">空白字元</span><span class="sxs-lookup"><span data-stu-id="c3068-172">space character</span></span> | <span data-ttu-id="c3068-173">如果數位是正數 (以符合否定的 '-' 正負號，請新增額外的空間) </span><span class="sxs-lookup"><span data-stu-id="c3068-173">Add an extra space if the number is positive (to match a '-' sign for negatives)</span></span> |

<span data-ttu-id="c3068-174">Printf `#` 旗標無效，如果使用，將會回報編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="c3068-174">The printf `#` flag is invalid and a compile-time error will be reported if it is used.</span></span>

<span data-ttu-id="c3068-175">值是使用不因文化特性而異的格式。</span><span class="sxs-lookup"><span data-stu-id="c3068-175">Values are formatted using invariant culture.</span></span> <span data-ttu-id="c3068-176">文化特性設定與格式無關， `printf` 不同之處在于它們會影響 `%O` 和格式化的結果 `%A` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-176">Culture settings are irrelevant to `printf` formatting except when they affect the results of `%O` and `%A` formatting.</span></span> <span data-ttu-id="c3068-177">如需詳細資訊，請參閱[結構化純文字格式](plaintext-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="c3068-177">For more information, see [structured plain text formatting](plaintext-formatting.md).</span></span>

## <a name="a-formatting"></a><span data-ttu-id="c3068-178">`%A`樣式</span><span class="sxs-lookup"><span data-stu-id="c3068-178">`%A` formatting</span></span>

<span data-ttu-id="c3068-179">`%A`格式規範是用來以人類看得懂的方式來格式化值，也適用于報告診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="c3068-179">The `%A` format specifier is used to format values in a human-readable way, and can also be useful for reporting diagnostic information.</span></span>

### <a name="primitive-values"></a><span data-ttu-id="c3068-180">基本值</span><span class="sxs-lookup"><span data-stu-id="c3068-180">Primitive values</span></span>

<span data-ttu-id="c3068-181">使用規範來格式化純文字時 `%A` ，F # 數值會使用其後綴和不因文化特性而異。</span><span class="sxs-lookup"><span data-stu-id="c3068-181">When formatting plain text using the `%A` specifier, F# numeric values are formatted with their suffix and invariant culture.</span></span> <span data-ttu-id="c3068-182">使用浮點精確度的10個位置來格式化浮點值。</span><span class="sxs-lookup"><span data-stu-id="c3068-182">Floating point values are formatted using 10 places of floating point precision.</span></span> <span data-ttu-id="c3068-183">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-183">For example,</span></span>

```fsharp
printfn "%A" (1L, 3n, 5u, 7, 4.03f, 5.000000001, 5.0000000001)
```

<span data-ttu-id="c3068-184">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-184">produces</span></span>

```console
(1L, 3n, 5u, 7, 4.03000021f, 5.000000001, 5.0)
```

<span data-ttu-id="c3068-185">使用規範時 `%A` ，字串會使用引號來格式化。</span><span class="sxs-lookup"><span data-stu-id="c3068-185">When using the `%A` specifier, strings are formatted using quotes.</span></span> <span data-ttu-id="c3068-186">不會新增轉義碼，而是會列印原始字元。</span><span class="sxs-lookup"><span data-stu-id="c3068-186">Escape codes are not added and instead the raw characters are printed.</span></span> <span data-ttu-id="c3068-187">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-187">For example,</span></span>

```fsharp
printfn "%A" ("abc", "a\tb\nc\"d")

```

<span data-ttu-id="c3068-188">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-188">produces</span></span>

```console
("abc", "a      b
c"d")
```

### <a name="net-values"></a><span data-ttu-id="c3068-189">.NET 值</span><span class="sxs-lookup"><span data-stu-id="c3068-189">.NET values</span></span>

<span data-ttu-id="c3068-190">使用規範來格式化純文字時 `%A` ，非 F # .net 物件是使用 `x.ToString()` 和所指定的 .net 預設設定來格式化 `System.Globalization.CultureInfo.CurrentCulture` `System.Globalization.CultureInfo.CurrentUICulture` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-190">When formatting plain text using the `%A` specifier, non-F# .NET objects are formatted by using `x.ToString()` using the default settings of .NET given by `System.Globalization.CultureInfo.CurrentCulture` and `System.Globalization.CultureInfo.CurrentUICulture`.</span></span>  <span data-ttu-id="c3068-191">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-191">For example,</span></span>

```fsharp
open System.Globalization

let date = System.DateTime(1999, 12, 31)

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("de-DE")
printfn "Culture 1: %A" date

CultureInfo.CurrentCulture <- CultureInfo.GetCultureInfo("en-US")
printfn "Culture 2: %A" date
```

<span data-ttu-id="c3068-192">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-192">produces</span></span>

```console
Culture 1: 31.12.1999 00:00:00
Culture 2: 12/31/1999 12:00:00 AM
```

### <a name="structured-values"></a><span data-ttu-id="c3068-193">結構化值</span><span class="sxs-lookup"><span data-stu-id="c3068-193">Structured values</span></span>

<span data-ttu-id="c3068-194">使用規範來格式化純文字時 `%A` ，區塊縮排會用於 F # 清單和元組。</span><span class="sxs-lookup"><span data-stu-id="c3068-194">When formatting plain text using the `%A` specifier, block indentation is used for F# lists and tuples.</span></span> <span data-ttu-id="c3068-195">如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="c3068-195">This shown in the previous example.</span></span>
<span data-ttu-id="c3068-196">陣列的結構也會使用，包括多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="c3068-196">The structure of arrays is also used, including multi-dimensional arrays.</span></span>  <span data-ttu-id="c3068-197">一維陣列會以語法顯示 `[| ... |]` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-197">Single-dimensional arrays are shown with `[| ... |]` syntax.</span></span> <span data-ttu-id="c3068-198">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-198">For example,</span></span>

```fsharp
printfn "%A" [| for i in 1 .. 20 -> (i, i*i) |]
```

<span data-ttu-id="c3068-199">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-199">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25); (6, 36); (7, 49); (8, 64); (9, 81);
  (10, 100); (11, 121); (12, 144); (13, 169); (14, 196); (15, 225); (16, 256);
  (17, 289); (18, 324); (19, 361); (20, 400)|]
```

<span data-ttu-id="c3068-200">預設列印寬度為80。</span><span class="sxs-lookup"><span data-stu-id="c3068-200">The default print width is 80.</span></span>  <span data-ttu-id="c3068-201">您可以使用格式規範中的列印寬度來自訂此寬度。</span><span class="sxs-lookup"><span data-stu-id="c3068-201">This width can be customized by using a print width in the format specifier.</span></span> <span data-ttu-id="c3068-202">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-202">For example,</span></span>

```fsharp
printfn "%10A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%20A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%50A" [| for i in 1 .. 5 -> (i, i*i) |]
```

<span data-ttu-id="c3068-203">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-203">produces</span></span>

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

<span data-ttu-id="c3068-204">將列印寬度指定為0會導致不使用列印寬度。</span><span class="sxs-lookup"><span data-stu-id="c3068-204">Specifying a print width of 0 results in no print width being used.</span></span> <span data-ttu-id="c3068-205">除了輸出中的內嵌字串包含分行符號以外，會產生一行文字。</span><span class="sxs-lookup"><span data-stu-id="c3068-205">A single line of text will result, except where embedded strings in the output contain line breaks.</span></span>  <span data-ttu-id="c3068-206">例如：</span><span class="sxs-lookup"><span data-stu-id="c3068-206">For example</span></span>

```fsharp
printfn "%0A" [| for i in 1 .. 5 -> (i, i*i) |]

printfn "%0A" [| for i in 1 .. 5 -> "abc\ndef" |]
```

<span data-ttu-id="c3068-207">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-207">produces</span></span>

```console
[|(1, 1); (2, 4); (3, 9); (4, 16); (5, 25)|]
[|"abc
def"; "abc
def"; "abc
def"; "abc
def"; "abc
def"|]
```

<span data-ttu-id="c3068-208">深度限制4用於順序 (`IEnumerable`) 值，這會顯示為 `seq { ...}` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-208">A depth limit of 4 is used for sequence (`IEnumerable`) values, which are shown as `seq { ...}`.</span></span> <span data-ttu-id="c3068-209">[深度限制] 100 用於清單和陣列值。</span><span class="sxs-lookup"><span data-stu-id="c3068-209">A depth limit of 100 is used for list and array values.</span></span>
<span data-ttu-id="c3068-210">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-210">For example,</span></span>

```fsharp
printfn "%A" (seq { for i in 1 .. 10 -> (i, i*i) })
```

<span data-ttu-id="c3068-211">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-211">produces</span></span>

```console
seq [(1, 1); (2, 4); (3, 9); (4, 16); ...]
```

<span data-ttu-id="c3068-212">區塊縮排也會用於公用記錄和聯集值的結構。</span><span class="sxs-lookup"><span data-stu-id="c3068-212">Block indentation is also used for the structure of public record and union values.</span></span> <span data-ttu-id="c3068-213">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-213">For example,</span></span>

```fsharp
type R = { X : int list; Y : string list }

printfn "%A" { X =  [ 1;2;3 ]; Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="c3068-214">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-214">produces</span></span>

```console
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

<span data-ttu-id="c3068-215">如果 `%+A` 使用了，則也會使用反映來顯示記錄和等位的私用結構。</span><span class="sxs-lookup"><span data-stu-id="c3068-215">If `%+A` is used, then the private structure of records and unions is also revealed by using reflection.</span></span> <span data-ttu-id="c3068-216">例如：</span><span class="sxs-lookup"><span data-stu-id="c3068-216">For example</span></span>

```fsharp
type internal R =
    { X : int list; Y : string list }
    override _.ToString() = "R"

let internal data = { X = [ 1;2;3 ]; Y = ["one"; "two"; "three"] }

printfn "external view:\n%A" data

printfn "internal view:\n%+A" data

```

<span data-ttu-id="c3068-217">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-217">produces</span></span>

```console
external view:
R

internal view:
{ X = [1; 2; 3]
  Y = ["one"; "two"; "three"] }
```

### <a name="large-cyclic-or-deeply-nested-values"></a><span data-ttu-id="c3068-218">大型、迴圈或深層的嵌套值</span><span class="sxs-lookup"><span data-stu-id="c3068-218">Large, cyclic, or deeply nested values</span></span>

<span data-ttu-id="c3068-219">大型結構化的值會格式化為最大整體物件節點計數10000。</span><span class="sxs-lookup"><span data-stu-id="c3068-219">Large structured values are formatted to a maximum overall object node count of 10000.</span></span>
<span data-ttu-id="c3068-220">深層的嵌套值會格式化為深度100。</span><span class="sxs-lookup"><span data-stu-id="c3068-220">Deeply nested values are formatted to a depth of 100.</span></span>  <span data-ttu-id="c3068-221">在這兩種情況下 `...` ，都是用來省略部分輸出。</span><span class="sxs-lookup"><span data-stu-id="c3068-221">In both cases `...` is used to elide some of the output.</span></span>  <span data-ttu-id="c3068-222">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-222">For example,</span></span>

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

<span data-ttu-id="c3068-223">會產生具有部分省略的大型輸出：</span><span class="sxs-lookup"><span data-stu-id="c3068-223">produces a large output with some parts elided:</span></span>

```console
Node(Tip, Node(Tip, ....Node (..., ...)...))
```

<span data-ttu-id="c3068-224">迴圈會在物件圖形中偵測到，並在偵測 `...` 到迴圈的位置使用。</span><span class="sxs-lookup"><span data-stu-id="c3068-224">Cycles are detected in the object graphs and `...` is used at places where cycles are detected.</span></span> <span data-ttu-id="c3068-225">例如：</span><span class="sxs-lookup"><span data-stu-id="c3068-225">For example</span></span>

```fsharp
type R = { mutable Links: R list }
let r = { Links = [] }
r.Links <- [r]
printfn "%A" r
```

<span data-ttu-id="c3068-226">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-226">produces</span></span>

```console
{ Links = [...] }
```

### <a name="lazy-null-and-function-values"></a><span data-ttu-id="c3068-227">Lazy、null 和 function 值</span><span class="sxs-lookup"><span data-stu-id="c3068-227">Lazy, null, and function values</span></span>

<span data-ttu-id="c3068-228">當尚未評估值時，延遲值會列印成 `Value is not created` 或對等的文字。</span><span class="sxs-lookup"><span data-stu-id="c3068-228">Lazy values are printed as `Value is not created` or equivalent text when the value has not yet been evaluated.</span></span>

<span data-ttu-id="c3068-229">Null 值會列印成， `null` 除非將值的靜態類型判斷為 `null` 允許標記法的聯集類型。</span><span class="sxs-lookup"><span data-stu-id="c3068-229">Null values are printed as `null` unless the static type of the value is determined to be a union type where `null` is a permitted representation.</span></span>

<span data-ttu-id="c3068-230">F # 函式值會列印為其內部產生的關閉名稱，例如 `<fun:it@43-7>` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-230">F# function values are printed as their internally generated closure name, for example, `<fun:it@43-7>`.</span></span>

### <a name="customize-plain-text-formatting-with-structuredformatdisplay"></a><span data-ttu-id="c3068-231">使用自訂純文字格式`StructuredFormatDisplay`</span><span class="sxs-lookup"><span data-stu-id="c3068-231">Customize plain text formatting with `StructuredFormatDisplay`</span></span>

<span data-ttu-id="c3068-232">使用規範時 `%A` ， `StructuredFormatDisplay` 會遵守類型宣告上的屬性是否存在。</span><span class="sxs-lookup"><span data-stu-id="c3068-232">When using the `%A` specifier, the presence of the `StructuredFormatDisplay` attribute on type declarations is respected.</span></span>  <span data-ttu-id="c3068-233">這可用來指定用來顯示值的代理文字和屬性。</span><span class="sxs-lookup"><span data-stu-id="c3068-233">This can be used to specify surrogate text and property to display a value.</span></span> <span data-ttu-id="c3068-234">例如：</span><span class="sxs-lookup"><span data-stu-id="c3068-234">For example:</span></span>

```fsharp
[<StructuredFormatDisplay("Counts({Clicks})")>]
type Counts = { Clicks:int list}

printfn "%20A" {Clicks=[0..20]}
```

<span data-ttu-id="c3068-235">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-235">produces</span></span>

```console
Counts([0; 1; 2; 3;
        4; 5; 6; 7;
        8; 9; 10; 11;
        12; 13; 14;
        15; 16; 17;
        18; 19; 20])
```

### <a name="customize-plain-text-formatting-by-overriding-tostring"></a><span data-ttu-id="c3068-236">藉由覆寫自訂純文字格式`ToString`</span><span class="sxs-lookup"><span data-stu-id="c3068-236">Customize plain text formatting by overriding `ToString`</span></span>

<span data-ttu-id="c3068-237">的預設執行 `ToString` 在 F # 程式設計中是可觀察的。</span><span class="sxs-lookup"><span data-stu-id="c3068-237">The default implementation of `ToString` is observable in F# programming.</span></span> <span data-ttu-id="c3068-238">通常，預設結果不適合在程式設計人員面向的資訊顯示或使用者輸出中使用，因此，通常會覆寫預設的執行。</span><span class="sxs-lookup"><span data-stu-id="c3068-238">Often, the default results aren't suitable for use in either programmer-facing information display or user output, and as a result it is common to override the default implementation.</span></span>  

<span data-ttu-id="c3068-239">根據預設，F # 記錄和聯集類型會以使用的執行來覆寫的執行 `ToString` `sprintf "%+A"` 。</span><span class="sxs-lookup"><span data-stu-id="c3068-239">By default, F# record and union types override the implementation of `ToString` with an implementation that uses `sprintf "%+A"`.</span></span>  <span data-ttu-id="c3068-240">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-240">For example,</span></span>

```fsharp
type Counts = { Clicks:int list }

printfn "%s" ({Clicks=[0..10]}.ToString())
```

<span data-ttu-id="c3068-241">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-241">produces</span></span>

```console
{ Clicks = [0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10] }
```

<span data-ttu-id="c3068-242">針對類別類型，不會提供的預設實作為， `ToString` 而且會使用 .net 預設值，這會報告類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="c3068-242">For class types, no default implementation of `ToString` is provided and the .NET default is used, which reports the name of the type.</span></span> <span data-ttu-id="c3068-243">例如</span><span class="sxs-lookup"><span data-stu-id="c3068-243">For example,</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Default structured print gives this:\n%A" data
printfn "Default ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="c3068-244">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-244">produces</span></span>

```console
Default structured print gives this:
[MyClassType; MyClassType]
Default ToString gives:
[MyClassType; MyClassType]
```

<span data-ttu-id="c3068-245">新增的覆寫 `ToString` 可以提供更好的格式。</span><span class="sxs-lookup"><span data-stu-id="c3068-245">Adding an override for `ToString` can give better formatting.</span></span>

```fsharp
type MyClassType(clicks: int list) =
   member _.Clicks = clicks
   override _.ToString() = sprintf "MyClassType(%0A)" clicks

let data = [ MyClassType([1..5]); MyClassType([1..5]) ]
printfn "Now structured print gives this:\n%A" data
printfn "Now ToString gives:\n%s" (data.ToString())
```

<span data-ttu-id="c3068-246">塊</span><span class="sxs-lookup"><span data-stu-id="c3068-246">produces</span></span>

```console
Now structured print gives this:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
Now ToString gives:
[MyClassType([1; 2; 3; 4; 5]); MyClassType([1; 2; 3; 4; 5])]
```

## <a name="f-interactive-structured-printing"></a><span data-ttu-id="c3068-247">F # 互動式結構化列印</span><span class="sxs-lookup"><span data-stu-id="c3068-247">F# Interactive structured printing</span></span>

<span data-ttu-id="c3068-248">F # Interactive (`dotnet fsi`) 會使用延伸版本的結構化純文字格式來報告值，並允許其他自訂能力。</span><span class="sxs-lookup"><span data-stu-id="c3068-248">F# Interactive (`dotnet fsi`) uses an extended version of structured plain text formatting to report values and allows additional customizability.</span></span> <span data-ttu-id="c3068-249">如需詳細資訊，請參閱[F # Interactive](fsharp-interactive-options.md)。</span><span class="sxs-lookup"><span data-stu-id="c3068-249">For more information, see [F# Interactive](fsharp-interactive-options.md).</span></span>

## <a name="customize-debug-displays"></a><span data-ttu-id="c3068-250">自訂 debug 顯示</span><span class="sxs-lookup"><span data-stu-id="c3068-250">Customize debug displays</span></span>

<span data-ttu-id="c3068-251">適用于 .NET 的偵錯工具會使用和之類的屬性 `DebuggerDisplay` `DebuggerTypeProxy` ，而且這些屬性會影響偵錯工具檢查視窗中物件的結構化顯示。</span><span class="sxs-lookup"><span data-stu-id="c3068-251">Debuggers for .NET respect the use of attributes such as `DebuggerDisplay` and `DebuggerTypeProxy`, and these affect the structured display of objects in debugger inspection windows.</span></span>
<span data-ttu-id="c3068-252">F # 編譯器會針對區分聯集和記錄類型自動產生這些屬性，但不會針對類別、介面或結構類型來產生。</span><span class="sxs-lookup"><span data-stu-id="c3068-252">The F# compiler automatically generated these attributes for discriminated union and record types, but not class, interface, or struct types.</span></span>

<span data-ttu-id="c3068-253">F # 純文字格式會忽略這些屬性，但在進行 F # 型別的調試時，執行這些方法以改善顯示會很有用。</span><span class="sxs-lookup"><span data-stu-id="c3068-253">These attributes are ignored in F# plain text formatting, but it can be useful to implement these methods to improve displays when debugging F# types.</span></span>

## <a name="see-also"></a><span data-ttu-id="c3068-254">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3068-254">See also</span></span>

- [<span data-ttu-id="c3068-255">字串</span><span class="sxs-lookup"><span data-stu-id="c3068-255">Strings</span></span>](strings.md)
- [<span data-ttu-id="c3068-256">記錄</span><span class="sxs-lookup"><span data-stu-id="c3068-256">Records</span></span>](records.md)
- [<span data-ttu-id="c3068-257">已區分的聯集</span><span class="sxs-lookup"><span data-stu-id="c3068-257">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="c3068-258">F# 互動</span><span class="sxs-lookup"><span data-stu-id="c3068-258">F# Interactive</span></span>](fsharp-interactive-options.md)
