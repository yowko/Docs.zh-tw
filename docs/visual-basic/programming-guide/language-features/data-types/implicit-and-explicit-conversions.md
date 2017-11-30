---
title: "隱含和明確轉換 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e9dd698e1cc84464cd12d33767feec960c511ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="6f2c4-102">隱含和明確轉換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f2c4-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="6f2c4-103">*隱含轉換*不需要任何特殊的語法，在原始程式碼中。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="6f2c4-104">在下列範例中，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]的值隱含轉換`k`的單精確度浮點值，然後再將它指派給`q`。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-104">In the following example, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="6f2c4-105">*明確轉換*使用類型轉換關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-105">An *explicit conversion* uses a type conversion keyword.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="6f2c4-106">提供數個這類關鍵字，會強制轉型為所需的資料類型的括號括住的運算式。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-106"> provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="6f2c4-107">這些關鍵字做為函式，但是編譯器會產生內嵌程式碼，因此執行速度稍微比函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="6f2c4-108">在上述範例中，下列延伸`CInt`關鍵字的值轉換`q`回之前將它指派給整數`k`。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="6f2c4-109">轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="6f2c4-109">Conversion Keywords</span></span>  
 <span data-ttu-id="6f2c4-110">下表顯示可用的轉換關鍵字。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="6f2c4-111">類型轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="6f2c4-111">Type conversion keyword</span></span>|<span data-ttu-id="6f2c4-112">將運算式轉換成資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-112">Converts an expression to data type</span></span>|<span data-ttu-id="6f2c4-113">要轉換之運算式的可允許的資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="6f2c4-114">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="6f2c4-115">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="6f2c4-116">Byte 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="6f2c4-117">任何數值類型 (包括`SByte`和列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="6f2c4-118">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="6f2c4-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="6f2c4-120">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="6f2c4-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="6f2c4-122">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="6f2c4-123">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="6f2c4-124">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="6f2c4-125">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="6f2c4-126">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="6f2c4-127">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="6f2c4-128">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="6f2c4-129">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="6f2c4-130">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="6f2c4-131">任何型別</span><span class="sxs-lookup"><span data-stu-id="6f2c4-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="6f2c4-132">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="6f2c4-133">任何數值類型 (包括`Byte`和列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="6f2c4-134">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="6f2c4-135">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="6f2c4-136">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="6f2c4-137">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="6f2c4-138">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="6f2c4-139">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `Char`，`Char`陣列、 `Date`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="6f2c4-140">輸入指定下列逗號 (`,`)</span><span class="sxs-lookup"><span data-stu-id="6f2c4-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="6f2c4-141">當轉換成*基本資料型別*（包括基礎類型的陣列），相同類型做為允許對應轉換關鍵字</span><span class="sxs-lookup"><span data-stu-id="6f2c4-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="6f2c4-142">當轉換成*複合資料類型*，它實作的介面以及它所繼承的類別</span><span class="sxs-lookup"><span data-stu-id="6f2c4-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="6f2c4-143">轉換為類別或結構上您有多載時`CType`，該類別或結構</span><span class="sxs-lookup"><span data-stu-id="6f2c4-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="6f2c4-144">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="6f2c4-145">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="6f2c4-146">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="6f2c4-147">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="6f2c4-148">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="6f2c4-149">任何數值類型 (包括`Byte`， `SByte`，並且會在列舉型別)， `Boolean`， `String`，`Object`</span><span class="sxs-lookup"><span data-stu-id="6f2c4-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="6f2c4-150">CType 函式</span><span class="sxs-lookup"><span data-stu-id="6f2c4-150">The CType Function</span></span>  
 <span data-ttu-id="6f2c4-151">[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)兩個引數上運作。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="6f2c4-152">第一個要轉換的運算式，而第二個目的地資料類型或物件類別。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="6f2c4-153">請注意第一個引數必須是運算式，不是型別。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="6f2c4-154">`CType`是*內嵌函式*，這表示已編譯的程式碼會進行轉換，通常不會產生函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="6f2c4-155">這可改善效能。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-155">This improves performance.</span></span>  
  
 <span data-ttu-id="6f2c4-156">如需的比較`CType`與其他類型轉換關鍵字，請參閱[DirectCast 運算子](../../../../visual-basic/language-reference/operators/directcast-operator.md)和[TryCast 運算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="6f2c4-157">基礎類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-157">Elementary Types</span></span>  
 <span data-ttu-id="6f2c4-158">下列範例示範 `CType` 的用法。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="6f2c4-159">複合類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-159">Composite Types</span></span>  
 <span data-ttu-id="6f2c4-160">您可以使用`CType`將值轉換為複合資料型別以及基本型別。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="6f2c4-161">您也可以使用要強制轉型物件類別類型的其中一個介面，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="6f2c4-162">陣列類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-162">Array Types</span></span>  
 <span data-ttu-id="6f2c4-163">`CType`也可以轉換陣列資料類型，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 <span data-ttu-id="6f2c4-164">如需詳細資訊和範例，請參閱[陣列轉換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="6f2c4-165">定義 CType 的類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-165">Types Defining CType</span></span>  
 <span data-ttu-id="6f2c4-166">您可以定義`CType`上類別或您已定義的結構。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="6f2c4-167">這可讓您將類別或結構的型別進行來回轉換的值。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="6f2c4-168">如需詳細資訊和範例，請參閱[如何： 定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f2c4-169">轉換關鍵字搭配使用的值必須是有效的目的地資料類型，或發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="6f2c4-170">比方說，如果您嘗試轉換`Long`至`Integer`，值`Long`的有效範圍內必須是`Integer`資料型別。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="6f2c4-171">指定`CType`如果目的型別並非衍生的來源類型，從一個類別類型轉換為另一個執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="6f2c4-172">這類失敗會擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="6f2c4-173">不過，如果其中一個類型是結構或類別定義，以及如果您已經定義`CType`該結構或類別，如果它符合的需求，可以成功轉換您`CType`。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="6f2c4-174">請參閱[如何： 定義轉換運算子](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="6f2c4-175">執行明確的轉換就是所謂*轉型*運算式，以指定的資料型別或物件類別。</span><span class="sxs-lookup"><span data-stu-id="6f2c4-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f2c4-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f2c4-176">See Also</span></span>  
 [<span data-ttu-id="6f2c4-177">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="6f2c4-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="6f2c4-178">字串與其他類型之間的轉換</span><span class="sxs-lookup"><span data-stu-id="6f2c4-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [<span data-ttu-id="6f2c4-179">如何： 將物件轉換成 Visual Basic 中的另一個類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="6f2c4-180">結構</span><span class="sxs-lookup"><span data-stu-id="6f2c4-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6f2c4-181">資料類型</span><span class="sxs-lookup"><span data-stu-id="6f2c4-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="6f2c4-182">類型轉換函式</span><span class="sxs-lookup"><span data-stu-id="6f2c4-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="6f2c4-183">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="6f2c4-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
