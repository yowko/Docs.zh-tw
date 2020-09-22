---
title: 建構函式 '<name>' 不能呼叫自己本身
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: dce98a4deef8fbb0e8bc024244b815e23d51c790
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874578"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="45f9e-102">建構函式 '\<name>' 不能呼叫自己本身</span><span class="sxs-lookup"><span data-stu-id="45f9e-102">Constructor '\<name>' cannot call itself</span></span>

<span data-ttu-id="45f9e-103">`Sub New`類別或結構中的程式會呼叫本身。</span><span class="sxs-lookup"><span data-stu-id="45f9e-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="45f9e-104">函式的目的是要在第一次建立類別或結構的實例時，將它初始化。</span><span class="sxs-lookup"><span data-stu-id="45f9e-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="45f9e-105">類別或結構可以有數個不同的函式，但前提是它們都有不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="45f9e-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="45f9e-106">除了它自己的功能之外，允許函式呼叫另一個函式來執行其功能。</span><span class="sxs-lookup"><span data-stu-id="45f9e-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="45f9e-107">但是，它對呼叫本身的函式沒有意義，事實上，如果允許，則會導致無限遞迴。</span><span class="sxs-lookup"><span data-stu-id="45f9e-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="45f9e-108">**錯誤識別碼：** BC30298</span><span class="sxs-lookup"><span data-stu-id="45f9e-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="45f9e-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="45f9e-109">To correct this error</span></span>  
  
1. <span data-ttu-id="45f9e-110">檢查所呼叫之函式的參數清單。</span><span class="sxs-lookup"><span data-stu-id="45f9e-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="45f9e-111">它應該與進行呼叫的函式不同。</span><span class="sxs-lookup"><span data-stu-id="45f9e-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="45f9e-112">如果您不想要呼叫不同的函式，請 `Sub New` 完全移除呼叫。</span><span class="sxs-lookup"><span data-stu-id="45f9e-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45f9e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45f9e-113">See also</span></span>

- [<span data-ttu-id="45f9e-114">物件存留期：物件的建立和終結</span><span class="sxs-lookup"><span data-stu-id="45f9e-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
