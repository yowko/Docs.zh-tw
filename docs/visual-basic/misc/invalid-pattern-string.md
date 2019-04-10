---
title: 無效的模式字串
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 7390b9b32eea248969813b52f8d9799798718de0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59298678"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="89a64-102">無效的模式字串</span><span class="sxs-lookup"><span data-stu-id="89a64-102">Invalid pattern string</span></span>
<span data-ttu-id="89a64-103">在搜尋的 `Like` 作業中指定的模式字串無效。</span><span class="sxs-lookup"><span data-stu-id="89a64-103">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="89a64-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="89a64-104">To correct this error</span></span>  
  
1. <span data-ttu-id="89a64-105">請檢閱清單運算式的有效字元。</span><span class="sxs-lookup"><span data-stu-id="89a64-105">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="89a64-106">在模式範圍中，確定起始範圍字元小於結束範圍字元，如同在 `[a-z]`。</span><span class="sxs-lookup"><span data-stu-id="89a64-106">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="89a64-107">在模式範圍中，確定沒有相鄰的多個連字號，如同在 `[a--z]`。</span><span class="sxs-lookup"><span data-stu-id="89a64-107">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="89a64-108">以右括弧結束模式範圍。</span><span class="sxs-lookup"><span data-stu-id="89a64-108">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a64-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89a64-109">See also</span></span>

- [<span data-ttu-id="89a64-110">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="89a64-110">Like Operator</span></span>](../../visual-basic/language-reference/operators/like-operator.md)
