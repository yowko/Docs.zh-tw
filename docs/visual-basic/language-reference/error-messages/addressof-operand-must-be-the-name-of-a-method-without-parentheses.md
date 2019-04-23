---
title: AddressOf' 運算元必須是方法名稱 (沒有括號)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323820"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="69e30-102">AddressOf' 運算元必須是方法名稱 (沒有括號)</span><span class="sxs-lookup"><span data-stu-id="69e30-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="69e30-103">`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="69e30-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="69e30-104">語法如下所示。</span><span class="sxs-lookup"><span data-stu-id="69e30-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="69e30-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="69e30-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="69e30-106">插入下列引數括`AddressOf`，沒有任何需要的地方。</span><span class="sxs-lookup"><span data-stu-id="69e30-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="69e30-107">**錯誤 ID:** BC30577</span><span class="sxs-lookup"><span data-stu-id="69e30-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69e30-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="69e30-108">To correct this error</span></span>  
  
1. <span data-ttu-id="69e30-109">移除引數下前後的括號`AddressOf`。</span><span class="sxs-lookup"><span data-stu-id="69e30-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2. <span data-ttu-id="69e30-110">請確定引數的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="69e30-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e30-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69e30-111">See also</span></span>

- [<span data-ttu-id="69e30-112">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="69e30-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="69e30-113">委派</span><span class="sxs-lookup"><span data-stu-id="69e30-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
