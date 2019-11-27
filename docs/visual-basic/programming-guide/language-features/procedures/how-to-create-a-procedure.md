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
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="13204-102">如何：建立程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13204-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="13204-103">您可以將程式括在起始宣告語句（`Sub` 或 `Function`）與結束宣告語句（`End Sub` 或 `End Function`）之間。</span><span class="sxs-lookup"><span data-stu-id="13204-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="13204-104">所有程式的程式碼都位於這些語句之間。</span><span class="sxs-lookup"><span data-stu-id="13204-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="13204-105">程式不能包含另一個程式，因此它的開始和結束語句必須在任何其他程式之外。</span><span class="sxs-lookup"><span data-stu-id="13204-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="13204-106">如果您的程式碼在不同的位置執行相同的工作，您可以撰寫一次工作，然後從程式碼中的不同位置呼叫它。</span><span class="sxs-lookup"><span data-stu-id="13204-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="13204-107">若要建立不會傳回值的程式</span><span class="sxs-lookup"><span data-stu-id="13204-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="13204-108">在任何其他程式之外，請使用 `Sub` 語句，後面接著 `End Sub` 語句。</span><span class="sxs-lookup"><span data-stu-id="13204-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="13204-109">在 `Sub` 語句中，在 `Sub` 關鍵字後面加上程式的名稱，然後以括弧括住參數清單。</span><span class="sxs-lookup"><span data-stu-id="13204-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="13204-110">將程式的程式碼語句放在 `Sub` 和 `End Sub` 語句之間。</span><span class="sxs-lookup"><span data-stu-id="13204-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="13204-111">若要建立會傳回值的程式</span><span class="sxs-lookup"><span data-stu-id="13204-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="13204-112">在任何其他程式之外，請使用 `Function` 語句，後面接著 `End Function` 語句。</span><span class="sxs-lookup"><span data-stu-id="13204-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="13204-113">在 `Function` 語句中，請在 `Function` 關鍵字後面加上程式的名稱，然後以括弧括住參數清單，然後再指定傳回值的資料類型 `As` 子句。</span><span class="sxs-lookup"><span data-stu-id="13204-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="13204-114">將程式的程式碼語句放在 `Function` 和 `End Function` 語句之間。</span><span class="sxs-lookup"><span data-stu-id="13204-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="13204-115">使用 `Return` 語句，將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="13204-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="13204-116">將您的新程式與舊的重複程式碼區塊連接</span><span class="sxs-lookup"><span data-stu-id="13204-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="13204-117">請務必將新程式定義在舊程式碼有權存取的位置。</span><span class="sxs-lookup"><span data-stu-id="13204-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="13204-118">在舊的重複程式碼區塊中，以呼叫 `Sub` 或 `Function` 程式的單一語句取代執行重複性工作的語句。</span><span class="sxs-lookup"><span data-stu-id="13204-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="13204-119">如果您的程式是會傳回值的 `Function`，請確定您的呼叫語句會執行具有傳回值的動作，例如將它儲存在變數中，否則值會遺失。</span><span class="sxs-lookup"><span data-stu-id="13204-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="13204-120">範例</span><span class="sxs-lookup"><span data-stu-id="13204-120">Example</span></span>

 <span data-ttu-id="13204-121">下列 `Function` 程式會計算直角三角形的最長邊（或斜邊），並指定其他兩邊的值：</span><span class="sxs-lookup"><span data-stu-id="13204-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="13204-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="13204-122">See also</span></span>

- [<span data-ttu-id="13204-123">程序</span><span class="sxs-lookup"><span data-stu-id="13204-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="13204-124">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="13204-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="13204-125">函式程序</span><span class="sxs-lookup"><span data-stu-id="13204-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="13204-126">屬性程序</span><span class="sxs-lookup"><span data-stu-id="13204-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="13204-127">運算子程序</span><span class="sxs-lookup"><span data-stu-id="13204-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="13204-128">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="13204-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="13204-129">遞迴程序</span><span class="sxs-lookup"><span data-stu-id="13204-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="13204-130">程序多載化</span><span class="sxs-lookup"><span data-stu-id="13204-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="13204-131">物件和類別</span><span class="sxs-lookup"><span data-stu-id="13204-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="13204-132">物件導向程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13204-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
