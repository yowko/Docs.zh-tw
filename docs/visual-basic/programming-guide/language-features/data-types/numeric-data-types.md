---
title: "數值資料類型 (Visual Basic) |Microsoft 文件"
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
- integral types, Visual Basic
- Short data type, numeric data types
- Double data type, numeric data types
- Long data type, Visual Basic numeric data types
- numbers, whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers, integer
- fractional data types
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type, numeric data types
- exponent, of fractional numbers
- integers
- numeric data types, Visual Basic
- Single data type, numeric types
- Decimal data type, numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
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
ms.openlocfilehash: af87b895c04cf89ba217c9c3a46dc259103d50b4
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="numeric-data-types-visual-basic"></a><span data-ttu-id="df13e-102">數字資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df13e-102">Numeric Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="df13e-103">提供數個*數值資料型別*來處理各種表示相互轉換的數字。</span><span class="sxs-lookup"><span data-stu-id="df13e-103"> supplies several *numeric data types* for handling numbers in various representations.</span></span> <span data-ttu-id="df13e-104">*整數類資料*類型表示只有整數 （正數、 負數和零），和*整數*類型表示的數字的整數和分數部分。</span><span class="sxs-lookup"><span data-stu-id="df13e-104">*Integral* types represent only whole numbers (positive, negative, and zero), and *nonintegral* types represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="df13e-105">顯示由並排比較資料表[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="df13e-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="integral-numeric-types"></a><span data-ttu-id="df13e-106">整數數字類型</span><span class="sxs-lookup"><span data-stu-id="df13e-106">Integral Numeric Types</span></span>  
 <span data-ttu-id="df13e-107">*整數類資料類型*」 用來表示沒有小數部分的唯一數字。</span><span class="sxs-lookup"><span data-stu-id="df13e-107">*Integral data types* are those that represent only numbers without fractional parts.</span></span>  
  
 <span data-ttu-id="df13e-108">*簽署*整數類資料類型是[SByte 資料類型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)（8 位元）、[簡短的資料型別](../../../../visual-basic/language-reference/data-types/short-data-type.md)（16 位元）、[整數資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)（32 位元） 和[Long 資料型別](../../../../visual-basic/language-reference/data-types/long-data-type.md)（64 位元）。</span><span class="sxs-lookup"><span data-stu-id="df13e-108">The *signed* integral data types are [SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8-bit), [Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bit), [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bit), and [Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bit).</span></span> <span data-ttu-id="df13e-109">如果變數一律是儲存整數，而不是小數的數字，將它宣告為其中一種類型。</span><span class="sxs-lookup"><span data-stu-id="df13e-109">If a variable always stores integers rather than fractional numbers, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="df13e-110">*不帶正負號*整數類資料類型[Byte 資料類型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)（8 位元）、 [UShort 資料類型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)（16 位元）、 [UInteger 資料類型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)（32 位元） 和[ULong 資料類型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)（64 位元）。</span><span class="sxs-lookup"><span data-stu-id="df13e-110">The *unsigned* integral types are [Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8-bit), [UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bit), and [ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bit).</span></span> <span data-ttu-id="df13e-111">如果變數包含二進位資料或未知的性質的資料，將它宣告為其中一種類型。</span><span class="sxs-lookup"><span data-stu-id="df13e-111">If a variable contains binary data, or data of unknown nature, declare it as one of these types.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="df13e-112">效能</span><span class="sxs-lookup"><span data-stu-id="df13e-112">Performance</span></span>  
 <span data-ttu-id="df13e-113">算術運算是整數類資料類型與其他資料型別的更快。</span><span class="sxs-lookup"><span data-stu-id="df13e-113">Arithmetic operations are faster with integral types than with other data types.</span></span> <span data-ttu-id="df13e-114">它們是以最快`Integer`和`UInteger`中的型別[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="df13e-114">They are fastest with the `Integer` and `UInteger` types in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
### <a name="large-integers"></a><span data-ttu-id="df13e-115">大整數</span><span class="sxs-lookup"><span data-stu-id="df13e-115">Large Integers</span></span>  
 <span data-ttu-id="df13e-116">如果您需要保存整數大於`Integer`可以保存的資料類型，您可以使用`Long`請改為輸入資料。</span><span class="sxs-lookup"><span data-stu-id="df13e-116">If you need to hold an integer larger than the `Integer` data type can hold, you can use the `Long` data type instead.</span></span> <span data-ttu-id="df13e-117">`Long`變數可以保留從-9223372036854775808 到 9223372036854775807 的數字。</span><span class="sxs-lookup"><span data-stu-id="df13e-117">`Long` variables can hold numbers from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807.</span></span> <span data-ttu-id="df13e-118">作業`Long`稍微低於與`Integer`。</span><span class="sxs-lookup"><span data-stu-id="df13e-118">Operations with `Long` are slightly slower than with `Integer`.</span></span>  
  
 <span data-ttu-id="df13e-119">如果您需要更大的值，您可以使用[Decimal 資料型別](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="df13e-119">If you need even larger values, you can use the [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md).</span></span> <span data-ttu-id="df13e-120">您可以保有數字-79228162514264337593543950335 到 79228162514264337593543950335 中從`Decimal`變數，如果您不使用任何小數位數。</span><span class="sxs-lookup"><span data-stu-id="df13e-120">You can hold numbers from -79,228,162,514,264,337,593,543,950,335 through 79,228,162,514,264,337,593,543,950,335 in a `Decimal` variable if you do not use any decimal places.</span></span> <span data-ttu-id="df13e-121">不過，作業`Decimal`數字會慢很多比其他任何數值資料型別。</span><span class="sxs-lookup"><span data-stu-id="df13e-121">However, operations with `Decimal` numbers are considerably slower than with any other numeric data type.</span></span>  
  
### <a name="small-integers"></a><span data-ttu-id="df13e-122">小整數</span><span class="sxs-lookup"><span data-stu-id="df13e-122">Small Integers</span></span>  
 <span data-ttu-id="df13e-123">如果您不需要完整的`Integer`資料型別，您可以使用`Short`資料型別，可以用來保留從-32768 到 32767 的整數。</span><span class="sxs-lookup"><span data-stu-id="df13e-123">If you do not need the full range of the `Integer` data type, you can use the `Short` data type, which can hold integers from -32,768 through 32,767.</span></span> <span data-ttu-id="df13e-124">最小的整數範圍內，`SByte`資料型別可保留從-128 到 127 的整數。</span><span class="sxs-lookup"><span data-stu-id="df13e-124">For the smallest integer range, the `SByte` data type holds integers from -128 through 127.</span></span> <span data-ttu-id="df13e-125">如果您有非常大量的保存小整數變數，有時可以儲存 common language runtime 程式`Short`和`SByte`變數更有效率且節省記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="df13e-125">If you have a very large number of variables that hold small integers, the common language runtime can sometimes store your `Short` and `SByte` variables more efficiently and save memory consumption.</span></span> <span data-ttu-id="df13e-126">不過，作業`Short`和`SByte`慢比使用`Integer`。</span><span class="sxs-lookup"><span data-stu-id="df13e-126">However, operations with `Short` and `SByte` are somewhat slower than with `Integer`.</span></span>  
  
### <a name="unsigned-integers"></a><span data-ttu-id="df13e-127">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="df13e-127">Unsigned Integers</span></span>  
 <span data-ttu-id="df13e-128">如果您知道，變數就永遠不需要保存負的數字，您可以使用*不帶正負號型別*`Byte`， `UShort`， `UInteger`，和`ULong`。</span><span class="sxs-lookup"><span data-stu-id="df13e-128">If you know that your variable never needs to hold a negative number, you can use the *unsigned types*`Byte`, `UShort`, `UInteger`, and `ULong`.</span></span> <span data-ttu-id="df13e-129">每一種資料類型可以保留正整數兩次大小，其對應的帶正負號的類型 (`SByte`， `Short`， `Integer`，和`Long`)。</span><span class="sxs-lookup"><span data-stu-id="df13e-129">Each of these data types can hold a positive integer twice as large as its corresponding signed type (`SByte`, `Short`, `Integer`, and `Long`).</span></span> <span data-ttu-id="df13e-130">在效能方面，每個不帶正負號的類型的處理效率都與其對應的帶正負號型別。</span><span class="sxs-lookup"><span data-stu-id="df13e-130">In terms of performance, each unsigned type is exactly as efficient as its corresponding signed type.</span></span> <span data-ttu-id="df13e-131">特別是，`UInteger`與共用`Integer`的差別是最有效率的所有基本的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="df13e-131">In particular, `UInteger` shares with `Integer` the distinction of being the most efficient of all the elementary numeric data types.</span></span>  
  
## <a name="nonintegral-numeric-types"></a><span data-ttu-id="df13e-132">非整數的數字類型</span><span class="sxs-lookup"><span data-stu-id="df13e-132">Nonintegral Numeric Types</span></span>  
 <span data-ttu-id="df13e-133">*非整數類資料型別*是指代表具有整數和分數部分的數字。</span><span class="sxs-lookup"><span data-stu-id="df13e-133">*Nonintegral data types* are those that represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="df13e-134">非整數數值資料型別`Decimal`（128 位元固定的點），[單一資料型別](../../../../visual-basic/language-reference/data-types/single-data-type.md)（32 位元浮點數），和[Double 資料型別](../../../../visual-basic/language-reference/data-types/double-data-type.md)（64 位元浮點數）。</span><span class="sxs-lookup"><span data-stu-id="df13e-134">The nonintegral numeric data types are `Decimal` (128-bit fixed point), [Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bit floating point), and [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit floating point).</span></span> <span data-ttu-id="df13e-135">是帶正負號的型別。</span><span class="sxs-lookup"><span data-stu-id="df13e-135">They are all signed types.</span></span> <span data-ttu-id="df13e-136">如果變數可以包含一小部分，將它宣告為其中一種類型。</span><span class="sxs-lookup"><span data-stu-id="df13e-136">If a variable can contain a fraction, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="df13e-137">`Decimal`不是浮點數資料類型。</span><span class="sxs-lookup"><span data-stu-id="df13e-137">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="df13e-138">`Decimal`數字有二進位整數值，並指定值的部分是十進位小數的整數縮放比例。</span><span class="sxs-lookup"><span data-stu-id="df13e-138">`Decimal` numbers have a binary integer value and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span>  
  
 <span data-ttu-id="df13e-139">您可以使用`Decimal`貨幣值的變數。</span><span class="sxs-lookup"><span data-stu-id="df13e-139">You can use `Decimal` variables for money values.</span></span> <span data-ttu-id="df13e-140">優點是值的精確度。</span><span class="sxs-lookup"><span data-stu-id="df13e-140">The advantage is the precision of the values.</span></span> <span data-ttu-id="df13e-141">`Double`資料型別比較快，而且需要較少的記憶體，但是它會受制於捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="df13e-141">The `Double` data type is faster and requires less memory, but it is subject to rounding errors.</span></span> <span data-ttu-id="df13e-142">`Decimal`資料類型會保留至 28 位小數的正確性。</span><span class="sxs-lookup"><span data-stu-id="df13e-142">The `Decimal` data type retains complete accuracy to 28 decimal places.</span></span>  
  
 <span data-ttu-id="df13e-143">浮點數 (`Single`和`Double`) 數字有更大範圍比`Decimal`數字，但可能會受限於捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="df13e-143">Floating-point (`Single` and `Double`) numbers have larger ranges than `Decimal` numbers but can be subject to rounding errors.</span></span> <span data-ttu-id="df13e-144">浮點類型支援較少的有效位數比`Decimal`但可以代表更大範圍的值。</span><span class="sxs-lookup"><span data-stu-id="df13e-144">Floating-point types support fewer significant digits than `Decimal` but can represent values of greater magnitude.</span></span>  
  
 <span data-ttu-id="df13e-145">非整數的數字值中能表示為 mmmEeee，即 mmm*尾數*（有效位數） 和 eee 是*指數*（10 的次方）。</span><span class="sxs-lookup"><span data-stu-id="df13e-145">Nonintegral number values can be expressed as mmmEeee, in which mmm is the *mantissa* (the significant digits) and eee is the *exponent* (a power of 10).</span></span> <span data-ttu-id="df13e-146">非整數類型的最高的正值是 7.9228162514264337593543950335 e + 28 `Decimal`，3.4028235 e + 38 `Single`，和 1.79769313486231570 e + 308 `Double`。</span><span class="sxs-lookup"><span data-stu-id="df13e-146">The highest positive values of the nonintegral types are 7.9228162514264337593543950335E+28 for `Decimal`, 3.4028235E+38 for `Single`, and 1.79769313486231570E+308 for `Double`.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="df13e-147">效能</span><span class="sxs-lookup"><span data-stu-id="df13e-147">Performance</span></span>  
 <span data-ttu-id="df13e-148">`Double`是最有效率的小數點後的資料型別，因為目前的平台上的處理器執行雙精度浮點數運算。</span><span class="sxs-lookup"><span data-stu-id="df13e-148">`Double` is the most efficient of the fractional data types, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="df13e-149">不過，作業`Double`速度與整數類資料型別，例如`Integer`。</span><span class="sxs-lookup"><span data-stu-id="df13e-149">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
### <a name="small-magnitudes"></a><span data-ttu-id="df13e-150">最小範圍</span><span class="sxs-lookup"><span data-stu-id="df13e-150">Small Magnitudes</span></span>  
 <span data-ttu-id="df13e-151">數字的最小的可能範圍 （最接近 0），`Double`變數可以保有數字越小越-4.94065645841246544 e-324 的負數值和 4.94065645841246544-324 的正數值。</span><span class="sxs-lookup"><span data-stu-id="df13e-151">For numbers with the smallest possible magnitude (closest to 0), `Double` variables can hold numbers as small as -4.94065645841246544E-324 for negative values and 4.94065645841246544E-324 for positive values.</span></span>  
  
### <a name="small-fractional-numbers"></a><span data-ttu-id="df13e-152">最小分數</span><span class="sxs-lookup"><span data-stu-id="df13e-152">Small Fractional Numbers</span></span>  
 <span data-ttu-id="df13e-153">如果您不需要完整的`Double`資料型別，您可以使用`Single`資料型別，可以用來保留從-3.4028235 e + 38 到 3.4028235 e + 38 的浮點數。</span><span class="sxs-lookup"><span data-stu-id="df13e-153">If you do not need the full range of the `Double` data type, you can use the `Single` data type, which can hold floating-point numbers from -3.4028235E+38 through 3.4028235E+38.</span></span> <span data-ttu-id="df13e-154">最小的範圍為`Single`變數是-1.401298 e-45 的負數值，以及從 1.401298 e-45 的正數值。</span><span class="sxs-lookup"><span data-stu-id="df13e-154">The smallest magnitudes for `Single` variables are -1.401298E-45 for negative values and 1.401298E-45 for positive values.</span></span> <span data-ttu-id="df13e-155">如果您有非常大量的保留小的浮點數的變數，有時可以儲存 common language runtime 程式`Single`變數更有效率且節省記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="df13e-155">If you have a very large number of variables that hold small floating-point numbers, the common language runtime can sometimes store your `Single` variables more efficiently and save memory consumption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df13e-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df13e-156">See Also</span></span>  
 <span data-ttu-id="df13e-157">[基本資料型別](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="df13e-157">[Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
<span data-ttu-id="df13e-158"> [字元資料類型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="df13e-158"> [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md) </span></span>  
<span data-ttu-id="df13e-159"> [其他資料類型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="df13e-159"> [Miscellaneous Data Types](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md) </span></span>  
<span data-ttu-id="df13e-160"> [資料類型疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="df13e-160"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="df13e-161"> [如何：呼叫使用不帶正負號類型的 Windows 函式](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)</span><span class="sxs-lookup"><span data-stu-id="df13e-161"> [How to: Call a Windows Function that Takes Unsigned Types](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)</span></span>
