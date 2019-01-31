---
title: AddressOf' 運算元必須是方法名稱 (沒有括號)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 37b02ab76730458b757835fda37b8cb145ed93ad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262110"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="c53c6-102">AddressOf' 運算元必須是方法名稱 (沒有括號)</span><span class="sxs-lookup"><span data-stu-id="c53c6-102">'AddressOf' operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="c53c6-103">`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="c53c6-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="c53c6-104">語法如下所示。</span><span class="sxs-lookup"><span data-stu-id="c53c6-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="c53c6-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="c53c6-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="c53c6-106">插入下列引數括`AddressOf`，沒有任何需要的地方。</span><span class="sxs-lookup"><span data-stu-id="c53c6-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="c53c6-107">**錯誤 ID:** BC30577</span><span class="sxs-lookup"><span data-stu-id="c53c6-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c53c6-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="c53c6-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c53c6-109">移除引數下前後的括號`AddressOf`。</span><span class="sxs-lookup"><span data-stu-id="c53c6-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="c53c6-110">請確定引數的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="c53c6-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c53c6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c53c6-111">See also</span></span>
- [<span data-ttu-id="c53c6-112">AddressOf 運算子</span><span class="sxs-lookup"><span data-stu-id="c53c6-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="c53c6-113">委派</span><span class="sxs-lookup"><span data-stu-id="c53c6-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
