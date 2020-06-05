---
title: 陳述式不能在 'If' 陳述式行之外結束區塊
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400314"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="8e382-102">陳述式不能在 'If' 陳述式行之外結束區塊</span><span class="sxs-lookup"><span data-stu-id="8e382-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="8e382-103">單行 `If` 語句包含數個以冒號分隔的語句（:)，其中一個是 `End` 單一行外之控制區塊的語句 `If` 。</span><span class="sxs-lookup"><span data-stu-id="8e382-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="8e382-104">單行 `If` 語句不會使用 `End If` 語句。</span><span class="sxs-lookup"><span data-stu-id="8e382-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="8e382-105">**錯誤識別碼：** BC32005</span><span class="sxs-lookup"><span data-stu-id="8e382-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e382-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="8e382-106">To correct this error</span></span>  
  
- <span data-ttu-id="8e382-107">將單行 `If` 語句移出包含語句的控制區塊外 `End If` 。</span><span class="sxs-lookup"><span data-stu-id="8e382-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e382-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e382-108">See also</span></span>

- [<span data-ttu-id="8e382-109">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="8e382-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
