---
title: 擴展和縮小轉換 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: d1822afc4b10a725e13c1469a068c30813d3a2d3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582729"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="8730e-102">擴展和縮小轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8730e-102">Widening and Narrowing Conversions (Visual Basic)</span></span>
<span data-ttu-id="8730e-103">類型轉換的重要考慮是轉換的結果是否在目的地資料類型的範圍內。</span><span class="sxs-lookup"><span data-stu-id="8730e-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="8730e-104">*擴輾轉換*會將值變更為資料類型，以允許原始資料的任何可能值。</span><span class="sxs-lookup"><span data-stu-id="8730e-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="8730e-105">擴輾轉換會保留來源值，但可以變更其表示。</span><span class="sxs-lookup"><span data-stu-id="8730e-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="8730e-106">如果您從整數類資料類型轉換成 `Decimal`，或從 `Char` 轉換成 `String`，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="8730e-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="8730e-107">*「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。</span><span class="sxs-lookup"><span data-stu-id="8730e-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="8730e-108">例如，當小數值轉換成整數類資料類型時，會將其四捨五入，而轉換成 `Boolean` 的數數值型別則會縮減為 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="8730e-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="8730e-109">擴展轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-109">Widening Conversions</span></span>  
 <span data-ttu-id="8730e-110">下表顯示標準的擴輾轉換。</span><span class="sxs-lookup"><span data-stu-id="8730e-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="8730e-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="8730e-111">Data type</span></span>|<span data-ttu-id="8730e-112">擴大至資料類型<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8730e-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="8730e-113">SByte</span><span class="sxs-lookup"><span data-stu-id="8730e-113">SByte</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="8730e-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="8730e-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="8730e-115">Byte</span><span class="sxs-lookup"><span data-stu-id="8730e-115">Byte</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="8730e-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="8730e-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="8730e-117">Short</span><span class="sxs-lookup"><span data-stu-id="8730e-117">Short</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="8730e-118">`Short`、 `Integer`、 `Long`、 `Decimal`、 `Single`、 `Double`</span><span class="sxs-lookup"><span data-stu-id="8730e-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="8730e-119">UShort</span><span class="sxs-lookup"><span data-stu-id="8730e-119">UShort</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="8730e-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="8730e-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="8730e-121">Integer</span><span class="sxs-lookup"><span data-stu-id="8730e-121">Integer</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="8730e-122">`Integer`、`Long`、`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8730e-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="8730e-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="8730e-123">UInteger</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="8730e-124">`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8730e-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="8730e-125">Long</span><span class="sxs-lookup"><span data-stu-id="8730e-125">Long</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="8730e-126">`Long`、`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8730e-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="8730e-127">ULong</span><span class="sxs-lookup"><span data-stu-id="8730e-127">ULong</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="8730e-128">`ULong`、`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8730e-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="8730e-129">Decimal</span><span class="sxs-lookup"><span data-stu-id="8730e-129">Decimal</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="8730e-130">`Decimal`、`Single`、`Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8730e-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="8730e-131">Single</span><span class="sxs-lookup"><span data-stu-id="8730e-131">Single</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="8730e-132">`Single`、 `Double`</span><span class="sxs-lookup"><span data-stu-id="8730e-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="8730e-133">Double</span><span class="sxs-lookup"><span data-stu-id="8730e-133">Double</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="8730e-134">任何列舉型別（[Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)）</span><span class="sxs-lookup"><span data-stu-id="8730e-134">Any enumerated type ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="8730e-135">其基礎整數類型，以及基礎類型所擴展的任何類型。</span><span class="sxs-lookup"><span data-stu-id="8730e-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="8730e-136">Char</span><span class="sxs-lookup"><span data-stu-id="8730e-136">Char</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="8730e-137">`Char`、 `String`</span><span class="sxs-lookup"><span data-stu-id="8730e-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="8730e-138">`Char` 陣列</span><span class="sxs-lookup"><span data-stu-id="8730e-138">`Char` array</span></span>|<span data-ttu-id="8730e-139">`Char` 陣列，`String`</span><span class="sxs-lookup"><span data-stu-id="8730e-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="8730e-140">任何類型</span><span class="sxs-lookup"><span data-stu-id="8730e-140">Any type</span></span>|[<span data-ttu-id="8730e-141">物件</span><span class="sxs-lookup"><span data-stu-id="8730e-141">Object</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="8730e-142">任何衍生類型</span><span class="sxs-lookup"><span data-stu-id="8730e-142">Any derived type</span></span>|<span data-ttu-id="8730e-143">衍生它的任何基底類型<sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="8730e-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="8730e-144">任何類型</span><span class="sxs-lookup"><span data-stu-id="8730e-144">Any type</span></span>|<span data-ttu-id="8730e-145">它所實行的任何介面。</span><span class="sxs-lookup"><span data-stu-id="8730e-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="8730e-146">Nothing</span><span class="sxs-lookup"><span data-stu-id="8730e-146">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)|<span data-ttu-id="8730e-147">任何資料類型或物件類型。</span><span class="sxs-lookup"><span data-stu-id="8730e-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="8730e-148"><sup>1</sup>根據定義，每個資料類型會擴展到其本身。</span><span class="sxs-lookup"><span data-stu-id="8730e-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="8730e-149"><sup>2</sup>從 `Integer`、`UInteger`、`Long`、`ULong` 或 `Decimal` 轉換成 `Single` 或 `Double` 可能會導致精確度遺失，但不會遺失大小。</span><span class="sxs-lookup"><span data-stu-id="8730e-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="8730e-150">就這一點而言，它們不會造成資訊遺失。</span><span class="sxs-lookup"><span data-stu-id="8730e-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="8730e-151"><sup>3</sup>在從衍生型別轉換成其中一個基底類型時，它看起來可能會很令人驚訝。</span><span class="sxs-lookup"><span data-stu-id="8730e-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="8730e-152">理由是，衍生的型別包含基底型別的所有成員，因此它會限定為基底型別的實例。</span><span class="sxs-lookup"><span data-stu-id="8730e-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="8730e-153">相反地，基底類型不會包含衍生類型所定義的任何新成員。</span><span class="sxs-lookup"><span data-stu-id="8730e-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="8730e-154">擴輾轉換一律會在執行時間成功，而且永遠不會產生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="8730e-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="8730e-155">無論[Option Strict 語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)是否將類型檢查參數設定為 `On` 或 `Off`，一律可以隱含地執行它們。</span><span class="sxs-lookup"><span data-stu-id="8730e-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="8730e-156">縮小轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-156">Narrowing Conversions</span></span>  
 <span data-ttu-id="8730e-157">標準的縮小轉換包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="8730e-157">The standard narrowing conversions include the following:</span></span>  
  
