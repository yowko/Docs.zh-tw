---
title: Widening and Narrowing Conversions
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
ms.openlocfilehash: c0e10f5593ce5c81002233516444e415571541f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058530"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="20d03-102">擴展和縮小轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20d03-102">Widening and Narrowing Conversions (Visual Basic)</span></span>

<span data-ttu-id="20d03-103">類型轉換的重要考慮是轉換的結果是否在目的地資料類型的範圍內。</span><span class="sxs-lookup"><span data-stu-id="20d03-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="20d03-104">「 *擴展」轉換* 會將值變更為資料類型，以允許任何可能的原始資料值。</span><span class="sxs-lookup"><span data-stu-id="20d03-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="20d03-105">擴輾轉換會保留來源值，但可以變更其標記法。</span><span class="sxs-lookup"><span data-stu-id="20d03-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="20d03-106">如果您從整數類資料類型轉換為，或從轉換成，就會發生這種情況 `Decimal` `Char` `String` 。</span><span class="sxs-lookup"><span data-stu-id="20d03-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="20d03-107">*「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。</span><span class="sxs-lookup"><span data-stu-id="20d03-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="20d03-108">例如，當小數值轉換成整數類資料類型，而且要轉換的數數值型別縮減為或時，會將其四捨五入 `Boolean` `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="20d03-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="20d03-109">擴展轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-109">Widening Conversions</span></span>  

 <span data-ttu-id="20d03-110">下表顯示標準的擴輾轉換。</span><span class="sxs-lookup"><span data-stu-id="20d03-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="20d03-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="20d03-111">Data type</span></span>|<span data-ttu-id="20d03-112">擴大至資料類型 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="20d03-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="20d03-113">SByte</span><span class="sxs-lookup"><span data-stu-id="20d03-113">SByte</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="20d03-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="20d03-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="20d03-115">位元組</span><span class="sxs-lookup"><span data-stu-id="20d03-115">Byte</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="20d03-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="20d03-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="20d03-117">短</span><span class="sxs-lookup"><span data-stu-id="20d03-117">Short</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="20d03-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="20d03-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="20d03-119">UShort</span><span class="sxs-lookup"><span data-stu-id="20d03-119">UShort</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="20d03-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="20d03-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="20d03-121">整數</span><span class="sxs-lookup"><span data-stu-id="20d03-121">Integer</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="20d03-122">`Integer`、 `Long` 、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="20d03-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="20d03-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="20d03-123">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="20d03-124">`UInteger`、 `Long` 、 `ULong` 、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="20d03-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="20d03-125">Long</span><span class="sxs-lookup"><span data-stu-id="20d03-125">Long</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="20d03-126">`Long`、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="20d03-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="20d03-127">ULong</span><span class="sxs-lookup"><span data-stu-id="20d03-127">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="20d03-128">`ULong`、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="20d03-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="20d03-129">十進位</span><span class="sxs-lookup"><span data-stu-id="20d03-129">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="20d03-130">`Decimal`、 `Single` 、 `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="20d03-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="20d03-131">Single</span><span class="sxs-lookup"><span data-stu-id="20d03-131">Single</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="20d03-132">`Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="20d03-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="20d03-133">Double</span><span class="sxs-lookup"><span data-stu-id="20d03-133">Double</span></span>](../../../language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="20d03-134">[列舉 (列舉](../../../language-reference/statements/enum-statement.md)型別) </span><span class="sxs-lookup"><span data-stu-id="20d03-134">Any enumerated type ([Enum](../../../language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="20d03-135">其基礎整數型別，以及基礎類型擴展的任何型別。</span><span class="sxs-lookup"><span data-stu-id="20d03-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="20d03-136">字元</span><span class="sxs-lookup"><span data-stu-id="20d03-136">Char</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="20d03-137">`Char`, `String`</span><span class="sxs-lookup"><span data-stu-id="20d03-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="20d03-138">`Char` 陣列</span><span class="sxs-lookup"><span data-stu-id="20d03-138">`Char` array</span></span>|<span data-ttu-id="20d03-139">`Char` 陣 列 `String`</span><span class="sxs-lookup"><span data-stu-id="20d03-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="20d03-140">任何型別</span><span class="sxs-lookup"><span data-stu-id="20d03-140">Any type</span></span>|[<span data-ttu-id="20d03-141">Object</span><span class="sxs-lookup"><span data-stu-id="20d03-141">Object</span></span>](../../../language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="20d03-142">任何衍生類型</span><span class="sxs-lookup"><span data-stu-id="20d03-142">Any derived type</span></span>|<span data-ttu-id="20d03-143">衍生自的任何基底類型 <sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="20d03-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="20d03-144">任何型別</span><span class="sxs-lookup"><span data-stu-id="20d03-144">Any type</span></span>|<span data-ttu-id="20d03-145">它所實行的任何介面。</span><span class="sxs-lookup"><span data-stu-id="20d03-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="20d03-146">什麼</span><span class="sxs-lookup"><span data-stu-id="20d03-146">Nothing</span></span>](../../../language-reference/nothing.md)|<span data-ttu-id="20d03-147">任何資料類型或物件類型。</span><span class="sxs-lookup"><span data-stu-id="20d03-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="20d03-148"><sup>1</sup> 依照定義，每個資料類型都會擴大為本身。</span><span class="sxs-lookup"><span data-stu-id="20d03-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="20d03-149"><sup>2</sup> 從 `Integer` 、 `UInteger` 、 `Long` 、或轉換 `ULong` `Decimal` 成 `Single` 或 `Double` 可能會導致精確度遺失，但不會遺失大小。</span><span class="sxs-lookup"><span data-stu-id="20d03-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="20d03-150">在這種情況下，不會導致資訊遺失。</span><span class="sxs-lookup"><span data-stu-id="20d03-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="20d03-151"><sup>3</sup> 看看從衍生型別轉換成其基底類型的其中一個基底類型，可能看起來很奇怪。</span><span class="sxs-lookup"><span data-stu-id="20d03-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="20d03-152">理由是衍生型別包含基底類型的所有成員，因此它會限定為基底類型的實例。</span><span class="sxs-lookup"><span data-stu-id="20d03-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="20d03-153">相反地，基底類型不包含任何由衍生型別所定義的新成員。</span><span class="sxs-lookup"><span data-stu-id="20d03-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="20d03-154">擴輾轉換一律會在執行時間成功，且不會產生資料遺失。</span><span class="sxs-lookup"><span data-stu-id="20d03-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="20d03-155">您一律可以隱含地執行它們，無論 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md) 是否將型別檢查參數設定為 `On` 或 `Off` 。</span><span class="sxs-lookup"><span data-stu-id="20d03-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="20d03-156">縮小轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-156">Narrowing Conversions</span></span>  

 <span data-ttu-id="20d03-157">標準的縮小轉換包含下列各項：</span><span class="sxs-lookup"><span data-stu-id="20d03-157">The standard narrowing conversions include the following:</span></span>  
  
