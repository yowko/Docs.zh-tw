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
ms.openlocfilehash: 56dad921b2900061dbe2db0d8f1faaf759641f87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148131"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="e806f-102">類型轉換函式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e806f-102">Type Conversion Functions (Visual Basic)</span></span>
<span data-ttu-id="e806f-103">這些函式是編譯的內嵌，這表示，轉換程式碼評估運算式的程式碼的一部分。</span><span class="sxs-lookup"><span data-stu-id="e806f-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="e806f-104">有時是沒有呼叫程序來完成轉換，進而改善效能。</span><span class="sxs-lookup"><span data-stu-id="e806f-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="e806f-105">每個函式強制轉型為特定的資料類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="e806f-105">Each function coerces an expression to a specific data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e806f-106">語法</span><span class="sxs-lookup"><span data-stu-id="e806f-106">Syntax</span></span>  
  
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
  
## <a name="part"></a><span data-ttu-id="e806f-107">組件</span><span class="sxs-lookup"><span data-stu-id="e806f-107">Part</span></span>  
 `expression`  
 <span data-ttu-id="e806f-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="e806f-108">Required.</span></span> <span data-ttu-id="e806f-109">來源資料型別的任何運算式。</span><span class="sxs-lookup"><span data-stu-id="e806f-109">Any expression of the source data type.</span></span>  
  
## <a name="return-value-data-type"></a><span data-ttu-id="e806f-110">傳回值的資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-110">Return Value Data Type</span></span>  
 <span data-ttu-id="e806f-111">下表所示，函式名稱會決定它所傳回的值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e806f-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>  
  