- <span data-ttu-id="8730e-158">上表中擴輾轉換的反向指示（不同的是，每個類型會擴展為其本身）</span><span class="sxs-lookup"><span data-stu-id="8730e-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
- <span data-ttu-id="8730e-159">[布林值](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)與任何數數值型別之間任一方向的轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-159">Conversions in either direction between [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
- <span data-ttu-id="8730e-160">從任何數數值型別轉換成任何列舉類型（`Enum`）</span><span class="sxs-lookup"><span data-stu-id="8730e-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
- <span data-ttu-id="8730e-161">[字串](../../../../visual-basic/language-reference/data-types/string-data-type.md)與任何數數值型別、`Boolean` 或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)之間任一方向的轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-161">Conversions in either direction between [String](../../../../visual-basic/language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span></span>  
  
- <span data-ttu-id="8730e-162">從資料類型或物件類型轉換成衍生自它的類型</span><span class="sxs-lookup"><span data-stu-id="8730e-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="8730e-163">縮小轉換在執行時間不一定會成功，而且可能會失敗或產生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="8730e-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="8730e-164">如果目的地資料類型無法接收要轉換的值，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="8730e-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="8730e-165">例如，數值轉換可能會造成溢位。</span><span class="sxs-lookup"><span data-stu-id="8730e-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="8730e-166">編譯器不允許您隱含執行縮小轉換，除非[Option Strict 語句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)將類型檢查參數設定為 `Off`。</span><span class="sxs-lookup"><span data-stu-id="8730e-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8730e-167">從 `For Each…Next` 集合中的元素轉換為迴圈控制變數時，會抑制縮小轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="8730e-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="8730e-168">如需詳細資訊和範例，請參閱 For Each ... 中的「縮小轉換」一節。 [下一個語句](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="8730e-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="8730e-169">使用縮小轉換的時機</span><span class="sxs-lookup"><span data-stu-id="8730e-169">When to Use Narrowing Conversions</span></span>  
 <span data-ttu-id="8730e-170">當您知道來源值可以轉換成目的地資料類型，而不會發生錯誤或資料遺失時，您會使用縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="8730e-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="8730e-171">例如，如果您的 `String` 知道包含 "True" 或 "False"，則可以使用 `CBool` 關鍵字將它轉換成 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="8730e-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="8730e-172">轉換期間的例外狀況</span><span class="sxs-lookup"><span data-stu-id="8730e-172">Exceptions During Conversion</span></span>  
 <span data-ttu-id="8730e-173">由於擴輾轉換一律會成功，因此不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8730e-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="8730e-174">縮小轉換時，當它們失敗時，最常擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="8730e-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
