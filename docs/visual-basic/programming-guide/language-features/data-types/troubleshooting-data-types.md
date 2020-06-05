---
title: 疑難排解資料類型的問題
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: 239e1c2f908a9023aeca6e92aff4633b60f27b69
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393399"
---
# <a name="troubleshooting-data-types-visual-basic"></a><span data-ttu-id="59f70-102">疑難排解資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59f70-102">Troubleshooting Data Types (Visual Basic)</span></span>

<span data-ttu-id="59f70-103">此頁面會列出當您對內部資料類型執行作業時，可能會發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="59f70-103">This page lists some common problems that can occur when you perform operations on intrinsic data types.</span></span>

## <a name="floating-point-expressions-do-not-compare-as-equal"></a><span data-ttu-id="59f70-104">浮點運算式不會比較為相等</span><span class="sxs-lookup"><span data-stu-id="59f70-104">Floating-Point Expressions Do Not Compare as Equal</span></span>

<span data-ttu-id="59f70-105">當您使用浮點數（[單一資料類型](../../../language-reference/data-types/single-data-type.md)和[Double 資料類型](../../../language-reference/data-types/double-data-type.md)）時，請記住這些數位會儲存為二進位分數。</span><span class="sxs-lookup"><span data-stu-id="59f70-105">When you work with floating-point numbers ([Single Data Type](../../../language-reference/data-types/single-data-type.md) and [Double Data Type](../../../language-reference/data-types/double-data-type.md)), remember that they are stored as binary fractions.</span></span> <span data-ttu-id="59f70-106">這表示它們無法針對不是二進位分數的任何數量（其格式為 k/（2 ^ n），其中 k 和 n 是整數），不能有精確的標記法。</span><span class="sxs-lookup"><span data-stu-id="59f70-106">This means they cannot hold an exact representation of any quantity that is not a binary fraction (of the form k / (2 ^ n) where k and n are integers).</span></span> <span data-ttu-id="59f70-107">例如，0.5 （= 1/2）和0.3125 （= 5/16）可以保留為精確值，而 [0.2 （= 1/5）] 和 [0.3] （= [3/10]）只能是近似值。</span><span class="sxs-lookup"><span data-stu-id="59f70-107">For example, 0.5 (= 1/2) and 0.3125 (= 5/16) can be held as precise values, whereas 0.2 (= 1/5) and 0.3 (= 3/10) can be only approximations.</span></span>

<span data-ttu-id="59f70-108">由於此不精確，當您操作浮點值時，您無法依賴確切的結果。</span><span class="sxs-lookup"><span data-stu-id="59f70-108">Because of this imprecision, you cannot rely on exact results when you operate on floating-point values.</span></span> <span data-ttu-id="59f70-109">特別是，理論上相等的兩個值可能會有稍微不同的標記法。</span><span class="sxs-lookup"><span data-stu-id="59f70-109">In particular, two values that are theoretically equal might have slightly different representations.</span></span>

| <span data-ttu-id="59f70-110">比較浮點數量</span><span class="sxs-lookup"><span data-stu-id="59f70-110">To compare floating-point quantities</span></span> |
|---|
|<span data-ttu-id="59f70-111">1. 使用 <xref:System.Math.Abs%2A> <xref:System.Math> 命名空間中類別的方法，計算其差異的絕對值 <xref:System> 。</span><span class="sxs-lookup"><span data-stu-id="59f70-111">1.  Calculate the absolute value of their difference by using the <xref:System.Math.Abs%2A> method of the <xref:System.Math> class in the <xref:System> namespace.</span></span><br /><span data-ttu-id="59f70-112">2. 判斷可接受的最大差異，如此一來，如果兩個數量的差異不大，您就可以將其視為實際用途。</span><span class="sxs-lookup"><span data-stu-id="59f70-112">2.  Determine an acceptable maximum difference, such that you can consider the two quantities to be equal for practical purposes if their difference is no larger.</span></span><br /><span data-ttu-id="59f70-113">3. 將差異的絕對值與可接受的差異做比較。</span><span class="sxs-lookup"><span data-stu-id="59f70-113">3.  Compare the absolute value of the difference to the acceptable difference.</span></span>|

