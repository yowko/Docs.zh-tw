---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords: WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="10124-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10124-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="10124-103">指定一或多個宣告的成員變數會參照可引發事件類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="10124-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10124-104">備註</span><span class="sxs-lookup"><span data-stu-id="10124-104">Remarks</span></span>  
 <span data-ttu-id="10124-105">當變數定義使用`WithEvents`，您可以以宣告方式指定，則方法會處理使用的變數的事件`Handles`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="10124-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="10124-106">您可以使用`WithEvents`只能在類別或模組層級。</span><span class="sxs-lookup"><span data-stu-id="10124-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="10124-107">這表示宣告內容`WithEvents`變數必須是類別或模組，而且不能是原始程式檔、 命名空間、 結構、 或程序。</span><span class="sxs-lookup"><span data-stu-id="10124-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="10124-108">您無法使用`WithEvents`結構成員上。</span><span class="sxs-lookup"><span data-stu-id="10124-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="10124-109">您可以宣告只有個別變數 — 不陣列 — 與`WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="10124-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="10124-110">規則</span><span class="sxs-lookup"><span data-stu-id="10124-110">Rules</span></span>  
  
-   <span data-ttu-id="10124-111">**項目型別。**</span><span class="sxs-lookup"><span data-stu-id="10124-111">**Element Types.**</span></span> <span data-ttu-id="10124-112">您必須宣告`WithEvents`為物件變數使其可接受的變數類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="10124-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="10124-113">不過，您無法宣告它們當做`Object`。</span><span class="sxs-lookup"><span data-stu-id="10124-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="10124-114">您必須宣告為可引發事件的特定類別。</span><span class="sxs-lookup"><span data-stu-id="10124-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="10124-115">`WithEvents`修飾詞可用於此內容： [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="10124-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10124-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10124-116">See Also</span></span>  
 [<span data-ttu-id="10124-117">Handles</span><span class="sxs-lookup"><span data-stu-id="10124-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="10124-118">關鍵字</span><span class="sxs-lookup"><span data-stu-id="10124-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="10124-119">事件</span><span class="sxs-lookup"><span data-stu-id="10124-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
