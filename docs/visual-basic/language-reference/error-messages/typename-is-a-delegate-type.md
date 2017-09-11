---
title: "&quot;&lt;typename&gt;&quot; 是委派型別 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
dev_langs:
- VB
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
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
ms.openlocfilehash: 55532e269a7d6756157d324a2db14320df5d3f55
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="12808-102">'&lt;typename&gt;' 是委派型別</span><span class="sxs-lookup"><span data-stu-id="12808-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="12808-103">'\<typename >' 是委派型別。</span><span class="sxs-lookup"><span data-stu-id="12808-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="12808-104">委派建構允許只有單一 AddressOf 運算式做為引數清單。</span><span class="sxs-lookup"><span data-stu-id="12808-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="12808-105">通常可以使用 AddressOf 運算式，而不是委派建構。</span><span class="sxs-lookup"><span data-stu-id="12808-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="12808-106">A`New`子句建立委派類別的執行個體無效的引數清單提供給委派建構函式。</span><span class="sxs-lookup"><span data-stu-id="12808-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="12808-107">您可以提供只會有一個`AddressOf`運算式時建立新的委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="12808-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="12808-108">如果您沒有傳遞任何引數的委派建構函式，如果您傳遞多個引數，或如果您傳遞單一引數，不是有效，此錯誤可能會造成`AddressOf`運算式。</span><span class="sxs-lookup"><span data-stu-id="12808-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="12808-109">**錯誤識別碼︰** BC32008</span><span class="sxs-lookup"><span data-stu-id="12808-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="12808-110">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="12808-110">To correct this error</span></span>  
  
-   <span data-ttu-id="12808-111">使用單一`AddressOf`委派類別中的引數清單中的運算式`New`子句。</span><span class="sxs-lookup"><span data-stu-id="12808-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12808-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12808-112">See Also</span></span>  
 <span data-ttu-id="12808-113">[New 運算子](../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="12808-113">[New Operator](../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
<span data-ttu-id="12808-114"> [AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="12808-114"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="12808-115"> [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="12808-115"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="12808-116"> [如何：叫用委派方法](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span><span class="sxs-lookup"><span data-stu-id="12808-116"> [How to: Invoke a Delegate Method](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span></span>
