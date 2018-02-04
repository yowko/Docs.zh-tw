---
title: "類型字元 (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: bdb675b9605d03829c95897382daa6d03cf1b041
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="3c7b2-102">輸入的字元 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c7b2-102">Type characters (Visual Basic)</span></span>

<span data-ttu-id="3c7b2-103">除了宣告陳述式中指定的資料類型，您可以強制使用一些程式設計項目的資料型別*類型字元*。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="3c7b2-104">型別字元必須緊接的項目，其中沒有任何種類的中介字元。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="3c7b2-105">類型字元不是項目的名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="3c7b2-106">型別字元定義的項目可以參考不含類型字元。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-106">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="3c7b2-107">識別項類型字元</span><span class="sxs-lookup"><span data-stu-id="3c7b2-107">Identifier type characters</span></span>

<span data-ttu-id="3c7b2-108">Visual Basic 提供的一組*識別項類型字元*您可以使用在宣告中指定的變數或常數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-108">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="3c7b2-109">下表顯示可用的識別項類型字元，與使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-109">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="3c7b2-110">識別項類型字元</span><span class="sxs-lookup"><span data-stu-id="3c7b2-110">Identifier type character</span></span>|<span data-ttu-id="3c7b2-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-111">Data type</span></span>|<span data-ttu-id="3c7b2-112">範例</span><span class="sxs-lookup"><span data-stu-id="3c7b2-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="3c7b2-113">存在任何識別項類型字元`Boolean`， `Byte`， `Char`， `Date`， `Object`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`資料型別，或任何複合資料類型，例如陣列或結構。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="3c7b2-114">在某些情況下，您可以將附加`$`字元為 Visual Basic 函式，例如`Left$`而不是`Left`，以取得傳回的值類型為`String`。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-114">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="3c7b2-115">在所有情況下，識別項類型字元必須緊接的識別項名稱。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="3c7b2-116">常值類型字元</span><span class="sxs-lookup"><span data-stu-id="3c7b2-116">Literal type characters</span></span>

<span data-ttu-id="3c7b2-117">A*常值*是特定值的資料類型的文字表示法。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="3c7b2-118">預設常值類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-118">Default literal types</span></span>

<span data-ttu-id="3c7b2-119">常值的形式通常出現在您的程式碼會判斷其資料類型。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="3c7b2-120">下表顯示這些預設型別。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="3c7b2-121">文字格式的常值</span><span class="sxs-lookup"><span data-stu-id="3c7b2-121">Textual form of literal</span></span>|<span data-ttu-id="3c7b2-122">預設資料類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-122">Default data type</span></span>|<span data-ttu-id="3c7b2-123">範例</span><span class="sxs-lookup"><span data-stu-id="3c7b2-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="3c7b2-124">數字，沒有小數部分</span><span class="sxs-lookup"><span data-stu-id="3c7b2-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="3c7b2-125">數字，沒有小數部分，針對太大`Integer`</span><span class="sxs-lookup"><span data-stu-id="3c7b2-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="3c7b2-126">數字，小數部分</span><span class="sxs-lookup"><span data-stu-id="3c7b2-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="3c7b2-127">以雙引號括住</span><span class="sxs-lookup"><span data-stu-id="3c7b2-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="3c7b2-128">數字符號括住</span><span class="sxs-lookup"><span data-stu-id="3c7b2-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="3c7b2-129">強制的常值類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-129">Forced literal types</span></span>

<span data-ttu-id="3c7b2-130">Visual Basic 提供的一組*常值類型字元*，您可以使用強制常之外的資料類型的形式表示。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-130">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="3c7b2-131">您可以將字元附加到常值的結尾。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="3c7b2-132">下表顯示可用的常值類型字元，與使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-132">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="3c7b2-133">常值類型字元</span><span class="sxs-lookup"><span data-stu-id="3c7b2-133">Literal type character</span></span>|<span data-ttu-id="3c7b2-134">資料類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-134">Data type</span></span>|<span data-ttu-id="3c7b2-135">範例</span><span class="sxs-lookup"><span data-stu-id="3c7b2-135">Example</span></span>|  
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

