---
title: 如何：建立程序 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e23358e26dbc993b0f9290a8491a3c66717b4c6
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="e9397-102">如何：建立程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9397-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="e9397-103">您將開始的宣告陳述式之間的程序 (`Sub`或`Function`) 和結束的宣告陳述式 (`End Sub`或`End Function`)。</span><span class="sxs-lookup"><span data-stu-id="e9397-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="e9397-104">所有程序的程式碼都位於這些陳述式之間。</span><span class="sxs-lookup"><span data-stu-id="e9397-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="e9397-105">程序不能包含另一個程序，因此其開始和結束的陳述式必須是其他程序之外。</span><span class="sxs-lookup"><span data-stu-id="e9397-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="e9397-106">如果您在不同的地方執行相同工作的程式碼，您可以撰寫一次做為程序工作，然後依照從不同的地方程式碼中呼叫它。</span><span class="sxs-lookup"><span data-stu-id="e9397-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="e9397-107">若要建立程序不會傳回值</span><span class="sxs-lookup"><span data-stu-id="e9397-107">To create a procedure that does not return a value</span></span>  
  
1.  <span data-ttu-id="e9397-108">任何其他程序，之外使用`Sub`陳述式，後面接著`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e9397-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="e9397-109">在`Sub`陳述式，請遵循`Sub`關鍵字的程序，則參數清單括號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="e9397-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="e9397-110">放置程序的程式碼陳述式之間`Sub`和`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e9397-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="e9397-111">若要建立程序傳回值</span><span class="sxs-lookup"><span data-stu-id="e9397-111">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="e9397-112">任何其他程序，之外使用`Function`陳述式，後面接著`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e9397-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="e9397-113">在`Function`陳述式，請遵循`Function`關鍵字的程序，則參數清單括號中，名稱，然後`As`子句指定的傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e9397-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3.  <span data-ttu-id="e9397-114">放置程序的程式碼陳述式之間`Function`和`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="e9397-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4.  <span data-ttu-id="e9397-115">使用`Return`陳述式來將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9397-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="e9397-116">連接新的程序與舊重複區塊的程式碼</span><span class="sxs-lookup"><span data-stu-id="e9397-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1.  <span data-ttu-id="e9397-117">請確定您在舊的程式碼可以存取它的其中一個位置中定義新的程序。</span><span class="sxs-lookup"><span data-stu-id="e9397-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2.  <span data-ttu-id="e9397-118">在舊而重複的程式碼區塊中，取代執行呼叫的單一陳述式的重複性工作的陳述式`Sub`或`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="e9397-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3.  <span data-ttu-id="e9397-119">如果您的程序是`Function`傳回值，請確定您呼叫的陳述式執行的動作，以傳回的值，例如儲存在變數中，否則值將會遺失。</span><span class="sxs-lookup"><span data-stu-id="e9397-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9397-120">範例</span><span class="sxs-lookup"><span data-stu-id="e9397-120">Example</span></span>  
 <span data-ttu-id="e9397-121">下列`Function`已知值的其他兩個邊直角三角形斜邊的最長邊，程序會計算。</span><span class="sxs-lookup"><span data-stu-id="e9397-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e9397-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9397-122">See also</span></span>

 [<span data-ttu-id="e9397-123">程序</span><span class="sxs-lookup"><span data-stu-id="e9397-123">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="e9397-124">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="e9397-124">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="e9397-125">函式程序</span><span class="sxs-lookup"><span data-stu-id="e9397-125">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="e9397-126">屬性程序</span><span class="sxs-lookup"><span data-stu-id="e9397-126">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="e9397-127">運算子程序</span><span class="sxs-lookup"><span data-stu-id="e9397-127">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="e9397-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="e9397-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="e9397-129">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="e9397-129">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="e9397-130">程序多載化</span><span class="sxs-lookup"><span data-stu-id="e9397-130">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="e9397-131">物件和類別</span><span class="sxs-lookup"><span data-stu-id="e9397-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="e9397-132">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9397-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
