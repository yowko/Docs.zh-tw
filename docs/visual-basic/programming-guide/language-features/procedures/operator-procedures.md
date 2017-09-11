---
title: "運算子程序 (Visual Basic) |Microsoft 文件"
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
- Visual Basic code, procedures
- procedures, operator
- Visual Basic code, operators
- syntax, Operator procedures
- operators [Visual Basic], overloading
- overloaded operators
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: 17
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
ms.openlocfilehash: 3b2e8466ad355521dcec3cf7b2949037e569eb9a
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="83cae-102">運算子程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83cae-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="83cae-103">運算子程序是一系列的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]陳述式，定義標準的運算子的行為 (例如`*`， `<>`，或`And`) 上的類別或您已定義的結構。</span><span class="sxs-lookup"><span data-stu-id="83cae-103">An operator procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="83cae-104">這也稱為*運算子多載*。</span><span class="sxs-lookup"><span data-stu-id="83cae-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="83cae-105">當定義運算子程序</span><span class="sxs-lookup"><span data-stu-id="83cae-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="83cae-106">當您已經定義的類別或結構時，您可以宣告為該類別或結構的型別變數。</span><span class="sxs-lookup"><span data-stu-id="83cae-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="83cae-107">有時這類變數需要參與作業為運算式的一部分。</span><span class="sxs-lookup"><span data-stu-id="83cae-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="83cae-108">若要這樣做，它必須是運算子的運算元。</span><span class="sxs-lookup"><span data-stu-id="83cae-108">To do this, it must be an operand of an operator.</span></span>  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="83cae-109">只在它的基本資料型別定義運算子。</span><span class="sxs-lookup"><span data-stu-id="83cae-109"> defines operators only on its fundamental data types.</span></span> <span data-ttu-id="83cae-110">您可以定義一種運算子的行為，或兩個運算元屬於類別或結構的型別。</span><span class="sxs-lookup"><span data-stu-id="83cae-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="83cae-111">如需詳細資訊，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="83cae-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="83cae-112">運算子程序的類型</span><span class="sxs-lookup"><span data-stu-id="83cae-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="83cae-113">運算子程序可以是下列類型的其中一個︰</span><span class="sxs-lookup"><span data-stu-id="83cae-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="83cae-114">一元運算子，其中引數是類別或結構的型別定義。</span><span class="sxs-lookup"><span data-stu-id="83cae-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="83cae-115">二元運算子，其中至少一個引數是類別或結構的型別定義。</span><span class="sxs-lookup"><span data-stu-id="83cae-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="83cae-116">轉換運算子，其中引數是類別或結構的型別定義。</span><span class="sxs-lookup"><span data-stu-id="83cae-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="83cae-117">轉換運算子會傳回類別或結構的型別定義。</span><span class="sxs-lookup"><span data-stu-id="83cae-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="83cae-118">轉換運算子一律是一元，且一律使用`CType`做為您定義的運算子。</span><span class="sxs-lookup"><span data-stu-id="83cae-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="83cae-119">宣告語法</span><span class="sxs-lookup"><span data-stu-id="83cae-119">Declaration Syntax</span></span>  
 <span data-ttu-id="83cae-120">宣告運算子程序的語法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="83cae-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="83cae-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span><span class="sxs-lookup"><span data-stu-id="83cae-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="83cae-122">您使用`Widening`或`Narrowing`關鍵字只有在類型轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="83cae-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="83cae-123">運算子符號總是[CType 函式](../../../../visual-basic/language-reference/functions/ctype-function.md)類型轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="83cae-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="83cae-124">宣告兩個運算元，以定義一個二元運算子，並宣告一個定義的一元運算子，包括型別轉換運算子的運算元。</span><span class="sxs-lookup"><span data-stu-id="83cae-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="83cae-125">必須宣告所有運算元`ByVal`。</span><span class="sxs-lookup"><span data-stu-id="83cae-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="83cae-126">同樣的方法宣告的參數宣告每一個運算元[Sub 程序](./sub-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="83cae-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="83cae-127">資料類型</span><span class="sxs-lookup"><span data-stu-id="83cae-127">Data Type</span></span>  
 <span data-ttu-id="83cae-128">由於您在類別或結構定義上定義運算子，其中至少一個運算元必須是該類別或結構的資料型別。</span><span class="sxs-lookup"><span data-stu-id="83cae-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="83cae-129">類型轉換運算子，運算元或傳回型別必須是類別或結構的資料型別。</span><span class="sxs-lookup"><span data-stu-id="83cae-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="83cae-130">如需詳細資訊，請參閱[Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="83cae-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="83cae-131">呼叫語法</span><span class="sxs-lookup"><span data-stu-id="83cae-131">Calling Syntax</span></span>  
 <span data-ttu-id="83cae-132">在運算式中使用運算子符號以隱含方式呼叫運算子程序。</span><span class="sxs-lookup"><span data-stu-id="83cae-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="83cae-133">您提供運算元的方式相同的預先定義的運算子。</span><span class="sxs-lookup"><span data-stu-id="83cae-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="83cae-134">運算子程序的隱含呼叫的語法如下所示︰</span><span class="sxs-lookup"><span data-stu-id="83cae-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="83cae-135">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="83cae-135">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="83cae-136">`Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol    *  `10`</span><span class="sxs-lookup"><span data-stu-id="83cae-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="83cae-137">宣告和呼叫的圖例</span><span class="sxs-lookup"><span data-stu-id="83cae-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="83cae-138">下列結構儲存 128 位元帶正負號的整數值為構成的高序位和低序位組件。</span><span class="sxs-lookup"><span data-stu-id="83cae-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="83cae-139">它會定義`+`運算子，以將兩個`veryLong`值，並產生結果`veryLong`值。</span><span class="sxs-lookup"><span data-stu-id="83cae-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 <span data-ttu-id="83cae-140">[!code-vb[VbVbcnProcedures #&23;](./codesnippet/VisualBasic/operator-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="83cae-140">[!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="83cae-141">下列範例會示範一般呼叫`+`上定義的運算子`veryLong`。</span><span class="sxs-lookup"><span data-stu-id="83cae-141">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 <span data-ttu-id="83cae-142">[!code-vb[VbVbcnProcedures #&24;](./codesnippet/VisualBasic/operator-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="83cae-142">[!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]</span></span>  
  
 <span data-ttu-id="83cae-143">如需詳細資訊和範例，請參閱[Visual Basic 2005 中的運算子多載](http://go.microsoft.com/fwlink/?LinkId=101703)。</span><span class="sxs-lookup"><span data-stu-id="83cae-143">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83cae-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83cae-144">See Also</span></span>  
 <span data-ttu-id="83cae-145">[程序](./index.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-145">[Procedures](./index.md) </span></span>  
<span data-ttu-id="83cae-146"> [Sub 程序](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-146"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="83cae-147"> [Function 程序](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-147"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="83cae-148"> [Property 程序](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-148"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="83cae-149"> [程序參數和引數](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-149"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="83cae-150"> [Operator 陳述式](../../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-150"> [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="83cae-151"> [如何︰ 定義運算子](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-151"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="83cae-152"> [如何︰ 定義轉換運算子](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-152"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="83cae-153"> [如何︰ 呼叫運算子程序](./how-to-call-an-operator-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="83cae-153"> [How to: Call an Operator Procedure](./how-to-call-an-operator-procedure.md) </span></span>  
<span data-ttu-id="83cae-154"> [如何：使用定義運算子的類別](./how-to-use-a-class-that-defines-operators.md)</span><span class="sxs-lookup"><span data-stu-id="83cae-154"> [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md)</span></span>