<span data-ttu-id="3c7b2-136">沒有常值類型字元存在`Boolean`， `Byte`， `Date`， `Object`， `SByte`，或`String`資料型別，或任何複合資料類型，例如陣列或結構。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="3c7b2-137">常值也可以使用識別項類型字元 (`%`， `&`， `@`， `!`， `#`， `$`)，可能是變數、 常數和運算式。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="3c7b2-138">不過，常值類型字元 (`S`， `I`， `L`， `D`， `F`， `R`， `C`) 可以僅能搭配常值。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="3c7b2-139">在所有情況下，常值類型字元必須緊接的常值。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-139">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="3c7b2-140">十六進位、 二進位以及八進位常值</span><span class="sxs-lookup"><span data-stu-id="3c7b2-140">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="3c7b2-141">編譯器通常會解譯為十進位 (基底 10) 數字系統中的常值的整數。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-141">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="3c7b2-142">您也可以定義一個整數常值的十六進位 (基底 16) 數字`&H`前置詞的二進位 (基底 2) 數字`&B`前置詞，以及八進位 (基底 8) 編號，以`&O`前置詞。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-142">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="3c7b2-143">請依照下列前置詞的數字必須適用於數字系統。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="3c7b2-144">下表將說明這點。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="3c7b2-145">數字基底</span><span class="sxs-lookup"><span data-stu-id="3c7b2-145">Number base</span></span>|<span data-ttu-id="3c7b2-146">前置詞</span><span class="sxs-lookup"><span data-stu-id="3c7b2-146">Prefix</span></span>|<span data-ttu-id="3c7b2-147">有效的數字值</span><span class="sxs-lookup"><span data-stu-id="3c7b2-147">Valid digit values</span></span>|<span data-ttu-id="3c7b2-148">範例</span><span class="sxs-lookup"><span data-stu-id="3c7b2-148">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="3c7b2-149">十六進位 (基底 16)</span><span class="sxs-lookup"><span data-stu-id="3c7b2-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="3c7b2-150">0-9 和 A-F</span><span class="sxs-lookup"><span data-stu-id="3c7b2-150">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="3c7b2-151">二進位 (基底 2)</span><span class="sxs-lookup"><span data-stu-id="3c7b2-151">Binary (base 2)</span></span>|`0B`|<span data-ttu-id="3c7b2-152">0-1</span><span class="sxs-lookup"><span data-stu-id="3c7b2-152">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="3c7b2-153">八進位 (基底 8)</span><span class="sxs-lookup"><span data-stu-id="3c7b2-153">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="3c7b2-154">0-7</span><span class="sxs-lookup"><span data-stu-id="3c7b2-154">0-7</span></span>|`&O77`|

<span data-ttu-id="3c7b2-155">從 Visual Basic 2017 開始，您可以使用底線字元 (`_`) 做為群組分隔符號，來增強整數常值的可讀性。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-155">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="3c7b2-156">下列範例會使用`_`成 8 位元群組分組的二進位常值的字元：</span><span class="sxs-lookup"><span data-stu-id="3c7b2-156">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="3c7b2-157">您可以遵循前置的常值與常值類型字元。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-157">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="3c7b2-158">下列範例顯示這點。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-158">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="3c7b2-159">在上述範例中，`counter`的十進位值為-32768，和`flags`具有 32768 的十進位值。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-159">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="3c7b2-160">從 Visual Basic 15.5 開始，您也可以使用底線字元 (`_`) 做為前置詞和十六進位、 二進位或八進位的數字之間的前置分隔符號。</span><span class="sxs-lookup"><span data-stu-id="3c7b2-160">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="3c7b2-161">例如: </span><span class="sxs-lookup"><span data-stu-id="3c7b2-161">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="3c7b2-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c7b2-162">See Also</span></span>

 [<span data-ttu-id="3c7b2-163">資料類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-163">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="3c7b2-164">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-164">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="3c7b2-165">值類型和參考類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-165">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="3c7b2-166">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="3c7b2-166">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="3c7b2-167">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="3c7b2-167">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="3c7b2-168">變數宣告</span><span class="sxs-lookup"><span data-stu-id="3c7b2-168">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="3c7b2-169">資料類型</span><span class="sxs-lookup"><span data-stu-id="3c7b2-169">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
