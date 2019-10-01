---
title: + 運算子（Visual Basic）
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
ms.openlocfilehash: 3187551afb7d25470f48dad894188766a811bb0a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701003"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="5f115-102">+ 運算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f115-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="5f115-103">將兩個數字相加，或傳回數值運算式的正數值。</span><span class="sxs-lookup"><span data-stu-id="5f115-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="5f115-104">也可以用來串連兩個字串運算式。</span><span class="sxs-lookup"><span data-stu-id="5f115-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f115-105">語法</span><span class="sxs-lookup"><span data-stu-id="5f115-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="5f115-106">或</span><span class="sxs-lookup"><span data-stu-id="5f115-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="5f115-107">組件</span><span class="sxs-lookup"><span data-stu-id="5f115-107">Parts</span></span>  
  
|<span data-ttu-id="5f115-108">詞彙</span><span class="sxs-lookup"><span data-stu-id="5f115-108">Term</span></span>|<span data-ttu-id="5f115-109">定義</span><span class="sxs-lookup"><span data-stu-id="5f115-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="5f115-110">必要項。</span><span class="sxs-lookup"><span data-stu-id="5f115-110">Required.</span></span> <span data-ttu-id="5f115-111">任何數值或字串運算式。</span><span class="sxs-lookup"><span data-stu-id="5f115-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="5f115-112">除非`+`運算子正在計算負數值，否則為必要。</span><span class="sxs-lookup"><span data-stu-id="5f115-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="5f115-113">任何數值或字串運算式。</span><span class="sxs-lookup"><span data-stu-id="5f115-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="5f115-114">結果</span><span class="sxs-lookup"><span data-stu-id="5f115-114">Result</span></span>  
 <span data-ttu-id="5f115-115">如果`expression1` 和`expression2`都是數值，則結果會是其算術總和。</span><span class="sxs-lookup"><span data-stu-id="5f115-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="5f115-116">如果 `expression2` 不存在，則 `+` 運算子是運算式未變更值的*一元*識別運算子。</span><span class="sxs-lookup"><span data-stu-id="5f115-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="5f115-117">就這一點而言，此作業包含保留的正負號`expression1`，因此如果`expression1`為負數，則結果為負數。</span><span class="sxs-lookup"><span data-stu-id="5f115-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="5f115-118">如果`expression1` 和`expression2`都是字串，則結果會是其值的串連。</span><span class="sxs-lookup"><span data-stu-id="5f115-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="5f115-119">如果 `expression1`，而 `expression2` 是混合類型，則採取的動作取決於其類型、其內容，以及[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)的設定。</span><span class="sxs-lookup"><span data-stu-id="5f115-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="5f115-120">如需詳細資訊，請參閱「備註」中的表格。</span><span class="sxs-lookup"><span data-stu-id="5f115-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="5f115-121">支援的型別</span><span class="sxs-lookup"><span data-stu-id="5f115-121">Supported Types</span></span>  
 <span data-ttu-id="5f115-122">所有數數值型別，包括不帶正負號的和浮點類型`Decimal`，以及`String`和。</span><span class="sxs-lookup"><span data-stu-id="5f115-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f115-123">備註</span><span class="sxs-lookup"><span data-stu-id="5f115-123">Remarks</span></span>  
 <span data-ttu-id="5f115-124">一般來說， `+`會在可能的情況下執行算術加法，而且只有在兩個運算式都是字串時，才會串連。</span><span class="sxs-lookup"><span data-stu-id="5f115-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="5f115-125">如果兩個運算式都`Object`不是，Visual Basic 會採取下列動作。</span><span class="sxs-lookup"><span data-stu-id="5f115-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="5f115-126">運算式的資料類型</span><span class="sxs-lookup"><span data-stu-id="5f115-126">Data types of expressions</span></span>|<span data-ttu-id="5f115-127">由編譯器執行的動作</span><span class="sxs-lookup"><span data-stu-id="5f115-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="5f115-128">這兩個運算式都是數值`SByte`資料`Byte`類型（ `UShort`、 `Integer` `ULong` `UInteger` `Short` 、、`Single`、、 `Decimal` 、、`Double`、、或） `Long`</span><span class="sxs-lookup"><span data-stu-id="5f115-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="5f115-129">載入.</span><span class="sxs-lookup"><span data-stu-id="5f115-129">Add.</span></span> <span data-ttu-id="5f115-130">結果資料類型是適用于和`expression1` `expression2`之資料類型的數數值型別。</span><span class="sxs-lookup"><span data-stu-id="5f115-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="5f115-131">請參閱[運算子結果的資料類型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)中的「整數算術」資料表。</span><span class="sxs-lookup"><span data-stu-id="5f115-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="5f115-132">這兩個運算式的類型都是`String`</span><span class="sxs-lookup"><span data-stu-id="5f115-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="5f115-133">串連.</span><span class="sxs-lookup"><span data-stu-id="5f115-133">Concatenate.</span></span>|  
