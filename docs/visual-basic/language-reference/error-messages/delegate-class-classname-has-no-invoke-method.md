---
title: 委派類別 '<classname>' 沒有 Invoke 方法，因此這個類型的運算式不可成為方法呼叫的目標
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 4e0fc61c7356008755134f670fa1fab0165cfd48
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162787"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="6f8fa-102">BC30220：委派類別 ' \<classname> ' 沒有 Invoke 方法，因此這個類型的運算式不可以是方法呼叫的目標</span><span class="sxs-lookup"><span data-stu-id="6f8fa-102">BC30220: Delegate class '\<classname>' has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>

<span data-ttu-id="6f8fa-103">`Invoke`透過委派的呼叫失敗，因為未 `Invoke` 在委派類別上執行。</span><span class="sxs-lookup"><span data-stu-id="6f8fa-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>

 <span data-ttu-id="6f8fa-104">**錯誤識別碼：** BC30220</span><span class="sxs-lookup"><span data-stu-id="6f8fa-104">**Error ID:** BC30220</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6f8fa-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6f8fa-105">To correct this error</span></span>

1. <span data-ttu-id="6f8fa-106">確定已使用語句建立委派類別的實例 `Dim` ，而且已使用運算子將程式指派給委派實例 `AddressOf` 。</span><span class="sxs-lookup"><span data-stu-id="6f8fa-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>

2. <span data-ttu-id="6f8fa-107">找出可執行委派類別的程式碼，並確定它會執行程式 `Invoke` 。</span><span class="sxs-lookup"><span data-stu-id="6f8fa-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f8fa-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f8fa-108">See also</span></span>

- [<span data-ttu-id="6f8fa-109">委派</span><span class="sxs-lookup"><span data-stu-id="6f8fa-109">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="6f8fa-110">Delegate 陳述式</span><span class="sxs-lookup"><span data-stu-id="6f8fa-110">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="6f8fa-111">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="6f8fa-111">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="6f8fa-112">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="6f8fa-112">Dim Statement</span></span>](../statements/dim-statement.md)
