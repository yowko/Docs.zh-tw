---
title: "&#39;&lt;typename&gt;&#39; 是委派型別"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords: BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="6dd79-102">&#39;&lt;typename&gt;&#39; 是委派型別</span><span class="sxs-lookup"><span data-stu-id="6dd79-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="6dd79-103">'\<類型名稱 >' 是委派型別。</span><span class="sxs-lookup"><span data-stu-id="6dd79-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="6dd79-104">委派建構允許只有單一 AddressOf 運算式作為引數清單。</span><span class="sxs-lookup"><span data-stu-id="6dd79-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="6dd79-105">通常可以使用 AddressOf 運算式，而不是委派建構。</span><span class="sxs-lookup"><span data-stu-id="6dd79-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="6dd79-106">A`New`子句建立委派類別的執行個體提供給委派建構函式無效的引數清單。</span><span class="sxs-lookup"><span data-stu-id="6dd79-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="6dd79-107">您可以提供只有一個`AddressOf`運算式建立新的委派執行個體時。</span><span class="sxs-lookup"><span data-stu-id="6dd79-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="6dd79-108">如果您沒有傳遞任何引數的委派建構函式，如果您將多個引數，或如果傳遞單一引數，不是有效，此錯誤可能會造成`AddressOf`運算式。</span><span class="sxs-lookup"><span data-stu-id="6dd79-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="6dd79-109">**錯誤 ID:** BC32008</span><span class="sxs-lookup"><span data-stu-id="6dd79-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6dd79-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="6dd79-110">To correct this error</span></span>  
  
-   <span data-ttu-id="6dd79-111">使用單一`AddressOf`委派類別中的引數清單中的運算式`New`子句。</span><span class="sxs-lookup"><span data-stu-id="6dd79-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd79-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dd79-112">See Also</span></span>  
 [<span data-ttu-id="6dd79-113">New 運算子</span><span class="sxs-lookup"><span data-stu-id="6dd79-113">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="6dd79-114">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="6dd79-114">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="6dd79-115">委派</span><span class="sxs-lookup"><span data-stu-id="6dd79-115">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="6dd79-116">如何：叫用委派方法</span><span class="sxs-lookup"><span data-stu-id="6dd79-116">How to: Invoke a Delegate Method</span></span>](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
