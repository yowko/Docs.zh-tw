---
title: "疑難排解資料類型 (Visual Basic) |Microsoft 文件"
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
- Char data type, converting
- Decimal data type, conversions
- data types [Visual Basic], troubleshooting
- literals, default types
- type characters, literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types
- floating-point numbers, precision
- Boolean data type, converting
- literal types
- literal type characters
- floating-point numbers, imprecision
- String data type, converting
- floating-point numbers, comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
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
ms.openlocfilehash: 7ac7dfbda8c39024fc0aa07c9830d70b3a566e50
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-data-types-visual-basic"></a><span data-ttu-id="eedc8-102">疑難排解資料類型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eedc8-102">Troubleshooting Data Types (Visual Basic)</span></span>
<span data-ttu-id="eedc8-103">此頁面會列出您的內建函式的資料類型上執行作業時所發生的一些常見問題。</span><span class="sxs-lookup"><span data-stu-id="eedc8-103">This page lists some common problems that can occur when you perform operations on intrinsic data types.</span></span>  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a><span data-ttu-id="eedc8-104">浮點運算式不會比較為相等</span><span class="sxs-lookup"><span data-stu-id="eedc8-104">Floating-Point Expressions Do Not Compare as Equal</span></span>  
 <span data-ttu-id="eedc8-105">當您使用浮點數 ([單一資料型別](../../../../visual-basic/language-reference/data-types/single-data-type.md)和[Double 資料型別](../../../../visual-basic/language-reference/data-types/double-data-type.md))，請記住它們會儲存為二進位分數。</span><span class="sxs-lookup"><span data-stu-id="eedc8-105">When you work with floating-point numbers ([Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) and [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md)), remember that they are stored as binary fractions.</span></span> <span data-ttu-id="eedc8-106">這表示它們不能保存任何不是二進位分數的數量的精確表示 (在表單 k / (2 ^ n) k 和 n 都是整數)。</span><span class="sxs-lookup"><span data-stu-id="eedc8-106">This means they cannot hold an exact representation of any quantity that is not a binary fraction (of the form k / (2 ^ n) where k and n are integers).</span></span> <span data-ttu-id="eedc8-107">例如，0.5 （= 1/2） 和 0.3125 （= 5/16） 可以保留為精確的值，而 0.2 （= 1/5） 和 0.3 （= 3/10） 可以僅為近似值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-107">For example, 0.5 (= 1/2) and 0.3125 (= 5/16) can be held as precise values, whereas 0.2 (= 1/5) and 0.3 (= 3/10) can be only approximations.</span></span>  
  
 <span data-ttu-id="eedc8-108">正因為如此的不精確，當您操作的浮點值不能依賴確切的結果。</span><span class="sxs-lookup"><span data-stu-id="eedc8-108">Because of this imprecision, you cannot rely on exact results when you operate on floating-point values.</span></span> <span data-ttu-id="eedc8-109">特別是，理論上相等的兩個值可能稍有不同的表示法。</span><span class="sxs-lookup"><span data-stu-id="eedc8-109">In particular, two values that are theoretically equal might have slightly different representations.</span></span>  
  
