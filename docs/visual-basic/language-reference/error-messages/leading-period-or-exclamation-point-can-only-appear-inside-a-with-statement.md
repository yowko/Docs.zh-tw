---
title: 前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 4821dbab90eec3c99c0996e8bff10d51b5a8f99d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824945"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="5ee8b-102">前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現</span><span class="sxs-lookup"><span data-stu-id="5ee8b-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="5ee8b-103">句號 （.） 或驚嘆號 （！） 不深入探討`With`區塊就會發生，而不需要在左邊的運算式。</span><span class="sxs-lookup"><span data-stu-id="5ee8b-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="5ee8b-104">成員存取 (`.`) 和字典成員存取 (`!`) 需要一個運算式來指定包含該成員的項目。</span><span class="sxs-lookup"><span data-stu-id="5ee8b-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="5ee8b-105">這必須立刻出現左側的存取子，或做為目標的`With`記錄檔區塊內含成員存取。</span><span class="sxs-lookup"><span data-stu-id="5ee8b-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="5ee8b-106">**錯誤 ID:** BC30157</span><span class="sxs-lookup"><span data-stu-id="5ee8b-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5ee8b-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5ee8b-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="5ee8b-108">請確認`With`區塊的格式正確。</span><span class="sxs-lookup"><span data-stu-id="5ee8b-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2.  <span data-ttu-id="5ee8b-109">如果沒有任何`With`區塊中，將運算式加入至定義的項目，包含成員的存取子，會評估的左邊。</span><span class="sxs-lookup"><span data-stu-id="5ee8b-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee8b-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ee8b-110">See also</span></span>

- [<span data-ttu-id="5ee8b-111">程式碼中的特殊字元</span><span class="sxs-lookup"><span data-stu-id="5ee8b-111">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="5ee8b-112">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="5ee8b-112">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
