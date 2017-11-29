---
title: "委派類別 &#39;&lt;classname&gt;&#39; 已沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords: BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="f5c0a-102">委派類別 &#39;&lt;classname&gt;&#39; 已沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標</span><span class="sxs-lookup"><span data-stu-id="f5c0a-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="f5c0a-103">呼叫`Invoke`透過委派失敗，因為`Invoke`委派類別未實作。</span><span class="sxs-lookup"><span data-stu-id="f5c0a-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="f5c0a-104">**錯誤 ID:** BC30220</span><span class="sxs-lookup"><span data-stu-id="f5c0a-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f5c0a-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f5c0a-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="f5c0a-106">請確定委派類別的執行個體已建立具有`Dim`陳述式和程序已被指派委派執行個體，但`AddressOf`運算子。</span><span class="sxs-lookup"><span data-stu-id="f5c0a-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="f5c0a-107">找出實作委派類別的程式碼，並確定它會實作`Invoke`程序。</span><span class="sxs-lookup"><span data-stu-id="f5c0a-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c0a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5c0a-108">See Also</span></span>  
 [<span data-ttu-id="f5c0a-109">委派</span><span class="sxs-lookup"><span data-stu-id="f5c0a-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="f5c0a-110">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="f5c0a-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="f5c0a-111">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="f5c0a-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="f5c0a-112">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="f5c0a-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