|<span data-ttu-id="e806f-112">函式名稱</span><span class="sxs-lookup"><span data-stu-id="e806f-112">Function name</span></span>|<span data-ttu-id="e806f-113">傳回資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-113">Return data type</span></span>|<span data-ttu-id="e806f-114">範圍`expression`引數</span><span class="sxs-lookup"><span data-stu-id="e806f-114">Range for `expression` argument</span></span>|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[<span data-ttu-id="e806f-115">Boolean 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-115">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="e806f-116">任何有效`Char`或`String`或數值運算式。</span><span class="sxs-lookup"><span data-stu-id="e806f-116">Any valid `Char` or `String` or numeric expression.</span></span>|  
|`CByte`|[<span data-ttu-id="e806f-117">Byte 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-117">Byte Data Type</span></span>](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> <span data-ttu-id="e806f-118">(0) 透過<xref:System.Byte.MaxValue?displayProperty=nameWithType>(255) （不帶正負號），會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e806f-118">(0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e806f-119">從 Visual Basic 15.8 開始，Visual Basic 最佳化的效能與位元組轉換成浮點數`CByte`函式; 請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e806f-120">請參閱[CInt 範例](#cint-example)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="e806f-120">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CChar`|[<span data-ttu-id="e806f-121">Char 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-121">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="e806f-122">任何有效`Char`或是`String`運算式; 只有第一個字元`String`轉換; 值可以是 0 到 65535 （不帶正負號）。</span><span class="sxs-lookup"><span data-stu-id="e806f-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|  
|`CDate`|[<span data-ttu-id="e806f-123">Date 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-123">Date Data Type</span></span>](../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="e806f-124">日期和時間的任何有效表示法。</span><span class="sxs-lookup"><span data-stu-id="e806f-124">Any valid representation of a date and time.</span></span>|  
|`CDbl`|[<span data-ttu-id="e806f-125">Double 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-125">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="e806f-126">-1.79769313486231570 e + 308 到-4.94065645841246544-324 (負值）4.94065645841246544-324 到 1.79769313486231570 e + 308 的正值。</span><span class="sxs-lookup"><span data-stu-id="e806f-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|  
|`CDec`|[<span data-ttu-id="e806f-127">Decimal 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-127">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="e806f-128">+ /-零擴充的數字，也就是任何小數位數的數字 79228162514264337593543950335。</span><span class="sxs-lookup"><span data-stu-id="e806f-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="e806f-129">如 28 位小數的數字，範圍是 + /--7.9228162514264337593543950335。</span><span class="sxs-lookup"><span data-stu-id="e806f-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="e806f-130">最小可能的非零值是 0.0000000000000000000000000001 （+ /-1E-28)。</span><span class="sxs-lookup"><span data-stu-id="e806f-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|  
|`CInt`|[<span data-ttu-id="e806f-131">Integer 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> <span data-ttu-id="e806f-132">(-2,147,483,648) 到<xref:System.Int32.MaxValue?displayProperty=nameWithType>(2147483647)，會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e806f-132">(-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="e806f-133">從 Visual Basic 15.8 開始，Visual Basic 最佳化與整數轉換成浮點數的效能`CInt`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e806f-134">請參閱[CInt 範例](#cint-example)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="e806f-134">See the [CInt Example](#cint-example) section for an example.</span></span> |  
|`CLng`|[<span data-ttu-id="e806f-135">Long 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-135">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> <span data-ttu-id="e806f-136">(-9223372036854775808) 到<xref:System.Int64.MaxValue?displayProperty=nameWithType>(9223372036854775807)，會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e806f-136">(-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e806f-137">從 Visual Basic 15.8 開始，Visual Basic 將效能最佳化浮點，以使用 64 位元的整數轉換`CLng`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e806f-138">請參閱[CInt 範例](#cint-example)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="e806f-138">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CObj`|[<span data-ttu-id="e806f-139">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="e806f-139">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="e806f-140">任何有效的運算式。</span><span class="sxs-lookup"><span data-stu-id="e806f-140">Any valid expression.</span></span>|  
|`CSByte`|[<span data-ttu-id="e806f-141">SByte 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-141">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> <span data-ttu-id="e806f-142">(-128) 透過<xref:System.SByte.MaxValue?displayProperty=nameWithType>(127)，會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e806f-142">(-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e806f-143">從 Visual Basic 15.8 開始，Visual Basic 最佳化的效能與帶正負號的位元組轉換成浮點數`CSByte`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e806f-144">請參閱[CInt 範例](#cint-example)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="e806f-144">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CShort`|[<span data-ttu-id="e806f-145">Short 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-145">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> <span data-ttu-id="e806f-146">(-32,768) 到<xref:System.Int16.MaxValue?displayProperty=nameWithType>(32,767)，會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e806f-146">(-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e806f-147">從 Visual Basic 15.8 開始，Visual Basic 最佳化的效能與 16 位元的整數轉換成浮點數`CShort`函式; 請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e806f-148">請參閱[CInt 範例](#cint-example)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="e806f-148">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CSng`|[<span data-ttu-id="e806f-149">Single 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-149">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="e806f-150">-3.402823 e + 38 到-1.401298E-45 (負值）從 1.401298E-45 到 3.402823 e + 38 的正數值。</span><span class="sxs-lookup"><span data-stu-id="e806f-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|  
|`CStr`|[<span data-ttu-id="e806f-151">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-151">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="e806f-152">會傳回`CStr`取決於`expression`引數。</span><span class="sxs-lookup"><span data-stu-id="e806f-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="e806f-153">請參閱[CStr 函式的傳回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。</span><span class="sxs-lookup"><span data-stu-id="e806f-153">See [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>|  
|`CUInt`|[<span data-ttu-id="e806f-154">UInteger 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-154">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> <span data-ttu-id="e806f-155">(0) 透過<xref:System.UInt32.MaxValue?displayProperty=nameWithType>(4,294,967,295) （不帶正負號），會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e806f-155">(0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e806f-156">從 Visual Basic 15.8 開始，Visual Basic 將效能最佳化的與不帶正負號的整數轉換成浮點數`CUInt`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e806f-157">請參閱[CInt 範例](#cint-example)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="e806f-157">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CULng`|[<span data-ttu-id="e806f-158">ULong 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-158">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> <span data-ttu-id="e806f-159">(0) 透過<xref:System.UInt64.MaxValue?displayProperty=nameWithType>(18446744073709551615) （不帶正負號），會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e806f-159">(0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e806f-160">從 Visual Basic 15.8 開始，Visual Basic 將效能最佳化的與不帶正負號的長整數轉換成浮點數`CULng`函式; 請參閱 <<c2> [ 備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e806f-161">請參閱[CInt 範例](#cint-example)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="e806f-161">See the [CInt Example](#cint-example) section for an example.</span></span>|  
|`CUShort`|[<span data-ttu-id="e806f-162">UShort 資料類型</span><span class="sxs-lookup"><span data-stu-id="e806f-162">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> <span data-ttu-id="e806f-163">(0) 透過<xref:System.UInt16.MaxValue?displayProperty=nameWithType>(65,535) （不帶正負號），會捨去小數部分。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="e806f-163">(0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="e806f-164">從 Visual Basic 15.8 開始，Visual Basic 將效能最佳化的與不帶正負號的 16 位元整數轉換成浮點數`CUShort`函式; 請參閱[備註](#remarks)節的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="e806f-165">請參閱[CInt 範例](#cint-example)一節中的範例。</span><span class="sxs-lookup"><span data-stu-id="e806f-165">See the [CInt Example](#cint-example) section for an example.</span></span>|  
  
 <span data-ttu-id="e806f-166"><sup>1</sup>小數部分可能會受到特殊類型的捨入呼叫影響*銀行進位*。</span><span class="sxs-lookup"><span data-stu-id="e806f-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="e806f-167">如需詳細資訊，請參閱 < 備註 >。</span><span class="sxs-lookup"><span data-stu-id="e806f-167">See "Remarks" for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e806f-168">備註</span><span class="sxs-lookup"><span data-stu-id="e806f-168">Remarks</span></span>  
 <span data-ttu-id="e806f-169">因此，您應該使用 Visual Basic 型別轉換函式，而非.NET Framework 方法，例如`ToString()`，在<xref:System.Convert>類別或個別類型結構或類別。</span><span class="sxs-lookup"><span data-stu-id="e806f-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="e806f-170">Visual Basic 函式專為 Visual Basic 程式碼，最佳的互動，它們也可讓您的程式碼更簡短、 更方便閱讀。</span><span class="sxs-lookup"><span data-stu-id="e806f-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="e806f-171">此外，.NET Framework 轉換方法不一定會產生與 Visual Basic 函式，例如，轉換時相同的結果`Boolean`至`Integer`。</span><span class="sxs-lookup"><span data-stu-id="e806f-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="e806f-172">如需詳細資訊，請參閱 <<c0> [ 疑難排解資料型別](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e806f-172">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  

<span data-ttu-id="e806f-173">從 Visual Basic 15.8，浮點-點對點-整數的轉換的效能最佳化傳遞時<xref:System.Single>或是<xref:System.Double>遵循以下方法傳回整數的轉換函式的其中一個值 (`CByte`， `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span><span class="sxs-lookup"><span data-stu-id="e806f-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

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

<span data-ttu-id="e806f-174">此最佳化可讓執行整數轉換為以兩倍速度執行的一大堆程式碼。</span><span class="sxs-lookup"><span data-stu-id="e806f-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="e806f-175">下列範例會說明這些最佳化浮點-點對點對整數的轉換：</span><span class="sxs-lookup"><span data-stu-id="e806f-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="e806f-176">行為</span><span class="sxs-lookup"><span data-stu-id="e806f-176">Behavior</span></span>  
  
-   **<span data-ttu-id="e806f-177">強制型轉。</span><span class="sxs-lookup"><span data-stu-id="e806f-177">Coercion.</span></span>** <span data-ttu-id="e806f-178">一般情況下，您可以使用資料類型轉換函式，以強制轉型作業特定的資料類型，而不是預設的資料類型的結果。</span><span class="sxs-lookup"><span data-stu-id="e806f-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="e806f-179">例如，使用`CDec`來強制執行在其中單精確度、 雙精確度或整數算術會通常會發生的情況下的十進位運算。</span><span class="sxs-lookup"><span data-stu-id="e806f-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>  
  
-   **<span data-ttu-id="e806f-180">轉換失敗。</span><span class="sxs-lookup"><span data-stu-id="e806f-180">Failed Conversions.</span></span>** <span data-ttu-id="e806f-181">如果`expression`傳遞至函式超出範圍的資料型別，它就是轉換， <xref:System.OverflowException> ，就會發生。</span><span class="sxs-lookup"><span data-stu-id="e806f-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>  
  
-   **<span data-ttu-id="e806f-182">小數部分。</span><span class="sxs-lookup"><span data-stu-id="e806f-182">Fractional Parts.</span></span>** <span data-ttu-id="e806f-183">當您將非整數值轉換成整數類型，整數的轉換函式 (`CByte`， `CInt`， `CLng`， `CSByte`， `CShort`， `CUInt`， `CULng`，以及`CUShort`) 移除小數部分，並捨入為最接近的整數值。</span><span class="sxs-lookup"><span data-stu-id="e806f-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>  
  
     <span data-ttu-id="e806f-184">如果小數部分正好 0.5，整數的轉換函式將它四捨五入到最接近的偶數整數。</span><span class="sxs-lookup"><span data-stu-id="e806f-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="e806f-185">比方說，0.5 捨入為 0，1.5 和 2.5 都會捨入為 2。</span><span class="sxs-lookup"><span data-stu-id="e806f-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="e806f-186">這有時候稱為*銀行進位*，其用途是為了彌補可能會不斷累積時將許多這類的數字相加的偏差。</span><span class="sxs-lookup"><span data-stu-id="e806f-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>  
  
     `CInt` <span data-ttu-id="e806f-187">並`CLng`有所不同<xref:Microsoft.VisualBasic.Conversion.Int%2A>和<xref:Microsoft.VisualBasic.Conversion.Fix%2A>函式，其截斷，而不是四捨五入，數字的小數部分。</span><span class="sxs-lookup"><span data-stu-id="e806f-187">and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="e806f-188">此外，`Fix`和`Int`一律傳回相同的資料類型的值，因為您傳入。</span><span class="sxs-lookup"><span data-stu-id="e806f-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>  
  
-   **<span data-ttu-id="e806f-189">日期/時間轉換。</span><span class="sxs-lookup"><span data-stu-id="e806f-189">Date/Time Conversions.</span></span>** <span data-ttu-id="e806f-190">使用<xref:Microsoft.VisualBasic.Information.IsDate%2A>函式來判斷值是否可轉換成日期和時間。</span><span class="sxs-lookup"><span data-stu-id="e806f-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> `CDate` <span data-ttu-id="e806f-191">可辨識的日期常值和時間常值，但不是數值。</span><span class="sxs-lookup"><span data-stu-id="e806f-191">recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="e806f-192">若要轉換 Visual Basic 6.0`Date`值加入`Date`Visual Basic 2005 中的值或更新版本，您可以使用<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="e806f-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>  
  
-   **<span data-ttu-id="e806f-193">中性日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="e806f-193">Neutral Date/Time Values.</span></span>** <span data-ttu-id="e806f-194">[日期資料型別](../../../visual-basic/language-reference/data-types/date-data-type.md)一定會包含日期和時間資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-194">The [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="e806f-195">基於型別轉換的詳細資訊，Visual Basic，請考慮為的 1/1/0001 (1 年的 1 年)*中性值*是中性的值時間的日期和 00:00:00 （午夜）。</span><span class="sxs-lookup"><span data-stu-id="e806f-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="e806f-196">如果您將轉換`Date`值為字串，`CStr`不產生的字串中包含中性的值。</span><span class="sxs-lookup"><span data-stu-id="e806f-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="e806f-197">例如，如果您將轉換`#January 1, 0001 9:30:00#`為字串，結果會是 「 上午 9:30:00"，隱藏的日期資訊。</span><span class="sxs-lookup"><span data-stu-id="e806f-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="e806f-198">不過，日期資訊是仍會出現在原始`Date`值，而且可以使用函式這類復原<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>函式。</span><span class="sxs-lookup"><span data-stu-id="e806f-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>  
  
-   **<span data-ttu-id="e806f-199">區分文化。</span><span class="sxs-lookup"><span data-stu-id="e806f-199">Culture Sensitivity.</span></span>** <span data-ttu-id="e806f-200">字串類型轉換函式會執行目前的文化特性設定，應用程式為基礎的轉換。</span><span class="sxs-lookup"><span data-stu-id="e806f-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="e806f-201">比方說，`CDate`會辨識您的系統地區設定的日期格式。</span><span class="sxs-lookup"><span data-stu-id="e806f-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="e806f-202">您必須提供一天、 月和年在您的地區設定，以正確的順序，或可能不正確地解譯日期。</span><span class="sxs-lookup"><span data-stu-id="e806f-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="e806f-203">如果它包含的週日期字串，例如"Wednesday"無法辨識的長日期格式。</span><span class="sxs-lookup"><span data-stu-id="e806f-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>  
  
     <span data-ttu-id="e806f-204">如果您需要將轉換成或從您的地區設定所指定以外格式的值的字串表示，您無法使用 Visual Basic 型別轉換函式。</span><span class="sxs-lookup"><span data-stu-id="e806f-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="e806f-205">若要這樣做，請使用`ToString(IFormatProvider)`和`Parse(String, IFormatProvider)`該實值型別的方法。</span><span class="sxs-lookup"><span data-stu-id="e806f-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="e806f-206">比方說，使用<xref:System.Double.Parse%2A?displayProperty=nameWithType>若要將字串轉換成`Double`，並使用<xref:System.Double.ToString%2A?displayProperty=nameWithType>轉換類型的值時`Double`為字串。</span><span class="sxs-lookup"><span data-stu-id="e806f-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>  
  
## <a name="ctype-function"></a><span data-ttu-id="e806f-207">CType Function</span><span class="sxs-lookup"><span data-stu-id="e806f-207">CType Function</span></span>  
 <span data-ttu-id="e806f-208">[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)採用第二個引數`typename`，會強制轉型`expression`來`typename`，其中`typename`可以是任何資料類型、 結構、 類別或介面要有有效的轉換。</span><span class="sxs-lookup"><span data-stu-id="e806f-208">The [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>  
  
 <span data-ttu-id="e806f-209">如需的比較`CType`類型轉換關鍵字，請參閱[DirectCast 運算子](../../../visual-basic/language-reference/operators/directcast-operator.md)並[TryCast 運算子](../../../visual-basic/language-reference/operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="e806f-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
## <a name="cbool-example"></a><span data-ttu-id="e806f-210">CBool 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-210">CBool Example</span></span>  
 <span data-ttu-id="e806f-211">下列範例會使用`CBool`函式將轉換運算式到`Boolean`值。</span><span class="sxs-lookup"><span data-stu-id="e806f-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="e806f-212">如果運算式評估為非零值，`CBool`會傳回`True`; 否則它會傳回`False`。</span><span class="sxs-lookup"><span data-stu-id="e806f-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a><span data-ttu-id="e806f-213">CByte 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-213">CByte Example</span></span>  
 <span data-ttu-id="e806f-214">下列範例會使用`CByte`函式將轉換運算式，以`Byte`。</span><span class="sxs-lookup"><span data-stu-id="e806f-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a><span data-ttu-id="e806f-215">CChar 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-215">CChar Example</span></span>  
 <span data-ttu-id="e806f-216">下列範例會使用`CChar`要轉換的第一個字元的函式`String`運算式`Char`型別。</span><span class="sxs-lookup"><span data-stu-id="e806f-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 <span data-ttu-id="e806f-217">若要輸入的引數`CChar`必須是資料型別`Char`或`String`。</span><span class="sxs-lookup"><span data-stu-id="e806f-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="e806f-218">您無法使用`CChar`轉換成字元，數字，因為`CChar`無法接受的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="e806f-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="e806f-219">下列範例會取得代表的字碼指標 （字元碼） 的數字，並將它轉換成對應的字元。</span><span class="sxs-lookup"><span data-stu-id="e806f-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="e806f-220">它會使用<xref:Microsoft.VisualBasic.Interaction.InputBox%2A>函式來取得的數字、 字串`CInt`若要將字串轉換為類型`Integer`，和`ChrW`轉換要輸入的數字`Char`。</span><span class="sxs-lookup"><span data-stu-id="e806f-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a><span data-ttu-id="e806f-221">CDate 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-221">CDate Example</span></span>  
 <span data-ttu-id="e806f-222">下列範例會使用`CDate`函式來將字串轉換為`Date`值。</span><span class="sxs-lookup"><span data-stu-id="e806f-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="e806f-223">一般情況下，不建議硬式編碼的日期和時間字串 （如本範例所示）。</span><span class="sxs-lookup"><span data-stu-id="e806f-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="e806f-224">使用日期常值和時間常值，例如 #Feb 12，1969 # 和 # 4:45:23 PM #，改為。</span><span class="sxs-lookup"><span data-stu-id="e806f-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a><span data-ttu-id="e806f-225">CDbl 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-225">CDbl Example</span></span>  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a><span data-ttu-id="e806f-226">CDec 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-226">CDec Example</span></span>  
 <span data-ttu-id="e806f-227">下列範例會使用`CDec`函數來轉換數值`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="e806f-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a><span data-ttu-id="e806f-228">CInt 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-228">CInt Example</span></span>  
 <span data-ttu-id="e806f-229">下列範例會使用`CInt`函式，將值轉換成`Integer`。</span><span class="sxs-lookup"><span data-stu-id="e806f-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a><span data-ttu-id="e806f-230">CLng 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-230">CLng Example</span></span>
 <span data-ttu-id="e806f-231">下列範例會使用`CLng`函式來將值轉換成`Long`。</span><span class="sxs-lookup"><span data-stu-id="e806f-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a><span data-ttu-id="e806f-232">CObj 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-232">CObj Example</span></span>  
 <span data-ttu-id="e806f-233">下列範例會使用`CObj`函數來轉換數值`Object`。</span><span class="sxs-lookup"><span data-stu-id="e806f-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="e806f-234">`Object`變數本身包含只有四位元組指標，指向`Double`指派給它的值。</span><span class="sxs-lookup"><span data-stu-id="e806f-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a><span data-ttu-id="e806f-235">CSByte 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-235">CSByte Example</span></span>  
 <span data-ttu-id="e806f-236">下列範例會使用`CSByte`函數來轉換數值`SByte`。</span><span class="sxs-lookup"><span data-stu-id="e806f-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a><span data-ttu-id="e806f-237">CShort 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-237">CShort Example</span></span>  
 <span data-ttu-id="e806f-238">下列範例會使用`CShort`函數來轉換數值`Short`。</span><span class="sxs-lookup"><span data-stu-id="e806f-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a><span data-ttu-id="e806f-239">CSng 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-239">CSng Example</span></span>  
 <span data-ttu-id="e806f-240">下列範例會使用`CSng`函式來將值轉換成`Single`。</span><span class="sxs-lookup"><span data-stu-id="e806f-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a><span data-ttu-id="e806f-241">CStr 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-241">CStr Example</span></span>  
 <span data-ttu-id="e806f-242">下列範例會使用`CStr`函數來轉換數值`String`。</span><span class="sxs-lookup"><span data-stu-id="e806f-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 <span data-ttu-id="e806f-243">下列範例會使用`CStr`要轉換的函式`Date`值來`String`值。</span><span class="sxs-lookup"><span data-stu-id="e806f-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` <span data-ttu-id="e806f-244">一律會呈現`Date`目前地區設定，例如，標準的簡短格式的值 」 時間 2003 年 6 月 15 日下午 4:35:47"。</span><span class="sxs-lookup"><span data-stu-id="e806f-244">always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="e806f-245">不過，`CStr`抑制*中性值*的 1/1/0001 的日期和時間為 00:00:00。</span><span class="sxs-lookup"><span data-stu-id="e806f-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>  
  
 <span data-ttu-id="e806f-246">如需詳細資訊，所傳回的值`CStr`，請參閱 < [CStr 函式的傳回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。</span><span class="sxs-lookup"><span data-stu-id="e806f-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).</span></span>  
  
## <a name="cuint-example"></a><span data-ttu-id="e806f-247">CUInt 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-247">CUInt Example</span></span>  
 <span data-ttu-id="e806f-248">下列範例會使用`CUInt`函數來轉換數值`UInteger`。</span><span class="sxs-lookup"><span data-stu-id="e806f-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a><span data-ttu-id="e806f-249">CULng 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-249">CULng Example</span></span>  
 <span data-ttu-id="e806f-250">下列範例會使用`CULng`函數來轉換數值`ULong`。</span><span class="sxs-lookup"><span data-stu-id="e806f-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a><span data-ttu-id="e806f-251">CUShort 範例</span><span class="sxs-lookup"><span data-stu-id="e806f-251">CUShort Example</span></span>  
 <span data-ttu-id="e806f-252">下列範例會使用`CUShort`函數來轉換數值`UShort`。</span><span class="sxs-lookup"><span data-stu-id="e806f-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a><span data-ttu-id="e806f-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e806f-253">See also</span></span>

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
- [<span data-ttu-id="e806f-254">轉換函式</span><span class="sxs-lookup"><span data-stu-id="e806f-254">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="e806f-255">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="e806f-255">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
