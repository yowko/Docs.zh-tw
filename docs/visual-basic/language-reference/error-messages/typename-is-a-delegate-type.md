---
title: "'<typename>' 是委派類型"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: dcb52188c53b38ac14de0002b5212bb33c9f7203
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161773"
---
# <a name="bc32008-typename-is-a-delegate-type"></a><span data-ttu-id="2d625-102">BC32008： ' \<typename> ' 是委派類型</span><span class="sxs-lookup"><span data-stu-id="2d625-102">BC32008: '\<typename>' is a delegate type</span></span>

<span data-ttu-id="2d625-103">' \<typename> ' 是委派型別。</span><span class="sxs-lookup"><span data-stu-id="2d625-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="2d625-104">委派結構只允許單一 AddressOf 運算式作為引數清單。</span><span class="sxs-lookup"><span data-stu-id="2d625-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="2d625-105">您通常可以使用 AddressOf 運算式，而不是委派結構。</span><span class="sxs-lookup"><span data-stu-id="2d625-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>

 <span data-ttu-id="2d625-106">`New`建立委派類別實例的子句會提供不正確引數清單給委派的函式。</span><span class="sxs-lookup"><span data-stu-id="2d625-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>

 <span data-ttu-id="2d625-107">`AddressOf`建立新的委派實例時，您只能提供單一運算式。</span><span class="sxs-lookup"><span data-stu-id="2d625-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>

 <span data-ttu-id="2d625-108">如果您傳遞一個以上的引數，或傳遞的單一引數不是有效的運算式，就會產生這個錯誤 `AddressOf` 。</span><span class="sxs-lookup"><span data-stu-id="2d625-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>

 <span data-ttu-id="2d625-109">**錯誤識別碼：** BC32008</span><span class="sxs-lookup"><span data-stu-id="2d625-109">**Error ID:** BC32008</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2d625-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2d625-110">To correct this error</span></span>

- <span data-ttu-id="2d625-111">在 `AddressOf` 子句中使用委派類別的引數清單中的單一運算式 `New` 。</span><span class="sxs-lookup"><span data-stu-id="2d625-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d625-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d625-112">See also</span></span>

- [<span data-ttu-id="2d625-113">New 運算子</span><span class="sxs-lookup"><span data-stu-id="2d625-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="2d625-114">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="2d625-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="2d625-115">委派</span><span class="sxs-lookup"><span data-stu-id="2d625-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="2d625-116">如何：叫用委派方法</span><span class="sxs-lookup"><span data-stu-id="2d625-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
