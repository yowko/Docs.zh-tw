---
title: 在類別建構函式中使用類別的「預設執行個體」，可能會導致無限遞迴呼叫。
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: b4cae7802019cba569cf15517b1e948266a576f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631434"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="a455e-102">在類別建構函式中使用類別的「預設執行個體」，可能會導致無限遞迴呼叫。</span><span class="sxs-lookup"><span data-stu-id="a455e-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="a455e-103">類別的預設執行個體已用於類別的建構函式中。</span><span class="sxs-lookup"><span data-stu-id="a455e-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="a455e-104">這可能會導致無限遞迴呼叫 (也稱為無限迴圈)。</span><span class="sxs-lookup"><span data-stu-id="a455e-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a455e-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a455e-105">To correct this error</span></span>  
  
-   <span data-ttu-id="a455e-106">從類別建構函式中移除預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="a455e-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a455e-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a455e-107">See also</span></span>
- [<span data-ttu-id="a455e-108">建構函式</span><span class="sxs-lookup"><span data-stu-id="a455e-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
