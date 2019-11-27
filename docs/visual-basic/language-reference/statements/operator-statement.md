---
title: Operator 陳述式
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
ms.openlocfilehash: aa6ae3977977ded05e47d12dabe72f09251f262d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353799"
---
# <a name="operator-statement"></a><span data-ttu-id="bd1f5-102">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="bd1f5-102">Operator Statement</span></span>

<span data-ttu-id="bd1f5-103">宣告運算子符號、運算元，以及在類別或結構上定義運算子程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd1f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd1f5-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="bd1f5-105">組件</span><span class="sxs-lookup"><span data-stu-id="bd1f5-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="bd1f5-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-106">Optional.</span></span> <span data-ttu-id="bd1f5-107">請參閱[屬性清單](../../../visual-basic/language-reference/statements/attribute-list.md)。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="bd1f5-108">必要。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-108">Required.</span></span> <span data-ttu-id="bd1f5-109">指出此運算子程式具有[公用](../../../visual-basic/language-reference/modifiers/public.md)存取權。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="bd1f5-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-110">Optional.</span></span> <span data-ttu-id="bd1f5-111">請[參閱](../../../visual-basic/language-reference/modifiers/overloads.md)多載。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="bd1f5-112">必要。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-112">Required.</span></span> <span data-ttu-id="bd1f5-113">表示此運算子程式是[共用](../../../visual-basic/language-reference/modifiers/shared.md)程式。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="bd1f5-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-114">Optional.</span></span> <span data-ttu-id="bd1f5-115">請參閱[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="bd1f5-116">轉換運算子的必要參數，除非您指定 `Narrowing`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="bd1f5-117">表示此運算子程式會定義[擴展](../../../visual-basic/language-reference/modifiers/widening.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="bd1f5-118">請參閱此說明頁面上的「擴展和縮小轉換」。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="bd1f5-119">轉換運算子的必要參數，除非您指定 `Widening`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="bd1f5-120">表示此運算子程式會定義[縮小](../../../visual-basic/language-reference/modifiers/narrowing.md)轉換。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="bd1f5-121">請參閱此說明頁面上的「擴展和縮小轉換」。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="bd1f5-122">必要。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-122">Required.</span></span> <span data-ttu-id="bd1f5-123">這個運算子程式所定義之運算子的符號或識別碼。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="bd1f5-124">必要。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-124">Required.</span></span> <span data-ttu-id="bd1f5-125">一元運算子之單一運算元的名稱和類型（包括轉換運算子）或二元運算子的左運算元。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="bd1f5-126">二元運算子的必要參數。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-126">Required for binary operators.</span></span> <span data-ttu-id="bd1f5-127">二元運算子右運算元的名稱和類型。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="bd1f5-128">`operand1` 和 `operand2` 具有下列語法和部分：</span><span class="sxs-lookup"><span data-stu-id="bd1f5-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="bd1f5-129">組件</span><span class="sxs-lookup"><span data-stu-id="bd1f5-129">Part</span></span>|<span data-ttu-id="bd1f5-130">描述</span><span class="sxs-lookup"><span data-stu-id="bd1f5-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="bd1f5-131">選擇性，但傳遞機制必須是[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="bd1f5-132">必要。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-132">Required.</span></span> <span data-ttu-id="bd1f5-133">代表這個運算元之變數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="bd1f5-134">請參閱 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="bd1f5-135">除非 `On``Option Strict`，否則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="bd1f5-136">這個運算元的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="bd1f5-137">除非 `On``Option Strict`，否則為選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="bd1f5-138">運算子程式傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="bd1f5-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-139">Optional.</span></span> <span data-ttu-id="bd1f5-140">運算子程式執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="bd1f5-141">必要。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-141">Required.</span></span> <span data-ttu-id="bd1f5-142">運算子程式傳回給呼叫程式碼的值。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="bd1f5-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="bd1f5-143">`End` `Operator`</span></span>  
<span data-ttu-id="bd1f5-144">必要。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-144">Required.</span></span> <span data-ttu-id="bd1f5-145">終止此運算子程式的定義。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd1f5-146">備註</span><span class="sxs-lookup"><span data-stu-id="bd1f5-146">Remarks</span></span>

<span data-ttu-id="bd1f5-147">您只能在類別或結構中使用 `Operator`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="bd1f5-148">這表示運算子的宣告*內容*不能是原始程式檔、命名空間、模組、介面、程式或區塊。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="bd1f5-149">如需詳細資訊，請參閱[宣告內容和預設存取層級](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="bd1f5-150">所有的運算子都必須 `Public Shared`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="bd1f5-151">您不能為任一運算元指定 `ByRef`、`Optional`或 `ParamArray`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="bd1f5-152">您不能使用運算子符號或識別碼來保存傳回值。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="bd1f5-153">您必須使用 `Return` 語句，而且必須指定值。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="bd1f5-154">任何數目的 `Return` 語句都可以出現在程式中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="bd1f5-155">不論您是否使用 `Overloads` 關鍵字，以這種方式定義運算子稱為「*運算子*多載」。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="bd1f5-156">下表列出您可以定義的運算子清單。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="bd1f5-157">類型</span><span class="sxs-lookup"><span data-stu-id="bd1f5-157">Type</span></span>|<span data-ttu-id="bd1f5-158">運算子</span><span class="sxs-lookup"><span data-stu-id="bd1f5-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="bd1f5-159">一元</span><span class="sxs-lookup"><span data-stu-id="bd1f5-159">Unary</span></span>|<span data-ttu-id="bd1f5-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="bd1f5-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="bd1f5-161">Binary</span><span class="sxs-lookup"><span data-stu-id="bd1f5-161">Binary</span></span>|<span data-ttu-id="bd1f5-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="bd1f5-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="bd1f5-163">轉換 (一元)</span><span class="sxs-lookup"><span data-stu-id="bd1f5-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="bd1f5-164">請注意，二進位清單中的 `=` 運算子是比較運算子，而不是指派運算子。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="bd1f5-165">當您定義 `CType`時，您必須指定 [`Widening`] 或 [`Narrowing`]。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="bd1f5-166">相符的配對</span><span class="sxs-lookup"><span data-stu-id="bd1f5-166">Matched Pairs</span></span>

<span data-ttu-id="bd1f5-167">您必須將某些運算子定義為相符的配對。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="bd1f5-168">如果您定義這類配對的任一個運算子，則也必須定義另一個。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="bd1f5-169">相符的配對如下所示：</span><span class="sxs-lookup"><span data-stu-id="bd1f5-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="bd1f5-170">`=` 和 `<>`</span><span class="sxs-lookup"><span data-stu-id="bd1f5-170">`=` and `<>`</span></span>

- <span data-ttu-id="bd1f5-171">`>` 和 `<`</span><span class="sxs-lookup"><span data-stu-id="bd1f5-171">`>` and `<`</span></span>

- <span data-ttu-id="bd1f5-172">`>=` 和 `<=`</span><span class="sxs-lookup"><span data-stu-id="bd1f5-172">`>=` and `<=`</span></span>

- <span data-ttu-id="bd1f5-173">`IsTrue` 和 `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="bd1f5-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="bd1f5-174">資料類型限制</span><span class="sxs-lookup"><span data-stu-id="bd1f5-174">Data Type Restrictions</span></span>

<span data-ttu-id="bd1f5-175">您定義的每個運算子都必須包含您定義它所在的類別或結構。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="bd1f5-176">這表示類別或結構必須以下列資料類型的形式出現：</span><span class="sxs-lookup"><span data-stu-id="bd1f5-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="bd1f5-177">一元運算子的運算元。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="bd1f5-178">二元運算子的至少一個運算元。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="bd1f5-179">轉換運算子的運算元或傳回型別。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="bd1f5-180">某些運算子具有額外的資料類型限制，如下所示：</span><span class="sxs-lookup"><span data-stu-id="bd1f5-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="bd1f5-181">如果您定義 `IsTrue` 和 `IsFalse` 運算子，則兩者都必須傳回 `Boolean` 類型。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="bd1f5-182">如果您定義 `<<` 和 `>>` 運算子，它們必須同時為 `operand2`的 `operandtype` 指定 `Integer` 類型。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="bd1f5-183">傳回型別不一定要對應至任一運算元的型別。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="bd1f5-184">例如，即使兩個運算元都不 `Boolean`，比較運算子（例如 `=` 或 `<>` 也可以傳回 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="bd1f5-185">邏輯運算子和位元運算子</span><span class="sxs-lookup"><span data-stu-id="bd1f5-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="bd1f5-186">`And`、`Or`、`Not`和 `Xor` 運算子可以在 Visual Basic 中執行邏輯 or 位運算。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="bd1f5-187">不過，如果您在類別或結構上定義其中一個運算子，則只能定義其位運算。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="bd1f5-188">您不能直接使用 `Operator` 語句來定義 `AndAlso` 運算子。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="bd1f5-189">不過，如果您已完成下列條件，您可以使用 `AndAlso`：</span><span class="sxs-lookup"><span data-stu-id="bd1f5-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="bd1f5-190">您已在要用於 `AndAlso`的相同運算元類型上定義 `And`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="bd1f5-191">您的 `And` 定義會傳回與您已定義的類別或結構相同的類型。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="bd1f5-192">您已在定義 `And`的類別或結構上定義 `IsFalse` 運算子。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="bd1f5-193">同樣地，如果您已在相同的運算元上定義 `Or`、使用類別或結構的傳回型別，而且您已在類別或結構上定義 `IsTrue`，則可以使用 `OrElse`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="bd1f5-194">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="bd1f5-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="bd1f5-195">*擴輾轉換*一律會在執行時間成功，而*縮小轉換*可能會在執行時間失敗。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="bd1f5-196">如需詳細資訊，請參閱 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="bd1f5-197">如果您宣告要 `Widening`的轉換過程，程式碼就不能產生任何失敗。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="bd1f5-198">這表示：</span><span class="sxs-lookup"><span data-stu-id="bd1f5-198">This means the following:</span></span>

- <span data-ttu-id="bd1f5-199">它必須一律傳回 `type`類型的有效值。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="bd1f5-200">它必須處理所有可能的例外狀況和其他錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="bd1f5-201">它必須處理從它所呼叫的任何程式傳回的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="bd1f5-202">如果轉換程式可能不會成功，或可能造成未處理的例外狀況，您必須將它宣告為 `Narrowing`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="bd1f5-203">範例</span><span class="sxs-lookup"><span data-stu-id="bd1f5-203">Example</span></span>

<span data-ttu-id="bd1f5-204">下列程式碼範例會使用 `Operator` 語句來定義結構的外框，其中包含 `And`、`Or`、`IsFalse`和 `IsTrue` 運算子的運算子程式。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="bd1f5-205">`And` 和 `Or` 都會採用類型 `abc` 的兩個運算元，並 `abc`傳回型別。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="bd1f5-206">`IsFalse` 和 `IsTrue` 都會採用類型 `abc` 的單一運算元，並傳回 `Boolean`。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="bd1f5-207">這些定義可讓呼叫程式碼使用 `And`、`AndAlso`、`Or`和 `OrElse`，並搭配 `abc`類型的運算元。</span><span class="sxs-lookup"><span data-stu-id="bd1f5-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="bd1f5-208">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd1f5-208">See also</span></span>

- [<span data-ttu-id="bd1f5-209">IsFalse 運算子</span><span class="sxs-lookup"><span data-stu-id="bd1f5-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="bd1f5-210">IsTrue 運算子</span><span class="sxs-lookup"><span data-stu-id="bd1f5-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="bd1f5-211">Widening</span><span class="sxs-lookup"><span data-stu-id="bd1f5-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="bd1f5-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="bd1f5-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="bd1f5-213">擴展和縮小轉換</span><span class="sxs-lookup"><span data-stu-id="bd1f5-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="bd1f5-214">運算子程序</span><span class="sxs-lookup"><span data-stu-id="bd1f5-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="bd1f5-215">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="bd1f5-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="bd1f5-216">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="bd1f5-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="bd1f5-217">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="bd1f5-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="bd1f5-218">如何：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="bd1f5-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
