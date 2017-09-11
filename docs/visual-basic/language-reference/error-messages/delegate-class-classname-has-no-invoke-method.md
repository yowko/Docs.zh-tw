---
title: "委派類別&lt;classname&gt;&quot; 有沒有 Invoke 方法，所以此類型的運算式不可成為方法呼叫的目標 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
dev_langs:
- VB
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
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
ms.openlocfilehash: 54cd62bc2b4cafa89873728ba4e5b31c46f1aab1
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="09e7f-102">委派類別&lt;classname&gt;' 有沒有 Invoke 方法，所以此類型的運算式不可成為方法呼叫的目標</span><span class="sxs-lookup"><span data-stu-id="09e7f-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="09e7f-103">呼叫`Invoke`透過委派失敗，因為`Invoke`委派類別未實作。</span><span class="sxs-lookup"><span data-stu-id="09e7f-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="09e7f-104">**錯誤識別碼︰** BC30220</span><span class="sxs-lookup"><span data-stu-id="09e7f-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="09e7f-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="09e7f-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="09e7f-106">確定委派類別的執行個體已建立並`Dim`陳述式和程序已被指派委派執行個體，但`AddressOf`運算子。</span><span class="sxs-lookup"><span data-stu-id="09e7f-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="09e7f-107">找出實作委派類別的程式碼，並確定它會實作`Invoke`程序。</span><span class="sxs-lookup"><span data-stu-id="09e7f-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e7f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09e7f-108">See Also</span></span>  
 <span data-ttu-id="09e7f-109">[委派](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="09e7f-109">[Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="09e7f-110"> [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="09e7f-110"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="09e7f-111"> [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="09e7f-111"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="09e7f-112"> [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="09e7f-112"> [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>
