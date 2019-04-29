---
title: + 運算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 4fc8ce96caea436b63fe346139e27ec8dd048f10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778601"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="99da4-102">+ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99da4-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="99da4-103">兩個數字相加，或傳回數值運算式的正值。</span><span class="sxs-lookup"><span data-stu-id="99da4-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="99da4-104">也可以用來串連兩個字串運算式。</span><span class="sxs-lookup"><span data-stu-id="99da4-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99da4-105">語法</span><span class="sxs-lookup"><span data-stu-id="99da4-105">Syntax</span></span>  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="99da4-106">組件</span><span class="sxs-lookup"><span data-stu-id="99da4-106">Parts</span></span>  
  
|<span data-ttu-id="99da4-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="99da4-107">Term</span></span>|<span data-ttu-id="99da4-108">定義</span><span class="sxs-lookup"><span data-stu-id="99da4-108">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="99da4-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="99da4-109">Required.</span></span> <span data-ttu-id="99da4-110">任何數值或字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="99da4-110">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="99da4-111">除非`+`運算子會計算為負數值。</span><span class="sxs-lookup"><span data-stu-id="99da4-111">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="99da4-112">任何數值或字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="99da4-112">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="99da4-113">結果</span><span class="sxs-lookup"><span data-stu-id="99da4-113">Result</span></span>  
 <span data-ttu-id="99da4-114">如果`expression1`和`expression2`兩者都是數值，結果就是其算術的總和。</span><span class="sxs-lookup"><span data-stu-id="99da4-114">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="99da4-115">如果`expression2`不存在，`+`運算子*一元*身分識別操作員未變更值的運算式。</span><span class="sxs-lookup"><span data-stu-id="99da4-115">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="99da4-116">在這種情況下，作業會組成保留正負號的`expression1`，結果為負的因此如果`expression1`為負數。</span><span class="sxs-lookup"><span data-stu-id="99da4-116">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="99da4-117">如果`expression1`和`expression2`都是字串，結果就是其值的串連。</span><span class="sxs-lookup"><span data-stu-id="99da4-117">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="99da4-118">如果`expression1`並`expression2`是混合的類型，所採取的動作取決於其類型、 其內容，以及設定[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="99da4-118">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="99da4-119">如需詳細資訊，請參閱 < 備註 >。 中的資料表</span><span class="sxs-lookup"><span data-stu-id="99da4-119">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="99da4-120">支援的型別</span><span class="sxs-lookup"><span data-stu-id="99da4-120">Supported Types</span></span>  
 <span data-ttu-id="99da4-121">所有的數字類型，包括不帶正負號和浮點類型和`Decimal`，和`String`。</span><span class="sxs-lookup"><span data-stu-id="99da4-121">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99da4-122">備註</span><span class="sxs-lookup"><span data-stu-id="99da4-122">Remarks</span></span>  
 <span data-ttu-id="99da4-123">一般情況下，`+`執行算術加法，如果可能的話，並串連僅當這兩個運算式都是字串。</span><span class="sxs-lookup"><span data-stu-id="99da4-123">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="99da4-124">如果兩個運算式是`Object`，Visual Basic 會採取下列動作。</span><span class="sxs-lookup"><span data-stu-id="99da4-124">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="99da4-125">資料類型的運算式</span><span class="sxs-lookup"><span data-stu-id="99da4-125">Data types of expressions</span></span>|<span data-ttu-id="99da4-126">編譯器的動作</span><span class="sxs-lookup"><span data-stu-id="99da4-126">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="99da4-127">這兩個運算式都是數值資料類型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，或`Double`)</span><span class="sxs-lookup"><span data-stu-id="99da4-127">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="99da4-128">新增。</span><span class="sxs-lookup"><span data-stu-id="99da4-128">Add.</span></span> <span data-ttu-id="99da4-129">將結果資料類型是數值類型適合的資料型別`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="99da4-129">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="99da4-130">請參閱中的 「 整數算術 」 表格[資料類型的運算子結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="99da4-130">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="99da4-131">這兩個運算式屬於類型 `String`</span><span class="sxs-lookup"><span data-stu-id="99da4-131">Both expressions are of type `String`</span></span>|<span data-ttu-id="99da4-132">串連。</span><span class="sxs-lookup"><span data-stu-id="99da4-132">Concatenate.</span></span>|  
|<span data-ttu-id="99da4-133">一個運算式為數值資料類型，另一個是字串</span><span class="sxs-lookup"><span data-stu-id="99da4-133">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="99da4-134">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="99da4-134">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="99da4-135">如果`Option Strict`是`Off`，然後以隱含方式轉換`String`到`Double`並新增。</span><span class="sxs-lookup"><span data-stu-id="99da4-135">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="99da4-136">如果`String`無法轉換成`Double`，然後擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99da4-136">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="99da4-137">一個運算式為數值資料類型，而另一個是[Nothing](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="99da4-137">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="99da4-138">新增，請使用`Nothing`值為零。</span><span class="sxs-lookup"><span data-stu-id="99da4-138">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="99da4-139">一個運算式是字串，而且另一個則是 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="99da4-139">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="99da4-140">串連，與`Nothing`值為""。</span><span class="sxs-lookup"><span data-stu-id="99da4-140">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="99da4-141">如果一個運算式`Object`運算式中，Visual Basic 會採取下列動作。</span><span class="sxs-lookup"><span data-stu-id="99da4-141">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="99da4-142">資料類型的運算式</span><span class="sxs-lookup"><span data-stu-id="99da4-142">Data types of expressions</span></span>|<span data-ttu-id="99da4-143">編譯器的動作</span><span class="sxs-lookup"><span data-stu-id="99da4-143">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="99da4-144">`Object` 運算式包含數值，另一個是數值資料類型</span><span class="sxs-lookup"><span data-stu-id="99da4-144">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="99da4-145">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="99da4-145">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="99da4-146">如果`Option Strict`是`Off`，然後新增。</span><span class="sxs-lookup"><span data-stu-id="99da4-146">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="99da4-147">`Object` 運算式會保留一個數字值，另一個是類型 `String`</span><span class="sxs-lookup"><span data-stu-id="99da4-147">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="99da4-148">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="99da4-148">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="99da4-149">如果`Option Strict`是`Off`，然後以隱含方式轉換`String`到`Double`並新增。</span><span class="sxs-lookup"><span data-stu-id="99da4-149">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="99da4-150">如果`String`無法轉換成`Double`，然後擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99da4-150">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="99da4-151">`Object` 運算式會保留為字串，另一個是數值資料類型</span><span class="sxs-lookup"><span data-stu-id="99da4-151">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="99da4-152">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="99da4-152">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="99da4-153">如果`Option Strict`是`Off`，然後以隱含方式將字串轉換`Object`到`Double`並新增。</span><span class="sxs-lookup"><span data-stu-id="99da4-153">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="99da4-154">如果字串`Object`無法轉換成`Double`，然後擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99da4-154">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="99da4-155">`Object` 運算式會保留為字串，另一個是類型 `String`</span><span class="sxs-lookup"><span data-stu-id="99da4-155">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="99da4-156">如果`Option Strict`是`On`，然後產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="99da4-156">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="99da4-157">如果`Option Strict`是`Off`，然後以隱含方式轉換`Object`到`String`和串連。</span><span class="sxs-lookup"><span data-stu-id="99da4-157">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="99da4-158">如果這兩個運算式都`Object`運算式，Visual Basic 會採取下列動作 (`Option Strict Off`只)。</span><span class="sxs-lookup"><span data-stu-id="99da4-158">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="99da4-159">資料類型的運算式</span><span class="sxs-lookup"><span data-stu-id="99da4-159">Data types of expressions</span></span>|<span data-ttu-id="99da4-160">編譯器的動作</span><span class="sxs-lookup"><span data-stu-id="99da4-160">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="99da4-161">兩者`Object`運算式保存數值</span><span class="sxs-lookup"><span data-stu-id="99da4-161">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="99da4-162">新增。</span><span class="sxs-lookup"><span data-stu-id="99da4-162">Add.</span></span>|  
|<span data-ttu-id="99da4-163">兩者`Object`運算式屬於類型 `String`</span><span class="sxs-lookup"><span data-stu-id="99da4-163">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="99da4-164">串連。</span><span class="sxs-lookup"><span data-stu-id="99da4-164">Concatenate.</span></span>|  
|<span data-ttu-id="99da4-165">一個`Object`運算式包含數值，而其他則會保留字串</span><span class="sxs-lookup"><span data-stu-id="99da4-165">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="99da4-166">將字串隱含轉換`Object`至`Double`並新增。</span><span class="sxs-lookup"><span data-stu-id="99da4-166">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="99da4-167">如果字串`Object`無法轉換成數值，則會擲回<xref:System.InvalidCastException>例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99da4-167">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="99da4-168">如果有任一個`Object`運算式會評估為[Nothing](../../../visual-basic/language-reference/nothing.md)或<xref:System.DBNull>，則`+`運算子會將其視為`String`值是""。</span><span class="sxs-lookup"><span data-stu-id="99da4-168">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99da4-169">當您使用`+`運算子，可能無法判斷是否會發生加法或字串的串連。</span><span class="sxs-lookup"><span data-stu-id="99da4-169">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="99da4-170">使用`&`運算子串連消除模稜兩可，並提供自我記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="99da4-170">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="99da4-171">多載化</span><span class="sxs-lookup"><span data-stu-id="99da4-171">Overloading</span></span>  
 <span data-ttu-id="99da4-172">`+`運算子只能*多載*，這表示，類別或結構可以重新定義其行為時運算元具有該類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="99da4-172">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="99da4-173">如果您的程式碼會使用這個運算子，這類類別或結構上，請務必了解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="99da4-173">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="99da4-174">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="99da4-174">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99da4-175">範例</span><span class="sxs-lookup"><span data-stu-id="99da4-175">Example</span></span>  
 <span data-ttu-id="99da4-176">下列範例會使用`+`運算子，將數字。</span><span class="sxs-lookup"><span data-stu-id="99da4-176">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="99da4-177">如果運算元是數字的同時，Visual Basic 會計算算術的結果。</span><span class="sxs-lookup"><span data-stu-id="99da4-177">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="99da4-178">算術的結果表示兩個運算元的總和。</span><span class="sxs-lookup"><span data-stu-id="99da4-178">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="99da4-179">您也可以使用`+`運算子來串連字串。</span><span class="sxs-lookup"><span data-stu-id="99da4-179">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="99da4-180">如果運算元都是字串，Visual Basic 會串連它們。</span><span class="sxs-lookup"><span data-stu-id="99da4-180">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="99da4-181">串連結果代表接續所組成的兩個運算元其中一個內容的單一字串。</span><span class="sxs-lookup"><span data-stu-id="99da4-181">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="99da4-182">如果混合類型的運算元，結果會取決於設定[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="99da4-182">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="99da4-183">下列範例說明結果時`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="99da4-183">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="99da4-184">下列範例說明結果時`Option Strict`是`Off`。</span><span class="sxs-lookup"><span data-stu-id="99da4-184">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="99da4-185">若要避免模稜兩可，您應該使用`&`運算子來取代`+`串連。</span><span class="sxs-lookup"><span data-stu-id="99da4-185">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99da4-186">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99da4-186">See also</span></span>

- [<span data-ttu-id="99da4-187">& 運算子</span><span class="sxs-lookup"><span data-stu-id="99da4-187">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="99da4-188">串連運算子</span><span class="sxs-lookup"><span data-stu-id="99da4-188">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="99da4-189">算術運算子</span><span class="sxs-lookup"><span data-stu-id="99da4-189">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="99da4-190">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="99da4-190">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="99da4-191">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="99da4-191">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="99da4-192">在 Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="99da4-192">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="99da4-193">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="99da4-193">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
