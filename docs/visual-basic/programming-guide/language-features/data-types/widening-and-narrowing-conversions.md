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
ms.openlocfilehash: ad49e5443016dc4fed57be4a991df9f6d6095b55
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391390"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="7de14-102">擴展和縮小轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7de14-102">Widening and Narrowing Conversions (Visual Basic)</span></span>
<span data-ttu-id="7de14-103">使用類型轉換的重要考量是轉換的結果是否在目的地資料類型的範圍內。</span><span class="sxs-lookup"><span data-stu-id="7de14-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="7de14-104">A*擴展轉換*值變更為可允許任何可能的值，原始資料的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7de14-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="7de14-105">擴展轉換保留原始值，但可以變更其表示法。</span><span class="sxs-lookup"><span data-stu-id="7de14-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="7de14-106">如果您從整數類資料類型轉換的之所以`Decimal`，或從`Char`至`String`。</span><span class="sxs-lookup"><span data-stu-id="7de14-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="7de14-107">*「縮小轉換」* (narrowing conversion) 會將值變更為資料類型，而可能無法保留一些可能的值。</span><span class="sxs-lookup"><span data-stu-id="7de14-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="7de14-108">比方說，小數的值，則會轉換成整數類資料類型，並轉換成數值類型後便會四捨五入`Boolean`縮減為其中一個`True`或`False`。</span><span class="sxs-lookup"><span data-stu-id="7de14-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="7de14-109">擴展轉換</span><span class="sxs-lookup"><span data-stu-id="7de14-109">Widening Conversions</span></span>  
 <span data-ttu-id="7de14-110">下表顯示標準的擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="7de14-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="7de14-111">資料類型</span><span class="sxs-lookup"><span data-stu-id="7de14-111">Data type</span></span>|<span data-ttu-id="7de14-112">資料類型可擴展<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="7de14-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="7de14-113">SByte</span><span class="sxs-lookup"><span data-stu-id="7de14-113">SByte</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="7de14-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="7de14-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="7de14-115">Byte</span><span class="sxs-lookup"><span data-stu-id="7de14-115">Byte</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="7de14-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="7de14-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="7de14-117">Short</span><span class="sxs-lookup"><span data-stu-id="7de14-117">Short</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="7de14-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="7de14-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="7de14-119">UShort</span><span class="sxs-lookup"><span data-stu-id="7de14-119">UShort</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="7de14-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="7de14-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="7de14-121">Integer</span><span class="sxs-lookup"><span data-stu-id="7de14-121">Integer</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="7de14-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7de14-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="7de14-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="7de14-123">UInteger</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="7de14-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7de14-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="7de14-125">Long</span><span class="sxs-lookup"><span data-stu-id="7de14-125">Long</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="7de14-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7de14-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="7de14-127">ULong</span><span class="sxs-lookup"><span data-stu-id="7de14-127">ULong</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="7de14-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7de14-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="7de14-129">Decimal</span><span class="sxs-lookup"><span data-stu-id="7de14-129">Decimal</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="7de14-130">`Decimal`, `Single`, `Double`<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="7de14-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="7de14-131">Single</span><span class="sxs-lookup"><span data-stu-id="7de14-131">Single</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="7de14-132">`Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="7de14-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="7de14-133">Double</span><span class="sxs-lookup"><span data-stu-id="7de14-133">Double</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="7de14-134">任何列舉型別 ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))</span><span class="sxs-lookup"><span data-stu-id="7de14-134">Any enumerated type ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="7de14-135">其基礎的整數類資料類型和任何類型的擴展基礎的型別。</span><span class="sxs-lookup"><span data-stu-id="7de14-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="7de14-136">Char</span><span class="sxs-lookup"><span data-stu-id="7de14-136">Char</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="7de14-137">`Char`, `String`</span><span class="sxs-lookup"><span data-stu-id="7de14-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="7de14-138">`Char` 陣列</span><span class="sxs-lookup"><span data-stu-id="7de14-138">`Char` array</span></span>|<span data-ttu-id="7de14-139">`Char` 陣列， `String`</span><span class="sxs-lookup"><span data-stu-id="7de14-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="7de14-140">任何型別</span><span class="sxs-lookup"><span data-stu-id="7de14-140">Any type</span></span>|[<span data-ttu-id="7de14-141">物件</span><span class="sxs-lookup"><span data-stu-id="7de14-141">Object</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="7de14-142">任何衍生型別</span><span class="sxs-lookup"><span data-stu-id="7de14-142">Any derived type</span></span>|<span data-ttu-id="7de14-143">任何基底的類型衍生自此<sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="7de14-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="7de14-144">任何型別</span><span class="sxs-lookup"><span data-stu-id="7de14-144">Any type</span></span>|<span data-ttu-id="7de14-145">它會實作任何介面。</span><span class="sxs-lookup"><span data-stu-id="7de14-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="7de14-146">Nothing</span><span class="sxs-lookup"><span data-stu-id="7de14-146">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)|<span data-ttu-id="7de14-147">任何資料型別或物件型別。</span><span class="sxs-lookup"><span data-stu-id="7de14-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="7de14-148"><sup>1</sup>根據定義，每個資料類型可擴展為本身。</span><span class="sxs-lookup"><span data-stu-id="7de14-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="7de14-149"><sup>2</sup>從不`Integer`， `UInteger`， `Long`， `ULong`，或`Decimal`至`Single`或`Double`可能會導致遺失有效位數，但永遠不會遺失大小。</span><span class="sxs-lookup"><span data-stu-id="7de14-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="7de14-150">在這種情況下它們不會造成資訊遺失。</span><span class="sxs-lookup"><span data-stu-id="7de14-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="7de14-151"><sup>3</sup>一定很驚訝從衍生的型別轉換為其基底型別會擴展。</span><span class="sxs-lookup"><span data-stu-id="7de14-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="7de14-152">理由是衍生型別包含的基底類型中，所有成員，因此它有資格做為基底類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="7de14-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="7de14-153">朝相反的方向的基底類型不包含任何新的成員所衍生的型別定義。</span><span class="sxs-lookup"><span data-stu-id="7de14-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="7de14-154">擴展轉換時，一律在執行階段成功，而且永遠不會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="7de14-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="7de14-155">您可以隱含地執行它們是否[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定檢查參數的型別`On`或`Off`。</span><span class="sxs-lookup"><span data-stu-id="7de14-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="7de14-156">縮小轉換</span><span class="sxs-lookup"><span data-stu-id="7de14-156">Narrowing Conversions</span></span>  
 <span data-ttu-id="7de14-157">標準的縮小轉換包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="7de14-157">The standard narrowing conversions include the following:</span></span>  
  
-   <span data-ttu-id="7de14-158">在上述的擴展轉換的反向資料表 （不同之處在於每個類型可擴展為本身）</span><span class="sxs-lookup"><span data-stu-id="7de14-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
-   <span data-ttu-id="7de14-159">在任一方向之間的轉換[布林](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)和任何數值類型</span><span class="sxs-lookup"><span data-stu-id="7de14-159">Conversions in either direction between [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
-   <span data-ttu-id="7de14-160">從任何數值類型轉換為任何列舉型別 (`Enum`)</span><span class="sxs-lookup"><span data-stu-id="7de14-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
-   <span data-ttu-id="7de14-161">在任一方向之間的轉換[字串](../../../../visual-basic/language-reference/data-types/string-data-type.md)任何數值類型，以及`Boolean`，或[日期](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="7de14-161">Conversions in either direction between [String](../../../../visual-basic/language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)</span></span>  
  
-   <span data-ttu-id="7de14-162">從資料型別或物件型別轉換成從其衍生類型</span><span class="sxs-lookup"><span data-stu-id="7de14-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="7de14-163">縮小轉換執行不一定成功在執行階段，並可能會失敗或者會造成資料遺失。</span><span class="sxs-lookup"><span data-stu-id="7de14-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="7de14-164">如果目的地資料類型無法接收轉換的值，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7de14-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="7de14-165">例如，數值轉換可能會導致溢位。</span><span class="sxs-lookup"><span data-stu-id="7de14-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="7de14-166">編譯器不允許以隱含方式執行縮小轉換，除非[Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定類型檢查參數以`Off`。</span><span class="sxs-lookup"><span data-stu-id="7de14-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7de14-167">轉換中的項目隱藏的縮小轉換錯誤`For Each…Next`迴圈控制變數的集合。</span><span class="sxs-lookup"><span data-stu-id="7de14-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="7de14-168">如需詳細資訊和範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="7de14-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="7de14-169">何時使用縮小轉換</span><span class="sxs-lookup"><span data-stu-id="7de14-169">When to Use Narrowing Conversions</span></span>  
 <span data-ttu-id="7de14-170">當您知道來源值可以轉換成目的資料型別，而不會錯誤或資料遺失時，您可以使用縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="7de14-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="7de14-171">例如，如果您有`String`您知道包含"True"False"，您可以使用`CBool`關鍵字來將它轉換成`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="7de14-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="7de14-172">在轉換期間的例外狀況</span><span class="sxs-lookup"><span data-stu-id="7de14-172">Exceptions During Conversion</span></span>  
 <span data-ttu-id="7de14-173">因為一律擴展轉換成功，則不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7de14-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="7de14-174">縮小轉換，失敗時，通常會擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="7de14-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
