---
title: "輸入字元 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals
- F literal type character
- '& identifier type character'
- type characters
- octal literals
- literals, hexadecimal
- '&O prefix for octal values'
- literals, default types
- defaults, literal types
- C literal type character
- type characters, literal
- $ identifier type character
- L literal type character
- UI literal type characters
- default literal types
- D literal type character
- literals, octal
- S literal type character
- '! identifier type character'
- US literal type characters
- '% identifier type character'
- data types [Visual Basic], type characters
- characters, identifier type
- type characters, identifier
- '# identifier type character'
- identifier type characters
- literal type characters
- I literal type character
- R literal type character
- '@ identifier type character'
- UL literal type characters
- literal types, default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 335306eca12070de456a72e918bcbba1e22ab55b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="cfc28-102">類型字元 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfc28-102">Type Characters (Visual Basic)</span></span>
<span data-ttu-id="cfc28-103">除了宣告陳述式中指定的資料類型，您可以強制一些程式設計項目使用的資料型別*輸入字元*。</span><span class="sxs-lookup"><span data-stu-id="cfc28-103">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="cfc28-104">型別字元必須緊接元素中，但沒有任何種類的中介字元。</span><span class="sxs-lookup"><span data-stu-id="cfc28-104">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>  
  
 <span data-ttu-id="cfc28-105">型別字元不是項目的名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="cfc28-105">The type character is not part of the name of the element.</span></span> <span data-ttu-id="cfc28-106">定義型別字元的項目可以參考不含型別字元。</span><span class="sxs-lookup"><span data-stu-id="cfc28-106">An element defined with a type character can be referenced without the type character.</span></span>  
  
## <a name="identifier-type-characters"></a><span data-ttu-id="cfc28-107">識別項類型字元</span><span class="sxs-lookup"><span data-stu-id="cfc28-107">Identifier Type Characters</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="cfc28-108">提供一組*識別項類型字元*，其中您可以使用宣告中指定變數或常數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="cfc28-108"> supplies a set of *identifier type characters*, which you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="cfc28-109">下表顯示可用的識別項類型字元，與使用方式的範例。</span><span class="sxs-lookup"><span data-stu-id="cfc28-109">The following table shows the available identifier type characters with examples of usage.</span></span>  
  
|<span data-ttu-id="cfc28-110">識別項類型字元</span><span class="sxs-lookup"><span data-stu-id="cfc28-110">Identifier type character</span></span>|<span data-ttu-id="cfc28-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="cfc28-111">Data type</span></span>|<span data-ttu-id="cfc28-112">範例</span><span class="sxs-lookup"><span data-stu-id="cfc28-112">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="cfc28-113">存在任何識別項類型字元`Boolean`， `Byte`， `Char`， `Date`， `Object`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`資料型別，或任何複合資料類型，例如陣列或結構。</span><span class="sxs-lookup"><span data-stu-id="cfc28-113">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>  
  
 <span data-ttu-id="cfc28-114">在某些情況下，您可以附加`$`字元[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]函式，例如`Left$`而不是`Left`，以取得傳回的值型別為`String`。</span><span class="sxs-lookup"><span data-stu-id="cfc28-114">In some cases, you can append the `$` character to a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>  
  
 <span data-ttu-id="cfc28-115">在所有情況下，識別項類型字元必須緊接識別項名稱。</span><span class="sxs-lookup"><span data-stu-id="cfc28-115">In all cases, the identifier type character must immediately follow the identifier name.</span></span>  
  
## <a name="literal-type-characters"></a><span data-ttu-id="cfc28-116">常值類型字元</span><span class="sxs-lookup"><span data-stu-id="cfc28-116">Literal Type Characters</span></span>  
 <span data-ttu-id="cfc28-117">A*常值*是資料類型的特定值的文字表示。</span><span class="sxs-lookup"><span data-stu-id="cfc28-117">A *literal* is a textual representation of a particular value of a data type.</span></span>  
  
### <a name="default-literal-types"></a><span data-ttu-id="cfc28-118">預設常值類型</span><span class="sxs-lookup"><span data-stu-id="cfc28-118">Default Literal Types</span></span>  
 <span data-ttu-id="cfc28-119">常值的形式通常出現在您的程式碼中決定其資料型別。</span><span class="sxs-lookup"><span data-stu-id="cfc28-119">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="cfc28-120">下表顯示這些預設型別。</span><span class="sxs-lookup"><span data-stu-id="cfc28-120">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="cfc28-121">文字格式的常值</span><span class="sxs-lookup"><span data-stu-id="cfc28-121">Textual form of literal</span></span>|<span data-ttu-id="cfc28-122">預設資料類型</span><span class="sxs-lookup"><span data-stu-id="cfc28-122">Default data type</span></span>|<span data-ttu-id="cfc28-123">範例</span><span class="sxs-lookup"><span data-stu-id="cfc28-123">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="cfc28-124">數字，沒有小數部分</span><span class="sxs-lookup"><span data-stu-id="cfc28-124">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="cfc28-125">數字，沒有小數部分，太大`Integer`</span><span class="sxs-lookup"><span data-stu-id="cfc28-125">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="cfc28-126">數字，分數部分</span><span class="sxs-lookup"><span data-stu-id="cfc28-126">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="cfc28-127">以雙引號括住</span><span class="sxs-lookup"><span data-stu-id="cfc28-127">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="cfc28-128">數字符號括住</span><span class="sxs-lookup"><span data-stu-id="cfc28-128">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  
  
