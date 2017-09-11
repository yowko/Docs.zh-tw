---
title: "AddressOf&quot; 運算元必須是 （沒有括號） 的方法名稱 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
dev_langs:
- VB
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 10
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
ms.openlocfilehash: c4ee57896b70d8af1a7bc245bdb45521c2442fea
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="ef6bb-102">AddressOf' 運算元必須是方法的 （沒有括號） 名稱</span><span class="sxs-lookup"><span data-stu-id="ef6bb-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="ef6bb-103">`AddressOf` 運算子會建立參考特定程序的程序委派執行個體。</span><span class="sxs-lookup"><span data-stu-id="ef6bb-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="ef6bb-104">語法為，如下所示。</span><span class="sxs-lookup"><span data-stu-id="ef6bb-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="ef6bb-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="ef6bb-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="ef6bb-106">插入下列引數括`AddressOf`，不需要的地方。</span><span class="sxs-lookup"><span data-stu-id="ef6bb-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="ef6bb-107">**錯誤識別碼︰** BC30577</span><span class="sxs-lookup"><span data-stu-id="ef6bb-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ef6bb-108">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ef6bb-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="ef6bb-109">移除引數下前後的括號`AddressOf`。</span><span class="sxs-lookup"><span data-stu-id="ef6bb-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="ef6bb-110">請確定引數是方法名稱。</span><span class="sxs-lookup"><span data-stu-id="ef6bb-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6bb-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef6bb-111">See Also</span></span>  
 <span data-ttu-id="ef6bb-112">[AddressOf 運算子](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="ef6bb-112">[AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="ef6bb-113"> [委派](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="ef6bb-113"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span></span>