- <span data-ttu-id="20d03-158">上表中擴輾轉換的反向指示 (，但每個類型會擴大為本身) </span><span class="sxs-lookup"><span data-stu-id="20d03-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
- <span data-ttu-id="20d03-159">在 [布林值](../../../language-reference/data-types/boolean-data-type.md) 與任何數數值型別之間的雙向轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-159">Conversions in either direction between [Boolean](../../../language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
- <span data-ttu-id="20d03-160">從任何數數值型別轉換成任何列舉型別 (`Enum`) </span><span class="sxs-lookup"><span data-stu-id="20d03-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
- <span data-ttu-id="20d03-161">[字串](../../../language-reference/data-types/string-data-type.md)與任何數數值型別、 `Boolean` 或[日期](../../../language-reference/data-types/date-data-type.md)之間的任何方向轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-161">Conversions in either direction between [String](../../../language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../language-reference/data-types/date-data-type.md)</span></span>  
  
- <span data-ttu-id="20d03-162">從資料類型或物件類型轉換成衍生自它的型別</span><span class="sxs-lookup"><span data-stu-id="20d03-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="20d03-163">縮小轉換在執行時間不一定會成功，而且可能會失敗或導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="20d03-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="20d03-164">如果目的地資料類型無法接收要轉換的值，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="20d03-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="20d03-165">例如，數值轉換可能會造成溢位。</span><span class="sxs-lookup"><span data-stu-id="20d03-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="20d03-166">編譯器不允許您隱含地執行縮小轉換，除非 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md) 將類型檢查參數設定為 `Off` 。</span><span class="sxs-lookup"><span data-stu-id="20d03-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20d03-167">從集合中的專案轉換 `For Each…Next` 到迴圈控制變數時，會隱藏縮小轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="20d03-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="20d03-168">如需詳細資訊和範例，請參閱 For Each 中的「縮小轉換」一節。 [下一個語句](../../../language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="20d03-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="20d03-169">使用縮小轉換的時機</span><span class="sxs-lookup"><span data-stu-id="20d03-169">When to Use Narrowing Conversions</span></span>  

 <span data-ttu-id="20d03-170">當您知道來源值可以轉換為目的地資料類型，而沒有發生錯誤或資料遺失時，您可以使用縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="20d03-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="20d03-171">例如，如果您 `String` 知道您知道包含 "True" 或 "False"，您可以使用 `CBool` 關鍵字將它轉換成 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="20d03-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="20d03-172">轉換期間的例外狀況</span><span class="sxs-lookup"><span data-stu-id="20d03-172">Exceptions During Conversion</span></span>  

 <span data-ttu-id="20d03-173">因為擴輾轉換一律會成功，所以不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="20d03-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="20d03-174">縮小轉換失敗時，最常擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="20d03-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
