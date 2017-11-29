---
title: "其他控制結構 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="44c16-102">其他控制結構 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44c16-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="44c16-103">提供可協助您控制結構的資源處置或減少您必須重複的物件參考的次數。</span><span class="sxs-lookup"><span data-stu-id="44c16-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="44c16-104">使用...使用建構的結束</span><span class="sxs-lookup"><span data-stu-id="44c16-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="44c16-105">`Using...End Using`建構會建立陳述式區塊，請在其中使用的資源，例如 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="44c16-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="44c16-106">您可以選擇性地取得的資源`Using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="44c16-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="44c16-107">當您結束`Using`區塊，[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]使其可供其他程式碼以使用自動處置資源。</span><span class="sxs-lookup"><span data-stu-id="44c16-107">When you exit the `Using` block, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="44c16-108">資源必須是本機和處置。</span><span class="sxs-lookup"><span data-stu-id="44c16-108">The resource must be local and disposable.</span></span> <span data-ttu-id="44c16-109">如需詳細資訊，請參閱 [Using 陳述式](../../../../visual-basic/language-reference/statements/using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="44c16-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="44c16-110">與...建構的結尾</span><span class="sxs-lookup"><span data-stu-id="44c16-110">With...End With Construction</span></span>  
 <span data-ttu-id="44c16-111">`With...End With`建構可讓您一次指定的物件參考，然後再執行一系列陳述式來存取其成員。</span><span class="sxs-lookup"><span data-stu-id="44c16-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="44c16-112">這可以簡化您的程式碼，並改善效能，因為[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]不需要重新建立每個陳述式會存取它的參考。</span><span class="sxs-lookup"><span data-stu-id="44c16-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="44c16-113">如需詳細資訊，請參閱[與...With 陳述式](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="44c16-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c16-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44c16-114">See Also</span></span>  
 [<span data-ttu-id="44c16-115">控制流程</span><span class="sxs-lookup"><span data-stu-id="44c16-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="44c16-116">決策結構</span><span class="sxs-lookup"><span data-stu-id="44c16-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="44c16-117">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="44c16-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="44c16-118">巢狀控制結構</span><span class="sxs-lookup"><span data-stu-id="44c16-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="44c16-119">Using 陳述式</span><span class="sxs-lookup"><span data-stu-id="44c16-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="44c16-120">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="44c16-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
