---
title: 類型轉換函式 (Visual Basic)
ms.date: 10/24/2018
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
ms.openlocfilehash: 6b448fa23368f7a0848c44362337b0ccc70b6162
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592079"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="4e89b-102">類型轉換函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e89b-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="4e89b-103">這些函式是以內嵌方式編譯，這表示轉換程式碼是評估運算式之程式碼的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e89b-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="4e89b-104">有時候不會呼叫程式來完成轉換，這可改善效能。</span><span class="sxs-lookup"><span data-stu-id="4e89b-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="4e89b-105">每個函式會將運算式強制轉型為特定的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4e89b-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e89b-106">語法</span><span class="sxs-lookup"><span data-stu-id="4e89b-106">Syntax</span></span>  
  
```vb  
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
  
## <a name="part"></a><span data-ttu-id="4e89b-107">組件</span><span class="sxs-lookup"><span data-stu-id="4e89b-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="4e89b-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="4e89b-108">Required.</span></span> <span data-ttu-id="4e89b-109">源資料類型的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="4e89b-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="4e89b-110">傳回值資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-110">Return Value Data Type</span></span>  
 <span data-ttu-id="4e89b-111">函式名稱會決定所傳回之值的資料類型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="4e89b-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="4e89b-112">函式名稱</span><span class="sxs-lookup"><span data-stu-id="4e89b-112">Function name</span></span>|<span data-ttu-id="4e89b-113">傳回資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-113">Return data type</span></span>|<span data-ttu-id="4e89b-114">@No__t-0 引數的範圍</span><span class="sxs-lookup"><span data-stu-id="4e89b-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="4e89b-115">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="4e89b-116">任何有效的 `Char` 或 @no__t 1 或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="4e89b-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="4e89b-117">Byte 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="4e89b-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> （0）到 <xref:System.Byte.MaxValue?displayProperty=nameWithType> （255）（不帶正負號）;小數部分會四捨五入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4e89b-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="4e89b-119">從 Visual Basic 15.8 開始，Visual Basic 使用 `CByte` 函式，將浮點到位元組轉換的效能優化。如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="4e89b-120">如需範例，請參閱[CInt 範例](#cint-example)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-120">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CChar`|[<span data-ttu-id="4e89b-121">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="4e89b-122">任何有效的 `Char` 或 `String` 運算式;只會轉換 `String` 的第一個字元;值可以是0到65535（不帶正負號）。</span><span class="sxs-lookup"><span data-stu-id="4e89b-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="4e89b-123">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="4e89b-124">日期和時間的任何有效表示。</span><span class="sxs-lookup"><span data-stu-id="4e89b-124">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="4e89b-125">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="4e89b-126">-1.79769313486231570 e + 308 到-4.94065645841246544 E-324 表示負值;4.94065645841246544 e-324 到 1.79769313486231570 E + 308 （適用于正值）。</span><span class="sxs-lookup"><span data-stu-id="4e89b-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="4e89b-127">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="4e89b-128">+/-79228162514264337593543950335 零縮放數位，也就是沒有小數的數位。</span><span class="sxs-lookup"><span data-stu-id="4e89b-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="4e89b-129">若為具有28位小數位數的數值，範圍為 +/-7.9228162514264337593543950335。</span><span class="sxs-lookup"><span data-stu-id="4e89b-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="4e89b-130">最小的可能非零數位為0.0000000000000000000000000001 （+/-1E-28）。</span><span class="sxs-lookup"><span data-stu-id="4e89b-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="4e89b-131">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="4e89b-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> （-2147483648）到 <xref:System.Int32.MaxValue?displayProperty=nameWithType> （2147483647）;小數部分會四捨五入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4e89b-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="4e89b-133">從 Visual Basic 15.8 開始，Visual Basic 使用 `CInt` 函式，將浮點到整數轉換的效能優化。如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="4e89b-134">如需範例，請參閱[CInt 範例](#cint-example)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-134">See the [CInt Example](#cint-example) section for an example.</span></span> |  
|`CLng`|[<span data-ttu-id="4e89b-135">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="4e89b-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> （-9223372036854775808）到 <xref:System.Int64.MaxValue?displayProperty=nameWithType> （9223372036854775807）;小數部分會四捨五入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4e89b-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="4e89b-137">從 Visual Basic 15.8 開始，Visual Basic 使用 `CLng` 函式，將浮點到64位整數轉換的效能優化。如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="4e89b-138">如需範例，請參閱[CInt 範例](#cint-example)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-138">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CObj`|[<span data-ttu-id="4e89b-139">Object 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="4e89b-140">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="4e89b-140">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="4e89b-141">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="4e89b-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> （-128）到 <xref:System.SByte.MaxValue?displayProperty=nameWithType> （127）;小數部分會四捨五入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4e89b-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="4e89b-143">從 Visual Basic 15.8 開始，Visual Basic 使用 `CSByte` 函式，將浮點到帶正負號位元組轉換的效能優化。如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="4e89b-144">如需範例，請參閱[CInt 範例](#cint-example)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-144">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CShort`|[<span data-ttu-id="4e89b-145">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="4e89b-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> （-32768）到 <xref:System.Int16.MaxValue?displayProperty=nameWithType> （32767）;小數部分會四捨五入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4e89b-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="4e89b-147">從 Visual Basic 15.8 開始，Visual Basic 使用 `CShort` 函式，將浮點到16位整數轉換的效能優化。如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="4e89b-148">如需範例，請參閱[CInt 範例](#cint-example)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-148">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CSng`|[<span data-ttu-id="4e89b-149">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="4e89b-150">-3.402823 e + 38 到-1.401298 E-45 表示負值;1.401298 e-45 到 3.402823 E + 38 （適用于正值）。</span><span class="sxs-lookup"><span data-stu-id="4e89b-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="4e89b-151">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="4e89b-152">@No__t-0 的傳回取決於 `expression` 引數。</span><span class="sxs-lookup"><span data-stu-id="4e89b-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="4e89b-153">請參閱[CStr 函數](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="4e89b-154">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="4e89b-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> （0）到 <xref:System.UInt32.MaxValue?displayProperty=nameWithType> （4294967295）（不帶正負號）;小數部分會四捨五入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4e89b-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="4e89b-156">從 Visual Basic 15.8 開始，Visual Basic 使用 `CUInt` 函式，將浮點到不帶正負號整數轉換的效能優化。如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="4e89b-157">如需範例，請參閱[CInt 範例](#cint-example)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-157">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CULng`|[<span data-ttu-id="4e89b-158">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="4e89b-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> （0）到 <xref:System.UInt64.MaxValue?displayProperty=nameWithType> （18446744073709551615）（不帶正負號）;小數部分會四捨五入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4e89b-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="4e89b-160">從 Visual Basic 15.8 開始，Visual Basic 使用 `CULng` 函式，將浮點到不帶正負號長整數轉換的效能優化。如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="4e89b-161">如需範例，請參閱[CInt 範例](#cint-example)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-161">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CUShort`|[<span data-ttu-id="4e89b-162">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="4e89b-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="4e89b-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> （0）到 <xref:System.UInt16.MaxValue?displayProperty=nameWithType> （65535）（不帶正負號）;小數部分會四捨五入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="4e89b-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="4e89b-164">從 Visual Basic 15.8 開始，Visual Basic 使用 `CUShort` 函式，將浮點到不帶正負號16位整數轉換的效能優化。如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="4e89b-165">如需範例，請參閱[CInt 範例](#cint-example)一節。</span><span class="sxs-lookup"><span data-stu-id="4e89b-165">See the [CInt Example](#cint-example) section for an example.</span></span>|  
  
 <span data-ttu-id="4e89b-166"><sup>1</sup>小數部分可能會受到一種特殊的舍入類型，稱為「四*進位*」。</span><span class="sxs-lookup"><span data-stu-id="4e89b-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="4e89b-167">如需詳細資訊，請參閱「備註」。</span><span class="sxs-lookup"><span data-stu-id="4e89b-167">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e89b-168">備註</span><span class="sxs-lookup"><span data-stu-id="4e89b-168">Remarks</span></span>  
 <span data-ttu-id="4e89b-169">作為規則，您應該在 @no__t 1 類別或個別類型結構或類別上，對 .NET Framework 方法（例如 `ToString()`）使用 Visual Basic 類型轉換函式。</span><span class="sxs-lookup"><span data-stu-id="4e89b-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="4e89b-170">Visual Basic 函式是針對與 Visual Basic 程式碼的最佳互動所設計，而且也讓您的原始程式碼更短且更容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="4e89b-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="4e89b-171">此外，.NET Framework 轉換方法不一定會產生與 Visual Basic 函數相同的結果，例如，將 `Boolean` 轉換成 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="4e89b-172">如需詳細資訊，請參閱針對[資料類型進行疑難排解](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4e89b-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  

<span data-ttu-id="4e89b-173">從 Visual Basic 15.8 開始，當您將下列方法傳回的 <xref:System.Single> 或 <xref:System.Double> 值傳遞給其中一個整數轉換函式（`CByte`、`CShort`、`CInt`、@no__ 時，就會將浮點對整數轉換的效能優化。t-5、`CSByte`、`CUShort`、`CUInt`、`CULng`）：</span><span class="sxs-lookup"><span data-stu-id="4e89b-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="4e89b-174">這項優化可讓執行大量整數轉換的程式碼，執行速度最多兩次。</span><span class="sxs-lookup"><span data-stu-id="4e89b-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="4e89b-175">下列範例說明這些優化的浮點對整數轉換：</span><span class="sxs-lookup"><span data-stu-id="4e89b-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="4e89b-176">行為</span><span class="sxs-lookup"><span data-stu-id="4e89b-176">Behavior</span></span>  
  
- <span data-ttu-id="4e89b-177">**強制.**</span><span class="sxs-lookup"><span data-stu-id="4e89b-177">**Coercion.**</span></span> <span data-ttu-id="4e89b-178">一般來說，您可以使用資料類型轉換函數，將作業的結果強制轉型為特定的資料類型，而不是預設的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4e89b-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="4e89b-179">例如，在通常會發生單精確度、雙精確度或整數算術的情況下，請使用 `CDec` 來強制執行十進位運算。</span><span class="sxs-lookup"><span data-stu-id="4e89b-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
- <span data-ttu-id="4e89b-180">**轉換失敗。**</span><span class="sxs-lookup"><span data-stu-id="4e89b-180">**Failed Conversions.**</span></span> <span data-ttu-id="4e89b-181">如果傳遞至函式的 `expression` 超出要轉換的目標資料類型範圍，就會發生 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="4e89b-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
- <span data-ttu-id="4e89b-182">**小數部分。**</span><span class="sxs-lookup"><span data-stu-id="4e89b-182">**Fractional Parts.**</span></span> <span data-ttu-id="4e89b-183">當您將非整數值轉換成整數類資料類型時，integer 轉換函式（`CByte`、`CInt`、`CLng`、`CSByte`、`CShort`、`CUInt`、`CULng` 和 `CUShort`）會移除小數部分，並將值四捨五入為最接近的整數。</span><span class="sxs-lookup"><span data-stu-id="4e89b-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="4e89b-184">如果小數部分正好為0.5，則整數轉換函式會將它舍入至最接近的偶數整數。</span><span class="sxs-lookup"><span data-stu-id="4e89b-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="4e89b-185">例如，0.5 會四捨五入為0，而1.5 和2.5 都會舍入為2。</span><span class="sxs-lookup"><span data-stu-id="4e89b-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="4e89b-186">這有時稱為「四*進位*」（），其目的是要彌補同時新增許多這類數位時可能累積的偏差。</span><span class="sxs-lookup"><span data-stu-id="4e89b-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     <span data-ttu-id="4e89b-187">`CInt` 和 `CLng` 與 <xref:Microsoft.VisualBasic.Conversion.Int%2A> 和 <xref:Microsoft.VisualBasic.Conversion.Fix%2A> 函式不同，而這兩個函式會截斷，而不是舍入數位的小數部分。</span><span class="sxs-lookup"><span data-stu-id="4e89b-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="4e89b-188">此外，`Fix` 和 `Int` 一律會傳回與您傳入時相同資料類型的值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
- <span data-ttu-id="4e89b-189">**日期/時間轉換。**</span><span class="sxs-lookup"><span data-stu-id="4e89b-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="4e89b-190">使用 <xref:Microsoft.VisualBasic.Information.IsDate%2A> 函數來判斷值是否可以轉換成日期和時間。</span><span class="sxs-lookup"><span data-stu-id="4e89b-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="4e89b-191">`CDate` 可識別日期常值和時間常值，但不能辨識數值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="4e89b-192">若要將 Visual Basic 6.0 `Date` 值轉換為 Visual Basic 2005 或更新版本中的 @no__t 1 值，您可以使用 <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4e89b-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="4e89b-193">**中性日期/時間值。**</span><span class="sxs-lookup"><span data-stu-id="4e89b-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="4e89b-194">[Date 資料類型](../../../visual-basic/language-reference/data-types/date-data-type.md)一律會同時包含日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="4e89b-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="4e89b-195">基於類型轉換的目的，Visual Basic 會將1/1/0001 （第1年1月1日）視為日期的*中性值*，而00:00:00 （午夜）則是時間的中性值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="4e89b-196">如果您將 `Date` 值轉換成字串，`CStr` 不會在產生的字串中包含中性值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="4e89b-197">例如，如果您將 `#January 1, 0001 9:30:00#` 轉換成字串，則結果會是 "9:30:00 AM";會隱藏日期資訊。</span><span class="sxs-lookup"><span data-stu-id="4e89b-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="4e89b-198">不過，日期資訊仍然會出現在原始的 @no__t 0 值中，而且可以使用 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> 函式之類的函數來復原。</span><span class="sxs-lookup"><span data-stu-id="4e89b-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
- <span data-ttu-id="4e89b-199">**區分文化特性。**</span><span class="sxs-lookup"><span data-stu-id="4e89b-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="4e89b-200">涉及字串的類型轉換函式會根據應用程式目前的文化特性設定來執行轉換。</span><span class="sxs-lookup"><span data-stu-id="4e89b-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="4e89b-201">例如，`CDate` 會根據您系統的地區設定來辨識日期格式。</span><span class="sxs-lookup"><span data-stu-id="4e89b-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="4e89b-202">您必須以正確的地區設定順序來提供日期、月和年，否則可能無法正確地解讀日期。</span><span class="sxs-lookup"><span data-stu-id="4e89b-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="4e89b-203">如果包含一周中的字串，例如「星期三」，就無法辨識完整的日期格式。</span><span class="sxs-lookup"><span data-stu-id="4e89b-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="4e89b-204">如果您需要以不是由地區設定所指定的格式，從值的字串表示轉換為或，則不能使用 Visual Basic 類型轉換函式。</span><span class="sxs-lookup"><span data-stu-id="4e89b-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="4e89b-205">若要這麼做，請使用該數值型別的 `ToString(IFormatProvider)` 和 `Parse(String, IFormatProvider)` 方法。</span><span class="sxs-lookup"><span data-stu-id="4e89b-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="4e89b-206">例如，將字串轉換成 `Double` 時，請使用 <xref:System.Double.Parse%2A?displayProperty=nameWithType>，並在將類型的值 `Double` 轉換成字串時，使用 <xref:System.Double.ToString%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="4e89b-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="4e89b-207">CType Function</span><span class="sxs-lookup"><span data-stu-id="4e89b-207">CType Function</span></span>  
 <span data-ttu-id="4e89b-208">[CType 函數](../../../visual-basic/language-reference/functions/ctype-function.md)會接受第二個引數，`typename`，並將 `expression` 強制轉型為 `typename`，其中 `typename` 可以是存在有效轉換的任何資料類型、結構、類別或介面。</span><span class="sxs-lookup"><span data-stu-id="4e89b-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="4e89b-209">如需 `CType` 與其他類型轉換關鍵字的比較，請參閱[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)和[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="4e89b-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="4e89b-210">CBool 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-210">CBool Example</span></span>  
 <span data-ttu-id="4e89b-211">下列範例會使用 `CBool` 函式，將運算式轉換成 @no__t 1 的值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="4e89b-212">如果運算式評估為非零值，`CBool` 會傳回 `True`;否則，它會傳回 `False`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="4e89b-213">CByte 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-213">CByte Example</span></span>  
 <span data-ttu-id="4e89b-214">下列範例會使用 `CByte` 函式將運算式轉換成 `Byte`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a><span data-ttu-id="4e89b-215">CChar 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-215">CChar Example</span></span>  
 <span data-ttu-id="4e89b-216">下列範例會使用 `CChar` 函式，將 `String` 運算式的第一個字元轉換成 @no__t 2 類型。</span><span class="sxs-lookup"><span data-stu-id="4e89b-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 <span data-ttu-id="4e89b-217">@No__t-0 的輸入引數必須是 `Char` 或 `String` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="4e89b-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="4e89b-218">您無法使用 `CChar` 將數位轉換成字元，因為 `CChar` 無法接受數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="4e89b-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="4e89b-219">下列範例會取得代表程式碼點（字元碼）的數位，並將它轉換成對應的字元。</span><span class="sxs-lookup"><span data-stu-id="4e89b-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="4e89b-220">它會使用 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> 函式來取得數位的字串，`CInt` 將字串轉換成類型 `Integer`，並 `ChrW` 將數位轉換成類型 `Char`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a><span data-ttu-id="4e89b-221">CDate 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-221">CDate Example</span></span>  
 <span data-ttu-id="4e89b-222">下列範例會使用 `CDate` 函式將字串轉換成 `Date` 值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="4e89b-223">一般而言，不建議將日期和時間硬式編碼為字串（如本範例所示）。</span><span class="sxs-lookup"><span data-stu-id="4e89b-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="4e89b-224">請改用日期常值和時間常值，例如 #Feb 12、1969 # 和 #4： 45:23 PM #。</span><span class="sxs-lookup"><span data-stu-id="4e89b-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="4e89b-225">CDbl 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-225">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a><span data-ttu-id="4e89b-226">CDec 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-226">CDec Example</span></span>  
 <span data-ttu-id="4e89b-227">下列範例會使用 `CDec` 函數將數值轉換成 `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a><span data-ttu-id="4e89b-228">CInt 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-228">CInt Example</span></span>  
 <span data-ttu-id="4e89b-229">下列範例會使用 `CInt` 函式，將值轉換成 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a><span data-ttu-id="4e89b-230">CLng 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-230">CLng Example</span></span>
 <span data-ttu-id="4e89b-231">下列範例會使用 `CLng` 函式將值轉換為 `Long`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a><span data-ttu-id="4e89b-232">CObj 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-232">CObj Example</span></span>  
 <span data-ttu-id="4e89b-233">下列範例會使用 `CObj` 函數將數值轉換成 `Object`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="4e89b-234">@No__t-0 變數本身只包含四個位元組的指標，指向指派給它的 `Double` 值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="4e89b-235">CSByte 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-235">CSByte Example</span></span>  
 <span data-ttu-id="4e89b-236">下列範例會使用 `CSByte` 函數將數值轉換成 `SByte`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a><span data-ttu-id="4e89b-237">CShort 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-237">CShort Example</span></span>  
 <span data-ttu-id="4e89b-238">下列範例會使用 `CShort` 函數將數值轉換成 `Short`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a><span data-ttu-id="4e89b-239">CSng 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-239">CSng Example</span></span>  
 <span data-ttu-id="4e89b-240">下列範例會使用 `CSng` 函式將值轉換為 `Single`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a><span data-ttu-id="4e89b-241">CStr 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-241">CStr Example</span></span>  
 <span data-ttu-id="4e89b-242">下列範例會使用 `CStr` 函數將數值轉換成 `String`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 <span data-ttu-id="4e89b-243">下列範例會使用 `CStr` 函式，將 `Date` 值轉換成 @no__t 2 值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="4e89b-244">`CStr` 一律會以標準簡短格式呈現目前地區設定的 `Date` 值，例如 "6/15/2003 4:35:47 PM"。</span><span class="sxs-lookup"><span data-stu-id="4e89b-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="4e89b-245">不過，`CStr` 會針對日期和00:00:00 隱藏時間的*中性值*1/1/0001。</span><span class="sxs-lookup"><span data-stu-id="4e89b-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="4e89b-246">如需 `CStr` 所傳回之值的詳細資訊，請參閱[CStr 函數](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)的傳回值。</span><span class="sxs-lookup"><span data-stu-id="4e89b-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="4e89b-247">CUInt 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-247">CUInt Example</span></span>  
 <span data-ttu-id="4e89b-248">下列範例會使用 `CUInt` 函數將數值轉換成 `UInteger`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a><span data-ttu-id="4e89b-249">CULng 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-249">CULng Example</span></span>  
 <span data-ttu-id="4e89b-250">下列範例會使用 `CULng` 函數將數值轉換成 `ULong`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a><span data-ttu-id="4e89b-251">CUShort 範例</span><span class="sxs-lookup"><span data-stu-id="4e89b-251">CUShort Example</span></span>  
 <span data-ttu-id="4e89b-252">下列範例會使用 `CUShort` 函數將數值轉換成 `UShort`。</span><span class="sxs-lookup"><span data-stu-id="4e89b-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="4e89b-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e89b-253">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="4e89b-254">轉換函式</span><span class="sxs-lookup"><span data-stu-id="4e89b-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="4e89b-255">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="4e89b-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
