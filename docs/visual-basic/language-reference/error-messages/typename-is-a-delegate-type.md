---
title: "'<typename>' 是委派類型"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4278ea0fc6a8dc2c6a90b720d2da70b1c26f2a17
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283448"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="d7713-102">'\<類型名稱 >' 是委派型別</span><span class="sxs-lookup"><span data-stu-id="d7713-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="d7713-103">'\<類型名稱 >' 是委派型別。</span><span class="sxs-lookup"><span data-stu-id="d7713-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="d7713-104">委派建構允許只使用單一 AddressOf 運算式做為引數清單。</span><span class="sxs-lookup"><span data-stu-id="d7713-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="d7713-105">通常可以使用 AddressOf 運算式，而不是委派建構。</span><span class="sxs-lookup"><span data-stu-id="d7713-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="d7713-106">A`New`子句建立委派類別的執行個體提供無效的引數清單之委派建構函式。</span><span class="sxs-lookup"><span data-stu-id="d7713-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="d7713-107">您可以提供只會有一個`AddressOf`運算式建立新的委派執行個體時。</span><span class="sxs-lookup"><span data-stu-id="d7713-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="d7713-108">如果您沒有傳遞任何引數的委派建構函式，如果傳遞多個引數，或如果您傳遞單一引數，不是有效，此錯誤可能會造成`AddressOf`運算式。</span><span class="sxs-lookup"><span data-stu-id="d7713-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="d7713-109">**錯誤 ID:** BC32008</span><span class="sxs-lookup"><span data-stu-id="d7713-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d7713-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d7713-110">To correct this error</span></span>  
  
-   <span data-ttu-id="d7713-111">使用單一`AddressOf`委派類別中的引數清單中的運算式`New`子句。</span><span class="sxs-lookup"><span data-stu-id="d7713-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7713-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7713-112">See also</span></span>
- [<span data-ttu-id="d7713-113">New 運算子</span><span class="sxs-lookup"><span data-stu-id="d7713-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="d7713-114">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="d7713-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="d7713-115">委派</span><span class="sxs-lookup"><span data-stu-id="d7713-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="d7713-116">如何：叫用委派方法</span><span class="sxs-lookup"><span data-stu-id="d7713-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
