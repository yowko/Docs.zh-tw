---
title: 運算子程序
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: b395f5fcf1b89bb49e55e207c4910e95f2aae69d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346003"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="d8207-102">運算子程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8207-102">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="d8207-103">運算子程式是一系列的 Visual Basic 語句，可在您定義的類別或結構上定義標準運算子的行為（例如 `*`、`<>`或 `And`）。</span><span class="sxs-lookup"><span data-stu-id="d8207-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="d8207-104">這也稱為「*運算子*多載」。</span><span class="sxs-lookup"><span data-stu-id="d8207-104">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="d8207-105">定義運算子程式的時機</span><span class="sxs-lookup"><span data-stu-id="d8207-105">When to Define Operator Procedures</span></span>

<span data-ttu-id="d8207-106">當您已定義類別或結構時，您可以將變數宣告為該類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="d8207-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="d8207-107">有時候這類變數需要參與作業做為運算式的一部分。</span><span class="sxs-lookup"><span data-stu-id="d8207-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="d8207-108">若要這樣做，它必須是運算子的運算元。</span><span class="sxs-lookup"><span data-stu-id="d8207-108">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="d8207-109">Visual Basic 只會定義其基本資料類型的運算子。</span><span class="sxs-lookup"><span data-stu-id="d8207-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="d8207-110">當一或兩個運算元屬於您的類別或結構類型時，您可以定義運算子的行為。</span><span class="sxs-lookup"><span data-stu-id="d8207-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="d8207-111">如需詳細資訊，請參閱[Operator 語句](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d8207-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="d8207-112">運算子程式的類型</span><span class="sxs-lookup"><span data-stu-id="d8207-112">Types of Operator Procedure</span></span>

<span data-ttu-id="d8207-113">運算子程式可以是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="d8207-113">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="d8207-114">一元運算子的定義，其中引數是您的類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="d8207-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="d8207-115">二元運算子的定義，其中至少有一個引數屬於您的類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="d8207-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="d8207-116">轉換運算子的定義，其中的引數是您的類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="d8207-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="d8207-117">轉換運算子的定義，可傳回您的類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="d8207-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="d8207-118">轉換運算子一律是一元，而且您一律會使用 `CType` 做為您所定義的運算子。</span><span class="sxs-lookup"><span data-stu-id="d8207-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="d8207-119">宣告語法</span><span class="sxs-lookup"><span data-stu-id="d8207-119">Declaration Syntax</span></span>

<span data-ttu-id="d8207-120">宣告運算子程式的語法如下：</span><span class="sxs-lookup"><span data-stu-id="d8207-120">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="d8207-121">您只會在類型轉換運算子上使用 `Widening` 或 `Narrowing` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d8207-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="d8207-122">類型轉換運算子的運算子符號一律是[CType 函數](../../../../visual-basic/language-reference/functions/ctype-function.md)。</span><span class="sxs-lookup"><span data-stu-id="d8207-122">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="d8207-123">您可以宣告兩個運算元來定義二元運算子，並宣告一個運算元來定義一元運算子，包括型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="d8207-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="d8207-124">所有運算元都必須宣告 `ByVal`。</span><span class="sxs-lookup"><span data-stu-id="d8207-124">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="d8207-125">您可以用宣告[Sub 程式](./sub-procedures.md)參數的相同方式來宣告每個運算元。</span><span class="sxs-lookup"><span data-stu-id="d8207-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="d8207-126">資料類型</span><span class="sxs-lookup"><span data-stu-id="d8207-126">Data Type</span></span>

<span data-ttu-id="d8207-127">因為您是在已定義的類別或結構上定義運算子，所以至少有一個運算元必須是該類別或結構的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d8207-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="d8207-128">若為類型轉換運算子，運算元或傳回類型必須是類別或結構的資料類型。</span><span class="sxs-lookup"><span data-stu-id="d8207-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="d8207-129">如需詳細資訊，請參閱[Operator 語句](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="d8207-129">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="d8207-130">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="d8207-130">Calling Syntax</span></span>

<span data-ttu-id="d8207-131">您可以在運算式中使用運算子符號，以隱含的方式叫用運算子程式。</span><span class="sxs-lookup"><span data-stu-id="d8207-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="d8207-132">提供運算元的方式與預先定義的運算子相同。</span><span class="sxs-lookup"><span data-stu-id="d8207-132">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="d8207-133">對運算子程式進行隱含呼叫的語法如下：</span><span class="sxs-lookup"><span data-stu-id="d8207-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="d8207-134">`Dim testStruct As`  *結構名稱*</span><span class="sxs-lookup"><span data-stu-id="d8207-134">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="d8207-135">`Dim testNewStruct As`  *結構名稱*  `= testStruct`  *運算子符號*  `10`</span><span class="sxs-lookup"><span data-stu-id="d8207-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="d8207-136">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="d8207-136">Illustration of Declaration and Call</span></span>

<span data-ttu-id="d8207-137">下列結構會將帶正負號的128位整數值儲存為組成高順序和低序位部分。</span><span class="sxs-lookup"><span data-stu-id="d8207-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="d8207-138">它會定義 `+` 運算子，以加入兩個 `veryLong` 值，並產生產生的 `veryLong` 值。</span><span class="sxs-lookup"><span data-stu-id="d8207-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="d8207-139">下列範例顯示 `veryLong`上所定義之 `+` 運算子的一般呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8207-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="d8207-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8207-140">See also</span></span>

- [<span data-ttu-id="d8207-141">程序</span><span class="sxs-lookup"><span data-stu-id="d8207-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d8207-142">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="d8207-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="d8207-143">函式程序</span><span class="sxs-lookup"><span data-stu-id="d8207-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="d8207-144">屬性程序</span><span class="sxs-lookup"><span data-stu-id="d8207-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="d8207-145">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="d8207-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="d8207-146">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="d8207-146">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="d8207-147">如何：定義運算子</span><span class="sxs-lookup"><span data-stu-id="d8207-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="d8207-148">如何：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="d8207-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="d8207-149">如何：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="d8207-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="d8207-150">如何：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="d8207-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
