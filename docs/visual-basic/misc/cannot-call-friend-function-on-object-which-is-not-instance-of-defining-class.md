---
title: 無法在不是定義類別執行個體的物件上呼叫 Friend 函式
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a227e5761bacc36c0682844a833e70c34582a5d3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622599"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="f8bf7-102">無法在不是定義類別執行個體的物件上呼叫 Friend 函式</span><span class="sxs-lookup"><span data-stu-id="f8bf7-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="f8bf7-103">可能是您嘗試呼叫類別的 `Friend` 程序，或嘗試存取跨處理序或跨執行緒的 `Friend` 屬性或方法。</span><span class="sxs-lookup"><span data-stu-id="f8bf7-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="f8bf7-104">`Friend` 程序可以從類別外部的模組呼叫，但其為已定義類別之專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="f8bf7-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f8bf7-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f8bf7-105">To correct this error</span></span>  
  
- <span data-ttu-id="f8bf7-106">確定您從屬於已定義類別之專案的模組，呼叫或存取程序。</span><span class="sxs-lookup"><span data-stu-id="f8bf7-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bf7-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8bf7-107">See also</span></span>

- [<span data-ttu-id="f8bf7-108">Friend</span><span class="sxs-lookup"><span data-stu-id="f8bf7-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
