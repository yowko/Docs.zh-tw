---
title: 陳述式不能在之外結束區塊一條線&#39;如果&#39;陳述式
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 78fe136acbd09e202b1daeb16dd540cf42ada390
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574712"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="1142d-102">陳述式不能在之外結束區塊一條線&#39;如果&#39;陳述式</span><span class="sxs-lookup"><span data-stu-id="1142d-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="1142d-103">單行`If`陳述式包含的冒號 （:），其中之一就是隔開的多個陳述式`End`單行外控制區塊的陳述式`If`。</span><span class="sxs-lookup"><span data-stu-id="1142d-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="1142d-104">單行`If`陳述式不使用`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1142d-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="1142d-105">**錯誤 ID:** BC32005</span><span class="sxs-lookup"><span data-stu-id="1142d-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1142d-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1142d-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1142d-107">移動單行`If`陳述式包含在控制區塊外的`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="1142d-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1142d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1142d-108">See also</span></span>
- [<span data-ttu-id="1142d-109">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="1142d-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