<span data-ttu-id="59f70-114">下列範例示範兩個值的不正確和正確比較 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-114">The following example demonstrates both incorrect and correct comparison of two `Double` values.</span></span>

[!code-vb[VbVbalrDataTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#10)]

<span data-ttu-id="59f70-115">上一個範例會使用 <xref:System.Double.ToString%2A> 結構的方法， <xref:System.Double> 讓它可以指定比關鍵字使用更好的有效位數 `CStr` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-115">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better  precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="59f70-116">預設值為15位數，但 "G17" 格式會將它延伸至17個數字。</span><span class="sxs-lookup"><span data-stu-id="59f70-116">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>

## <a name="mod-operator-does-not-return-accurate-result"></a><span data-ttu-id="59f70-117">Mod 運算子不會傳回精確的結果</span><span class="sxs-lookup"><span data-stu-id="59f70-117">Mod Operator Does Not Return Accurate Result</span></span>

<span data-ttu-id="59f70-118">由於浮點儲存區的不精確，當至少有一個運算元為浮點時， [Mod 運算子](../../../language-reference/operators/mod-operator.md)可能會傳回非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="59f70-118">Because of the imprecision of floating-point storage, the [Mod Operator](../../../language-reference/operators/mod-operator.md) can return an unexpected result when at least one of the operands is floating-point.</span></span>

<span data-ttu-id="59f70-119">[Decimal 資料類型](../../../language-reference/data-types/decimal-data-type.md)不會使用浮點標記法。</span><span class="sxs-lookup"><span data-stu-id="59f70-119">The [Decimal Data Type](../../../language-reference/data-types/decimal-data-type.md) does not use floating-point representation.</span></span> <span data-ttu-id="59f70-120">許多在和中不精確的數位（例如， `Single` `Double` `Decimal` 0.2 和0.3）。</span><span class="sxs-lookup"><span data-stu-id="59f70-120">Many numbers that are inexact in `Single` and `Double` are exact in `Decimal` (for example 0.2 and 0.3).</span></span> <span data-ttu-id="59f70-121">雖然算術的速度低於 `Decimal` 浮點，但可能值得降低效能，以達到更佳的精確度。</span><span class="sxs-lookup"><span data-stu-id="59f70-121">Although arithmetic is slower in `Decimal` than in floating-point, it might be worth the performance decrease to achieve better precision.</span></span>

|<span data-ttu-id="59f70-122">若要找出浮點數量的整數餘數</span><span class="sxs-lookup"><span data-stu-id="59f70-122">To find the integer remainder of floating-point quantities</span></span>|
|---|
|<span data-ttu-id="59f70-123">1. 將變數宣告為 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-123">1.  Declare variables as `Decimal`.</span></span><br /><span data-ttu-id="59f70-124">2. 使用常數值型別字元 `D` 來強制常 `Decimal` 值，以在其值對資料類型而言太大的情況下 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-124">2.  Use the literal type character `D` to force literals to `Decimal`, in case their values are too large for the `Long` data type.</span></span>|

<span data-ttu-id="59f70-125">下列範例示範浮點運算元的潛在不精確。</span><span class="sxs-lookup"><span data-stu-id="59f70-125">The following example demonstrates the potential imprecision of floating-point operands.</span></span>

[!code-vb[VbVbalrDataTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#11)]

<span data-ttu-id="59f70-126">上一個範例會使用 <xref:System.Double.ToString%2A> 結構的方法， <xref:System.Double> 讓它可以指定比關鍵字使用更好的有效位數 `CStr` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-126">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="59f70-127">預設值為15位數，但 "G17" 格式會將它延伸至17個數字。</span><span class="sxs-lookup"><span data-stu-id="59f70-127">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>

<span data-ttu-id="59f70-128">因為 `zeroPointTwo` 是 `Double` ，所以0.2 的值是具有儲存值0.20000000000000001 的無限重複二進位分數。</span><span class="sxs-lookup"><span data-stu-id="59f70-128">Because `zeroPointTwo` is `Double`, its value for 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="59f70-129">將2.0 除以此數量會產生9.9999999999999995，餘數為0.19999999999999991。</span><span class="sxs-lookup"><span data-stu-id="59f70-129">Dividing 2.0 by this quantity yields 9.9999999999999995 with a remainder of 0.19999999999999991.</span></span>

<span data-ttu-id="59f70-130">在的運算式中 `decimalRemainder` ，常數值型別字元會 `D` 強制執行這兩個運算元 `Decimal` ，而0.2 具有精確的標記法。</span><span class="sxs-lookup"><span data-stu-id="59f70-130">In the expression for `decimalRemainder`, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span> <span data-ttu-id="59f70-131">因此， `Mod` 運算子會產生預期的餘數0.0。</span><span class="sxs-lookup"><span data-stu-id="59f70-131">Therefore the `Mod` operator yields the expected remainder of 0.0.</span></span>

<span data-ttu-id="59f70-132">請注意，宣告為是不夠的 `decimalRemainder` `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-132">Note that it is not sufficient to declare `decimalRemainder` as `Decimal`.</span></span> <span data-ttu-id="59f70-133">您也必須強制將常值設為 `Decimal` ，或預設為使用， `Double` 並接收與不 `decimalRemainder` 正確的值 `doubleRemainder` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-133">You must also force the literals to `Decimal`, or they use `Double` by default and `decimalRemainder` receives the same inaccurate value as `doubleRemainder`.</span></span>

## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a><span data-ttu-id="59f70-134">布林值類型未正確轉換為數數值型別</span><span class="sxs-lookup"><span data-stu-id="59f70-134">Boolean Type Does Not Convert to Numeric Type Accurately</span></span>

<span data-ttu-id="59f70-135">[布林資料類型](../../../language-reference/data-types/boolean-data-type.md)值不會儲存為數字，而且儲存的值不會等同于數位。</span><span class="sxs-lookup"><span data-stu-id="59f70-135">[Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md) values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="59f70-136">為了與舊版相容，Visual Basic 提供轉換關鍵字（[CType 函數](../../../language-reference/functions/ctype-function.md)、 `CBool` 、等等 `CInt` ）來轉換 `Boolean` 和數數值型別。</span><span class="sxs-lookup"><span data-stu-id="59f70-136">For compatibility with earlier versions, Visual Basic provides conversion keywords ([CType Function](../../../language-reference/functions/ctype-function.md), `CBool`, `CInt`, and so on) to convert between `Boolean` and numeric types.</span></span> <span data-ttu-id="59f70-137">不過，其他語言有時候會以不同的方式執行這些轉換，如同 .NET Framework 方法一樣。</span><span class="sxs-lookup"><span data-stu-id="59f70-137">However, other languages sometimes perform these conversions differently, as do the .NET Framework methods.</span></span>

<span data-ttu-id="59f70-138">您絕對不應該撰寫依賴和的對等數值的程式碼 `True` `False` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-138">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="59f70-139">可能的話，您應該將變數的使用限制 `Boolean` 為其設計的邏輯值。</span><span class="sxs-lookup"><span data-stu-id="59f70-139">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span> <span data-ttu-id="59f70-140">如果您必須混合 `Boolean` 和數值，請確定您瞭解所選取的轉換方法。</span><span class="sxs-lookup"><span data-stu-id="59f70-140">If you must mix `Boolean` and numeric values, make sure that you understand the conversion method that you select.</span></span>

### <a name="conversion-in-visual-basic"></a><span data-ttu-id="59f70-141">Visual Basic 中的轉換</span><span class="sxs-lookup"><span data-stu-id="59f70-141">Conversion in Visual Basic</span></span>

<span data-ttu-id="59f70-142">當您使用 `CType` 或 `CBool` 轉換關鍵字將數值資料類型轉換為時 `Boolean` ，0會變成， `False` 而所有其他值會變成 `True` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-142">When you use the `CType` or `CBool` conversion keywords to convert numeric data types to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="59f70-143">當您 `Boolean` 使用轉換關鍵字將值轉換成數數值型別時， `False` 會變成0，並 `True` 變成-1。</span><span class="sxs-lookup"><span data-stu-id="59f70-143">When you convert `Boolean` values to numeric types by using the conversion keywords, `False` becomes 0 and `True` becomes -1.</span></span>

### <a name="conversion-in-the-framework"></a><span data-ttu-id="59f70-144">架構中的轉換</span><span class="sxs-lookup"><span data-stu-id="59f70-144">Conversion in the Framework</span></span>

<span data-ttu-id="59f70-145"><xref:System.Convert.ToInt32%2A> <xref:System.Convert> 命名空間中類別的方法會 <xref:System> 將轉換 `True` 為 + 1。</span><span class="sxs-lookup"><span data-stu-id="59f70-145">The <xref:System.Convert.ToInt32%2A> method of the <xref:System.Convert> class in the <xref:System> namespace converts `True` to +1.</span></span>

<span data-ttu-id="59f70-146">如果您必須將 `Boolean` 值轉換成數值資料類型，請留意您使用的轉換方法。</span><span class="sxs-lookup"><span data-stu-id="59f70-146">If you must convert a `Boolean` value to a numeric data type, be careful about which conversion method you use.</span></span>

## <a name="character-literal-generates-compiler-error"></a><span data-ttu-id="59f70-147">字元常值會產生編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="59f70-147">Character Literal Generates Compiler Error</span></span>

<span data-ttu-id="59f70-148">如果沒有任何類型字元，Visual Basic 會假設常值的預設資料類型。</span><span class="sxs-lookup"><span data-stu-id="59f70-148">In the absence of any type characters, Visual Basic assumes default data types for literals.</span></span> <span data-ttu-id="59f70-149">字元常值的預設類型（以引號（）括住 `" "` ）為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-149">The default type for a character literal — enclosed in quotation marks (`" "`) — is `String`.</span></span>

<span data-ttu-id="59f70-150">`String`資料類型不會擴展到[Char 資料型別](../../../language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="59f70-150">The `String` data type does not widen to the [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span> <span data-ttu-id="59f70-151">這表示如果您想要將常值指派給 `Char` 變數，則必須進行縮小轉換，或強制將常值設為 `Char` 類型。</span><span class="sxs-lookup"><span data-stu-id="59f70-151">This means that if you want to assign a literal to a `Char` variable, you must either make a narrowing conversion or force the literal to the `Char` type.</span></span>

|<span data-ttu-id="59f70-152">若要建立要指派給變數或常數的 Char 常值</span><span class="sxs-lookup"><span data-stu-id="59f70-152">To create a Char literal to assign to a variable or constant</span></span>|
|---|
|<span data-ttu-id="59f70-153">1. 將變數或常數宣告為 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-153">1.  Declare the variable or constant as `Char`.</span></span><br /><span data-ttu-id="59f70-154">2. 將字元值括在引號中（ `" "` ）。</span><span class="sxs-lookup"><span data-stu-id="59f70-154">2.  Enclose the character value in quotation marks (`" "`).</span></span><br /><span data-ttu-id="59f70-155">3. 在結尾的雙引號後面加上常數值型別字元， `C` 以強制將常值設為 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-155">3.  Follow the closing double quotation mark with the literal type character `C` to force the literal to `Char`.</span></span> <span data-ttu-id="59f70-156">如果類型檢查參數（[Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)）為，則這是必要的 `On` ，而且在任何情況下都是合適的。</span><span class="sxs-lookup"><span data-stu-id="59f70-156">This is necessary if the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `On`, and it is desirable in any case.</span></span>|

<span data-ttu-id="59f70-157">下列範例示範不成功和成功的常值指派至 `Char` 變數。</span><span class="sxs-lookup"><span data-stu-id="59f70-157">The following example demonstrates both unsuccessful and successful assignments of a literal to a `Char` variable.</span></span>

[!code-vb[VbVbalrDataTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#12)]

<span data-ttu-id="59f70-158">使用縮小轉換時，一律會有風險，因為它們可能會在執行時間失敗。</span><span class="sxs-lookup"><span data-stu-id="59f70-158">There is always a risk in using narrowing conversions, because they can fail at run time.</span></span> <span data-ttu-id="59f70-159">例如， `String` `Char` 如果 `String` 值包含一個以上的字元，從到的轉換可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="59f70-159">For example, a conversion from `String` to `Char` can fail if the `String` value contains more than one character.</span></span> <span data-ttu-id="59f70-160">因此，使用類型字元是較佳的程式設計 `C` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-160">Therefore, it is better programming to use the `C` type character.</span></span>

## <a name="string-conversion-fails-at-run-time"></a><span data-ttu-id="59f70-161">字串轉換在執行時間失敗</span><span class="sxs-lookup"><span data-stu-id="59f70-161">String Conversion Fails at Run Time</span></span>

<span data-ttu-id="59f70-162">[String 資料類型](../../../language-reference/data-types/string-data-type.md)只會參與非常少的擴輾轉換。</span><span class="sxs-lookup"><span data-stu-id="59f70-162">The [String Data Type](../../../language-reference/data-types/string-data-type.md) participates in very few widening conversions.</span></span> <span data-ttu-id="59f70-163">`String`只會擴大至本身和 `Object` ，且只有 `Char` 和 `Char()` （ `Char` 陣列）會擴展為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-163">`String` widens only to itself and `Object`, and only `Char` and `Char()` (a `Char` array) widen to `String`.</span></span> <span data-ttu-id="59f70-164">這是因為 `String` 變數和常數可以包含其他資料類型不能包含的值。</span><span class="sxs-lookup"><span data-stu-id="59f70-164">This is because `String` variables and constants can contain values that other data types cannot contain.</span></span>

<span data-ttu-id="59f70-165">當類型檢查參數（[Option Strict 語句](../../../language-reference/statements/option-strict-statement.md)）為時 `On` ，編譯器不允許所有隱含的縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="59f70-165">When the type checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) is `On`, the compiler disallows all implicit narrowing conversions.</span></span> <span data-ttu-id="59f70-166">這包括涉及的相關內容 `String` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-166">This includes those involving `String`.</span></span> <span data-ttu-id="59f70-167">您的程式碼仍然可以使用轉換關鍵字（例如 `CStr` 和[CType](../../../language-reference/functions/ctype-function.md)函式），以指示 .NET Framework 嘗試轉換。</span><span class="sxs-lookup"><span data-stu-id="59f70-167">Your code can still use conversion keywords such as `CStr` and [CType Function](../../../language-reference/functions/ctype-function.md), which direct the .NET Framework to attempt the conversion.</span></span>

> [!NOTE]
> <span data-ttu-id="59f70-168">將集合中的專案轉換 `For Each…Next` 為迴圈控制變數時，會抑制縮小轉換錯誤。</span><span class="sxs-lookup"><span data-stu-id="59f70-168">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="59f70-169">如需詳細資訊和範例，請參閱 For Each ... 中的「縮小轉換」一節。 [下一個語句](../../../language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="59f70-169">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>

### <a name="narrowing-conversion-protection"></a><span data-ttu-id="59f70-170">縮小轉換保護</span><span class="sxs-lookup"><span data-stu-id="59f70-170">Narrowing Conversion Protection</span></span>

<span data-ttu-id="59f70-171">縮小轉換的缺點是它們可能會在執行時間失敗。</span><span class="sxs-lookup"><span data-stu-id="59f70-171">The disadvantage of narrowing conversions is that they can fail at run time.</span></span> <span data-ttu-id="59f70-172">例如，如果 `String` 變數包含 "True" 或 "False" 以外的任何專案，就無法將它轉換成 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-172">For example, if a `String` variable contains anything other than "True" or "False," it cannot be converted to `Boolean`.</span></span> <span data-ttu-id="59f70-173">如果它包含標點符號字元，轉換成任何數數值型別會失敗。</span><span class="sxs-lookup"><span data-stu-id="59f70-173">If it contains punctuation characters, conversion to any numeric type fails.</span></span> <span data-ttu-id="59f70-174">除非您知道 `String` 變數一律保留目的地類型可接受的值，否則您不應該嘗試轉換。</span><span class="sxs-lookup"><span data-stu-id="59f70-174">Unless you know that your `String` variable always holds values that the destination type can accept, you should not try a conversion.</span></span>

<span data-ttu-id="59f70-175">如果您必須從轉換成 `String` 另一種資料類型，最安全的程式是將嘗試的轉換放在[Try .。。Catch .。。Finally 語句](../../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="59f70-175">If you must convert from `String` to another data type, the safest procedure is to enclose the attempted conversion in the [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="59f70-176">這可讓您處理運行時失敗。</span><span class="sxs-lookup"><span data-stu-id="59f70-176">This lets you deal with a run-time failure.</span></span>

### <a name="character-arrays"></a><span data-ttu-id="59f70-177">字元陣列</span><span class="sxs-lookup"><span data-stu-id="59f70-177">Character Arrays</span></span>

<span data-ttu-id="59f70-178">單一 `Char` 和 `Char` 元素陣列都會擴大為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-178">A single `Char` and an array of `Char` elements both widen to `String`.</span></span> <span data-ttu-id="59f70-179">不過，不 `String` 會擴展為 `Char()` 。</span><span class="sxs-lookup"><span data-stu-id="59f70-179">However, `String` does not widen to `Char()`.</span></span> <span data-ttu-id="59f70-180">若要將 `String` 值轉換成 `Char` 陣列，您可以使用 <xref:System.String.ToCharArray%2A> 類別的方法 <xref:System.String?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="59f70-180">To convert a `String` value to a `Char` array, you can use the <xref:System.String.ToCharArray%2A> method of the <xref:System.String?displayProperty=nameWithType> class.</span></span>

### <a name="meaningless-values"></a><span data-ttu-id="59f70-181">無意義的值</span><span class="sxs-lookup"><span data-stu-id="59f70-181">Meaningless Values</span></span>

<span data-ttu-id="59f70-182">一般而言， `String` 值在其他資料類型中沒有意義，而且轉換會具有高度的人工和危險性。</span><span class="sxs-lookup"><span data-stu-id="59f70-182">In general, `String` values are not meaningful in other data types, and conversion is highly artificial and dangerous.</span></span> <span data-ttu-id="59f70-183">可能的話，您應該將變數的使用限制 `String` 為其設計所在的字元序列。</span><span class="sxs-lookup"><span data-stu-id="59f70-183">Whenever possible, you should restrict usage of `String` variables to the character sequences for which they are designed.</span></span> <span data-ttu-id="59f70-184">您絕對不應該撰寫依賴其他類型之對等值的程式碼。</span><span class="sxs-lookup"><span data-stu-id="59f70-184">You should never write code that relies on equivalent values in other types.</span></span>

## <a name="see-also"></a><span data-ttu-id="59f70-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59f70-185">See also</span></span>

- [<span data-ttu-id="59f70-186">資料類型</span><span class="sxs-lookup"><span data-stu-id="59f70-186">Data Types</span></span>](index.md)
- [<span data-ttu-id="59f70-187">類型字元</span><span class="sxs-lookup"><span data-stu-id="59f70-187">Type Characters</span></span>](type-characters.md)
- [<span data-ttu-id="59f70-188">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="59f70-188">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="59f70-189">Visual Basic 中的類型轉換</span><span class="sxs-lookup"><span data-stu-id="59f70-189">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="59f70-190">資料類型</span><span class="sxs-lookup"><span data-stu-id="59f70-190">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="59f70-191">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="59f70-191">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="59f70-192">有效率地使用資料類型</span><span class="sxs-lookup"><span data-stu-id="59f70-192">Efficient Use of Data Types</span></span>](efficient-use-of-data-types.md)
