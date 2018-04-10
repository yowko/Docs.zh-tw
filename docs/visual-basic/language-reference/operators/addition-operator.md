---
title: + 運算子 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb0d66db2d777c046ccec69acc1f2069d21baf6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="7e7b1-102">+ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e7b1-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="7e7b1-103">兩個數字相加或傳回數值運算式的正值。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="7e7b1-104">也可以用來串連兩個字串運算式。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e7b1-105">語法</span><span class="sxs-lookup"><span data-stu-id="7e7b1-105">Syntax</span></span>  
  
```  
      expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="7e7b1-106">組件</span><span class="sxs-lookup"><span data-stu-id="7e7b1-106">Parts</span></span>  
  
|<span data-ttu-id="7e7b1-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="7e7b1-107">Term</span></span>|<span data-ttu-id="7e7b1-108">定義</span><span class="sxs-lookup"><span data-stu-id="7e7b1-108">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="7e7b1-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-109">Required.</span></span> <span data-ttu-id="7e7b1-110">任何數值或字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-110">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="7e7b1-111">除非`+`運算子會計算為負值。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-111">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="7e7b1-112">任何數值或字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-112">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="7e7b1-113">結果</span><span class="sxs-lookup"><span data-stu-id="7e7b1-113">Result</span></span>  
 <span data-ttu-id="7e7b1-114">如果`expression1`和`expression2`都是數值，則結果會是其算術的總和。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-114">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="7e7b1-115">如果`expression2`不存在，`+`運算子是*一元*未變更的運算式值的相同比較運算子。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-115">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="7e7b1-116">就這個意義而言，作業會組成保留正負號的`expression1`，所以結果為負如果`expression1`為負數。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-116">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="7e7b1-117">如果`expression1`和`expression2`都是字串，其值的串連後得出結果。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-117">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="7e7b1-118">如果`expression1`和`expression2`是混合的類型，所採取的動作取決於其類型、 其內容，以及設定[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-118">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="7e7b1-119">如需詳細資訊，請參閱 < 備註 >。 中的資料表</span><span class="sxs-lookup"><span data-stu-id="7e7b1-119">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="7e7b1-120">支援的型別</span><span class="sxs-lookup"><span data-stu-id="7e7b1-120">Supported Types</span></span>  
 <span data-ttu-id="7e7b1-121">所有數字類型，包括不帶正負號和浮點類型和`Decimal`，和`String`。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-121">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e7b1-122">備註</span><span class="sxs-lookup"><span data-stu-id="7e7b1-122">Remarks</span></span>  
 <span data-ttu-id="7e7b1-123">一般情況下，`+`執行算術加法，如果可能的話，然後將串連只有當這兩個運算式都是字串。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-123">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="7e7b1-124">如果兩個運算式是`Object`，Visual Basic 會採取下列動作。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-124">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="7e7b1-125">資料類型的運算式</span><span class="sxs-lookup"><span data-stu-id="7e7b1-125">Data types of expressions</span></span>|<span data-ttu-id="7e7b1-126">編譯器的動作</span><span class="sxs-lookup"><span data-stu-id="7e7b1-126">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="7e7b1-127">這兩個運算式都是數值資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，或`Double`)</span><span class="sxs-lookup"><span data-stu-id="7e7b1-127">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="7e7b1-128">加入。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-128">Add.</span></span> <span data-ttu-id="7e7b1-129">結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-129">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="7e7b1-130">請參閱中的 「 整數算術 」 資料表[運算子結果的資料類型的](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-130">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="7e7b1-131">這兩個運算式都是類型`String`</span><span class="sxs-lookup"><span data-stu-id="7e7b1-131">Both expressions are of type `String`</span></span>|<span data-ttu-id="7e7b1-132">串連。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-132">Concatenate.</span></span>|  
|<span data-ttu-id="7e7b1-133">一個運算式為數值資料類型，另一個是字串</span><span class="sxs-lookup"><span data-stu-id="7e7b1-133">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="7e7b1-134">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-134">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="7e7b1-135">如果`Option Strict`是`Off`，隱含地轉換`String`至`Double`並加入。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-135">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="7e7b1-136">如果`String`無法轉換成`Double`，就會擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-136">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="7e7b1-137">一個運算式是數值資料類型，而另一個方法是[做任何動作](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="7e7b1-137">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="7e7b1-138">新增，請使用`Nothing`值為零。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-138">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="7e7b1-139">一個運算式是字串，而且另一個方法是`Nothing`</span><span class="sxs-lookup"><span data-stu-id="7e7b1-139">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="7e7b1-140">串連與`Nothing`值為""。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-140">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="7e7b1-141">如果一個運算式為`Object`運算式中，Visual Basic 會採取下列動作。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-141">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="7e7b1-142">資料類型的運算式</span><span class="sxs-lookup"><span data-stu-id="7e7b1-142">Data types of expressions</span></span>|<span data-ttu-id="7e7b1-143">編譯器的動作</span><span class="sxs-lookup"><span data-stu-id="7e7b1-143">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="7e7b1-144">`Object`運算式會保留一個數字值，另一個是數值資料類型</span><span class="sxs-lookup"><span data-stu-id="7e7b1-144">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="7e7b1-145">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-145">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="7e7b1-146">如果`Option Strict`是`Off`，然後加入。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-146">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="7e7b1-147">`Object`運算式會保留一個數字值，另一個是型別`String`</span><span class="sxs-lookup"><span data-stu-id="7e7b1-147">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="7e7b1-148">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-148">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="7e7b1-149">如果`Option Strict`是`Off`，隱含地轉換`String`至`Double`並加入。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-149">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="7e7b1-150">如果`String`無法轉換成`Double`，就會擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-150">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="7e7b1-151">`Object`運算式會保留一個字串，另一個是數值資料類型</span><span class="sxs-lookup"><span data-stu-id="7e7b1-151">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="7e7b1-152">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-152">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="7e7b1-153">如果`Option Strict`是`Off`，隱含地轉換字串`Object`至`Double`並加入。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-153">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="7e7b1-154">如果字串`Object`無法轉換成`Double`，就會擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-154">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="7e7b1-155">`Object`運算式會保留一個字串，另一個是型別`String`</span><span class="sxs-lookup"><span data-stu-id="7e7b1-155">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="7e7b1-156">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-156">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="7e7b1-157">如果`Option Strict`是`Off`，隱含地轉換`Object`至`String`處理並串連。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-157">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="7e7b1-158">如果這兩個運算式都是`Object`運算式中，Visual Basic 會採取下列動作 (`Option Strict Off`只)。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-158">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="7e7b1-159">資料類型的運算式</span><span class="sxs-lookup"><span data-stu-id="7e7b1-159">Data types of expressions</span></span>|<span data-ttu-id="7e7b1-160">編譯器的動作</span><span class="sxs-lookup"><span data-stu-id="7e7b1-160">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="7e7b1-161">同時`Object`運算式保存數值</span><span class="sxs-lookup"><span data-stu-id="7e7b1-161">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="7e7b1-162">加入。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-162">Add.</span></span>|  
|<span data-ttu-id="7e7b1-163">同時`Object`運算式屬於類型`String`</span><span class="sxs-lookup"><span data-stu-id="7e7b1-163">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="7e7b1-164">串連。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-164">Concatenate.</span></span>|  
|<span data-ttu-id="7e7b1-165">一個`Object`運算式會保留一個數字值，其他保留字串</span><span class="sxs-lookup"><span data-stu-id="7e7b1-165">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="7e7b1-166">將字串隱含轉換`Object`至`Double`並加入。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-166">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="7e7b1-167">如果字串`Object`無法轉換成數值，則會擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-167">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="7e7b1-168">如果`Object`運算式評估為[Nothing](../../../visual-basic/language-reference/nothing.md)或<xref:System.DBNull>、`+`運算子會將它視為`String`值是""。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-168">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e7b1-169">當您使用`+`運算子，可能無法判斷發生加法或字串串連。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-169">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="7e7b1-170">使用`&`運算子串連避免模稜兩可，以及提供自我記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-170">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="7e7b1-171">多載化</span><span class="sxs-lookup"><span data-stu-id="7e7b1-171">Overloading</span></span>  
 <span data-ttu-id="7e7b1-172">`+`運算子可以是*多載*，這表示，類別或結構可以重新定義它的行為時的運算元有該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-172">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7e7b1-173">如果您的程式碼會使用此運算子，這類類別或結構上，請確定您了解其重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-173">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7e7b1-174">如需詳細資訊，請參閱[運算子程序](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-174">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e7b1-175">範例</span><span class="sxs-lookup"><span data-stu-id="7e7b1-175">Example</span></span>  
 <span data-ttu-id="7e7b1-176">下列範例會使用`+`運算子，將數字。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-176">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="7e7b1-177">如果運算元都是數字的同時，Visual Basic 會計算算術的結果。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-177">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="7e7b1-178">算術結果代表兩個運算元的總和。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-178">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_1.vb)]  
  
 <span data-ttu-id="7e7b1-179">您也可以使用`+`運算子來串連字串。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-179">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="7e7b1-180">如果運算元都是字串，Visual Basic 將它們串連。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-180">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="7e7b1-181">串連結果代表之後的其他內容的兩個運算元一個組成的單一字串。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-181">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="7e7b1-182">如果運算元都是混合型別，結果會隨著設定[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-182">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="7e7b1-183">下列範例說明結果時`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-183">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_2.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#51](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_4.vb)]  
  
 <span data-ttu-id="7e7b1-184">下列範例說明結果時`Option Strict`是`Off`。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-184">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_5.vb)]  
  
 [!code-vb[VbVbalrOperators#50](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_3.vb)]  
[!code-vb[VbVbalrOperators#52](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-operator_6.vb)]  
  
 <span data-ttu-id="7e7b1-185">若要避免模稜兩可，您應該使用`&`運算子，而不是`+`串連。</span><span class="sxs-lookup"><span data-stu-id="7e7b1-185">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7b1-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e7b1-186">See Also</span></span>  
 [<span data-ttu-id="7e7b1-187">& 運算子</span><span class="sxs-lookup"><span data-stu-id="7e7b1-187">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="7e7b1-188">串連運算子</span><span class="sxs-lookup"><span data-stu-id="7e7b1-188">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="7e7b1-189">算術運算子</span><span class="sxs-lookup"><span data-stu-id="7e7b1-189">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="7e7b1-190">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="7e7b1-190">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="7e7b1-191">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="7e7b1-191">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="7e7b1-192">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="7e7b1-192">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="7e7b1-193">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="7e7b1-193">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
