---
title: 委派類別 '<classname>' 沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321298"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="41e65-102">委派類別\<類別名稱 >' 已經沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標</span><span class="sxs-lookup"><span data-stu-id="41e65-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="41e65-103">呼叫`Invoke`透過委派失敗，因為`Invoke`上委派類別未實作。</span><span class="sxs-lookup"><span data-stu-id="41e65-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="41e65-104">**錯誤 ID:** BC30220</span><span class="sxs-lookup"><span data-stu-id="41e65-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41e65-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="41e65-105">To correct this error</span></span>  
  
1. <span data-ttu-id="41e65-106">確保委派類別的執行個體，已經建立具有`Dim`陳述式和程序已被指派委派執行個體，但`AddressOf`運算子。</span><span class="sxs-lookup"><span data-stu-id="41e65-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="41e65-107">找出實作的委派類別的程式碼，並確定它會實作`Invoke`程序。</span><span class="sxs-lookup"><span data-stu-id="41e65-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e65-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41e65-108">See also</span></span>

- [<span data-ttu-id="41e65-109">委派</span><span class="sxs-lookup"><span data-stu-id="41e65-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="41e65-110">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="41e65-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="41e65-111">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="41e65-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="41e65-112">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="41e65-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
