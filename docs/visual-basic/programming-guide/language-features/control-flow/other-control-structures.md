---
title: "其他控制結構 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8f8bd57f193be0d7f410f7325355ffc47ab10e3f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="4f043-102">其他控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f043-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="4f043-103">提供可協助您控制結構處置資源，或減少您必須重複執行的物件參考的次數。</span><span class="sxs-lookup"><span data-stu-id="4f043-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="4f043-104">使用...結束使用結構</span><span class="sxs-lookup"><span data-stu-id="4f043-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="4f043-105">`Using...End Using`建構建立陳述式區塊，請在其中使用的 SQL 連線之類的資源。</span><span class="sxs-lookup"><span data-stu-id="4f043-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="4f043-106">您可以選擇性地取得與資源`Using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="4f043-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="4f043-107">當您結束`Using`區塊，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使其可供其他程式碼以使用自動處置資源。</span><span class="sxs-lookup"><span data-stu-id="4f043-107">When you exit the `Using` block, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="4f043-108">資源必須是本機和可處置。</span><span class="sxs-lookup"><span data-stu-id="4f043-108">The resource must be local and disposable.</span></span> <span data-ttu-id="4f043-109">如需詳細資訊，請參閱[Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4f043-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="4f043-110">與...結尾結構</span><span class="sxs-lookup"><span data-stu-id="4f043-110">With...End With Construction</span></span>  
 <span data-ttu-id="4f043-111">`With...End With`建構可讓您一次指定的物件參考，然後再執行一系列的陳述式來存取其成員。</span><span class="sxs-lookup"><span data-stu-id="4f043-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="4f043-112">這可以簡化您的程式碼，並改善效能，因為[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不需要重新建立每個陳述式中存取它的參考。</span><span class="sxs-lookup"><span data-stu-id="4f043-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="4f043-113">如需詳細資訊，請參閱[與...With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="4f043-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f043-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f043-114">See Also</span></span>  
 <span data-ttu-id="4f043-115">[控制流程](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span><span class="sxs-lookup"><span data-stu-id="4f043-115">[Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md) </span></span>  
<span data-ttu-id="4f043-116"> [決策結構](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="4f043-116"> [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="4f043-117"> [迴圈結構](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="4f043-117"> [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="4f043-118"> [巢狀的控制結構](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="4f043-118"> [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="4f043-119"> [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4f043-119"> [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md) </span></span>  
<span data-ttu-id="4f043-120"> [With...End With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="4f043-120"> [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span></span>
