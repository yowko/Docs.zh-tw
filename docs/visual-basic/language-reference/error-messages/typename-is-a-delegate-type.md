---
title: "'<typename>' 是委派類型"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 7056bbf2b4de26feba3bfbe0e02b3239311271c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382168"
---
# <a name="typename-is-a-delegate-type"></a><span data-ttu-id="49550-102">'\<typename>' 是委派類型</span><span class="sxs-lookup"><span data-stu-id="49550-102">'\<typename>' is a delegate type</span></span>
<span data-ttu-id="49550-103">' \<typename> ' 是委派類型。</span><span class="sxs-lookup"><span data-stu-id="49550-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="49550-104">委派結構只允許單一 AddressOf 運算式做為引數清單。</span><span class="sxs-lookup"><span data-stu-id="49550-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="49550-105">您通常可以使用 AddressOf 運算式，而不是委派結構。</span><span class="sxs-lookup"><span data-stu-id="49550-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="49550-106">`New`建立委派類別之實例的子句會提供不正確引數清單給委派的函式。</span><span class="sxs-lookup"><span data-stu-id="49550-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="49550-107">`AddressOf`建立新的委派實例時，您只能提供單一運算式。</span><span class="sxs-lookup"><span data-stu-id="49550-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="49550-108">如果您傳遞多個引數，或是傳遞不是有效運算式的單一引數，則不會將任何引數傳遞至委派的函式時，就會產生這個錯誤 `AddressOf` 。</span><span class="sxs-lookup"><span data-stu-id="49550-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="49550-109">**錯誤識別碼：** BC32008</span><span class="sxs-lookup"><span data-stu-id="49550-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49550-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="49550-110">To correct this error</span></span>  
  
- <span data-ttu-id="49550-111">在子句的 `AddressOf` 委派類別中，使用引數清單中的單一運算式 `New` 。</span><span class="sxs-lookup"><span data-stu-id="49550-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49550-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49550-112">See also</span></span>

- [<span data-ttu-id="49550-113">New 運算子</span><span class="sxs-lookup"><span data-stu-id="49550-113">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="49550-114">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="49550-114">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="49550-115">委派</span><span class="sxs-lookup"><span data-stu-id="49550-115">Delegates</span></span>](../../programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="49550-116">如何：叫用委派方法</span><span class="sxs-lookup"><span data-stu-id="49550-116">How to: Invoke a Delegate Method</span></span>](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
