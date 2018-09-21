---
title: Operator 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 69dea99cf71bd1e091116e54e244abfca291ffdb
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46517896"
---
# <a name="operator-statement"></a><span data-ttu-id="68b5a-102">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="68b5a-102">Operator Statement</span></span>
<span data-ttu-id="68b5a-103">宣告運算子符號、 運算元與類別或結構定義的運算子程序的程式碼。</span><span class="sxs-lookup"><span data-stu-id="68b5a-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="68b5a-104">Syntax</span></span>  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a><span data-ttu-id="68b5a-105">組件</span><span class="sxs-lookup"><span data-stu-id="68b5a-105">Parts</span></span>  
 `attrlist`  
 <span data-ttu-id="68b5a-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="68b5a-106">Optional.</span></span> <span data-ttu-id="68b5a-107">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="68b5a-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `Public`  
 <span data-ttu-id="68b5a-108">必要。</span><span class="sxs-lookup"><span data-stu-id="68b5a-108">Required.</span></span> <span data-ttu-id="68b5a-109">表示這個運算子程序[公開](../../../visual-basic/language-reference/modifiers/public.md)存取。</span><span class="sxs-lookup"><span data-stu-id="68b5a-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>  
  
 `Overloads`  
 <span data-ttu-id="68b5a-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="68b5a-110">Optional.</span></span> <span data-ttu-id="68b5a-111">請參閱[多載](../../../visual-basic/language-reference/modifiers/overloads.md)。</span><span class="sxs-lookup"><span data-stu-id="68b5a-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>  
  
 `Shared`  
 <span data-ttu-id="68b5a-112">必要。</span><span class="sxs-lookup"><span data-stu-id="68b5a-112">Required.</span></span> <span data-ttu-id="68b5a-113">指出此運算子程序[共用](../../../visual-basic/language-reference/modifiers/shared.md)程序。</span><span class="sxs-lookup"><span data-stu-id="68b5a-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>  
  
 `Shadows`  
 <span data-ttu-id="68b5a-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="68b5a-114">Optional.</span></span> <span data-ttu-id="68b5a-115">請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="68b5a-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `Widening`  
 <span data-ttu-id="68b5a-116">除非您指定所需的轉換運算子`Narrowing`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="68b5a-117">表示定義這個運算子程序[Widening](../../../visual-basic/language-reference/modifiers/widening.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="68b5a-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="68b5a-118">在此 [說明] 頁面上，請參閱 「 擴展和縮小轉換 」。</span><span class="sxs-lookup"><span data-stu-id="68b5a-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `Narrowing`  
 <span data-ttu-id="68b5a-119">除非您指定所需的轉換運算子`Widening`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="68b5a-120">表示定義這個運算子程序[Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="68b5a-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="68b5a-121">在此 [說明] 頁面上，請參閱 「 擴展和縮小轉換 」。</span><span class="sxs-lookup"><span data-stu-id="68b5a-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `operatorsymbol`  
 <span data-ttu-id="68b5a-122">必要。</span><span class="sxs-lookup"><span data-stu-id="68b5a-122">Required.</span></span> <span data-ttu-id="68b5a-123">符號或運算子，此運算子程序定義的識別碼。</span><span class="sxs-lookup"><span data-stu-id="68b5a-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>  
  
 `operand1`  
 <span data-ttu-id="68b5a-124">必要。</span><span class="sxs-lookup"><span data-stu-id="68b5a-124">Required.</span></span> <span data-ttu-id="68b5a-125">名稱和類型的一元運算子 （包括轉換運算子） 的單一運算元或二元運算子的左的運算元。</span><span class="sxs-lookup"><span data-stu-id="68b5a-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>  
  
 `operand2`  
 <span data-ttu-id="68b5a-126">二元運算子的必要項。</span><span class="sxs-lookup"><span data-stu-id="68b5a-126">Required for binary operators.</span></span> <span data-ttu-id="68b5a-127">名稱和類型的二元運算子的右運算元。</span><span class="sxs-lookup"><span data-stu-id="68b5a-127">The name and type of the right operand of a binary operator.</span></span>  
  
 <span data-ttu-id="68b5a-128">`operand1` 和`operand2`具有下列語法和組成部分：</span><span class="sxs-lookup"><span data-stu-id="68b5a-128">`operand1` and `operand2` have the following syntax and parts:</span></span>  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|<span data-ttu-id="68b5a-129">組件</span><span class="sxs-lookup"><span data-stu-id="68b5a-129">Part</span></span>|<span data-ttu-id="68b5a-130">描述</span><span class="sxs-lookup"><span data-stu-id="68b5a-130">Description</span></span>|  
|----------|-----------------|  
|`ByVal`|<span data-ttu-id="68b5a-131">必須是選擇性，但傳遞機制[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="68b5a-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|  
|`operandname`|<span data-ttu-id="68b5a-132">必要。</span><span class="sxs-lookup"><span data-stu-id="68b5a-132">Required.</span></span> <span data-ttu-id="68b5a-133">表示此運算元的變數名稱。</span><span class="sxs-lookup"><span data-stu-id="68b5a-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="68b5a-134">請參閱[宣告項目名稱](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="68b5a-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`operandtype`|<span data-ttu-id="68b5a-135">選擇性除非`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="68b5a-136">此運算元資料類型。</span><span class="sxs-lookup"><span data-stu-id="68b5a-136">Data type of this operand.</span></span>|  
  
 `type`  
 <span data-ttu-id="68b5a-137">選擇性除非`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="68b5a-138">傳回值的運算子程序的資料類型。</span><span class="sxs-lookup"><span data-stu-id="68b5a-138">Data type of the value the operator procedure returns.</span></span>  
  
 `statements`  
 <span data-ttu-id="68b5a-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="68b5a-139">Optional.</span></span> <span data-ttu-id="68b5a-140">運算子程序執行的陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="68b5a-140">Block of statements that the operator procedure runs.</span></span>  
  
 `returnvalue`  
 <span data-ttu-id="68b5a-141">必要。</span><span class="sxs-lookup"><span data-stu-id="68b5a-141">Required.</span></span> <span data-ttu-id="68b5a-142">運算子程序傳回呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="68b5a-142">The value that the operator procedure returns to the calling code.</span></span>  
  
 <span data-ttu-id="68b5a-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="68b5a-143">`End` `Operator`</span></span>  
 <span data-ttu-id="68b5a-144">必要。</span><span class="sxs-lookup"><span data-stu-id="68b5a-144">Required.</span></span> <span data-ttu-id="68b5a-145">此運算子程序的定義就會終止。</span><span class="sxs-lookup"><span data-stu-id="68b5a-145">Terminates the definition of this operator procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68b5a-146">備註</span><span class="sxs-lookup"><span data-stu-id="68b5a-146">Remarks</span></span>  
 <span data-ttu-id="68b5a-147">您可以使用`Operator`只能在類別或結構中。</span><span class="sxs-lookup"><span data-stu-id="68b5a-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="68b5a-148">這表示*宣告內容*運算子不能是原始程式檔、 命名空間、 模組、 介面、 程序或區塊。</span><span class="sxs-lookup"><span data-stu-id="68b5a-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="68b5a-149">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="68b5a-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="68b5a-150">所有的操作員必須為`Public Shared`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="68b5a-151">您無法指定`ByRef`， `Optional`，或`ParamArray`的任一個運算元。</span><span class="sxs-lookup"><span data-stu-id="68b5a-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>  
  
 <span data-ttu-id="68b5a-152">您無法使用的運算子符號或識別項，傳回的值。</span><span class="sxs-lookup"><span data-stu-id="68b5a-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="68b5a-153">您必須使用`Return`陳述式，而且必須指定一個值。</span><span class="sxs-lookup"><span data-stu-id="68b5a-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="68b5a-154">任意數目的`Return`陳述式可以出現在任何位置的程序。</span><span class="sxs-lookup"><span data-stu-id="68b5a-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>  
  
 <span data-ttu-id="68b5a-155">以這種方式定義的運算子會呼叫*運算子多載*無論您使用`Overloads`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="68b5a-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="68b5a-156">下表列出您可以定義的運算子清單。</span><span class="sxs-lookup"><span data-stu-id="68b5a-156">The following table lists the operators you can define.</span></span>  
  
|<span data-ttu-id="68b5a-157">類型</span><span class="sxs-lookup"><span data-stu-id="68b5a-157">Type</span></span>|<span data-ttu-id="68b5a-158">運算子</span><span class="sxs-lookup"><span data-stu-id="68b5a-158">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="68b5a-159">一元</span><span class="sxs-lookup"><span data-stu-id="68b5a-159">Unary</span></span>|<span data-ttu-id="68b5a-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="68b5a-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="68b5a-161">二元</span><span class="sxs-lookup"><span data-stu-id="68b5a-161">Binary</span></span>|<span data-ttu-id="68b5a-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="68b5a-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="68b5a-163">轉換 (一元)</span><span class="sxs-lookup"><span data-stu-id="68b5a-163">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="68b5a-164">請注意， `=` ，二元清單中的運算子為比較運算子，而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="68b5a-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="68b5a-165">當您定義`CType`，您必須指定`Widening`或`Narrowing`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>  
  
## <a name="matched-pairs"></a><span data-ttu-id="68b5a-166">相符的配對</span><span class="sxs-lookup"><span data-stu-id="68b5a-166">Matched Pairs</span></span>  
 <span data-ttu-id="68b5a-167">您必須定義特定的運算子為相符的配對。</span><span class="sxs-lookup"><span data-stu-id="68b5a-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="68b5a-168">如果您定義這類組的其中一個運算子，您必須將另也定義。</span><span class="sxs-lookup"><span data-stu-id="68b5a-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="68b5a-169">相符的配對，如下所示：</span><span class="sxs-lookup"><span data-stu-id="68b5a-169">The matched pairs are the following:</span></span>  
  
-   <span data-ttu-id="68b5a-170">`=` 和 `<>`</span><span class="sxs-lookup"><span data-stu-id="68b5a-170">`=` and `<>`</span></span>  
  
-   <span data-ttu-id="68b5a-171">`>` 和 `<`</span><span class="sxs-lookup"><span data-stu-id="68b5a-171">`>` and `<`</span></span>  
  
-   <span data-ttu-id="68b5a-172">`>=` 和 `<=`</span><span class="sxs-lookup"><span data-stu-id="68b5a-172">`>=` and `<=`</span></span>  
  
-   <span data-ttu-id="68b5a-173">`IsTrue` 和 `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="68b5a-173">`IsTrue` and `IsFalse`</span></span>  
  
## <a name="data-type-restrictions"></a><span data-ttu-id="68b5a-174">資料類型限制</span><span class="sxs-lookup"><span data-stu-id="68b5a-174">Data Type Restrictions</span></span>  
 <span data-ttu-id="68b5a-175">您定義每個運算子必須投入您定義它所在的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="68b5a-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="68b5a-176">這表示類別或結構必須顯示為下列資料類型：</span><span class="sxs-lookup"><span data-stu-id="68b5a-176">This means that the class or structure must appear as the data type of the following:</span></span>  
  
-   <span data-ttu-id="68b5a-177">一元運算子的運算元。</span><span class="sxs-lookup"><span data-stu-id="68b5a-177">The operand of a unary operator.</span></span>  
  
-   <span data-ttu-id="68b5a-178">至少其中一個二元運算子的運算元。</span><span class="sxs-lookup"><span data-stu-id="68b5a-178">At least one of the operands of a binary operator.</span></span>  
  
-   <span data-ttu-id="68b5a-179">運算元或轉換運算子的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="68b5a-179">Either the operand or the return type of a conversion operator.</span></span>  
  
 <span data-ttu-id="68b5a-180">某些運算子具有其他資料型別限制，如下所示：</span><span class="sxs-lookup"><span data-stu-id="68b5a-180">Certain operators have additional data type restrictions, as follows:</span></span>  
  
-   <span data-ttu-id="68b5a-181">如果您定義`IsTrue`並`IsFalse`運算子，它們必須都傳回`Boolean`型別。</span><span class="sxs-lookup"><span data-stu-id="68b5a-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>  
  
-   <span data-ttu-id="68b5a-182">如果您定義`<<`並`>>`運算子，它們必須同時指定`Integer`類型`operandtype`的`operand2`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>  
  
 <span data-ttu-id="68b5a-183">傳回的型別沒有對應至其中一個運算元的類型。</span><span class="sxs-lookup"><span data-stu-id="68b5a-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="68b5a-184">比方說，這類的比較運算子`=`或是`<>`可能會傳回`Boolean`即使兩個運算元是`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>  
  
## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="68b5a-185">邏輯和位元運算子</span><span class="sxs-lookup"><span data-stu-id="68b5a-185">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="68b5a-186">`And`， `Or`， `Not`，和`Xor`運算子可以執行在 Visual Basic 中的邏輯或位元運算。</span><span class="sxs-lookup"><span data-stu-id="68b5a-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="68b5a-187">不過，如果您定義這些運算子的其中一個類別或結構上，您可以定義只有其位元的作業。</span><span class="sxs-lookup"><span data-stu-id="68b5a-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>  
  
 <span data-ttu-id="68b5a-188">您不能定義`AndAlso`直接與運算子`Operator`陳述式。</span><span class="sxs-lookup"><span data-stu-id="68b5a-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="68b5a-189">不過，您可以使用`AndAlso`如果您已符合下列條件：</span><span class="sxs-lookup"><span data-stu-id="68b5a-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>  
  
-   <span data-ttu-id="68b5a-190">您已定義`And`在您想要使用的相同運算元類型`AndAlso`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>  
  
-   <span data-ttu-id="68b5a-191">您定義`And`傳回相同的類型為類別或結構的項目，在其上已定義它。</span><span class="sxs-lookup"><span data-stu-id="68b5a-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>  
  
-   <span data-ttu-id="68b5a-192">您已定義`IsFalse`上類別或結構的項目，您已定義的運算子`And`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>  
  
 <span data-ttu-id="68b5a-193">同樣地，您可以使用`OrElse`如果您已定義`Or`相同的運算元，使用類別或結構，而您的傳回型別已定義`IsTrue`類別或結構上。</span><span class="sxs-lookup"><span data-stu-id="68b5a-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>  
  
## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="68b5a-194">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="68b5a-194">Widening and Narrowing Conversions</span></span>  
 <span data-ttu-id="68b5a-195">A*擴展轉換*一定會成功在執行階段，而*縮小轉換*可以在執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="68b5a-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="68b5a-196">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="68b5a-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="68b5a-197">如果您宣告轉換程序，才能`Widening`，您的程序程式碼必須產生任何失敗。</span><span class="sxs-lookup"><span data-stu-id="68b5a-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="68b5a-198">這表示：</span><span class="sxs-lookup"><span data-stu-id="68b5a-198">This means the following:</span></span>  
  
-   <span data-ttu-id="68b5a-199">它必須一律傳回有效的值型別的`type`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-199">It must always return a valid value of type `type`.</span></span>  
  
-   <span data-ttu-id="68b5a-200">它必須處理所有可能的例外狀況或其他錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="68b5a-200">It must handle all possible exceptions and other error conditions.</span></span>  
  
-   <span data-ttu-id="68b5a-201">它必須處理傳回的任何程序，它會呼叫任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="68b5a-201">It must handle any error returns from any procedures it calls.</span></span>  
  
 <span data-ttu-id="68b5a-202">如果已轉換程序可能不會成功，或是它可能會造成未處理的例外狀況，您必須將它宣告`Narrowing`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="68b5a-203">範例</span><span class="sxs-lookup"><span data-stu-id="68b5a-203">Example</span></span>  
 <span data-ttu-id="68b5a-204">下列程式碼範例會使用`Operator`陳述式來定義結構，其中包含的運算子程序的外框`And`， `Or`， `IsFalse`，和`IsTrue`運算子。</span><span class="sxs-lookup"><span data-stu-id="68b5a-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="68b5a-205">`And` 並`Or`各自採用兩個運算元的型別`abc`並傳回型別`abc`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="68b5a-206">`IsFalse` 並`IsTrue`各自採用單一類型的運算元`abc`，並傳回`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="68b5a-207">這些定義允許呼叫的程式碼，以使用`And`， `AndAlso`， `Or`，以及`OrElse`類型的運算元使用`abc`。</span><span class="sxs-lookup"><span data-stu-id="68b5a-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="68b5a-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68b5a-208">See Also</span></span>  
 [<span data-ttu-id="68b5a-209">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="68b5a-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="68b5a-210">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="68b5a-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="68b5a-211">Widening</span><span class="sxs-lookup"><span data-stu-id="68b5a-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="68b5a-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="68b5a-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="68b5a-213">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="68b5a-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="68b5a-214">運算子程序</span><span class="sxs-lookup"><span data-stu-id="68b5a-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="68b5a-215">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="68b5a-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="68b5a-216">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="68b5a-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="68b5a-217">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="68b5a-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="68b5a-218">如何：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="68b5a-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
