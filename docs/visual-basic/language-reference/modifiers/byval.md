---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c192cdb4ac43ad614fbfb663079c03ddc6c358c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="byval-visual-basic"></a><span data-ttu-id="da2d6-102">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da2d6-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="da2d6-103">指定的引數會傳遞的方式呼叫的程序或屬性無法變更呼叫的程式碼中引數的基礎變數的值。</span><span class="sxs-lookup"><span data-stu-id="da2d6-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da2d6-104">備註</span><span class="sxs-lookup"><span data-stu-id="da2d6-104">Remarks</span></span>  
 <span data-ttu-id="da2d6-105">`ByVal` 修飾詞可用於以下內容：</span><span class="sxs-lookup"><span data-stu-id="da2d6-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="da2d6-106">Declare 陳述式</span><span class="sxs-lookup"><span data-stu-id="da2d6-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="da2d6-107">Function 陳述式</span><span class="sxs-lookup"><span data-stu-id="da2d6-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="da2d6-108">Operator 陳述式</span><span class="sxs-lookup"><span data-stu-id="da2d6-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="da2d6-109">Property 陳述式</span><span class="sxs-lookup"><span data-stu-id="da2d6-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="da2d6-110">Sub 陳述式</span><span class="sxs-lookup"><span data-stu-id="da2d6-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="da2d6-111">範例</span><span class="sxs-lookup"><span data-stu-id="da2d6-111">Example</span></span>  
 <span data-ttu-id="da2d6-112">下列範例示範如何使用`ByVal`參數傳遞參考型別引數的機制。</span><span class="sxs-lookup"><span data-stu-id="da2d6-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="da2d6-113">在此範例中，引數是`c1`，類別的執行個體`Class1`。</span><span class="sxs-lookup"><span data-stu-id="da2d6-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="da2d6-114">`ByVal`防止變更基礎值的參考引數中的程序的程式碼`c1`，但不會保護的可存取的欄位和屬性`c1`。</span><span class="sxs-lookup"><span data-stu-id="da2d6-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="da2d6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da2d6-115">See Also</span></span>  
 [<span data-ttu-id="da2d6-116">關鍵字</span><span class="sxs-lookup"><span data-stu-id="da2d6-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="da2d6-117">以傳值和傳址方式傳遞引數</span><span class="sxs-lookup"><span data-stu-id="da2d6-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
