---
title: 擴展和縮小轉換 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 960b4e4c7184309b6a84247d86fb94ccb2faf877
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="6ac61-102">擴展和縮小轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ac61-102">Widening and Narrowing Conversions (Visual Basic)</span></span>
<span data-ttu-id="6ac61-103">類型轉換的重要考量是轉換的結果是否目的地資料類型的範圍內。</span><span class="sxs-lookup"><span data-stu-id="6ac61-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="6ac61-104">A*擴展轉換*值變更為可允許任何的原始資料的可能值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="6ac61-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="6ac61-105">擴展轉換，保留原始值，但可以變更它的表示。</span><span class="sxs-lookup"><span data-stu-id="6ac61-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="6ac61-106">如果您從整數類資料類型轉換，發生這種的情況`Decimal`，或從`Char`至`String`。</span><span class="sxs-lookup"><span data-stu-id="6ac61-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="6ac61-107">*「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。</span><span class="sxs-lookup"><span data-stu-id="6ac61-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="6ac61-108">例如，小數的值會四捨五入時將它轉換成整數類型，並轉換成數值類型`Boolean`降低為`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="6ac61-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="6ac61-109">擴展轉換</span><span class="sxs-lookup"><span data-stu-id="6ac61-109">Widening Conversions</span></span>  
 <span data-ttu-id="6ac61-110">下表顯示標準的擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="6ac61-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="6ac61-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="6ac61-111">Data type</span></span>|<span data-ttu-id="6ac61-112">資料類型可擴展<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6ac61-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="6ac61-113">SByte</span><span class="sxs-lookup"><span data-stu-id="6ac61-113">SByte</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="6ac61-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="6ac61-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="6ac61-115">Byte</span><span class="sxs-lookup"><span data-stu-id="6ac61-115">Byte</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="6ac61-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="6ac61-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="6ac61-117">Short</span><span class="sxs-lookup"><span data-stu-id="6ac61-117">Short</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="6ac61-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="6ac61-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="6ac61-119">UShort</span><span class="sxs-lookup"><span data-stu-id="6ac61-119">UShort</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="6ac61-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="6ac61-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="6ac61-121">Integer</span><span class="sxs-lookup"><span data-stu-id="6ac61-121">Integer</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="6ac61-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6ac61-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="6ac61-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="6ac61-123">UInteger</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="6ac61-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6ac61-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="6ac61-125">Long</span><span class="sxs-lookup"><span data-stu-id="6ac61-125">Long</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="6ac61-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6ac61-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="6ac61-127">ULong</span><span class="sxs-lookup"><span data-stu-id="6ac61-127">ULong</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="6ac61-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6ac61-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="6ac61-129">Decimal</span><span class="sxs-lookup"><span data-stu-id="6ac61-129">Decimal</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="6ac61-130">`Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="6ac61-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="6ac61-131">Single</span><span class="sxs-lookup"><span data-stu-id="6ac61-131">Single</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="6ac61-132">`Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="6ac61-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="6ac61-133">Double</span><span class="sxs-lookup"><span data-stu-id="6ac61-133">Double</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="6ac61-134">任何列舉型別 ([列舉](../../../../visual-basic/language-reference/statements/enum-statement.md))</span><span class="sxs-lookup"><span data-stu-id="6ac61-134">Any enumerated type ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="6ac61-135">其基礎的整數類資料類型和任何類型的基礎類型將擴展。</span><span class="sxs-lookup"><span data-stu-id="6ac61-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="6ac61-136">Char</span><span class="sxs-lookup"><span data-stu-id="6ac61-136">Char</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="6ac61-137">`Char`, `String`</span><span class="sxs-lookup"><span data-stu-id="6ac61-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="6ac61-138">`Char` 陣列</span><span class="sxs-lookup"><span data-stu-id="6ac61-138">`Char` array</span></span>|<span data-ttu-id="6ac61-139">`Char` 陣列， `String`</span><span class="sxs-lookup"><span data-stu-id="6ac61-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="6ac61-140">任何型別</span><span class="sxs-lookup"><span data-stu-id="6ac61-140">Any type</span></span>|[<span data-ttu-id="6ac61-141">物件</span><span class="sxs-lookup"><span data-stu-id="6ac61-141">Object</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="6ac61-142">任何衍生型別</span><span class="sxs-lookup"><span data-stu-id="6ac61-142">Any derived type</span></span>|<span data-ttu-id="6ac61-143">任何基底的類型衍生的來源<sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="6ac61-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="6ac61-144">任何型別</span><span class="sxs-lookup"><span data-stu-id="6ac61-144">Any type</span></span>|<span data-ttu-id="6ac61-145">它會實作任何介面。</span><span class="sxs-lookup"><span data-stu-id="6ac61-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="6ac61-146">Nothing</span><span class="sxs-lookup"><span data-stu-id="6ac61-146">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)|<span data-ttu-id="6ac61-147">任何資料類型或物件類型。</span><span class="sxs-lookup"><span data-stu-id="6ac61-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="6ac61-148"><sup>1</sup>根據定義，每個資料類型可擴展為本身。</span><span class="sxs-lookup"><span data-stu-id="6ac61-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="6ac61-149"><sup>2</sup>從不`Integer`， `UInteger`， `Long`， `ULong`，或`Decimal`至`Single`或`Double`可能會產生在遺失有效位數，但永遠不會在遺失的大小。</span><span class="sxs-lookup"><span data-stu-id="6ac61-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="6ac61-150">就這個意義而言它們不會造成資訊遺失。</span><span class="sxs-lookup"><span data-stu-id="6ac61-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="6ac61-151"><sup>3</sup>看起來令人意外從衍生型別轉換為其基底型別會擴展。</span><span class="sxs-lookup"><span data-stu-id="6ac61-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="6ac61-152">原因是衍生的類型包含基底型別的所有成員，因此它符合基底類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6ac61-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="6ac61-153">相反的方向，基底型別不包含任何新的成員所衍生的型別定義。</span><span class="sxs-lookup"><span data-stu-id="6ac61-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="6ac61-154">擴展轉換，一定要成功執行階段，並永遠不會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="6ac61-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="6ac61-155">您可以隱含地執行它們是否[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定型別檢查切換到`On`或`Off`。</span><span class="sxs-lookup"><span data-stu-id="6ac61-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="6ac61-156">縮小轉換</span><span class="sxs-lookup"><span data-stu-id="6ac61-156">Narrowing Conversions</span></span>  
 <span data-ttu-id="6ac61-157">標準的縮小轉換包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="6ac61-157">The standard narrowing conversions include the following:</span></span>  
  
-   <span data-ttu-id="6ac61-158">在上述的擴展轉換的反向資料表 （不同之處在於擴展至其本身的型別）</span><span class="sxs-lookup"><span data-stu-id="6ac61-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
-   <span data-ttu-id="6ac61-159">轉換之間的任一方向[布林](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)和任何數值類型</span><span class="sxs-lookup"><span data-stu-id="6ac61-159">Conversions in either direction between [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
-   <span data-ttu-id="6ac61-160">從任何數值類型轉換為任何列舉型別 (`Enum`)</span><span class="sxs-lookup"><span data-stu-id="6ac61-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
-   <span data-ttu-id="6ac61-161">轉換之間的任一方向[字串](../../../../visual-basic/language-reference/data-types/string-data-type.md)和任何數值類型， `Boolean`，或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="6ac61-161">Conversions in either direction between [String](../../../../visual-basic/language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span></span>  
  
-   <span data-ttu-id="6ac61-162">從資料類型或物件型別轉換從它衍生的型別</span><span class="sxs-lookup"><span data-stu-id="6ac61-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="6ac61-163">縮小轉換執行不一定成功在執行階段，並可能會失敗或者造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="6ac61-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="6ac61-164">如果目的地資料類型無法接收要轉換的值，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6ac61-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="6ac61-165">例如，數字轉換導致溢位。</span><span class="sxs-lookup"><span data-stu-id="6ac61-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="6ac61-166">編譯器不允許隱含地執行縮小轉換，除非[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定型別檢查切換到`Off`。</span><span class="sxs-lookup"><span data-stu-id="6ac61-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ac61-167">縮小轉換錯誤的轉換中的項目隱藏`For Each…Next`迴圈控制變數的集合。</span><span class="sxs-lookup"><span data-stu-id="6ac61-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="6ac61-168">如需詳細資訊與範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6ac61-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="6ac61-169">何時使用縮小轉換</span><span class="sxs-lookup"><span data-stu-id="6ac61-169">When to Use Narrowing Conversions</span></span>  
 <span data-ttu-id="6ac61-170">當您知道來源值可以轉換成目的地資料類型，而不會錯誤或資料遺失時，您可以使用縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="6ac61-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="6ac61-171">例如，如果您有`String`您知道包含"True"False"，您可以使用`CBool`關鍵字來將它轉換成`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="6ac61-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="6ac61-172">轉換期間的例外狀況</span><span class="sxs-lookup"><span data-stu-id="6ac61-172">Exceptions During Conversion</span></span>  
 <span data-ttu-id="6ac61-173">因為永遠擴展轉換成功，它們不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6ac61-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="6ac61-174">縮小轉換，失敗時，通常會擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="6ac61-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
