---
title: HOW TO：建立程序傳回值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: ce0010762374baf5b19ab2e64f50e12fefda2dee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966960"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="213e3-102">HOW TO：建立程序傳回值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="213e3-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="213e3-103">您使用`Function`程序來將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="213e3-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="213e3-104">若要建立傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="213e3-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="213e3-105">任何其他程序外, 使用`Function`陳述式，後面接著`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="213e3-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="213e3-106">在 `Function`陳述式中，遵循`Function`關鍵字的程序，然後按一下 參數清單括號括住名稱。</span><span class="sxs-lookup"><span data-stu-id="213e3-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="213e3-107">括號後面`As`子句來指定傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="213e3-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="213e3-108">放置程序的程式碼陳述式之間`Function`和`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="213e3-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="213e3-109">使用`Return`陳述式來將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="213e3-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="213e3-110">下列`Function`程序會計算已知值的其他兩個邊直角三角形斜邊的最長的側邊。</span><span class="sxs-lookup"><span data-stu-id="213e3-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="213e3-111">下列範例示範的典型呼叫`hypotenuse`。</span><span class="sxs-lookup"><span data-stu-id="213e3-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="213e3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="213e3-112">See also</span></span>
- [<span data-ttu-id="213e3-113">程序</span><span class="sxs-lookup"><span data-stu-id="213e3-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="213e3-114">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="213e3-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="213e3-115">屬性程序</span><span class="sxs-lookup"><span data-stu-id="213e3-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="213e3-116">運算子程序</span><span class="sxs-lookup"><span data-stu-id="213e3-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="213e3-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="213e3-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="213e3-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="213e3-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="213e3-119">如何：從程序傳回值</span><span class="sxs-lookup"><span data-stu-id="213e3-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="213e3-120">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="213e3-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
