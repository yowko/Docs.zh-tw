---
title: 類型字元
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: a48260694c1dfcbbb8f804f220fe89b1663c7319
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393074"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="06503-102">類型字元（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="06503-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="06503-103">除了在宣告語句中指定資料類型之外，您還可以使用*類型字元*來強制某些程式設計項目的資料類型。</span><span class="sxs-lookup"><span data-stu-id="06503-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="06503-104">類型字元必須緊接在元素後面，不含任何類型的中間字元。</span><span class="sxs-lookup"><span data-stu-id="06503-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="06503-105">類型字元不是元素名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="06503-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="06503-106">以類型字元定義的專案，可以不使用類型字元來參考。</span><span class="sxs-lookup"><span data-stu-id="06503-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="06503-107">識別項型別字元</span><span class="sxs-lookup"><span data-stu-id="06503-107">Identifier type characters</span></span>

<span data-ttu-id="06503-108">Visual Basic 提供一組*識別項型別字元*，您可以在宣告中用來指定變數或常數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="06503-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="06503-109">下表顯示可用的識別項型別字元，以及使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="06503-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="06503-110">識別項型別字元</span><span class="sxs-lookup"><span data-stu-id="06503-110">Identifier type character</span></span>|<span data-ttu-id="06503-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="06503-111">Data type</span></span>|<span data-ttu-id="06503-112">範例</span><span class="sxs-lookup"><span data-stu-id="06503-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="06503-113">對於 `Boolean` 、、、、、、、 `Byte` 、 `Char` `Date` `Object` `SByte` `Short` `UInteger` `ULong` 或 `UShort` 資料類型，或任何複合資料型別（例如陣列或結構），都不會有任何識別項型別字元。</span><span class="sxs-lookup"><span data-stu-id="06503-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="06503-114">在某些情況下，您可以將 `$` 字元附加至 Visual Basic 函式（例如 `Left$` ，而不是 `Left` ），以取得類型的傳回值 `String` 。</span><span class="sxs-lookup"><span data-stu-id="06503-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="06503-115">在所有情況下，識別項型別字元必須緊接在識別碼名稱之後。</span><span class="sxs-lookup"><span data-stu-id="06503-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="06503-116">常數值型別字元</span><span class="sxs-lookup"><span data-stu-id="06503-116">Literal type characters</span></span>

<span data-ttu-id="06503-117">*常*值是資料類型之特定值的文字標記法。</span><span class="sxs-lookup"><span data-stu-id="06503-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="06503-118">預設常數值型別</span><span class="sxs-lookup"><span data-stu-id="06503-118">Default literal types</span></span>

<span data-ttu-id="06503-119">常值出現在程式碼中的形式，通常會決定其資料類型。</span><span class="sxs-lookup"><span data-stu-id="06503-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="06503-120">下表顯示這些預設類型。</span><span class="sxs-lookup"><span data-stu-id="06503-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="06503-121">文字形式的常值</span><span class="sxs-lookup"><span data-stu-id="06503-121">Textual form of literal</span></span>|<span data-ttu-id="06503-122">預設資料類型</span><span class="sxs-lookup"><span data-stu-id="06503-122">Default data type</span></span>|<span data-ttu-id="06503-123">範例</span><span class="sxs-lookup"><span data-stu-id="06503-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="06503-124">數值，無小數部分</span><span class="sxs-lookup"><span data-stu-id="06503-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="06503-125">數值，沒有小數部分，太大，無法用於`Integer`</span><span class="sxs-lookup"><span data-stu-id="06503-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="06503-126">數值、小數部分</span><span class="sxs-lookup"><span data-stu-id="06503-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="06503-127">括在雙引號中</span><span class="sxs-lookup"><span data-stu-id="06503-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="06503-128">包含在數位記號內</span><span class="sxs-lookup"><span data-stu-id="06503-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="06503-129">強制常數值型別</span><span class="sxs-lookup"><span data-stu-id="06503-129">Forced literal types</span></span>

