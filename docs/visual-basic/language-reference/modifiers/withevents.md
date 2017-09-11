---
title: "WithEvents (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
dev_langs:
- VB
helpviewer_keywords:
- WithEvents keyword
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
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
ms.openlocfilehash: b956f8f0d6f0a2fd9f41c5df6d6c82b43fa09018
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="withevents-visual-basic"></a><span data-ttu-id="eaada-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eaada-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="eaada-103">指定一或多個宣告的成員變數參考可以引發事件的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="eaada-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eaada-104">備註</span><span class="sxs-lookup"><span data-stu-id="eaada-104">Remarks</span></span>  
 <span data-ttu-id="eaada-105">當變數定義使用`WithEvents`，您可以以宣告方式指定，則方法會處理使用變數的事件`Handles`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="eaada-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="eaada-106">您可以使用`WithEvents`只能在類別或模組層級。</span><span class="sxs-lookup"><span data-stu-id="eaada-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="eaada-107">這表示宣告內容`WithEvents`變數必須是類別或模組，且不能原始程式檔、 命名空間、 結構或程序。</span><span class="sxs-lookup"><span data-stu-id="eaada-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="eaada-108">您不能使用`WithEvents`結構成員上。</span><span class="sxs-lookup"><span data-stu-id="eaada-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="eaada-109">您可以宣告只有個別變數 — 不陣列 — 與`WithEvents`。</span><span class="sxs-lookup"><span data-stu-id="eaada-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="eaada-110">規則</span><span class="sxs-lookup"><span data-stu-id="eaada-110">Rules</span></span>  
  
-   <span data-ttu-id="eaada-111">**項目型別。**</span><span class="sxs-lookup"><span data-stu-id="eaada-111">**Element Types.**</span></span> <span data-ttu-id="eaada-112">您必須宣告`WithEvents`變數是物件變數，如此可以接受以類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eaada-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="eaada-113">不過，您無法宣告這些`Object`。</span><span class="sxs-lookup"><span data-stu-id="eaada-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="eaada-114">您必須宣告為可引發事件的特定類別。</span><span class="sxs-lookup"><span data-stu-id="eaada-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="eaada-115">`WithEvents`修飾詞可用於此內容︰ [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="eaada-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaada-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaada-116">See Also</span></span>  
 <span data-ttu-id="eaada-117">[控制代碼](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="eaada-117">[Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="eaada-118"> [關鍵字](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="eaada-118"> [Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="eaada-119"> [事件](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="eaada-119"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
