---
title: "如何：建立傳回值的程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="45435-102">如何：建立傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45435-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="45435-103">您使用`Function`程序來將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="45435-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="45435-104">若要建立程序傳回值</span><span class="sxs-lookup"><span data-stu-id="45435-104">To create a procedure that returns a value</span></span>  
  
1.  <span data-ttu-id="45435-105">任何其他程序，之外使用`Function`陳述式，後面接著`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="45435-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2.  <span data-ttu-id="45435-106">在`Function`陳述式，請遵循`Function`關鍵字與程序，然後按一下 參數清單括號括住的名稱。</span><span class="sxs-lookup"><span data-stu-id="45435-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="45435-107">括號後面`As`子句來指定傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="45435-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4.  <span data-ttu-id="45435-108">放置程序的程式碼陳述式之間`Function`和`End Function`陳述式。</span><span class="sxs-lookup"><span data-stu-id="45435-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5.  <span data-ttu-id="45435-109">使用`Return`陳述式來將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="45435-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="45435-110">下列`Function`已知值的其他兩個邊直角三角形斜邊的最長邊，程序會計算。</span><span class="sxs-lookup"><span data-stu-id="45435-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     <span data-ttu-id="45435-111">下列範例會示範一般呼叫`hypotenuse`。</span><span class="sxs-lookup"><span data-stu-id="45435-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="45435-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45435-112">See Also</span></span>  
 [<span data-ttu-id="45435-113">程序</span><span class="sxs-lookup"><span data-stu-id="45435-113">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="45435-114">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="45435-114">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="45435-115">屬性程序</span><span class="sxs-lookup"><span data-stu-id="45435-115">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="45435-116">運算子程序</span><span class="sxs-lookup"><span data-stu-id="45435-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="45435-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="45435-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="45435-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="45435-118">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="45435-119">如何：傳回程序的值</span><span class="sxs-lookup"><span data-stu-id="45435-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="45435-120">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="45435-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