### <a name="forced-literal-types"></a><span data-ttu-id="cfc28-129">強制常值型別</span><span class="sxs-lookup"><span data-stu-id="cfc28-129">Forced Literal Types</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="cfc28-130">提供一組*常值類型字元*，您可以使用強制常以外的資料類型的形式來表示。</span><span class="sxs-lookup"><span data-stu-id="cfc28-130"> supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="cfc28-131">您可以將字元附加到常值的結尾。</span><span class="sxs-lookup"><span data-stu-id="cfc28-131">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="cfc28-132">下表顯示可用的常值型別字元與用法的範例。</span><span class="sxs-lookup"><span data-stu-id="cfc28-132">The following table shows the available literal type characters with examples of usage.</span></span>  
  
|<span data-ttu-id="cfc28-133">常值類型字元</span><span class="sxs-lookup"><span data-stu-id="cfc28-133">Literal type character</span></span>|<span data-ttu-id="cfc28-134">資料類型</span><span class="sxs-lookup"><span data-stu-id="cfc28-134">Data type</span></span>|<span data-ttu-id="cfc28-135">範例</span><span class="sxs-lookup"><span data-stu-id="cfc28-135">Example</span></span>|  
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
  
 <span data-ttu-id="cfc28-136">不常值類型字元存在`Boolean`， `Byte`， `Date`， `Object`， `SByte`，或`String`資料型別，或任何複合資料類型，例如陣列或結構。</span><span class="sxs-lookup"><span data-stu-id="cfc28-136">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>  
  
 <span data-ttu-id="cfc28-137">常值也可以使用識別項類型字元 (`%`， `&`， `@`， `!`， `#`， `$`)，可能是變數、 常數和運算式。</span><span class="sxs-lookup"><span data-stu-id="cfc28-137">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="cfc28-138">不過，常值類型字元 (`S`， `I`， `L`， `D`， `F`， `R`， `C`) 可以僅能搭配常值。</span><span class="sxs-lookup"><span data-stu-id="cfc28-138">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>  
  
 <span data-ttu-id="cfc28-139">在所有情況下，常值類型字元必須緊接的常值。</span><span class="sxs-lookup"><span data-stu-id="cfc28-139">In all cases, the literal type character must immediately follow the literal value.</span></span>  
  
## <a name="hexadecimal-and-octal-literals"></a><span data-ttu-id="cfc28-140">十六進位和八進位常值</span><span class="sxs-lookup"><span data-stu-id="cfc28-140">Hexadecimal and Octal Literals</span></span>  
 <span data-ttu-id="cfc28-141">編譯器通常 construes 整數常值為十進位 (基底 10) 數字系統。</span><span class="sxs-lookup"><span data-stu-id="cfc28-141">The compiler normally construes an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="cfc28-142">您可以強制整數常值是十六進位 (基底 16) 與`&H`前置詞，而且您可以強制為八進位 (基底 8) 與`&O`前置詞。</span><span class="sxs-lookup"><span data-stu-id="cfc28-142">You can force an integer literal to be hexadecimal (base 16) with the `&H` prefix, and you can force it to be octal (base 8) with the `&O` prefix.</span></span> <span data-ttu-id="cfc28-143">請依照下列前置詞的數字必須適用於數字系統。</span><span class="sxs-lookup"><span data-stu-id="cfc28-143">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="cfc28-144">下表將說明這點。</span><span class="sxs-lookup"><span data-stu-id="cfc28-144">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="cfc28-145">數字基底</span><span class="sxs-lookup"><span data-stu-id="cfc28-145">Number base</span></span>|<span data-ttu-id="cfc28-146">前置詞</span><span class="sxs-lookup"><span data-stu-id="cfc28-146">Prefix</span></span>|<span data-ttu-id="cfc28-147">有效的數字值</span><span class="sxs-lookup"><span data-stu-id="cfc28-147">Valid digit values</span></span>|<span data-ttu-id="cfc28-148">範例</span><span class="sxs-lookup"><span data-stu-id="cfc28-148">Example</span></span>|  
|-----------------|------------|------------------------|-------------|  
|<span data-ttu-id="cfc28-149">十六進位 (基底 16)</span><span class="sxs-lookup"><span data-stu-id="cfc28-149">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="cfc28-150">0-9 和 A-F</span><span class="sxs-lookup"><span data-stu-id="cfc28-150">0-9 and A-F</span></span>|`&HFFFF`|  
|<span data-ttu-id="cfc28-151">八進位 (基底 8)</span><span class="sxs-lookup"><span data-stu-id="cfc28-151">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="cfc28-152">0-7</span><span class="sxs-lookup"><span data-stu-id="cfc28-152">0-7</span></span>|`&O77`|  
  
 <span data-ttu-id="cfc28-153">您可以依照前置的常值與常值類型字元。</span><span class="sxs-lookup"><span data-stu-id="cfc28-153">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="cfc28-154">下列範例示範這點。</span><span class="sxs-lookup"><span data-stu-id="cfc28-154">The following example shows this.</span></span>  
  
```  
Dim counter As Short = &H8000S  
Dim flags As UShort = &H8000US  
```  
  
 <span data-ttu-id="cfc28-155">在上述範例中，`counter`的十進位值為-32768，和`flags`32768 十進位值。</span><span class="sxs-lookup"><span data-stu-id="cfc28-155">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc28-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cfc28-156">See Also</span></span>  
 <span data-ttu-id="cfc28-157">[資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="cfc28-157">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="cfc28-158"> [基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="cfc28-158"> [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="cfc28-159"> [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="cfc28-159"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="cfc28-160"> [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="cfc28-160"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="cfc28-161"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="cfc28-161"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="cfc28-162"> [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="cfc28-162"> [Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="cfc28-163"> [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span><span class="sxs-lookup"><span data-stu-id="cfc28-163"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)</span></span>
