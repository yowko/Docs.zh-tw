---
title: 陳述式不能在 'If' 陳述式行之外結束區塊
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0e645ccf17d0aba702a576791622aa4e9b3dd5e0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593260"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="87839-102">陳述式不能在 'If' 陳述式行之外結束區塊</span><span class="sxs-lookup"><span data-stu-id="87839-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="87839-103">單行`If`陳述式包含的冒號 （:），其中之一就是隔開的多個陳述式`End`單行外控制區塊的陳述式`If`。</span><span class="sxs-lookup"><span data-stu-id="87839-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="87839-104">單行`If`陳述式不使用`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="87839-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="87839-105">**錯誤 ID:** BC32005</span><span class="sxs-lookup"><span data-stu-id="87839-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="87839-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="87839-106">To correct this error</span></span>  
  
- <span data-ttu-id="87839-107">移動單行`If`陳述式包含在控制區塊外的`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="87839-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87839-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87839-108">See also</span></span>

- [<span data-ttu-id="87839-109">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="87839-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