| <span data-ttu-id="eedc8-110">若要比較浮點數量</span><span class="sxs-lookup"><span data-stu-id="eedc8-110">To compare floating-point quantities</span></span> | 
|---| 
|<span data-ttu-id="eedc8-111">1.使用計算差異的絕對值<xref:System.Math.Abs%2A>方法<xref:System.Math>類別<xref:System>命名空間。</xref:System> </xref:System.Math> </xref:System.Math.Abs%2A></span><span class="sxs-lookup"><span data-stu-id="eedc8-111">1.  Calculate the absolute value of their difference by using the <xref:System.Math.Abs%2A> method of the <xref:System.Math> class in the <xref:System> namespace.</span></span><br /><span data-ttu-id="eedc8-112">2.判斷可接受的最大差異，，，您可以考慮將兩個數量視為相等實際上如果差異不大。</span><span class="sxs-lookup"><span data-stu-id="eedc8-112">2.  Determine an acceptable maximum difference, such that you can consider the two quantities to be equal for practical purposes if their difference is no larger.</span></span><br /><span data-ttu-id="eedc8-113">3.比較數值到可接受的差異差異的絕對值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-113">3.  Compare the absolute value of the difference to the acceptable difference.</span></span>|  
  
 <span data-ttu-id="eedc8-114">下列範例會示範兩個不正確且正確比較`Double`值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-114">The following example demonstrates both incorrect and correct comparison of two `Double` values.</span></span>  
  
 <span data-ttu-id="eedc8-115">[!code-vb[VbVbalrDataTypes #&10;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="eedc8-115">[!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]</span></span>  
  
 <span data-ttu-id="eedc8-116">上述範例使用<xref:System.Double.ToString%2A>方法<xref:System.Double>結構，因此它可以指定更好的精確度超過`CStr`關鍵字使用。</xref:System.Double> </xref:System.Double.ToString%2A></span><span class="sxs-lookup"><span data-stu-id="eedc8-116">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better  precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="eedc8-117">預設值是 15 位數，但是"G17"格式將它擴充到 17 位數。</span><span class="sxs-lookup"><span data-stu-id="eedc8-117">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>  
  
## <a name="mod-operator-does-not-return-accurate-result"></a><span data-ttu-id="eedc8-118">Mod 運算子不會傳回精確的結果</span><span class="sxs-lookup"><span data-stu-id="eedc8-118">Mod Operator Does Not Return Accurate Result</span></span>  
 <span data-ttu-id="eedc8-119">由於不精確的浮點的儲存體， [Mod 運算子](../../../../visual-basic/language-reference/operators/mod-operator.md)至少其中一個運算元是浮點數時，會傳回非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="eedc8-119">Because of the imprecision of floating-point storage, the [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md) can return an unexpected result when at least one of the operands is floating-point.</span></span>  
  
 <span data-ttu-id="eedc8-120">[Decimal 資料型別](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)不會使用浮點表示。</span><span class="sxs-lookup"><span data-stu-id="eedc8-120">The [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) does not use floating-point representation.</span></span> <span data-ttu-id="eedc8-121">在不精確的許多數字`Single`和`Double`會完全在`Decimal`（例如 0.2 和 0.3）。</span><span class="sxs-lookup"><span data-stu-id="eedc8-121">Many numbers that are inexact in `Single` and `Double` are exact in `Decimal` (for example 0.2 and 0.3).</span></span> <span data-ttu-id="eedc8-122">雖然算術中更慢`Decimal`比在浮點數，它可能是值得以達到更好的精確度降低效能。</span><span class="sxs-lookup"><span data-stu-id="eedc8-122">Although arithmetic is slower in `Decimal` than in floating-point, it might be worth the performance decrease to achieve better precision.</span></span>  
  
|<span data-ttu-id="eedc8-123">若要尋找浮點數量的整數餘數</span><span class="sxs-lookup"><span data-stu-id="eedc8-123">To find the integer remainder of floating-point quantities</span></span>|  
|---|  
|<span data-ttu-id="eedc8-124">1.宣告變數為`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-124">1.  Declare variables as `Decimal`.</span></span><br /><span data-ttu-id="eedc8-125">2.使用常值類型字元`D`強制常值加入至`Decimal`，萬一它們的值太大`Long`資料型別。</span><span class="sxs-lookup"><span data-stu-id="eedc8-125">2.  Use the literal type character `D` to force literals to `Decimal`, in case their values are too large for the `Long` data type.</span></span>|  
  
 <span data-ttu-id="eedc8-126">下列範例將示範可能會不精確的浮點運算元。</span><span class="sxs-lookup"><span data-stu-id="eedc8-126">The following example demonstrates the potential imprecision of floating-point operands.</span></span>  
  
 <span data-ttu-id="eedc8-127">[!code-vb[VbVbalrDataTypes #&11;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="eedc8-127">[!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]</span></span>  
  
 <span data-ttu-id="eedc8-128">上述範例使用<xref:System.Double.ToString%2A>方法<xref:System.Double>結構，因此它可以指定更好的精確度超過`CStr`關鍵字使用。</xref:System.Double> </xref:System.Double.ToString%2A></span><span class="sxs-lookup"><span data-stu-id="eedc8-128">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="eedc8-129">預設值是 15 位數，但是"G17"格式將它擴充到 17 位數。</span><span class="sxs-lookup"><span data-stu-id="eedc8-129">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>  
  
 <span data-ttu-id="eedc8-130">因為`zeroPointTwo`是`Double`，其值 0.2 是預存值為 0.20000000000000001 無限重複二進位小數。</span><span class="sxs-lookup"><span data-stu-id="eedc8-130">Because `zeroPointTwo` is `Double`, its value for 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="eedc8-131">此數量除以 2.0 會得到 9.9999999999999995 0.19999999999999991 的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="eedc8-131">Dividing 2.0 by this quantity yields 9.9999999999999995 with a remainder of 0.19999999999999991.</span></span>  
  
 <span data-ttu-id="eedc8-132">在運算式中的`decimalRemainder`，常值類型字元`D`強制兩個運算元`Decimal`，0.2 且精確的表示。</span><span class="sxs-lookup"><span data-stu-id="eedc8-132">In the expression for `decimalRemainder`, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span> <span data-ttu-id="eedc8-133">因此`Mod`運算子會產生預期的餘數 0.0。</span><span class="sxs-lookup"><span data-stu-id="eedc8-133">Therefore the `Mod` operator yields the expected remainder of 0.0.</span></span>  
  
 <span data-ttu-id="eedc8-134">請注意，不足夠宣告`decimalRemainder`為`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-134">Note that it is not sufficient to declare `decimalRemainder` as `Decimal`.</span></span> <span data-ttu-id="eedc8-135">您也必須強制常值加入至`Decimal`，或者使用`Double`預設和`decimalRemainder`收到不正確的相同值，做為`doubleRemainder`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-135">You must also force the literals to `Decimal`, or they use `Double` by default and `decimalRemainder` receives the same inaccurate value as `doubleRemainder`.</span></span>  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a><span data-ttu-id="eedc8-136">布林型別不會準確地轉換為數字類型</span><span class="sxs-lookup"><span data-stu-id="eedc8-136">Boolean Type Does Not Convert to Numeric Type Accurately</span></span>  
 <span data-ttu-id="eedc8-137">[布林資料型別](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)值不會儲存成數字，並儲存的值不是數字相等。</span><span class="sxs-lookup"><span data-stu-id="eedc8-137">[Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="eedc8-138">為了與舊版中，相容[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供轉換關鍵字 ([CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)， `CBool`，`CInt`等) 之間進行轉換`Boolean`和數字類型。</span><span class="sxs-lookup"><span data-stu-id="eedc8-138">For compatibility with earlier versions, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] provides conversion keywords ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`, and so on) to convert between `Boolean` and numeric types.</span></span> <span data-ttu-id="eedc8-139">不過，其他語言有時會執行這些轉換以不同的方式，也是如此[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]方法。</span><span class="sxs-lookup"><span data-stu-id="eedc8-139">However, other languages sometimes perform these conversions differently, as do the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] methods.</span></span>  
  
 <span data-ttu-id="eedc8-140">您不需撰寫程式碼所使用的對等數值`True`和`False`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-140">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="eedc8-141">可能的話，您應該限制的使用方式`Boolean`它們專為邏輯值的變數。</span><span class="sxs-lookup"><span data-stu-id="eedc8-141">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span> <span data-ttu-id="eedc8-142">如果您要混合`Boolean`和數字的值，請確定您已了解您所選取的轉換方法。</span><span class="sxs-lookup"><span data-stu-id="eedc8-142">If you must mix `Boolean` and numeric values, make sure that you understand the conversion method that you select.</span></span>  
  
### <a name="conversion-in-visual-basic"></a><span data-ttu-id="eedc8-143">在 Visual Basic 中的轉換</span><span class="sxs-lookup"><span data-stu-id="eedc8-143">Conversion in Visual Basic</span></span>  
 <span data-ttu-id="eedc8-144">當您使用`CType`或`CBool`來轉換數值資料類型以轉換關鍵字`Boolean`，0 會變成`False`和所有其他值會變成`True`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-144">When you use the `CType` or `CBool` conversion keywords to convert numeric data types to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="eedc8-145">當您轉換`Boolean`使用轉換的關鍵字，數字類型的值`False`變成 0 和`True`變成-1。</span><span class="sxs-lookup"><span data-stu-id="eedc8-145">When you convert `Boolean` values to numeric types by using the conversion keywords, `False` becomes 0 and `True` becomes -1.</span></span>  
  
### <a name="conversion-in-the-framework"></a><span data-ttu-id="eedc8-146">Framework 中的轉換</span><span class="sxs-lookup"><span data-stu-id="eedc8-146">Conversion in the Framework</span></span>  
 <span data-ttu-id="eedc8-147"><xref:System.Convert.ToInt32%2A>方法<xref:System.Convert>類別<xref:System>命名空間將轉換`True`到 +&1;。</xref:System> </xref:System.Convert> </xref:System.Convert.ToInt32%2A></span><span class="sxs-lookup"><span data-stu-id="eedc8-147">The <xref:System.Convert.ToInt32%2A> method of the <xref:System.Convert> class in the <xref:System> namespace converts `True` to +1.</span></span>  
  
 <span data-ttu-id="eedc8-148">如果您必須先轉換`Boolean`值設為數值資料類型，請謹慎使用哪一種轉換方法的詳細。</span><span class="sxs-lookup"><span data-stu-id="eedc8-148">If you must convert a `Boolean` value to a numeric data type, be careful about which conversion method you use.</span></span>  
  
## <a name="character-literal-generates-compiler-error"></a><span data-ttu-id="eedc8-149">字元常值會產生編譯器錯誤</span><span class="sxs-lookup"><span data-stu-id="eedc8-149">Character Literal Generates Compiler Error</span></span>  
 <span data-ttu-id="eedc8-150">如果沒有任何型別字元，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]假設預設的常值的資料型別。</span><span class="sxs-lookup"><span data-stu-id="eedc8-150">In the absence of any type characters, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] assumes default data types for literals.</span></span> <span data-ttu-id="eedc8-151">字元常值的預設類型 — 以引號括住 (`" "`) — 是`String`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-151">The default type for a character literal — enclosed in quotation marks (`" "`) — is `String`.</span></span>  
  
 <span data-ttu-id="eedc8-152">`String`資料型別並不會擴展為[Char 資料型別](../../../../visual-basic/language-reference/data-types/char-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="eedc8-152">The `String` data type does not widen to the [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span> <span data-ttu-id="eedc8-153">這表示，如果您想要指派將常值`Char`變數時，您必須進行縮小轉換，或將常值來強制`Char`型別。</span><span class="sxs-lookup"><span data-stu-id="eedc8-153">This means that if you want to assign a literal to a `Char` variable, you must either make a narrowing conversion or force the literal to the `Char` type.</span></span>  

|<span data-ttu-id="eedc8-154">若要建立字元常值指派給變數或常數</span><span class="sxs-lookup"><span data-stu-id="eedc8-154">To create a Char literal to assign to a variable or constant</span></span>|
|---|  
|<span data-ttu-id="eedc8-155">1.宣告變數或常數當作`Char`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-155">1.  Declare the variable or constant as `Char`.</span></span><br /><span data-ttu-id="eedc8-156">2.以引號括住的字元值 (`" "`)。</span><span class="sxs-lookup"><span data-stu-id="eedc8-156">2.  Enclose the character value in quotation marks (`" "`).</span></span><br /><span data-ttu-id="eedc8-157">3.請遵循右雙引號常值型別字元`C`強制常值，以便`Char`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-157">3.  Follow the closing double quotation mark with the literal type character `C` to force the literal to `Char`.</span></span> <span data-ttu-id="eedc8-158">這是必要的型別檢查切換 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`，這時就在任何情況下。</span><span class="sxs-lookup"><span data-stu-id="eedc8-158">This is necessary if the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On`, and it is desirable in any case.</span></span>|  
  
 <span data-ttu-id="eedc8-159">下列範例示範將常值的失敗和成功指派`Char`變數。</span><span class="sxs-lookup"><span data-stu-id="eedc8-159">The following example demonstrates both unsuccessful and successful assignments of a literal to a `Char` variable.</span></span>  
  
 <span data-ttu-id="eedc8-160">[!code-vb[VbVbalrDataTypes #&12;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="eedc8-160">[!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]</span></span>  
  
 <span data-ttu-id="eedc8-161">總是有風險使用縮小轉換，因為它們可以在執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="eedc8-161">There is always a risk in using narrowing conversions, because they can fail at run time.</span></span> <span data-ttu-id="eedc8-162">例如，從轉換`String`至`Char`就會失敗`String`值包含多個字元。</span><span class="sxs-lookup"><span data-stu-id="eedc8-162">For example, a conversion from `String` to `Char` can fail if the `String` value contains more than one character.</span></span> <span data-ttu-id="eedc8-163">因此，它進一步撰寫使用`C`輸入字元。</span><span class="sxs-lookup"><span data-stu-id="eedc8-163">Therefore, it is better programming to use the `C` type character.</span></span>  
  
## <a name="string-conversion-fails-at-run-time"></a><span data-ttu-id="eedc8-164">字串轉換在執行階段失敗</span><span class="sxs-lookup"><span data-stu-id="eedc8-164">String Conversion Fails at Run Time</span></span>  
 <span data-ttu-id="eedc8-165">[字串資料型別](../../../../visual-basic/language-reference/data-types/string-data-type.md)參與很少的擴展轉換。</span><span class="sxs-lookup"><span data-stu-id="eedc8-165">The [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) participates in very few widening conversions.</span></span> <span data-ttu-id="eedc8-166">`String`擴展至本身只和`Object`，而且只有`Char`和`Char()`(`Char`陣列) 擴展為`String`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-166">`String` widens only to itself and `Object`, and only `Char` and `Char()` (a `Char` array) widen to `String`.</span></span> <span data-ttu-id="eedc8-167">這是因為`String`變數和常數可以包含其他資料型別不能包含的值。</span><span class="sxs-lookup"><span data-stu-id="eedc8-167">This is because `String` variables and constants can contain values that other data types cannot contain.</span></span>  
  
 <span data-ttu-id="eedc8-168">當型別檢查切換 ([Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) 是`On`，編譯器不允許所有隱含的縮小轉換。</span><span class="sxs-lookup"><span data-stu-id="eedc8-168">When the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On`, the compiler disallows all implicit narrowing conversions.</span></span> <span data-ttu-id="eedc8-169">這包括涉及`String`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-169">This includes those involving `String`.</span></span> <span data-ttu-id="eedc8-170">您的程式碼仍然可以使用轉換關鍵字例如`CStr`和[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)，哪些直接[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]嘗試轉換。</span><span class="sxs-lookup"><span data-stu-id="eedc8-170">Your code can still use conversion keywords such as `CStr` and [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md), which direct the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] to attempt the conversion.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eedc8-171">轉換中的項目會隱藏縮小轉換錯誤`For Each…Next`迴圈控制變數的集合。</span><span class="sxs-lookup"><span data-stu-id="eedc8-171">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="eedc8-172">如需詳細資訊和範例，請參閱 「 縮小轉換 」 一節[每個...下一個陳述式](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eedc8-172">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="narrowing-conversion-protection"></a><span data-ttu-id="eedc8-173">縮小轉換保護</span><span class="sxs-lookup"><span data-stu-id="eedc8-173">Narrowing Conversion Protection</span></span>  
 <span data-ttu-id="eedc8-174">縮小轉換的缺點是它們可以在執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="eedc8-174">The disadvantage of narrowing conversions is that they can fail at run time.</span></span> <span data-ttu-id="eedc8-175">例如，如果`String`變數包含任何項目不是"True"或"False，"無法轉換成`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-175">For example, if a `String` variable contains anything other than "True" or "False," it cannot be converted to `Boolean`.</span></span> <span data-ttu-id="eedc8-176">如果它包含標點符號字元，則任何數值類型的轉換會失敗。</span><span class="sxs-lookup"><span data-stu-id="eedc8-176">If it contains punctuation characters, conversion to any numeric type fails.</span></span> <span data-ttu-id="eedc8-177">除非您知道您`String`變數一律會保留在目的型別可接受的值，您不應該嘗試轉換。</span><span class="sxs-lookup"><span data-stu-id="eedc8-177">Unless you know that your `String` variable always holds values that the destination type can accept, you should not try a conversion.</span></span>  
  
 <span data-ttu-id="eedc8-178">如果您必須將`String`最安全的程序是來括住中的嘗試的轉換成其他資料類型，[試...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="eedc8-178">If you must convert from `String` to another data type, the safest procedure is to enclose the attempted conversion in the [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="eedc8-179">這可讓您處理執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="eedc8-179">This lets you deal with a run-time failure.</span></span>  
  
### <a name="character-arrays"></a><span data-ttu-id="eedc8-180">字元陣列</span><span class="sxs-lookup"><span data-stu-id="eedc8-180">Character Arrays</span></span>  
 <span data-ttu-id="eedc8-181">單一`Char`和陣列`Char`項目同時擴展為`String`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-181">A single `Char` and an array of `Char` elements both widen to `String`.</span></span> <span data-ttu-id="eedc8-182">不過，`String`並不會擴展為`Char()`。</span><span class="sxs-lookup"><span data-stu-id="eedc8-182">However, `String` does not widen to `Char()`.</span></span> <span data-ttu-id="eedc8-183">要轉換`String`值`Char`陣列，您可以使用<xref:System.String.ToCharArray%2A>方法的<xref:System.String?displayProperty=fullName>類別。</xref:System.String?displayProperty=fullName> </xref:System.String.ToCharArray%2A></span><span class="sxs-lookup"><span data-stu-id="eedc8-183">To convert a `String` value to a `Char` array, you can use the <xref:System.String.ToCharArray%2A> method of the <xref:System.String?displayProperty=fullName> class.</span></span>  
  
### <a name="meaningless-values"></a><span data-ttu-id="eedc8-184">無意義的值</span><span class="sxs-lookup"><span data-stu-id="eedc8-184">Meaningless Values</span></span>  
 <span data-ttu-id="eedc8-185">一般而言，`String`值不在其他資料類型的意義，而且轉換會相當麻煩且危險。</span><span class="sxs-lookup"><span data-stu-id="eedc8-185">In general, `String` values are not meaningful in other data types, and conversion is highly artificial and dangerous.</span></span> <span data-ttu-id="eedc8-186">可能的話，您應該限制的使用方式`String`變數，它們設計的字元序列。</span><span class="sxs-lookup"><span data-stu-id="eedc8-186">Whenever possible, you should restrict usage of `String` variables to the character sequences for which they are designed.</span></span> <span data-ttu-id="eedc8-187">您不需撰寫程式碼所使用的其他型別的值相等。</span><span class="sxs-lookup"><span data-stu-id="eedc8-187">You should never write code that relies on equivalent values in other types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eedc8-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eedc8-188">See Also</span></span>  
 <span data-ttu-id="eedc8-189">[資料型別](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="eedc8-189">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="eedc8-190"> [類型字元](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="eedc8-190"> [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
<span data-ttu-id="eedc8-191"> [實值型別和參考型別](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="eedc8-191"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="eedc8-192"> [在 Visual Basic 中的型別轉換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="eedc8-192"> [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="eedc8-193"> [資料型別](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="eedc8-193"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="eedc8-194"> [類型轉換函式](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="eedc8-194"> [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="eedc8-195"> [有效率地使用資料類型](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="eedc8-195"> [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)</span></span>
