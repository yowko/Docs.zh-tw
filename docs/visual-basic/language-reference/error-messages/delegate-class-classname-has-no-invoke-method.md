---
title: 委派類別 '<classname>' 沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: e6ad06262806088347c94b3040b743618a3b3695
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874494"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="9f929-102">委派類別 '\<classname>' 沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標</span><span class="sxs-lookup"><span data-stu-id="9f929-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>

<span data-ttu-id="9f929-103">`Invoke`透過委派的呼叫失敗，因為未 `Invoke` 在委派類別上執行。</span><span class="sxs-lookup"><span data-stu-id="9f929-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="9f929-104">**錯誤識別碼：** BC30220</span><span class="sxs-lookup"><span data-stu-id="9f929-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9f929-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9f929-105">To correct this error</span></span>  
  
1. <span data-ttu-id="9f929-106">確定已使用語句建立委派類別的實例 `Dim` ，而且已使用運算子將程式指派給委派實例 `AddressOf` 。</span><span class="sxs-lookup"><span data-stu-id="9f929-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="9f929-107">找出可執行委派類別的程式碼，並確定它會執行程式 `Invoke` 。</span><span class="sxs-lookup"><span data-stu-id="9f929-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f929-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f929-108">See also</span></span>

- [<span data-ttu-id="9f929-109">委派</span><span class="sxs-lookup"><span data-stu-id="9f929-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="9f929-110">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="9f929-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="9f929-111">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="9f929-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="9f929-112">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="9f929-112">Dim Statement</span></span>](../statements/dim-statement.md)