<span data-ttu-id="06503-130">Visual Basic 會提供一組*常數值型別字元*，您可以用它來強制常值採用其表單所表示的資料類型。</span><span class="sxs-lookup"><span data-stu-id="06503-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="06503-131">若要這麼做，請將字元附加到常值的結尾。</span><span class="sxs-lookup"><span data-stu-id="06503-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="06503-132">下表顯示可用的常數值型別字元，以及使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="06503-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="06503-133">常數值型別字元</span><span class="sxs-lookup"><span data-stu-id="06503-133">Literal type character</span></span>|<span data-ttu-id="06503-134">資料類型</span><span class="sxs-lookup"><span data-stu-id="06503-134">Data type</span></span>|<span data-ttu-id="06503-135">範例</span><span class="sxs-lookup"><span data-stu-id="06503-135">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="06503-136">對於 `Boolean` 、 `Byte` 、 `Date` 、 `Object` 、 `SByte` 或 `String` 資料類型，或任何複合資料型別（例如陣列或結構），都不會有常數值型別字元。</span><span class="sxs-lookup"><span data-stu-id="06503-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="06503-137">常值也可以使用識別項型別字元（ `%` 、 `&` 、 `@` 、 `!` 、 `#` 、 `$` ），就像變數、常數和運算式一樣。</span><span class="sxs-lookup"><span data-stu-id="06503-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="06503-138">不過，常數值型別字元（ `S` 、 `I` 、 `L` 、 `D` 、 `F` 、 `R` 、 `C` ）只能搭配常值使用。</span><span class="sxs-lookup"><span data-stu-id="06503-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="06503-139">在所有情況下，常數值型別字元必須緊接在常值後面。</span><span class="sxs-lookup"><span data-stu-id="06503-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="06503-140">十六進位、二進位和八進位常值</span><span class="sxs-lookup"><span data-stu-id="06503-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="06503-141">編譯器通常會將整數常值轉譯為十進位（基底10）數值系統中的。</span><span class="sxs-lookup"><span data-stu-id="06503-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="06503-142">您也可以將整數常值定義為具有前置詞的十六進位（基底16）數位 `&H` ，做為具有前置詞的二進位（基底2）數位， `&B` 以及前置詞為八進位（基底8）的數位 `&O` 。</span><span class="sxs-lookup"><span data-stu-id="06503-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="06503-143">前置詞後面的數位必須適用于數字系統。</span><span class="sxs-lookup"><span data-stu-id="06503-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="06503-144">下表將說明這一點。</span><span class="sxs-lookup"><span data-stu-id="06503-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="06503-145">數位基底</span><span class="sxs-lookup"><span data-stu-id="06503-145">Number base</span></span>|<span data-ttu-id="06503-146">前置詞</span><span class="sxs-lookup"><span data-stu-id="06503-146">Prefix</span></span>|<span data-ttu-id="06503-147">有效的數位值</span><span class="sxs-lookup"><span data-stu-id="06503-147">Valid digit values</span></span>|<span data-ttu-id="06503-148">範例</span><span class="sxs-lookup"><span data-stu-id="06503-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="06503-149">十六進位 (基底 16)</span><span class="sxs-lookup"><span data-stu-id="06503-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="06503-150">0-9 和 A-f</span><span class="sxs-lookup"><span data-stu-id="06503-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="06503-151">二進位（基底2）</span><span class="sxs-lookup"><span data-stu-id="06503-151">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="06503-152">0-1</span><span class="sxs-lookup"><span data-stu-id="06503-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="06503-153">八進位 (基底 8)</span><span class="sxs-lookup"><span data-stu-id="06503-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="06503-154">0-7</span><span class="sxs-lookup"><span data-stu-id="06503-154">0-7</span></span>|`&O77`|

<span data-ttu-id="06503-155">從 Visual Basic 2017 開始，您可以使用底線字元（ `_` ）做為群組分隔符號，以增強整數常值的可讀性。</span><span class="sxs-lookup"><span data-stu-id="06503-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="06503-156">下列範例會使用 `_` 字元，將二進位常值分組為8位群組：</span><span class="sxs-lookup"><span data-stu-id="06503-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="06503-157">您可以遵循具有常數值型別字元的首碼常值。</span><span class="sxs-lookup"><span data-stu-id="06503-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="06503-158">以下範例說明這點。</span><span class="sxs-lookup"><span data-stu-id="06503-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="06503-159">在上述範例中，的 `counter` 十進位值為-32768，而 `flags` 的十進位值為 + 32768。</span><span class="sxs-lookup"><span data-stu-id="06503-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="06503-160">從 Visual Basic 15.5 開始，您也可以使用底線字元（ `_` ）做為前置詞和十六進位、二進位或八進位數位之間的前置分隔符號。</span><span class="sxs-lookup"><span data-stu-id="06503-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="06503-161">例如：</span><span class="sxs-lookup"><span data-stu-id="06503-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="06503-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06503-162">See also</span></span>

- [<span data-ttu-id="06503-163">資料類型</span><span class="sxs-lookup"><span data-stu-id="06503-163">Data Types</span></span>](index.md)
- [<span data-ttu-id="06503-164">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="06503-164">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="06503-165">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="06503-165">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="06503-166">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="06503-166">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="06503-167">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="06503-167">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="06503-168">變數宣告</span><span class="sxs-lookup"><span data-stu-id="06503-168">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="06503-169">資料類型</span><span class="sxs-lookup"><span data-stu-id="06503-169">Data Types</span></span>](../../../language-reference/data-types/index.md)
