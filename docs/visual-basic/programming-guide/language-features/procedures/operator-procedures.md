---
title: 運算子程序 (Visual Basic)
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
ms.openlocfilehash: 80c9a77494be95365899c6a25435fcfc5d2a7293
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175015"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="46bb6-102">運算子程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46bb6-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="46bb6-103">運算子程序是一系列的 Visual Basic 陳述式可定義標準運算式的行為 (例如`*`， `<>`，或`And`) 上類別或您已定義的結構。</span><span class="sxs-lookup"><span data-stu-id="46bb6-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="46bb6-104">這也稱為*多載的運算子*。</span><span class="sxs-lookup"><span data-stu-id="46bb6-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="46bb6-105">定義運算子程序的時機</span><span class="sxs-lookup"><span data-stu-id="46bb6-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="46bb6-106">當您已定義類別或結構時，您可以宣告為該類別或結構類型的變數。</span><span class="sxs-lookup"><span data-stu-id="46bb6-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="46bb6-107">有時候這類變數必須參與作業為運算式的一部分。</span><span class="sxs-lookup"><span data-stu-id="46bb6-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="46bb6-108">若要這樣做，它必須是運算子的運算元。</span><span class="sxs-lookup"><span data-stu-id="46bb6-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="46bb6-109">Visual Basic 只能在其基本資料類型上定義運算子。</span><span class="sxs-lookup"><span data-stu-id="46bb6-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="46bb6-110">您可以定義一種運算子的行為，或兩個運算元屬於您的類別或結構的類型。</span><span class="sxs-lookup"><span data-stu-id="46bb6-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="46bb6-111">如需詳細資訊，請參閱 < [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="46bb6-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="46bb6-112">類型的運算子程序</span><span class="sxs-lookup"><span data-stu-id="46bb6-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="46bb6-113">運算子程序可以是下列類型之一：</span><span class="sxs-lookup"><span data-stu-id="46bb6-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="46bb6-114">一元運算子的引數會是您的類別或結構的類型定義。</span><span class="sxs-lookup"><span data-stu-id="46bb6-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="46bb6-115">二元運算子，其中至少一個引數是您自己的類別或結構之型別的定義。</span><span class="sxs-lookup"><span data-stu-id="46bb6-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="46bb6-116">轉換運算子，其中的引數是類別或結構的類型定義。</span><span class="sxs-lookup"><span data-stu-id="46bb6-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="46bb6-117">轉換運算子會傳回您類別或結構的型別定義。</span><span class="sxs-lookup"><span data-stu-id="46bb6-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="46bb6-118">轉換運算子一律是一元 （unary），且一律使用`CType`做為您正在定義的運算子。</span><span class="sxs-lookup"><span data-stu-id="46bb6-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="46bb6-119">宣告語法</span><span class="sxs-lookup"><span data-stu-id="46bb6-119">Declaration Syntax</span></span>  
 <span data-ttu-id="46bb6-120">宣告運算子程序的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="46bb6-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  <span data-ttu-id="46bb6-121">*operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span><span class="sxs-lookup"><span data-stu-id="46bb6-121">*operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="46bb6-122">您使用`Widening`或`Narrowing`關鍵字只在型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="46bb6-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="46bb6-123">運算子符號總是[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)的型別轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="46bb6-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="46bb6-124">您宣告兩個運算元來定義二元運算子，並宣告一個定義的一元運算子，包括型別轉換運算子的運算元。</span><span class="sxs-lookup"><span data-stu-id="46bb6-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="46bb6-125">所有的運算元必須宣告`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="46bb6-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="46bb6-126">同樣的方法宣告參數宣告每一個運算元[Sub 程序](./sub-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="46bb6-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="46bb6-127">資料類型</span><span class="sxs-lookup"><span data-stu-id="46bb6-127">Data Type</span></span>  
 <span data-ttu-id="46bb6-128">因為您正在定義的運算子上類別或您已定義的結構，其中至少一個運算元必須是該類別或結構的資料類型。</span><span class="sxs-lookup"><span data-stu-id="46bb6-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="46bb6-129">型別轉換運算子，運算元或傳回類型必須是類別或結構的資料類型。</span><span class="sxs-lookup"><span data-stu-id="46bb6-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="46bb6-130">如需詳細資訊，請參閱 < [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="46bb6-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="46bb6-131">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="46bb6-131">Calling Syntax</span></span>  
 <span data-ttu-id="46bb6-132">您叫用運算子程序隱含地在運算式中使用運算子的符號。</span><span class="sxs-lookup"><span data-stu-id="46bb6-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="46bb6-133">您提供運算元相同方式和預先定義的運算子。</span><span class="sxs-lookup"><span data-stu-id="46bb6-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="46bb6-134">隱含呼叫運算子程序的語法如下所示：</span><span class="sxs-lookup"><span data-stu-id="46bb6-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 `Dim testStruct As`  *<span data-ttu-id="46bb6-135">結構名稱</span><span class="sxs-lookup"><span data-stu-id="46bb6-135">structurename</span></span>*  
  
 `Dim testNewStruct As`  <span data-ttu-id="46bb6-136">*structurename*  `= testStruct`  *operatorsymbol*</span><span class="sxs-lookup"><span data-stu-id="46bb6-136">*structurename*  `= testStruct`  *operatorsymbol*</span></span>  `10`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="46bb6-137">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="46bb6-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="46bb6-138">下列結構儲存為構成的高序位和低序位部分的 128 位元帶正負號的整數值。</span><span class="sxs-lookup"><span data-stu-id="46bb6-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="46bb6-139">它會定義`+`運算子，將兩個`veryLong`值，並產生所產生`veryLong`值。</span><span class="sxs-lookup"><span data-stu-id="46bb6-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 <span data-ttu-id="46bb6-140">下列範例示範典型的呼叫來`+`上定義的運算子`veryLong`。</span><span class="sxs-lookup"><span data-stu-id="46bb6-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a><span data-ttu-id="46bb6-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46bb6-141">See also</span></span>

- [<span data-ttu-id="46bb6-142">程序</span><span class="sxs-lookup"><span data-stu-id="46bb6-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="46bb6-143">子程序</span><span class="sxs-lookup"><span data-stu-id="46bb6-143">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="46bb6-144">函式程序</span><span class="sxs-lookup"><span data-stu-id="46bb6-144">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="46bb6-145">屬性程序</span><span class="sxs-lookup"><span data-stu-id="46bb6-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="46bb6-146">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="46bb6-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="46bb6-147">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="46bb6-147">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="46bb6-148">HOW TO：定義運算子</span><span class="sxs-lookup"><span data-stu-id="46bb6-148">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="46bb6-149">HOW TO：定義轉換運算子</span><span class="sxs-lookup"><span data-stu-id="46bb6-149">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="46bb6-150">HOW TO：呼叫運算子程序</span><span class="sxs-lookup"><span data-stu-id="46bb6-150">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="46bb6-151">HOW TO：使用定義運算子的類別</span><span class="sxs-lookup"><span data-stu-id="46bb6-151">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