|<span data-ttu-id="5f115-134">一個運算式是數值資料類型，另一個則是字串</span><span class="sxs-lookup"><span data-stu-id="5f115-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="5f115-135">如果`Option Strict`為`On`，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f115-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5f115-136">如果`Option Strict`為`Off` ，`Double`則會隱含地將轉換成並加入。`String`</span><span class="sxs-lookup"><span data-stu-id="5f115-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="5f115-137">如果無法轉換成`Double`，則會擲<xref:System.InvalidCastException>回例外狀況。 `String`</span><span class="sxs-lookup"><span data-stu-id="5f115-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="5f115-138">一個運算式是數值資料類型，另一個則不是[任何](../../../visual-basic/language-reference/nothing.md)值</span><span class="sxs-lookup"><span data-stu-id="5f115-138">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="5f115-139">加入，其`Nothing`值為零。</span><span class="sxs-lookup"><span data-stu-id="5f115-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="5f115-140">一個運算式是字串，另一個則是`Nothing`</span><span class="sxs-lookup"><span data-stu-id="5f115-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="5f115-141">串連，`Nothing` 的值為 ""。</span><span class="sxs-lookup"><span data-stu-id="5f115-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="5f115-142">如果一個運算式是`Object`運算式，Visual Basic 會採取下列動作。</span><span class="sxs-lookup"><span data-stu-id="5f115-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="5f115-143">運算式的資料類型</span><span class="sxs-lookup"><span data-stu-id="5f115-143">Data types of expressions</span></span>|<span data-ttu-id="5f115-144">由編譯器執行的動作</span><span class="sxs-lookup"><span data-stu-id="5f115-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="5f115-145">`Object`運算式會保存數值，另一個則是數值資料類型</span><span class="sxs-lookup"><span data-stu-id="5f115-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="5f115-146">如果`Option Strict`為`On`，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f115-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5f115-147">如果`Option Strict` 為`Off`，則新增。</span><span class="sxs-lookup"><span data-stu-id="5f115-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="5f115-148">`Object`運算式會保存數值，另一個則屬於類型`String`</span><span class="sxs-lookup"><span data-stu-id="5f115-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="5f115-149">如果`Option Strict`為`On`，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f115-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5f115-150">如果`Option Strict`為`Off` ，`Double`則會隱含地將轉換成並加入。`String`</span><span class="sxs-lookup"><span data-stu-id="5f115-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="5f115-151">如果無法轉換成`Double`，則會擲<xref:System.InvalidCastException>回例外狀況。 `String`</span><span class="sxs-lookup"><span data-stu-id="5f115-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="5f115-152">`Object`運算式會保存字串，另一個則是數值資料類型</span><span class="sxs-lookup"><span data-stu-id="5f115-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="5f115-153">如果`Option Strict`為`On`，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f115-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5f115-154">如果`Option Strict`為`Off`，則會隱含地將`Object`字串`Double`轉換成並加入。</span><span class="sxs-lookup"><span data-stu-id="5f115-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="5f115-155">如果字串`Object`無法轉換成`Double`，則會擲<xref:System.InvalidCastException>回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5f115-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="5f115-156">`Object`運算式會保存一個字串，另一個則屬於類型`String`</span><span class="sxs-lookup"><span data-stu-id="5f115-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="5f115-157">如果`Option Strict`為`On`，則會產生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5f115-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="5f115-158">如果`Option Strict`為`Off`，則會隱含`Object`地`String`轉換為，並串連。</span><span class="sxs-lookup"><span data-stu-id="5f115-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="5f115-159">如果兩個運算式`Object`都是運算式，Visual Basic 會採取下列`Option Strict Off`動作（僅限）。</span><span class="sxs-lookup"><span data-stu-id="5f115-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="5f115-160">運算式的資料類型</span><span class="sxs-lookup"><span data-stu-id="5f115-160">Data types of expressions</span></span>|<span data-ttu-id="5f115-161">由編譯器執行的動作</span><span class="sxs-lookup"><span data-stu-id="5f115-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="5f115-162">兩`Object`個運算式都包含數值</span><span class="sxs-lookup"><span data-stu-id="5f115-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="5f115-163">載入.</span><span class="sxs-lookup"><span data-stu-id="5f115-163">Add.</span></span>|  
|<span data-ttu-id="5f115-164">這`Object`兩個運算式的類型都是`String`</span><span class="sxs-lookup"><span data-stu-id="5f115-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="5f115-165">串連.</span><span class="sxs-lookup"><span data-stu-id="5f115-165">Concatenate.</span></span>|  
|<span data-ttu-id="5f115-166">一個`Object`運算式保存一個數值，另一個則保存一個字串</span><span class="sxs-lookup"><span data-stu-id="5f115-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="5f115-167">將字串`Object`隱含地轉換`Double`為，並加入。</span><span class="sxs-lookup"><span data-stu-id="5f115-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="5f115-168">如果字串`Object`無法轉換為數值，則會<xref:System.InvalidCastException>擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5f115-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="5f115-169">如果任`Object`一個運算式評估為[任何](../../../visual-basic/language-reference/nothing.md) 或 <xref:System.DBNull>`String`，`+`則運算子會將它視為具有值 "" 的。</span><span class="sxs-lookup"><span data-stu-id="5f115-169">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f115-170">當您使用`+`運算子時，可能無法判斷是否會進行加法或字串串連。</span><span class="sxs-lookup"><span data-stu-id="5f115-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="5f115-171">`&`使用運算子進行串連，以消除不明確的情況，並提供自我記錄程式碼。</span><span class="sxs-lookup"><span data-stu-id="5f115-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5f115-172">多載化</span><span class="sxs-lookup"><span data-stu-id="5f115-172">Overloading</span></span>  
 <span data-ttu-id="5f115-173">@No__t-0 運算子可以多載 *，這*表示當運算元具有該類別或結構的類型時，類別或結構可以重新定義其行為。</span><span class="sxs-lookup"><span data-stu-id="5f115-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5f115-174">如果您的程式碼在這類類別或結構上使用這個運算子，請務必瞭解其已重新定義的行為。</span><span class="sxs-lookup"><span data-stu-id="5f115-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5f115-175">如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="5f115-175">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f115-176">範例</span><span class="sxs-lookup"><span data-stu-id="5f115-176">Example</span></span>  
 <span data-ttu-id="5f115-177">下列範例會使用`+`運算子來加入數位。</span><span class="sxs-lookup"><span data-stu-id="5f115-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="5f115-178">如果運算元都是數值，Visual Basic 會計算算術結果。</span><span class="sxs-lookup"><span data-stu-id="5f115-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="5f115-179">算術結果表示兩個運算元的總和。</span><span class="sxs-lookup"><span data-stu-id="5f115-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="5f115-180">您也可以使用`+`運算子來串連字號串。</span><span class="sxs-lookup"><span data-stu-id="5f115-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="5f115-181">如果運算元都是字串，Visual Basic 串連它們。</span><span class="sxs-lookup"><span data-stu-id="5f115-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="5f115-182">串連結果代表單一字串，其中包含兩個運算元的內容一次。</span><span class="sxs-lookup"><span data-stu-id="5f115-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="5f115-183">如果運算元是混合類型，則結果會視[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)的設定而定。</span><span class="sxs-lookup"><span data-stu-id="5f115-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="5f115-184">下列範例說明當為`Option Strict` `On`時的結果。</span><span class="sxs-lookup"><span data-stu-id="5f115-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="5f115-185">下列範例說明當為`Option Strict` `Off`時的結果。</span><span class="sxs-lookup"><span data-stu-id="5f115-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="5f115-186">若要消除不明確的情況`&` `+` ，您應該使用運算子，而不是進行串連。</span><span class="sxs-lookup"><span data-stu-id="5f115-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f115-187">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f115-187">See also</span></span>

- [<span data-ttu-id="5f115-188">& 運算子</span><span class="sxs-lookup"><span data-stu-id="5f115-188">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="5f115-189">串連運算子</span><span class="sxs-lookup"><span data-stu-id="5f115-189">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="5f115-190">算術運算子</span><span class="sxs-lookup"><span data-stu-id="5f115-190">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="5f115-191">運算子 (依功能排列)</span><span class="sxs-lookup"><span data-stu-id="5f115-191">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5f115-192">Visual Basic 中的運算子優先順序</span><span class="sxs-lookup"><span data-stu-id="5f115-192">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5f115-193">Visual Basic 中的算術運算子</span><span class="sxs-lookup"><span data-stu-id="5f115-193">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="5f115-194">Option Strict 陳述式</span><span class="sxs-lookup"><span data-stu-id="5f115-194">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