- <span data-ttu-id="20d03-175"><xref:System.InvalidCastException> -如果兩個類型之間沒有定義任何轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
- <span data-ttu-id="20d03-176"><xref:System.OverflowException> —只有在轉換的值對目標型別而言太大時，才)  (整數類型</span><span class="sxs-lookup"><span data-stu-id="20d03-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="20d03-177">如果類別或結構定義了 [CType](../../../language-reference/functions/ctype-function.md) 函式做為該類別或結構的轉換運算子，則 `CType` 可能會擲回它認為適當的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="20d03-177">If a class or structure defines a [CType Function](../../../language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="20d03-178">此外，這 `CType` 可能會呼叫 Visual Basic 函式或 .NET Framework 方法，進而擲回不同的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="20d03-178">In addition, that `CType` might call Visual Basic functions or .NET Framework methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="20d03-179">參考型別轉換期間的變更</span><span class="sxs-lookup"><span data-stu-id="20d03-179">Changes During Reference Type Conversions</span></span>  

 <span data-ttu-id="20d03-180">從 *參考型* 別進行轉換時，只會複製值的指標。</span><span class="sxs-lookup"><span data-stu-id="20d03-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="20d03-181">此值本身不會以任何方式複製或變更。</span><span class="sxs-lookup"><span data-stu-id="20d03-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="20d03-182">唯一可變更的內容是包含指標之變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="20d03-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="20d03-183">在下列範例中，資料類型會從衍生類別轉換成其基類，但兩個變數現在指向的物件也不會變更。</span><span class="sxs-lookup"><span data-stu-id="20d03-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="20d03-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20d03-184">See also</span></span>

- [<span data-ttu-id="20d03-185">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="20d03-185">Data Types</span></span>](index.md)
- [<span data-ttu-id="20d03-186">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-186">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="20d03-187">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-187">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="20d03-188">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-188">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="20d03-189">如何：在 Visual Basic 中將物件轉換成其他類型</span><span class="sxs-lookup"><span data-stu-id="20d03-189">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="20d03-190">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="20d03-190">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="20d03-191">Data types (資料類型)</span><span class="sxs-lookup"><span data-stu-id="20d03-191">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="20d03-192">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="20d03-192">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
