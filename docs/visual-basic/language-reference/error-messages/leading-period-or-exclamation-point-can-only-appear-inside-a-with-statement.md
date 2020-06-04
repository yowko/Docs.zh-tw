---
title: 前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現
ms.date: 07/20/2015
f1_keywords:
- vbc30157
- bc30157
helpviewer_keywords:
- BC30157
ms.assetid: 70daaee1-14f9-45b7-9f30-53794310b95e
ms.openlocfilehash: 149acc2baac0f45fa971a11f254d694526d140d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397320"
---
# <a name="leading--or--can-only-appear-inside-a-with-statement"></a><span data-ttu-id="f959c-102">前置的 '.' 或 '!' 只可以在 'With' 陳述式中出現</span><span class="sxs-lookup"><span data-stu-id="f959c-102">Leading '.' or '!' can only appear inside a 'With' statement</span></span>
<span data-ttu-id="f959c-103">不在區塊內的句號（.）或驚嘆號（！）不會 `With` 出現在左邊的運算式。</span><span class="sxs-lookup"><span data-stu-id="f959c-103">A period (.) or exclamation point (!) that is not inside a `With` block occurs without an expression on the left.</span></span> <span data-ttu-id="f959c-104">成員存取（ `.` ）和字典成員存取（ `!` ）需要一個運算式來指定包含該成員的元素。</span><span class="sxs-lookup"><span data-stu-id="f959c-104">Member access (`.`) and dictionary member access (`!`) require an expression specifying the element that contains the member.</span></span> <span data-ttu-id="f959c-105">這必須立即出現在存取子的左邊，或做為 `With` 包含成員存取之區塊的目標。</span><span class="sxs-lookup"><span data-stu-id="f959c-105">This must appear immediately to the left of the accessor or as the target of a `With` block containing the member access.</span></span>  
  
 <span data-ttu-id="f959c-106">**錯誤識別碼：** BC30157</span><span class="sxs-lookup"><span data-stu-id="f959c-106">**Error ID:** BC30157</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f959c-107">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f959c-107">To correct this error</span></span>  
  
1. <span data-ttu-id="f959c-108">請確定 `With` 已正確地格式化區塊。</span><span class="sxs-lookup"><span data-stu-id="f959c-108">Ensure that the `With` block is correctly formatted.</span></span>  
  
2. <span data-ttu-id="f959c-109">如果沒有 `With` 區塊，請在存取子的左邊加上運算式，以評估為包含該成員的已定義元素。</span><span class="sxs-lookup"><span data-stu-id="f959c-109">If there is no `With` block, add an expression to the left of the accessor that evaluates to a defined element containing the member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f959c-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f959c-110">See also</span></span>

- [<span data-ttu-id="f959c-111">程式碼中的特殊字元</span><span class="sxs-lookup"><span data-stu-id="f959c-111">Special Characters in Code</span></span>](../../programming-guide/program-structure/special-characters-in-code.md)
- [<span data-ttu-id="f959c-112">With...End With 陳述式</span><span class="sxs-lookup"><span data-stu-id="f959c-112">With...End With Statement</span></span>](../statements/with-end-with-statement.md)
