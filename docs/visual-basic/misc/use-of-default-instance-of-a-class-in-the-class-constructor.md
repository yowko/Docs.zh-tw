---
title: 在類別建構函式中使用類別的「預設執行個體」，可能會導致無限遞迴呼叫。
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 1cad1e3cf3943e945d519aee061a877c91684b4a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623475"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="bc1a9-102">在類別建構函式中使用類別的「預設執行個體」，可能會導致無限遞迴呼叫。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="bc1a9-103">類別的預設執行個體已用於類別的建構函式中。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="bc1a9-104">這可能會導致無限遞迴呼叫 (也稱為無限迴圈)。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bc1a9-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="bc1a9-105">To correct this error</span></span>  
  
- <span data-ttu-id="bc1a9-106">從類別建構函式中移除預設執行個體。</span><span class="sxs-lookup"><span data-stu-id="bc1a9-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1a9-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc1a9-107">See also</span></span>

- [<span data-ttu-id="bc1a9-108">建構函式</span><span class="sxs-lookup"><span data-stu-id="bc1a9-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
