---
title: "類型轉換函式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 117cd4ce038a533715bbc86558545f0f223dd149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="a65a7-102">類型轉換函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a65a7-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="a65a7-103">這些函式是編譯的內嵌，這表示，轉換程式碼程式碼可評估運算式的一部分。</span><span class="sxs-lookup"><span data-stu-id="a65a7-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="a65a7-104">有時候可能沒有任何呼叫程序來完成轉換，進而改善效能。</span><span class="sxs-lookup"><span data-stu-id="a65a7-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="a65a7-105">每個函式會強制特定資料型別運算式。</span><span class="sxs-lookup"><span data-stu-id="a65a7-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65a7-106">語法</span><span class="sxs-lookup"><span data-stu-id="a65a7-106">Syntax</span></span>  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## <a name="part"></a><span data-ttu-id="a65a7-107">組件</span><span class="sxs-lookup"><span data-stu-id="a65a7-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="a65a7-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="a65a7-108">Required.</span></span> <span data-ttu-id="a65a7-109">來源資料型別的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="a65a7-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="a65a7-110">傳回值的資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-110">Return Value Data Type</span></span>  
 <span data-ttu-id="a65a7-111">下表所示，函式名稱會決定它所傳回的值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a65a7-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="a65a7-112">函式名稱</span><span class="sxs-lookup"><span data-stu-id="a65a7-112">Function name</span></span>|<span data-ttu-id="a65a7-113">傳回資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-113">Return data type</span></span>|<span data-ttu-id="a65a7-114">範圍`expression`引數</span><span class="sxs-lookup"><span data-stu-id="a65a7-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="a65a7-115">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="a65a7-116">任何有效`Char`或`String`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="a65a7-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="a65a7-117">Byte 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="a65a7-118">0 到 255 之間 （不帶正負號）。會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a65a7-118">0 through 255 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CChar`|[<span data-ttu-id="a65a7-119">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-119">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="a65a7-120">任何有效`Char`或`String`運算式; 只有第一個字元的`String`轉換; 值可以是 0 到 65535 之間 （不帶正負號）。</span><span class="sxs-lookup"><span data-stu-id="a65a7-120">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="a65a7-121">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-121">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="a65a7-122">日期和時間的任何有效表示法。</span><span class="sxs-lookup"><span data-stu-id="a65a7-122">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="a65a7-123">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-123">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="a65a7-124">-1.79769313486231570 e + 308 到-4.94065645841246544 e-324 負數的值;4.94065645841246544 e-324 到 1.79769313486231570 e + 308 的正值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-124">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="a65a7-125">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-125">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="a65a7-126">+ /-零縮放的數字，也就是沒有小數點的數字 79228162514264337593543950335。</span><span class="sxs-lookup"><span data-stu-id="a65a7-126">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="a65a7-127">若是 28 位小數的數字，範圍是 + /--7.9228162514264337593543950335。</span><span class="sxs-lookup"><span data-stu-id="a65a7-127">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="a65a7-128">最小可能的非零值是 0.0000000000000000000000000001 （+ /-1E 28)。</span><span class="sxs-lookup"><span data-stu-id="a65a7-128">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="a65a7-129">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-129">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="a65a7-130">-2,147,483,648 到 2,147,483,647。會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a65a7-130">-2,147,483,648 through 2,147,483,647; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CLng`|[<span data-ttu-id="a65a7-131">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-131">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="a65a7-132">-9223372036854775808 到 9,223,372,036,854,775,807;會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a65a7-132">-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CObj`|[<span data-ttu-id="a65a7-133">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-133">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="a65a7-134">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="a65a7-134">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="a65a7-135">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-135">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="a65a7-136">-128 到 127。會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a65a7-136">-128 through 127; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CShort`|[<span data-ttu-id="a65a7-137">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-137">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="a65a7-138">-32,768 到 32,767。會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a65a7-138">-32,768 through 32,767; fractional parts are rounded.<sup>1</sup></span></span>|  
|`CSng`|[<span data-ttu-id="a65a7-139">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-139">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="a65a7-140">-3.402823 e + 38 到-1.401298-45 負數的值;1.401298-45 到 3.402823 e + 38 的正數值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-140">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="a65a7-141">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="a65a7-142">傳回`CStr`相依於`expression`引數。</span><span class="sxs-lookup"><span data-stu-id="a65a7-142">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="a65a7-143">請參閱[CStr 函式的傳回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。</span><span class="sxs-lookup"><span data-stu-id="a65a7-143">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="a65a7-144">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-144">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="a65a7-145">0 到 4294967295 （不帶正負號）。會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a65a7-145">0 through 4,294,967,295 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CULng`|[<span data-ttu-id="a65a7-146">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-146">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="a65a7-147">0 到 18446744073709551615 （不帶正負號）。會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a65a7-147">0 through 18,446,744,073,709,551,615 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
|`CUShort`|[<span data-ttu-id="a65a7-148">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="a65a7-148">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="a65a7-149">0 到 65535 （不帶正負號）。會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="a65a7-149">0 through 65,535 (unsigned); fractional parts are rounded.<sup>1</sup></span></span>|  
  
 <span data-ttu-id="a65a7-150"><sup>1</sup>小數部分可能會受到特殊類型的捨入呼叫影響*銀行進位*。</span><span class="sxs-lookup"><span data-stu-id="a65a7-150"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="a65a7-151">如需詳細資訊，請參閱 < 備註 >。</span><span class="sxs-lookup"><span data-stu-id="a65a7-151">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a65a7-152">備註</span><span class="sxs-lookup"><span data-stu-id="a65a7-152">Remarks</span></span>  
 <span data-ttu-id="a65a7-153">因此，您應該使用 Visual Basic 類型轉換函式，而非.NET Framework 方法例如`ToString()`，在上<xref:System.Convert>類別或個別的類型結構或類別。</span><span class="sxs-lookup"><span data-stu-id="a65a7-153">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="a65a7-154">Visual Basic 函式專為與 Visual Basic 程式碼，最佳的互動，而且它們也會使原始程式碼短也更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="a65a7-154">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="a65a7-155">此外，.NET Framework 轉換方法不一定會產生相同的結果做為 Visual Basic 函式，例如當轉換`Boolean`至`Integer`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-155">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="a65a7-156">如需詳細資訊，請參閱[疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a65a7-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="a65a7-157">行為</span><span class="sxs-lookup"><span data-stu-id="a65a7-157">Behavior</span></span>  
  
-   <span data-ttu-id="a65a7-158">**強制型轉。**</span><span class="sxs-lookup"><span data-stu-id="a65a7-158">**Coercion.**</span></span> <span data-ttu-id="a65a7-159">一般情況下，您可以使用資料類型轉換函式強制轉型為特定資料類型，而不是預設的資料型別作業的結果。</span><span class="sxs-lookup"><span data-stu-id="a65a7-159">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="a65a7-160">例如，使用`CDec`來強制執行在其中單精確度、 雙精確度或整數運算也通常不會發生的情況下的十進位運算。</span><span class="sxs-lookup"><span data-stu-id="a65a7-160">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   <span data-ttu-id="a65a7-161">**轉換失敗。**</span><span class="sxs-lookup"><span data-stu-id="a65a7-161">**Failed Conversions.**</span></span> <span data-ttu-id="a65a7-162">如果`expression`傳遞至函式超出範圍的資料類型會是轉換， <xref:System.OverflowException> ，就會發生。</span><span class="sxs-lookup"><span data-stu-id="a65a7-162">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   <span data-ttu-id="a65a7-163">**小數部分。**</span><span class="sxs-lookup"><span data-stu-id="a65a7-163">**Fractional Parts.**</span></span> <span data-ttu-id="a65a7-164">在您將非整數值轉換成整數類資料類型時，整數轉換函式 (`CByte`， `CInt`， `CLng`， `CSByte`， `CShort`， `CUInt`， `CULng`，和`CUShort`) 移除小數部分，四捨五入為最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-164">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="a65a7-165">如果小數部分正好 0.5，整數轉換函式捨入至最接近的偶數整數。</span><span class="sxs-lookup"><span data-stu-id="a65a7-165">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="a65a7-166">例如，0.5 捨入為 0，1.5 和 2.5 都會捨入為 2。</span><span class="sxs-lookup"><span data-stu-id="a65a7-166">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="a65a7-167">這有時候稱為*銀行進位*，和其目的是要彌補可能會不斷累積時將此類數字相加的偏差。</span><span class="sxs-lookup"><span data-stu-id="a65a7-167">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="a65a7-168">`CInt`和`CLng`不同<xref:Microsoft.VisualBasic.Conversion.Int%2A>和<xref:Microsoft.VisualBasic.Conversion.Fix%2A>函式，它們截斷，而不是圓形，數字的小數部分。</span><span class="sxs-lookup"><span data-stu-id="a65a7-168">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="a65a7-169">此外，`Fix`和`Int`一律傳回相同的資料類型的值，將傳入。</span><span class="sxs-lookup"><span data-stu-id="a65a7-169">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   <span data-ttu-id="a65a7-170">**日期/時間轉換。**</span><span class="sxs-lookup"><span data-stu-id="a65a7-170">**Date/Time Conversions.**</span></span> <span data-ttu-id="a65a7-171">使用<xref:Microsoft.VisualBasic.Information.IsDate%2A>函式來判斷值是否可以轉換成日期和時間。</span><span class="sxs-lookup"><span data-stu-id="a65a7-171">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="a65a7-172">`CDate`可辨識的日期常值和時間常值，但不是數值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-172">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="a65a7-173">要轉換的 Visual Basic 6.0`Date`值設定為`Date`在 Visual Basic 2005 中的值或更新版本，您可以使用<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="a65a7-173">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="a65a7-174">**中性日期/時間值。**</span><span class="sxs-lookup"><span data-stu-id="a65a7-174">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="a65a7-175">[日期資料型別](../../../visual-basic/language-reference/data-types/date-data-type.md)一定會包含日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="a65a7-175">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="a65a7-176">類型轉換的目的而言，Visual Basic 視為 1/1/0001 (1 年的 1 年)*中性值*日期，和 00:00:00 （午夜） 是中性值的時間。</span><span class="sxs-lookup"><span data-stu-id="a65a7-176">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="a65a7-177">如果您要轉換`Date`值到一個字串，`CStr`中產生的字串不包含中性的值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-177">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="a65a7-178">例如，如果您要轉換`#January 1, 0001 9:30:00#`為字串，結果會是 「 上午 9:30:00"; 隱藏日期資訊。</span><span class="sxs-lookup"><span data-stu-id="a65a7-178">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="a65a7-179">不過，將日期資訊是仍會出現在原始`Date`值，並可以復原與函式例如<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>函式。</span><span class="sxs-lookup"><span data-stu-id="a65a7-179">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   <span data-ttu-id="a65a7-180">**區分文化。**</span><span class="sxs-lookup"><span data-stu-id="a65a7-180">**Culture Sensitivity.**</span></span> <span data-ttu-id="a65a7-181">字串的相關的類型轉換函式會執行轉換取決於應用程式的目前文化特性設定。</span><span class="sxs-lookup"><span data-stu-id="a65a7-181">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="a65a7-182">例如，`CDate`可辨識的日期格式，根據您的系統地區設定。</span><span class="sxs-lookup"><span data-stu-id="a65a7-182">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="a65a7-183">您必須提供日、 月和年針對您的地區設定正確的順序，或可能不正確解譯日期。</span><span class="sxs-lookup"><span data-stu-id="a65a7-183">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="a65a7-184">如果它包含的週日期字串，例如 「 星期三 」 無法辨識的完整日期格式。</span><span class="sxs-lookup"><span data-stu-id="a65a7-184">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="a65a7-185">如果您需要轉換或從您的地區設定所指定以外的格式的值的字串表示，您無法使用 Visual Basic 的類型轉換函式。</span><span class="sxs-lookup"><span data-stu-id="a65a7-185">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="a65a7-186">若要這樣做，請使用`ToString(IFormatProvider)`和`Parse(String, IFormatProvider)`該實值類型的方法。</span><span class="sxs-lookup"><span data-stu-id="a65a7-186">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="a65a7-187">例如，使用<xref:System.Double.Parse%2A?displayProperty=nameWithType>字串轉換成`Double`，並使用<xref:System.Double.ToString%2A?displayProperty=nameWithType>轉換類型的值時`Double`為字串。</span><span class="sxs-lookup"><span data-stu-id="a65a7-187">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="a65a7-188">CType Function</span><span class="sxs-lookup"><span data-stu-id="a65a7-188">CType Function</span></span>  
 <span data-ttu-id="a65a7-189">[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)採用第二個引數， `typename`，並轉`expression`至`typename`，其中`typename`可以是任何資料類型、 結構、 類別或介面的有有效的轉換。</span><span class="sxs-lookup"><span data-stu-id="a65a7-189">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="a65a7-190">如需的比較`CType`與其他類型轉換關鍵字，請參閱[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)和[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="a65a7-190">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="a65a7-191">CBool 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-191">CBool Example</span></span>  
 <span data-ttu-id="a65a7-192">下列範例會使用`CBool`函式將轉換運算式到`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-192">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="a65a7-193">如果運算式評估為非零值，`CBool`傳回`True`; 否則它會傳回`False`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-193">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="a65a7-194">CByte 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-194">CByte Example</span></span>  
 <span data-ttu-id="a65a7-195">下列範例會使用`CByte`函式將轉換運算式，以便`Byte`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-195">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a><span data-ttu-id="a65a7-196">CChar 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-196">CChar Example</span></span>  
 <span data-ttu-id="a65a7-197">下列範例會使用`CChar`函式將轉換的第一個字元`String`運算式`Char`型別。</span><span class="sxs-lookup"><span data-stu-id="a65a7-197">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 <span data-ttu-id="a65a7-198">若要輸入的引數`CChar`的資料類型必須是`Char`或`String`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-198">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="a65a7-199">您無法使用`CChar`轉換成字元的數字，因為`CChar`無法接受的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="a65a7-199">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="a65a7-200">下列範例會取得代表的字碼指標 （字元碼） 的數字，並將它轉換成對應的字元。</span><span class="sxs-lookup"><span data-stu-id="a65a7-200">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="a65a7-201">它會使用<xref:Microsoft.VisualBasic.Interaction.InputBox%2A>函式可取得的數字、 字串`CInt`將輸入字串轉換`Integer`，和`ChrW`轉換要輸入的數字`Char`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-201">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a><span data-ttu-id="a65a7-202">CDate 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-202">CDate Example</span></span>  
 <span data-ttu-id="a65a7-203">下列範例會使用`CDate`函式可將字串轉換為`Date`值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-203">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="a65a7-204">一般情況下，不建議進行硬式編碼的日期和時間為字串 （如本範例所示）。</span><span class="sxs-lookup"><span data-stu-id="a65a7-204">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="a65a7-205">使用日期常值和時間常值，例如 #Feb 12，&#1969; 和 # 4:45:23 PM #，改為。</span><span class="sxs-lookup"><span data-stu-id="a65a7-205">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="a65a7-206">CDbl 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-206">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a><span data-ttu-id="a65a7-207">CDec 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-207">CDec Example</span></span>  
 <span data-ttu-id="a65a7-208">下列範例會使用`CDec`函式，將數字值轉換成`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-208">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a><span data-ttu-id="a65a7-209">CInt 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-209">CInt Example</span></span>  
 <span data-ttu-id="a65a7-210">下列範例會使用`CInt`函式，將值轉換成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-210">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a><span data-ttu-id="a65a7-211">CLng 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-211">CLng Example</span></span>  
 <span data-ttu-id="a65a7-212">下列範例會使用`CLng`函式，將值轉換為`Long`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-212">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a><span data-ttu-id="a65a7-213">CObj 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-213">CObj Example</span></span>  
 <span data-ttu-id="a65a7-214">下列範例會使用`CObj`函式，將數字值轉換成`Object`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-214">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="a65a7-215">`Object`變數本身僅包含四個位元組指標，指向`Double`指派給它的值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-215">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="a65a7-216">CSByte 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-216">CSByte Example</span></span>  
 <span data-ttu-id="a65a7-217">下列範例會使用`CSByte`函式，將數字值轉換成`SByte`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-217">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a><span data-ttu-id="a65a7-218">CShort 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-218">CShort Example</span></span>  
 <span data-ttu-id="a65a7-219">下列範例會使用`CShort`函式，將數字值轉換成`Short`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-219">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a><span data-ttu-id="a65a7-220">CSng 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-220">CSng Example</span></span>  
 <span data-ttu-id="a65a7-221">下列範例會使用`CSng`函式，將值轉換為`Single`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-221">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a><span data-ttu-id="a65a7-222">CStr 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-222">CStr Example</span></span>  
 <span data-ttu-id="a65a7-223">下列範例會使用`CStr`函式，將數字值轉換成`String`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-223">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 <span data-ttu-id="a65a7-224">下列範例會使用`CStr`函式將轉換`Date`值`String`值。</span><span class="sxs-lookup"><span data-stu-id="a65a7-224">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 <span data-ttu-id="a65a7-225">`CStr`一律會呈現`Date`目前地區設定，例如，標準的簡短格式的值"2003 年 6 月 15 日 4:35:47 PM"。</span><span class="sxs-lookup"><span data-stu-id="a65a7-225">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="a65a7-226">不過，`CStr`隱藏*中性值*的 1/1/0001 的日期和時間的 00:00:00。</span><span class="sxs-lookup"><span data-stu-id="a65a7-226">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="a65a7-227">如需詳細資訊，所傳回的值上`CStr`，請參閱[CStr 函式的傳回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。</span><span class="sxs-lookup"><span data-stu-id="a65a7-227">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="a65a7-228">CUInt 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-228">CUInt Example</span></span>  
 <span data-ttu-id="a65a7-229">下列範例會使用`CUInt`函式，將數字值轉換成`UInteger`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-229">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a><span data-ttu-id="a65a7-230">CULng 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-230">CULng Example</span></span>  
 <span data-ttu-id="a65a7-231">下列範例會使用`CULng`函式，將數字值轉換成`ULong`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-231">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a><span data-ttu-id="a65a7-232">CUShort 範例</span><span class="sxs-lookup"><span data-stu-id="a65a7-232">CUShort Example</span></span>  
 <span data-ttu-id="a65a7-233">下列範例會使用`CUShort`函式，將數字值轉換成`UShort`。</span><span class="sxs-lookup"><span data-stu-id="a65a7-233">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a65a7-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a65a7-234">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="a65a7-235">轉換函式</span><span class="sxs-lookup"><span data-stu-id="a65a7-235">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="a65a7-236">在 Visual Basic 中的型別轉換</span><span class="sxs-lookup"><span data-stu-id="a65a7-236">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
