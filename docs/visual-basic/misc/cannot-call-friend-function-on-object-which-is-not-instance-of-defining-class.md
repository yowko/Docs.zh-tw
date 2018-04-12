---
title: 無法在不是定義類別執行個體的物件上呼叫 Friend 函式
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2f1ac1ea14efb0cdf0d8ca03257e4da33d35e368
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="ca2a8-102">無法在不是定義類別執行個體的物件上呼叫 Friend 函式</span><span class="sxs-lookup"><span data-stu-id="ca2a8-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="ca2a8-103">可能是您嘗試呼叫類別的 `Friend` 程序，或嘗試存取跨處理序或跨執行緒的 `Friend` 屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="ca2a8-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="ca2a8-104">`Friend` 程序可以從類別外部的模組呼叫，但其為已定義類別之專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="ca2a8-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca2a8-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ca2a8-105">To correct this error</span></span>  
  
-   <span data-ttu-id="ca2a8-106">確定您從屬於已定義類別之專案的模組，呼叫或存取程序。</span><span class="sxs-lookup"><span data-stu-id="ca2a8-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca2a8-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca2a8-107">See Also</span></span>  
 [<span data-ttu-id="ca2a8-108">Friend</span><span class="sxs-lookup"><span data-stu-id="ca2a8-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
