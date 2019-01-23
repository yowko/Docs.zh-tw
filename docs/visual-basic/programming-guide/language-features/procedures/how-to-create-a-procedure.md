---
title: HOW TO：建立程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 06fed04a0ebe7a0b3111a94308d15d01bcf47c1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54636530"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="7d7e9-102">HOW TO：建立程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d7e9-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="7d7e9-103">您將開始的宣告陳述式之間的程序 (`Sub`或是`Function`) 和結束的宣告陳述式 (`End Sub`或`End Function`)。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="7d7e9-104">這些陳述式之間，位於所有程序的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="7d7e9-105">程序不能包含另一個程序，因此其開始和結束的陳述式必須是任何其他程序之外。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="7d7e9-106">如果您有不同的地方執行相同工作的程式碼時，您可以撰寫一次做為程序的工作，然後依照從不同的地方在程式碼中呼叫它。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="7d7e9-107">若要建立的程序，不會傳回值</span><span class="sxs-lookup"><span data-stu-id="7d7e9-107">To create a procedure that does not return a value</span></span>  
  
1.  <span data-ttu-id="7d7e9-108">任何其他程序外, 使用`Sub`陳述式，後面接著`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="7d7e9-109">在 `Sub`陳述式中，遵循`Sub`關鍵字的程序中，則參數清單括號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="7d7e9-110">放置程序的程式碼陳述式之間`Sub`和`End Sub`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="7d7e9-111">若要建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="7d7e9-111">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="7d7e9-112">任何其他程序外, 使用`Function`陳述式，後面接著`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="7d7e9-113">在`Function`陳述式，請依照下列`Function`關鍵字與程序中，則參數清單括號中的名稱，然後`As`子句指定的傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3.  <span data-ttu-id="7d7e9-114">放置程序的程式碼陳述式之間`Function`和`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4.  <span data-ttu-id="7d7e9-115">使用`Return`陳述式來將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="7d7e9-116">連接新的程序利用舊的重複性的區塊的程式碼</span><span class="sxs-lookup"><span data-stu-id="7d7e9-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1.  <span data-ttu-id="7d7e9-117">請確定您在舊的程式碼，能夠存取它的地方定義新的程序。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2.  <span data-ttu-id="7d7e9-118">在舊的重複性的程式碼區塊中，取代執行重複性工作，呼叫以單一陳述式的陳述式`Sub`或`Function`程序。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3.  <span data-ttu-id="7d7e9-119">如果您的程序是`Function`所傳回的值，請確保您呼叫的陳述式會執行的動作傳回的值，例如將它儲存在變數中，否則此值將會遺失。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d7e9-120">範例</span><span class="sxs-lookup"><span data-stu-id="7d7e9-120">Example</span></span>  
 <span data-ttu-id="7d7e9-121">下列`Function`程序會計算已知值的其他兩個邊直角三角形斜邊的最長的側邊。</span><span class="sxs-lookup"><span data-stu-id="7d7e9-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7d7e9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d7e9-122">See also</span></span>

- [<span data-ttu-id="7d7e9-123">程序</span><span class="sxs-lookup"><span data-stu-id="7d7e9-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7d7e9-124">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="7d7e9-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="7d7e9-125">函式程序</span><span class="sxs-lookup"><span data-stu-id="7d7e9-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="7d7e9-126">屬性程序</span><span class="sxs-lookup"><span data-stu-id="7d7e9-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="7d7e9-127">運算子程序</span><span class="sxs-lookup"><span data-stu-id="7d7e9-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="7d7e9-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="7d7e9-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7d7e9-129">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="7d7e9-129">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="7d7e9-130">程序多載化</span><span class="sxs-lookup"><span data-stu-id="7d7e9-130">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="7d7e9-131">物件和類別</span><span class="sxs-lookup"><span data-stu-id="7d7e9-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="7d7e9-132">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d7e9-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