- <span data-ttu-id="8730e-175"><xref:System.InvalidCastException>-如果兩個類型之間未定義任何轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
- <span data-ttu-id="8730e-176"><xref:System.OverflowException>-（僅限整數類型），如果轉換過的值對目標型別而言太大</span><span class="sxs-lookup"><span data-stu-id="8730e-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="8730e-177">如果類別或結構定義了一個[CType](../../../../visual-basic/language-reference/functions/ctype-function.md)函式，以做為該類別或結構的轉換運算子，`CType` 可能會擲回任何符合的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8730e-177">If a class or structure defines a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="8730e-178">此外，`CType` 可能會呼叫 Visual Basic 函數或 .NET Framework 方法，而這可能會擲回各種例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8730e-178">In addition, that `CType` might call Visual Basic functions or .NET Framework methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="8730e-179">參考型別轉換期間的變更</span><span class="sxs-lookup"><span data-stu-id="8730e-179">Changes During Reference Type Conversions</span></span>  
 <span data-ttu-id="8730e-180">從*參考型*別進行的轉換只會將指標複製到值。</span><span class="sxs-lookup"><span data-stu-id="8730e-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="8730e-181">值本身不會以任何方式複製也不會變更。</span><span class="sxs-lookup"><span data-stu-id="8730e-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="8730e-182">唯一可以變更的東西是包含指標之變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8730e-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="8730e-183">在下列範例中，資料類型會從衍生類別轉換為其基類，但目前這兩個變數所指向的物件不會變更。</span><span class="sxs-lookup"><span data-stu-id="8730e-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="8730e-184">請參閱</span><span class="sxs-lookup"><span data-stu-id="8730e-184">See also</span></span>

- [<span data-ttu-id="8730e-185">資料類型</span><span class="sxs-lookup"><span data-stu-id="8730e-185">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="8730e-186">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-186">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="8730e-187">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-187">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="8730e-188">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-188">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="8730e-189">如何：在 Visual Basic 中將物件轉換為另一種類型</span><span class="sxs-lookup"><span data-stu-id="8730e-189">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="8730e-190">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="8730e-190">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [<span data-ttu-id="8730e-191">資料類型</span><span class="sxs-lookup"><span data-stu-id="8730e-191">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="8730e-192">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="8730e-192">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
