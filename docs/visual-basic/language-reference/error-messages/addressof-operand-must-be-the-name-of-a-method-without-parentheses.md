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
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323820"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="2723c-102">AddressOf' 運算元必須是方法名稱 (沒有括號)</span><span class="sxs-lookup"><span data-stu-id="2723c-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="2723c-103">`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="2723c-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="2723c-104">語法如下所示。</span><span class="sxs-lookup"><span data-stu-id="2723c-104">The syntax is as follows.</span></span>  
  
 `AddressOf` `procedurename`  
  
 <span data-ttu-id="2723c-105">插入下列引數括`AddressOf`，沒有任何需要的地方。</span><span class="sxs-lookup"><span data-stu-id="2723c-105">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="2723c-106">**錯誤 ID:** BC30577</span><span class="sxs-lookup"><span data-stu-id="2723c-106">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2723c-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="2723c-107">To correct this error</span></span>  
  
1. <span data-ttu-id="2723c-108">移除引數下前後的括號`AddressOf`。</span><span class="sxs-lookup"><span data-stu-id="2723c-108">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2. <span data-ttu-id="2723c-109">請確定引數的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="2723c-109">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2723c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2723c-110">See also</span></span>

- [<span data-ttu-id="2723c-111">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="2723c-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="2723c-112">委派</span><span class="sxs-lookup"><span data-stu-id="2723c-112">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
