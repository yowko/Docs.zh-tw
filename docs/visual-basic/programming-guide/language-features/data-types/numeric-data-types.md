---
title: 數值資料類型
ms.date: 07/20/2015
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
ms.openlocfilehash: 317c0862953e7bb866faa4712d42dfd5995ecf35
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086227"
---
# <a name="numeric-data-types-visual-basic"></a><span data-ttu-id="8445e-102">數字資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8445e-102">Numeric Data Types (Visual Basic)</span></span>

<span data-ttu-id="8445e-103">Visual Basic 提供數種 *數值資料類型* 來處理各種標記法中的數位。</span><span class="sxs-lookup"><span data-stu-id="8445e-103">Visual Basic supplies several *numeric data types* for handling numbers in various representations.</span></span> <span data-ttu-id="8445e-104">*整數* 類資料類型只代表整數 (正數、 *負數和零) ，而非* 整數類型代表具有整數和小數部分的數位。</span><span class="sxs-lookup"><span data-stu-id="8445e-104">*Integral* types represent only whole numbers (positive, negative, and zero), and *nonintegral* types represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="8445e-105">如需顯示 Visual Basic 資料類型的並列比較的資料表，請參閱 [資料類型](../../../language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="8445e-105">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="integral-numeric-types"></a><span data-ttu-id="8445e-106">整數數數值型別</span><span class="sxs-lookup"><span data-stu-id="8445e-106">Integral Numeric Types</span></span>  

 <span data-ttu-id="8445e-107">*整數資料類型* 是指只代表沒有小數部分之數位的資料類型。</span><span class="sxs-lookup"><span data-stu-id="8445e-107">*Integral data types* are those that represent only numbers without fractional parts.</span></span>  
  
 <span data-ttu-id="8445e-108">*帶正負*號的整數資料類型是[SByte 資料類型](../../../language-reference/data-types/sbyte-data-type.md) (8 位) [、Short 資料類型](../../../language-reference/data-types/short-data-type.md) (16 位) 、[整數資料類型](../../../language-reference/data-types/integer-data-type.md) (32 位) 和[LONG 資料型別](../../../language-reference/data-types/long-data-type.md) (64 位) 。</span><span class="sxs-lookup"><span data-stu-id="8445e-108">The *signed* integral data types are [SByte Data Type](../../../language-reference/data-types/sbyte-data-type.md) (8-bit), [Short Data Type](../../../language-reference/data-types/short-data-type.md) (16-bit), [Integer Data Type](../../../language-reference/data-types/integer-data-type.md) (32-bit), and [Long Data Type](../../../language-reference/data-types/long-data-type.md) (64-bit).</span></span> <span data-ttu-id="8445e-109">如果變數一律儲存整數而不是小數，請將它宣告為這些類型的其中一種。</span><span class="sxs-lookup"><span data-stu-id="8445e-109">If a variable always stores integers rather than fractional numbers, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="8445e-110">不 *帶正負* 號的整數類資料類型是 (8 位) 的 [位元組資料](../../../language-reference/data-types/byte-data-type.md) 類型、 [UShort 資料類型](../../../language-reference/data-types/ushort-data-type.md) (16 位) 、 [UInteger 資料類型](../../../language-reference/data-types/uinteger-data-type.md) (32 位) 以及 [ULONG 資料型別](../../../language-reference/data-types/ulong-data-type.md) (64 位) 。</span><span class="sxs-lookup"><span data-stu-id="8445e-110">The *unsigned* integral types are [Byte Data Type](../../../language-reference/data-types/byte-data-type.md) (8-bit), [UShort Data Type](../../../language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Data Type](../../../language-reference/data-types/uinteger-data-type.md) (32-bit), and [ULong Data Type](../../../language-reference/data-types/ulong-data-type.md) (64-bit).</span></span> <span data-ttu-id="8445e-111">如果變數包含二進位資料或未知本質的資料，請將它宣告為這些類型的其中一種。</span><span class="sxs-lookup"><span data-stu-id="8445e-111">If a variable contains binary data, or data of unknown nature, declare it as one of these types.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="8445e-112">效能</span><span class="sxs-lookup"><span data-stu-id="8445e-112">Performance</span></span>  

 <span data-ttu-id="8445e-113">使用整數類資料類型比其他資料類型更快的算數運算。</span><span class="sxs-lookup"><span data-stu-id="8445e-113">Arithmetic operations are faster with integral types than with other data types.</span></span> <span data-ttu-id="8445e-114">它們在 `Integer` Visual Basic 中是和類型的速度最快 `UInteger` 。</span><span class="sxs-lookup"><span data-stu-id="8445e-114">They are fastest with the `Integer` and `UInteger` types in Visual Basic.</span></span>  
  
### <a name="large-integers"></a><span data-ttu-id="8445e-115">大型整數</span><span class="sxs-lookup"><span data-stu-id="8445e-115">Large Integers</span></span>  

 <span data-ttu-id="8445e-116">如果您需要保留大於 `Integer` 資料類型所能保存的整數，則可以 `Long` 改用資料類型。</span><span class="sxs-lookup"><span data-stu-id="8445e-116">If you need to hold an integer larger than the `Integer` data type can hold, you can use the `Long` data type instead.</span></span> <span data-ttu-id="8445e-117">`Long` 變數可以保留從-9223372036854775808 到9223372036854775807的數位。</span><span class="sxs-lookup"><span data-stu-id="8445e-117">`Long` variables can hold numbers from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807.</span></span> <span data-ttu-id="8445e-118">使用的作業 `Long` 會比使用稍微慢一點 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="8445e-118">Operations with `Long` are slightly slower than with `Integer`.</span></span>  
  
 <span data-ttu-id="8445e-119">如果您需要更大的值，您可以使用 [Decimal 資料類型](../../../language-reference/data-types/decimal-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="8445e-119">If you need even larger values, you can use the [Decimal Data Type](../../../language-reference/data-types/decimal-data-type.md).</span></span> <span data-ttu-id="8445e-120">`Decimal`如果您未使用任何小數位數，您可以在變數中保存-79228162514264337593543950335 到79228162514264337593543950335的數位。</span><span class="sxs-lookup"><span data-stu-id="8445e-120">You can hold numbers from -79,228,162,514,264,337,593,543,950,335 through 79,228,162,514,264,337,593,543,950,335 in a `Decimal` variable if you do not use any decimal places.</span></span> <span data-ttu-id="8445e-121">不過，具有數位的作業 `Decimal` 會比其他任何數值資料類型來得慢很多。</span><span class="sxs-lookup"><span data-stu-id="8445e-121">However, operations with `Decimal` numbers are considerably slower than with any other numeric data type.</span></span>  
  
### <a name="small-integers"></a><span data-ttu-id="8445e-122">小整數</span><span class="sxs-lookup"><span data-stu-id="8445e-122">Small Integers</span></span>  

 <span data-ttu-id="8445e-123">如果您不需要資料類型的完整範圍 `Integer` ，您可以使用 `Short` 資料類型，該資料類型可以保留從-32768 到32767的整數。</span><span class="sxs-lookup"><span data-stu-id="8445e-123">If you do not need the full range of the `Integer` data type, you can use the `Short` data type, which can hold integers from -32,768 through 32,767.</span></span> <span data-ttu-id="8445e-124">針對最小整數範圍， `SByte` 資料類型會保留從-128 到127的整數。</span><span class="sxs-lookup"><span data-stu-id="8445e-124">For the smallest integer range, the `SByte` data type holds integers from -128 through 127.</span></span> <span data-ttu-id="8445e-125">如果您有非常大量的變數來容納小整數，則 common language runtime 有時可以 `Short` `SByte` 更有效率地儲存和變數，並節省記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="8445e-125">If you have a very large number of variables that hold small integers, the common language runtime can sometimes store your `Short` and `SByte` variables more efficiently and save memory consumption.</span></span> <span data-ttu-id="8445e-126">不過，使用和的作業 `Short` `SByte` 有點慢于 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="8445e-126">However, operations with `Short` and `SByte` are somewhat slower than with `Integer`.</span></span>  
  
### <a name="unsigned-integers"></a><span data-ttu-id="8445e-127">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="8445e-127">Unsigned Integers</span></span>  

 <span data-ttu-id="8445e-128">如果您知道變數永遠不需要保留負數，則可以使用不帶正負號的*類型* `Byte` 、、 `UShort` `UInteger` 和 `ULong` 。</span><span class="sxs-lookup"><span data-stu-id="8445e-128">If you know that your variable never needs to hold a negative number, you can use the *unsigned types*`Byte`, `UShort`, `UInteger`, and `ULong`.</span></span> <span data-ttu-id="8445e-129">這些資料類型的每一個都可以將正整數保留為其對應的帶正負號類型 (`SByte` 、、 `Short` `Integer` 和 `Long`) 兩次。</span><span class="sxs-lookup"><span data-stu-id="8445e-129">Each of these data types can hold a positive integer twice as large as its corresponding signed type (`SByte`, `Short`, `Integer`, and `Long`).</span></span> <span data-ttu-id="8445e-130">在效能方面，每個不帶正負號的類型都與其對應的帶正負號型別一樣有效率。</span><span class="sxs-lookup"><span data-stu-id="8445e-130">In terms of performance, each unsigned type is exactly as efficient as its corresponding signed type.</span></span> <span data-ttu-id="8445e-131">尤其是， `UInteger` 共用的 `Integer` 差異在於最有效率的所有基本數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="8445e-131">In particular, `UInteger` shares with `Integer` the distinction of being the most efficient of all the elementary numeric data types.</span></span>  
  
## <a name="nonintegral-numeric-types"></a><span data-ttu-id="8445e-132">非整數數數值型別</span><span class="sxs-lookup"><span data-stu-id="8445e-132">Nonintegral Numeric Types</span></span>  

 <span data-ttu-id="8445e-133">非整數資料類型就是代表具有整數和小數部分之數位的*資料類型*。</span><span class="sxs-lookup"><span data-stu-id="8445e-133">*Nonintegral data types* are those that represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="8445e-134">非整數數值資料類型是 `Decimal` (128 位的固定點) 、 [單一資料類型](../../../language-reference/data-types/single-data-type.md) (32 位浮點數) ，以及 (64 位浮點數) 的 [Double 資料類型](../../../language-reference/data-types/double-data-type.md) 。</span><span class="sxs-lookup"><span data-stu-id="8445e-134">The nonintegral numeric data types are `Decimal` (128-bit fixed point), [Single Data Type](../../../language-reference/data-types/single-data-type.md) (32-bit floating point), and [Double Data Type](../../../language-reference/data-types/double-data-type.md) (64-bit floating point).</span></span> <span data-ttu-id="8445e-135">它們都是帶正負號的類型。</span><span class="sxs-lookup"><span data-stu-id="8445e-135">They are all signed types.</span></span> <span data-ttu-id="8445e-136">如果變數可以包含分數，請將它宣告為這些類型的其中一種。</span><span class="sxs-lookup"><span data-stu-id="8445e-136">If a variable can contain a fraction, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="8445e-137">`Decimal` 不是浮點資料類型。</span><span class="sxs-lookup"><span data-stu-id="8445e-137">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="8445e-138">`Decimal` 數位具有二進位整數值和整數縮放比例，可指定值的哪個部分是小數小數。</span><span class="sxs-lookup"><span data-stu-id="8445e-138">`Decimal` numbers have a binary integer value and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span>  
  
 <span data-ttu-id="8445e-139">您可以使用 `Decimal` 變數來取得 money 值。</span><span class="sxs-lookup"><span data-stu-id="8445e-139">You can use `Decimal` variables for money values.</span></span> <span data-ttu-id="8445e-140">優點是值的有效位數。</span><span class="sxs-lookup"><span data-stu-id="8445e-140">The advantage is the precision of the values.</span></span> <span data-ttu-id="8445e-141">`Double`資料類型的速度較快，而且需要較少的記憶體，但會受到舍入錯誤的要求。</span><span class="sxs-lookup"><span data-stu-id="8445e-141">The `Double` data type is faster and requires less memory, but it is subject to rounding errors.</span></span> <span data-ttu-id="8445e-142">`Decimal`資料類型會將完整的精確度保留為28個小數位數。</span><span class="sxs-lookup"><span data-stu-id="8445e-142">The `Decimal` data type retains complete accuracy to 28 decimal places.</span></span>  
  
 <span data-ttu-id="8445e-143">浮點數 (`Single` 和 `Double`) 數位的範圍比數位更大， `Decimal` 但可能受舍入錯誤所需。</span><span class="sxs-lookup"><span data-stu-id="8445e-143">Floating-point (`Single` and `Double`) numbers have larger ranges than `Decimal` numbers but can be subject to rounding errors.</span></span> <span data-ttu-id="8445e-144">浮點數類型支援的有效位數較少 `Decimal` ，但可代表較大範圍的值。</span><span class="sxs-lookup"><span data-stu-id="8445e-144">Floating-point types support fewer significant digits than `Decimal` but can represent values of greater magnitude.</span></span>  
  
 <span data-ttu-id="8445e-145">非整數值可以表示為 mmmEeee，其中 mmm 是) 的 *尾數* (有效位數，而 eee 是 *指數* (10) 的乘冪。</span><span class="sxs-lookup"><span data-stu-id="8445e-145">Nonintegral number values can be expressed as mmmEeee, in which mmm is the *mantissa* (the significant digits) and eee is the *exponent* (a power of 10).</span></span> <span data-ttu-id="8445e-146">非整數類型的最大正值為 7.9228162514264337593543950335 E + 28 （適用于、 `Decimal` 3.4028235 e + 38 `Single` 、以及 1.79769313486231570 e + 308） `Double` 。</span><span class="sxs-lookup"><span data-stu-id="8445e-146">The highest positive values of the nonintegral types are 7.9228162514264337593543950335E+28 for `Decimal`, 3.4028235E+38 for `Single`, and 1.79769313486231570E+308 for `Double`.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="8445e-147">效能</span><span class="sxs-lookup"><span data-stu-id="8445e-147">Performance</span></span>  

 <span data-ttu-id="8445e-148">`Double` 是最有效率的小數資料類型，因為目前平臺上的處理器會以雙精確度執行浮點運算。</span><span class="sxs-lookup"><span data-stu-id="8445e-148">`Double` is the most efficient of the fractional data types, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="8445e-149">不過，使用的作業 `Double` 不像整數類資料類型一樣快 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="8445e-149">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
### <a name="small-magnitudes"></a><span data-ttu-id="8445e-150">Small 巨量</span><span class="sxs-lookup"><span data-stu-id="8445e-150">Small Magnitudes</span></span>  

 <span data-ttu-id="8445e-151">若為具有最小可能幅度 (最接近 0) 的數位，則 `Double` 變數可以將數值以小於-4.94065645841246544 e-324 的數位保留給負值，並針對正值 4.94065645841246544 e-324。</span><span class="sxs-lookup"><span data-stu-id="8445e-151">For numbers with the smallest possible magnitude (closest to 0), `Double` variables can hold numbers as small as -4.94065645841246544E-324 for negative values and 4.94065645841246544E-324 for positive values.</span></span>  
  
### <a name="small-fractional-numbers"></a><span data-ttu-id="8445e-152">小小小數位數</span><span class="sxs-lookup"><span data-stu-id="8445e-152">Small Fractional Numbers</span></span>  

 <span data-ttu-id="8445e-153">如果您不需要資料類型的完整範圍 `Double` ，您可以使用 `Single` 資料類型，此資料類型可以保留從-3.4028235 e + 38 到 3.4028235 e + 38 的浮點數。</span><span class="sxs-lookup"><span data-stu-id="8445e-153">If you do not need the full range of the `Double` data type, you can use the `Single` data type, which can hold floating-point numbers from -3.4028235E+38 through 3.4028235E+38.</span></span> <span data-ttu-id="8445e-154">變數的最小巨量為 `Single` -1.401298 e-45 （代表負值）和 1.401298 e-45 （代表正數值）。</span><span class="sxs-lookup"><span data-stu-id="8445e-154">The smallest magnitudes for `Single` variables are -1.401298E-45 for negative values and 1.401298E-45 for positive values.</span></span> <span data-ttu-id="8445e-155">如果您有非常大量的變數來保存小型浮點數，則 common language runtime 有時可以 `Single` 更有效率地儲存變數並節省記憶體耗用量。</span><span class="sxs-lookup"><span data-stu-id="8445e-155">If you have a very large number of variables that hold small floating-point numbers, the common language runtime can sometimes store your `Single` variables more efficiently and save memory consumption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8445e-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8445e-156">See also</span></span>

- [<span data-ttu-id="8445e-157">基礎資料類型</span><span class="sxs-lookup"><span data-stu-id="8445e-157">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="8445e-158">字元資料類型</span><span class="sxs-lookup"><span data-stu-id="8445e-158">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="8445e-159">其他資料類型</span><span class="sxs-lookup"><span data-stu-id="8445e-159">Miscellaneous Data Types</span></span>](miscellaneous-data-types.md)
- [<span data-ttu-id="8445e-160">疑難排解資料類型的問題</span><span class="sxs-lookup"><span data-stu-id="8445e-160">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="8445e-161">作法：呼叫不帶正負號的類型的 Windows 函式</span><span class="sxs-lookup"><span data-stu-id="8445e-161">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
