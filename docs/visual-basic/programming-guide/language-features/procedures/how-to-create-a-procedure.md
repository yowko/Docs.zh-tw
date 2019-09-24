---
title: 作法：建立程式（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 2cf4c788ec421c1e74ef7198496a92149e049752
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216717"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="e96fd-102">作法：建立程式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="e96fd-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="e96fd-103">您可以將程式括在起始宣告語句（`Sub`或`Function`）和結束宣告語句（`End Sub`或`End Function`）之間。</span><span class="sxs-lookup"><span data-stu-id="e96fd-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="e96fd-104">所有程式的程式碼都位於這些語句之間。</span><span class="sxs-lookup"><span data-stu-id="e96fd-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="e96fd-105">程式不能包含另一個程式，因此它的開始和結束語句必須在任何其他程式之外。</span><span class="sxs-lookup"><span data-stu-id="e96fd-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="e96fd-106">如果您的程式碼在不同的位置執行相同的工作，您可以撰寫一次工作，然後從程式碼中的不同位置呼叫它。</span><span class="sxs-lookup"><span data-stu-id="e96fd-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="e96fd-107">若要建立不會傳回值的程式</span><span class="sxs-lookup"><span data-stu-id="e96fd-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="e96fd-108">在`Sub`任何其他程式之外，請使用語句，後面接著`End Sub`語句。</span><span class="sxs-lookup"><span data-stu-id="e96fd-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="e96fd-109">在語句中，在`Sub`關鍵字後面加上程式的名稱，然後以括弧括住參數清單。 `Sub`</span><span class="sxs-lookup"><span data-stu-id="e96fd-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="e96fd-110">將程式的程式碼語句放在`Sub`和`End Sub`語句之間。</span><span class="sxs-lookup"><span data-stu-id="e96fd-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="e96fd-111">若要建立會傳回值的程式</span><span class="sxs-lookup"><span data-stu-id="e96fd-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="e96fd-112">在`Function`任何其他程式之外，請使用語句，後面接著`End Function`語句。</span><span class="sxs-lookup"><span data-stu-id="e96fd-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="e96fd-113">在語句中，在`Function`關鍵字後面加上程式的名稱，然後以`As`括弧括住參數清單，然後指定傳回值的資料類型子句。 `Function`</span><span class="sxs-lookup"><span data-stu-id="e96fd-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="e96fd-114">將程式的程式碼語句放在`Function`和`End Function`語句之間。</span><span class="sxs-lookup"><span data-stu-id="e96fd-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="e96fd-115">`Return`使用語句，將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="e96fd-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="e96fd-116">將您的新程式與舊的重複程式碼區塊連接</span><span class="sxs-lookup"><span data-stu-id="e96fd-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="e96fd-117">請務必將新程式定義在舊程式碼有權存取的位置。</span><span class="sxs-lookup"><span data-stu-id="e96fd-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="e96fd-118">在舊的重複程式碼區塊中，以呼叫`Sub`或`Function`程式的單一語句取代執行重複性工作的語句。</span><span class="sxs-lookup"><span data-stu-id="e96fd-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="e96fd-119">如果您的程式是`Function` ，它會傳回值，請確定您的呼叫語句會執行具有傳回值的動作，例如將它儲存在變數中，否則值會遺失。</span><span class="sxs-lookup"><span data-stu-id="e96fd-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="e96fd-120">範例</span><span class="sxs-lookup"><span data-stu-id="e96fd-120">Example</span></span>

 <span data-ttu-id="e96fd-121">下列`Function`程式會計算直角三角形的最長邊（或斜邊），並指定其他兩邊的值：</span><span class="sxs-lookup"><span data-stu-id="e96fd-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="e96fd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e96fd-122">See also</span></span>

- [<span data-ttu-id="e96fd-123">程序</span><span class="sxs-lookup"><span data-stu-id="e96fd-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="e96fd-124">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="e96fd-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="e96fd-125">函式程序</span><span class="sxs-lookup"><span data-stu-id="e96fd-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="e96fd-126">屬性程序</span><span class="sxs-lookup"><span data-stu-id="e96fd-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="e96fd-127">運算子程序</span><span class="sxs-lookup"><span data-stu-id="e96fd-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="e96fd-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="e96fd-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e96fd-129">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="e96fd-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="e96fd-130">程序多載化</span><span class="sxs-lookup"><span data-stu-id="e96fd-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="e96fd-131">物件和類別</span><span class="sxs-lookup"><span data-stu-id="e96fd-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="e96fd-132">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e96fd-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