-   <span data-ttu-id="7de14-175"><xref:System.InvalidCastException> -如果任何轉換不定義兩個類型之間</span><span class="sxs-lookup"><span data-stu-id="7de14-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
-   <span data-ttu-id="7de14-176"><xref:System.OverflowException> -（只有整數類型） 如果已轉換的值太大的目標型別</span><span class="sxs-lookup"><span data-stu-id="7de14-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="7de14-177">如果類別或結構定義[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)做為與該類別或結構，轉換運算子，`CType`可能會擲回它認為適當的任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7de14-177">If a class or structure defines a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="7de14-178">此外，所`CType`可能會呼叫 Visual Basic 函式或[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]接著可能會擲回例外狀況的各種不同的方法。</span><span class="sxs-lookup"><span data-stu-id="7de14-178">In addition, that `CType` might call Visual Basic functions or [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="7de14-179">參考型別轉換期間的變更</span><span class="sxs-lookup"><span data-stu-id="7de14-179">Changes During Reference Type Conversions</span></span>  
 <span data-ttu-id="7de14-180">從轉換*參考的型別*複製值的指標。</span><span class="sxs-lookup"><span data-stu-id="7de14-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="7de14-181">值本身不會複製或以任何方式變更。</span><span class="sxs-lookup"><span data-stu-id="7de14-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="7de14-182">唯一可以變更為指標的變數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7de14-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="7de14-183">在下列範例中，資料類型轉換從衍生類別為其基底類別，但這兩個變數現在指向的物件不會變更。</span><span class="sxs-lookup"><span data-stu-id="7de14-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="7de14-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7de14-184">See Also</span></span>  
 [<span data-ttu-id="7de14-185">資料類型</span><span class="sxs-lookup"><span data-stu-id="7de14-185">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="7de14-186">在 Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="7de14-186">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="7de14-187">隱含和明確轉換</span><span class="sxs-lookup"><span data-stu-id="7de14-187">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="7de14-188">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="7de14-188">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="7de14-189">如何： 將物件轉換成 Visual Basic 中的另一個類型</span><span class="sxs-lookup"><span data-stu-id="7de14-189">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="7de14-190">陣列轉換</span><span class="sxs-lookup"><span data-stu-id="7de14-190">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="7de14-191">資料類型</span><span class="sxs-lookup"><span data-stu-id="7de14-191">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="7de14-192">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="7de14-192">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
