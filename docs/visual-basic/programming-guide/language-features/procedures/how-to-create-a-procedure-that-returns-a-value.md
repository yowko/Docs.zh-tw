---
title: 如何：建立傳回值的程序
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 3d28162d2a2103477a20b08fc03c937de8b5a475
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071868"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="add8a-102">如何：建立傳回值的程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="add8a-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="add8a-103">您可以使用程式 `Function` ，將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="add8a-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="add8a-104">若要建立傳回值的程式</span><span class="sxs-lookup"><span data-stu-id="add8a-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="add8a-105">在任何其他程式之外，請使用 `Function` 語句，然後使用語句 `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="add8a-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="add8a-106">在語句中，以程式的 `Function` `Function` 名稱後面加上關鍵字，然後以括弧括住參數清單。</span><span class="sxs-lookup"><span data-stu-id="add8a-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="add8a-107">在括弧後面加上 `As` 子句，以指定傳回值的資料類型。</span><span class="sxs-lookup"><span data-stu-id="add8a-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="add8a-108">在和語句之間放置程式的程式碼語句 `Function` `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="add8a-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="add8a-109">使用 `Return` 語句將值傳回給呼叫程式碼。</span><span class="sxs-lookup"><span data-stu-id="add8a-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="add8a-110">下列 `Function` 程式會計算出右邊三角形的最長邊（或斜邊），並指定其他兩側的值。</span><span class="sxs-lookup"><span data-stu-id="add8a-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="add8a-111">下列範例顯示一般的呼叫 `hypotenuse` 。</span><span class="sxs-lookup"><span data-stu-id="add8a-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="add8a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="add8a-112">See also</span></span>

- [<span data-ttu-id="add8a-113">程序</span><span class="sxs-lookup"><span data-stu-id="add8a-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="add8a-114">Sub 程序</span><span class="sxs-lookup"><span data-stu-id="add8a-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="add8a-115">屬性程序</span><span class="sxs-lookup"><span data-stu-id="add8a-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="add8a-116">運算子程序</span><span class="sxs-lookup"><span data-stu-id="add8a-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="add8a-117">程序參數和引數</span><span class="sxs-lookup"><span data-stu-id="add8a-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="add8a-118">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="add8a-118">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="add8a-119">如何：傳回程序的值</span><span class="sxs-lookup"><span data-stu-id="add8a-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="add8a-120">如何：呼叫傳回值的程序</span><span class="sxs-lookup"><span data-stu-id="add8a-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
