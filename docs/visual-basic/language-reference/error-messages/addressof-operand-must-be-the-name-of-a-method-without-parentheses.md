---
title: '&#39;AddressOf&#39;運算元必須是 （沒有括號） 的方法名稱'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583808"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="e1de9-102">&#39;AddressOf&#39;運算元必須是 （沒有括號） 的方法名稱</span><span class="sxs-lookup"><span data-stu-id="e1de9-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="e1de9-103">`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1de9-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="e1de9-104">語法如下所示。</span><span class="sxs-lookup"><span data-stu-id="e1de9-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="e1de9-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="e1de9-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="e1de9-106">插入括弧括住引數下`AddressOf`，沒有任何需要的地方。</span><span class="sxs-lookup"><span data-stu-id="e1de9-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="e1de9-107">**錯誤 ID:** BC30577</span><span class="sxs-lookup"><span data-stu-id="e1de9-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e1de9-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="e1de9-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="e1de9-109">移除引數下前後的括號`AddressOf`。</span><span class="sxs-lookup"><span data-stu-id="e1de9-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="e1de9-110">請確定引數是方法名稱。</span><span class="sxs-lookup"><span data-stu-id="e1de9-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1de9-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1de9-111">See Also</span></span>  
 [<span data-ttu-id="e1de9-112">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="e1de9-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="e1de9-113">委派</span><span class="sxs-lookup"><span data-stu-id="e1de9-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
