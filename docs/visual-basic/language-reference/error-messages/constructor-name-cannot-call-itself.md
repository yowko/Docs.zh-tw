---
title: 建構函式 '<name>' 不能呼叫自己本身
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 8459ee7fec6d761161a721c88ccdc88e513fc95f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324379"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="296a0-102">建構函式 '\<名稱 >' 不可呼叫其本身</span><span class="sxs-lookup"><span data-stu-id="296a0-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="296a0-103">A`Sub New`類別或結構中的程序呼叫本身。</span><span class="sxs-lookup"><span data-stu-id="296a0-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="296a0-104">建構函式的目的是要初始化類別的執行個體，或建立結構時第一次。</span><span class="sxs-lookup"><span data-stu-id="296a0-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="296a0-105">類別或結構可以有數個建構函式，前提是它們都有不同的參數清單。</span><span class="sxs-lookup"><span data-stu-id="296a0-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="296a0-106">建構函式可以呼叫其他建構函式，以執行其功能，除了它自己。</span><span class="sxs-lookup"><span data-stu-id="296a0-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="296a0-107">但是這樣做沒有意義的建構函式呼叫本身，而且事實上這會導致無限遞迴如果允許。</span><span class="sxs-lookup"><span data-stu-id="296a0-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="296a0-108">**錯誤 ID:** BC30298</span><span class="sxs-lookup"><span data-stu-id="296a0-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="296a0-109">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="296a0-109">To correct this error</span></span>  
  
1. <span data-ttu-id="296a0-110">請檢查建構函式所呼叫的參數清單。</span><span class="sxs-lookup"><span data-stu-id="296a0-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="296a0-111">它應該是不同的建構函式進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="296a0-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="296a0-112">如果您不想呼叫不同的建構函式，移除`Sub New`完全呼叫。</span><span class="sxs-lookup"><span data-stu-id="296a0-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296a0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="296a0-113">See also</span></span>

- [<span data-ttu-id="296a0-114">物件存留期：如何建立和終結物件</span><span class="sxs-lookup"><span data-stu-id="296a0-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
