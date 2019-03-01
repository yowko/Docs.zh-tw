---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: edee47e41ca78175a6fb24ed5eac255c03de0901
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972554"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="98785-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98785-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="98785-103">指定呼叫的程序或屬性無法變更基礎呼叫程式碼中的引數的變數值的方式傳遞引數。</span><span class="sxs-lookup"><span data-stu-id="98785-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98785-104">備註</span><span class="sxs-lookup"><span data-stu-id="98785-104">Remarks</span></span>  
 <span data-ttu-id="98785-105">
  `ByVal\` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="98785-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="98785-106">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="98785-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="98785-107">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="98785-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="98785-108">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="98785-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="98785-109">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="98785-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="98785-110">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="98785-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="98785-111">範例</span><span class="sxs-lookup"><span data-stu-id="98785-111">Example</span></span>  
 <span data-ttu-id="98785-112">下列範例示範如何使用`ByVal`參數傳遞參考型別引數的機制。</span><span class="sxs-lookup"><span data-stu-id="98785-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="98785-113">在此範例中，引數是`c1`，類別的執行個體`Class1`。</span><span class="sxs-lookup"><span data-stu-id="98785-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="98785-114">`ByVal` 防止程序中的程式碼變更基礎值的參考引數`c1`，但不會保護的可存取的欄位和屬性`c1`。</span><span class="sxs-lookup"><span data-stu-id="98785-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="98785-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98785-115">See also</span></span>
- [<span data-ttu-id="98785-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="98785-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="98785-117">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="98785-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
