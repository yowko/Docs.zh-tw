---
title: 如何：建立程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344915"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="cb894-102">如何：建立程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb894-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="cb894-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span><span class="sxs-lookup"><span data-stu-id="cb894-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="cb894-104">All the procedure's code lies between these statements.</span><span class="sxs-lookup"><span data-stu-id="cb894-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="cb894-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span><span class="sxs-lookup"><span data-stu-id="cb894-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="cb894-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span><span class="sxs-lookup"><span data-stu-id="cb894-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="cb894-107">To create a procedure that does not return a value</span><span class="sxs-lookup"><span data-stu-id="cb894-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="cb894-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span><span class="sxs-lookup"><span data-stu-id="cb894-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="cb894-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span><span class="sxs-lookup"><span data-stu-id="cb894-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="cb894-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span><span class="sxs-lookup"><span data-stu-id="cb894-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="cb894-111">To create a procedure that returns a value</span><span class="sxs-lookup"><span data-stu-id="cb894-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="cb894-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span><span class="sxs-lookup"><span data-stu-id="cb894-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="cb894-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span><span class="sxs-lookup"><span data-stu-id="cb894-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="cb894-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span><span class="sxs-lookup"><span data-stu-id="cb894-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="cb894-115">Use a `Return` statement to return the value to the calling code.</span><span class="sxs-lookup"><span data-stu-id="cb894-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="cb894-116">To connect your new procedure with the old, repetitive blocks of code</span><span class="sxs-lookup"><span data-stu-id="cb894-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="cb894-117">Make sure you define the new procedure in a place where the old code has access to it.</span><span class="sxs-lookup"><span data-stu-id="cb894-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="cb894-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="cb894-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="cb894-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span><span class="sxs-lookup"><span data-stu-id="cb894-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="cb894-120">範例</span><span class="sxs-lookup"><span data-stu-id="cb894-120">Example</span></span>

 <span data-ttu-id="cb894-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span><span class="sxs-lookup"><span data-stu-id="cb894-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="cb894-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="cb894-122">See also</span></span>

- [<span data-ttu-id="cb894-123">程序</span><span class="sxs-lookup"><span data-stu-id="cb894-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="cb894-124">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="cb894-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="cb894-125">函式程序</span><span class="sxs-lookup"><span data-stu-id="cb894-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="cb894-126">屬性程序</span><span class="sxs-lookup"><span data-stu-id="cb894-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="cb894-127">運算子程序</span><span class="sxs-lookup"><span data-stu-id="cb894-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="cb894-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="cb894-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cb894-129">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="cb894-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="cb894-130">程序多載化</span><span class="sxs-lookup"><span data-stu-id="cb894-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="cb894-131">物件和類別</span><span class="sxs-lookup"><span data-stu-id="cb894-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="cb894-132">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb894-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
