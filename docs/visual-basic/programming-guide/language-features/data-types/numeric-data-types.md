---
title: "數字資料類型 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9c185b7c04d589bfe74d1cca0c60df3e81ab80d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="numeric-data-types-visual-basic"></a><span data-ttu-id="acab1-102">數字資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acab1-102">Numeric Data Types (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="acab1-103">提供數個*數值資料型別*來處理各種表示相互轉換的數字。</span><span class="sxs-lookup"><span data-stu-id="acab1-103"> supplies several *numeric data types* for handling numbers in various representations.</span></span> <span data-ttu-id="acab1-104">*整數類資料*類型表示只有整數 （正數、 負數和零），和*整數*類型與整數和分數部分代表數字。</span><span class="sxs-lookup"><span data-stu-id="acab1-104">*Integral* types represent only whole numbers (positive, negative, and zero), and *nonintegral* types represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="acab1-105">顯示並行所比較資料表[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]資料類型，請參閱[資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md)。</span><span class="sxs-lookup"><span data-stu-id="acab1-105">For a table showing a side-by-side comparison of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="integral-numeric-types"></a><span data-ttu-id="acab1-106">整數數字類型</span><span class="sxs-lookup"><span data-stu-id="acab1-106">Integral Numeric Types</span></span>  
 <span data-ttu-id="acab1-107">*整數類資料類型*則代表不含小數部分的唯一數字。</span><span class="sxs-lookup"><span data-stu-id="acab1-107">*Integral data types* are those that represent only numbers without fractional parts.</span></span>  
  
 <span data-ttu-id="acab1-108">*簽署*整數類資料類型是[SByte 資料類型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)（8 位元）、[短的資料型別](../../../../visual-basic/language-reference/data-types/short-data-type.md)（16 位元）、[整數資料類型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)（32 位元） 和[Long 資料類型](../../../../visual-basic/language-reference/data-types/long-data-type.md)（64 位元）。</span><span class="sxs-lookup"><span data-stu-id="acab1-108">The *signed* integral data types are [SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8-bit), [Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bit), [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bit), and [Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bit).</span></span> <span data-ttu-id="acab1-109">如果變數一律是儲存整數，而不是小數的數字，將它宣告為其中一個類型。</span><span class="sxs-lookup"><span data-stu-id="acab1-109">If a variable always stores integers rather than fractional numbers, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="acab1-110">*不帶正負號*整數類資料類型[Byte 資料類型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)（8 位元）、 [UShort 資料類型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)（16 位元）、 [UInteger 資料類型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)（32 位元） 和[ULong 資料類型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)（64 位元）。</span><span class="sxs-lookup"><span data-stu-id="acab1-110">The *unsigned* integral types are [Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8-bit), [UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bit), and [ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bit).</span></span> <span data-ttu-id="acab1-111">如果變數包含二進位資料或未知的性質的資料，請將它做為其中一個這些類型宣告。</span><span class="sxs-lookup"><span data-stu-id="acab1-111">If a variable contains binary data, or data of unknown nature, declare it as one of these types.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="acab1-112">效能</span><span class="sxs-lookup"><span data-stu-id="acab1-112">Performance</span></span>  
 <span data-ttu-id="acab1-113">算術運算是整數類資料類型與其他資料型別的更快。</span><span class="sxs-lookup"><span data-stu-id="acab1-113">Arithmetic operations are faster with integral types than with other data types.</span></span> <span data-ttu-id="acab1-114">它們是以最快`Integer`和`UInteger`中的型別[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="acab1-114">They are fastest with the `Integer` and `UInteger` types in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="large-integers"></a><span data-ttu-id="acab1-115">大整數</span><span class="sxs-lookup"><span data-stu-id="acab1-115">Large Integers</span></span>  
 <span data-ttu-id="acab1-116">如果您需要保存整數大於`Integer`可以保存的資料類型，您可以使用`Long`資料改為輸入。</span><span class="sxs-lookup"><span data-stu-id="acab1-116">If you need to hold an integer larger than the `Integer` data type can hold, you can use the `Long` data type instead.</span></span> <span data-ttu-id="acab1-117">`Long`變數可以保留從-9223372036854775808 到 9,223,372,036,854,775,807 的數字。</span><span class="sxs-lookup"><span data-stu-id="acab1-117">`Long` variables can hold numbers from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807.</span></span> <span data-ttu-id="acab1-118">作業`Long`稍微低於與`Integer`。</span><span class="sxs-lookup"><span data-stu-id="acab1-118">Operations with `Long` are slightly slower than with `Integer`.</span></span>  
  
 <span data-ttu-id="acab1-119">如果您需要更大的值，您可以使用[Decimal 資料類型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="acab1-119">If you need even larger values, you can use the [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md).</span></span> <span data-ttu-id="acab1-120">您可以保有數字-79228162514264337593543950335 到 79228162514264337593543950335 中從`Decimal`變數，如果您未使用任何小數位數。</span><span class="sxs-lookup"><span data-stu-id="acab1-120">You can hold numbers from -79,228,162,514,264,337,593,543,950,335 through 79,228,162,514,264,337,593,543,950,335 in a `Decimal` variable if you do not use any decimal places.</span></span> <span data-ttu-id="acab1-121">不過，作業`Decimal`數字會慢很多超過其他任何數值資料型別。</span><span class="sxs-lookup"><span data-stu-id="acab1-121">However, operations with `Decimal` numbers are considerably slower than with any other numeric data type.</span></span>  
  
### <a name="small-integers"></a><span data-ttu-id="acab1-122">小整數</span><span class="sxs-lookup"><span data-stu-id="acab1-122">Small Integers</span></span>  
 <span data-ttu-id="acab1-123">如果您不需要的完整範圍`Integer`資料型別，您可以使用`Short`資料型別，可保存從-32,768 到 32,767 的整數。</span><span class="sxs-lookup"><span data-stu-id="acab1-123">If you do not need the full range of the `Integer` data type, you can use the `Short` data type, which can hold integers from -32,768 through 32,767.</span></span> <span data-ttu-id="acab1-124">最小的整數範圍內，`SByte`資料類型會保留從-128 到 127 的整數。</span><span class="sxs-lookup"><span data-stu-id="acab1-124">For the smallest integer range, the `SByte` data type holds integers from -128 through 127.</span></span> <span data-ttu-id="acab1-125">如果您有非常大量的變數，保存小整數，common language runtime 可以有時候會儲存您`Short`和`SByte`變數儲存記憶體耗用量和更有效率。</span><span class="sxs-lookup"><span data-stu-id="acab1-125">If you have a very large number of variables that hold small integers, the common language runtime can sometimes store your `Short` and `SByte` variables more efficiently and save memory consumption.</span></span> <span data-ttu-id="acab1-126">不過，作業`Short`和`SByte`稍微低於與`Integer`。</span><span class="sxs-lookup"><span data-stu-id="acab1-126">However, operations with `Short` and `SByte` are somewhat slower than with `Integer`.</span></span>  
  
### <a name="unsigned-integers"></a><span data-ttu-id="acab1-127">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="acab1-127">Unsigned Integers</span></span>  
 <span data-ttu-id="acab1-128">如果您知道您的變數就永遠不需要保存為負數，您可以使用*不帶正負號類型*`Byte`， `UShort`， `UInteger`，和`ULong`。</span><span class="sxs-lookup"><span data-stu-id="acab1-128">If you know that your variable never needs to hold a negative number, you can use the *unsigned types*`Byte`, `UShort`, `UInteger`, and `ULong`.</span></span> <span data-ttu-id="acab1-129">每個資料類型可以保存的正整數兩次大小，其對應的帶正負號的類型 (`SByte`， `Short`， `Integer`，和`Long`)。</span><span class="sxs-lookup"><span data-stu-id="acab1-129">Each of these data types can hold a positive integer twice as large as its corresponding signed type (`SByte`, `Short`, `Integer`, and `Long`).</span></span> <span data-ttu-id="acab1-130">在效能方面，每個不帶正負號的類型是完全效率和其對應的帶正負號型別一樣。</span><span class="sxs-lookup"><span data-stu-id="acab1-130">In terms of performance, each unsigned type is exactly as efficient as its corresponding signed type.</span></span> <span data-ttu-id="acab1-131">特別是，`UInteger`與共用`Integer`的所有基本的數值資料類型的最有效率的差別。</span><span class="sxs-lookup"><span data-stu-id="acab1-131">In particular, `UInteger` shares with `Integer` the distinction of being the most efficient of all the elementary numeric data types.</span></span>  
  
## <a name="nonintegral-numeric-types"></a><span data-ttu-id="acab1-132">非整數數值類型</span><span class="sxs-lookup"><span data-stu-id="acab1-132">Nonintegral Numeric Types</span></span>  
 <span data-ttu-id="acab1-133">*非整數類資料型別*是指代表整數和分數部分的數字。</span><span class="sxs-lookup"><span data-stu-id="acab1-133">*Nonintegral data types* are those that represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="acab1-134">非整數數值資料類型為`Decimal`（128 位元固定的點），[單一的資料型別](../../../../visual-basic/language-reference/data-types/single-data-type.md)（32 位元浮點） 和[Double 資料類型](../../../../visual-basic/language-reference/data-types/double-data-type.md)（64 位元浮點數）。</span><span class="sxs-lookup"><span data-stu-id="acab1-134">The nonintegral numeric data types are `Decimal` (128-bit fixed point), [Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bit floating point), and [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit floating point).</span></span> <span data-ttu-id="acab1-135">它們都是帶正負號的類型。</span><span class="sxs-lookup"><span data-stu-id="acab1-135">They are all signed types.</span></span> <span data-ttu-id="acab1-136">如果變數可以包含一小部分，將它宣告為其中一個類型。</span><span class="sxs-lookup"><span data-stu-id="acab1-136">If a variable can contain a fraction, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="acab1-137">`Decimal`不是浮點數資料類型。</span><span class="sxs-lookup"><span data-stu-id="acab1-137">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="acab1-138">`Decimal`數字必須是二進位的整數值，指定值的哪些部分是十進位小數的整數縮放比例。</span><span class="sxs-lookup"><span data-stu-id="acab1-138">`Decimal` numbers have a binary integer value and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span>  
  
 <span data-ttu-id="acab1-139">您可以使用`Decimal`貨幣值的變數。</span><span class="sxs-lookup"><span data-stu-id="acab1-139">You can use `Decimal` variables for money values.</span></span> <span data-ttu-id="acab1-140">優點是值的精確度。</span><span class="sxs-lookup"><span data-stu-id="acab1-140">The advantage is the precision of the values.</span></span> <span data-ttu-id="acab1-141">`Double`資料型別會加快，需要較少的記憶體，但它會受制於捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="acab1-141">The `Double` data type is faster and requires less memory, but it is subject to rounding errors.</span></span> <span data-ttu-id="acab1-142">`Decimal`資料類型會保留完整的精確度為 28 的小數位數。</span><span class="sxs-lookup"><span data-stu-id="acab1-142">The `Decimal` data type retains complete accuracy to 28 decimal places.</span></span>  
  
 <span data-ttu-id="acab1-143">浮點數 (`Single`和`Double`) 數字有更大範圍比`Decimal`數字，但可以是受制於捨入錯誤。</span><span class="sxs-lookup"><span data-stu-id="acab1-143">Floating-point (`Single` and `Double`) numbers have larger ranges than `Decimal` numbers but can be subject to rounding errors.</span></span> <span data-ttu-id="acab1-144">浮點類型支援較少的有效位數比`Decimal`但可以代表更大範圍的值。</span><span class="sxs-lookup"><span data-stu-id="acab1-144">Floating-point types support fewer significant digits than `Decimal` but can represent values of greater magnitude.</span></span>  
  
 <span data-ttu-id="acab1-145">非整數的數字值可以表示為 mmmEeee 中, 即 mmm*尾數*（有效位數） 而且 eee*指數*（10 的次方）。</span><span class="sxs-lookup"><span data-stu-id="acab1-145">Nonintegral number values can be expressed as mmmEeee, in which mmm is the *mantissa* (the significant digits) and eee is the *exponent* (a power of 10).</span></span> <span data-ttu-id="acab1-146">非整數類型的最高的正數值會 7.9228162514264337593543950335 e + 28 `Decimal`，3.4028235 e + 38 `Single`，和 1.79769313486231570 e + 308 `Double`。</span><span class="sxs-lookup"><span data-stu-id="acab1-146">The highest positive values of the nonintegral types are 7.9228162514264337593543950335E+28 for `Decimal`, 3.4028235E+38 for `Single`, and 1.79769313486231570E+308 for `Double`.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="acab1-147">效能</span><span class="sxs-lookup"><span data-stu-id="acab1-147">Performance</span></span>  
 <span data-ttu-id="acab1-148">`Double`是最有效率的分數的資料類型，因為在目前的平台上的處理器執行雙精度浮點數運算。</span><span class="sxs-lookup"><span data-stu-id="acab1-148">`Double` is the most efficient of the fractional data types, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="acab1-149">不過，作業`Double`速度與整數類資料類型，例如`Integer`。</span><span class="sxs-lookup"><span data-stu-id="acab1-149">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
### <a name="small-magnitudes"></a><span data-ttu-id="acab1-150">最小範圍</span><span class="sxs-lookup"><span data-stu-id="acab1-150">Small Magnitudes</span></span>  
 <span data-ttu-id="acab1-151">數字最小的可能範圍 （最接近 0），與`Double`變數可以保有數字越小越-4.94065645841246544-324 負值，4.94065645841246544-324 的正數值。</span><span class="sxs-lookup"><span data-stu-id="acab1-151">For numbers with the smallest possible magnitude (closest to 0), `Double` variables can hold numbers as small as -4.94065645841246544E-324 for negative values and 4.94065645841246544E-324 for positive values.</span></span>  
  
### <a name="small-fractional-numbers"></a><span data-ttu-id="acab1-152">最小分數</span><span class="sxs-lookup"><span data-stu-id="acab1-152">Small Fractional Numbers</span></span>  
 <span data-ttu-id="acab1-153">如果您不需要的完整範圍`Double`資料型別，您可以使用`Single`資料型別，可保存從-3.4028235 e + 38 到 3.4028235 e + 38 浮點數。</span><span class="sxs-lookup"><span data-stu-id="acab1-153">If you do not need the full range of the `Double` data type, you can use the `Single` data type, which can hold floating-point numbers from -3.4028235E+38 through 3.4028235E+38.</span></span> <span data-ttu-id="acab1-154">最小的範圍為`Single`變數是-1.401298-負數值和 1.401298 45-45 的正數值。</span><span class="sxs-lookup"><span data-stu-id="acab1-154">The smallest magnitudes for `Single` variables are -1.401298E-45 for negative values and 1.401298E-45 for positive values.</span></span> <span data-ttu-id="acab1-155">如果您有非常大量的保留小的浮點數的變數時，common language runtime 可以有時候會儲存您`Single`變數儲存記憶體耗用量和更有效率。</span><span class="sxs-lookup"><span data-stu-id="acab1-155">If you have a very large number of variables that hold small floating-point numbers, the common language runtime can sometimes store your `Single` variables more efficiently and save memory consumption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acab1-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acab1-156">See Also</span></span>  
 [<span data-ttu-id="acab1-157">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="acab1-157">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="acab1-158">字元資料類型</span><span class="sxs-lookup"><span data-stu-id="acab1-158">Character Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [<span data-ttu-id="acab1-159">其他資料類型</span><span class="sxs-lookup"><span data-stu-id="acab1-159">Miscellaneous Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [<span data-ttu-id="acab1-160">資料類型的疑難排解</span><span class="sxs-lookup"><span data-stu-id="acab1-160">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="acab1-161">操作說明：呼叫使用不帶正負號類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="acab1-161">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