-   <span data-ttu-id="6ac61-175"><xref:System.InvalidCastException> — 如果兩個類型之間不定義任何轉換</span><span class="sxs-lookup"><span data-stu-id="6ac61-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
-   <span data-ttu-id="6ac61-176"><xref:System.OverflowException> -（只有整數類型） 如果已轉換的值是目標類型而言太大</span><span class="sxs-lookup"><span data-stu-id="6ac61-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="6ac61-177">如果類別或結構定義[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)做為轉換運算子或從該類別或結構的`CType`可以擲回任何例外狀況，它認為適當的行動。</span><span class="sxs-lookup"><span data-stu-id="6ac61-177">If a class or structure defines a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="6ac61-178">此外的`CType`可能呼叫 Visual Basic 函式或[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]接著可能會擲回例外狀況的各種不同的方法。</span><span class="sxs-lookup"><span data-stu-id="6ac61-178">In addition, that `CType` might call Visual Basic functions or [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="6ac61-179">參考型別轉換期間的變更</span><span class="sxs-lookup"><span data-stu-id="6ac61-179">Changes During Reference Type Conversions</span></span>  
 <span data-ttu-id="6ac61-180">從轉換*參考型別*複製只有指標值。</span><span class="sxs-lookup"><span data-stu-id="6ac61-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="6ac61-181">值本身尚未複製或以任何方式變更。</span><span class="sxs-lookup"><span data-stu-id="6ac61-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="6ac61-182">唯一可以變更會保留指標變數的資料型別。</span><span class="sxs-lookup"><span data-stu-id="6ac61-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="6ac61-183">在下列範例中，資料類型會從衍生類別轉換為其基底類別，但這兩個變數指向的物件不會變更。</span><span class="sxs-lookup"><span data-stu-id="6ac61-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ac61-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ac61-184">See Also</span></span>  
 [<span data-ttu-id="6ac61-185">資料類型</span><span class="sxs-lookup"><span data-stu-id="6ac61-185">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="6ac61-186">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="6ac61-186">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="6ac61-187">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="6ac61-187">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="6ac61-188">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="6ac61-188">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="6ac61-189">如何： 將物件轉換成 Visual Basic 中的另一個類型</span><span class="sxs-lookup"><span data-stu-id="6ac61-189">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="6ac61-190">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="6ac61-190">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="6ac61-191">資料類型</span><span class="sxs-lookup"><span data-stu-id="6ac61-191">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="6ac61-192">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="6ac61-192">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
