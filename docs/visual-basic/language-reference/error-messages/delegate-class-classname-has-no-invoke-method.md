---
title: 委派類別 '<classname>' 沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 27be97ba2930791bcb9012c824bc418a0089b037
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409708"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="22a6b-102">委派類別 '\<classname>' 沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標</span><span class="sxs-lookup"><span data-stu-id="22a6b-102">Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="22a6b-103">`Invoke`透過委派的呼叫失敗，因為 `Invoke` 不是在委派類別上執行。</span><span class="sxs-lookup"><span data-stu-id="22a6b-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="22a6b-104">**錯誤識別碼：** BC30220</span><span class="sxs-lookup"><span data-stu-id="22a6b-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="22a6b-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="22a6b-105">To correct this error</span></span>  
  
1. <span data-ttu-id="22a6b-106">請確定已使用語句建立委派類別的實例 `Dim` ，而且已使用運算子將程式指派給委派實例 `AddressOf` 。</span><span class="sxs-lookup"><span data-stu-id="22a6b-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2. <span data-ttu-id="22a6b-107">找出用來執行委派類別的程式碼，並確定它會實作為程式 `Invoke` 。</span><span class="sxs-lookup"><span data-stu-id="22a6b-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a6b-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22a6b-108">See also</span></span>

- [<span data-ttu-id="22a6b-109">委派</span><span class="sxs-lookup"><span data-stu-id="22a6b-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="22a6b-110">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="22a6b-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="22a6b-111">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="22a6b-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="22a6b-112">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="22a6b-112">Dim Statement</span></span>](../statements/dim-statement.md)
