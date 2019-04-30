---
title: 陳述式不能在 'If' 陳述式行之外結束區塊
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 85573099ec0a3f8a23c17bdf384c4c105f9157df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055130"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="83aa3-102">陳述式不能在 'If' 陳述式行之外結束區塊</span><span class="sxs-lookup"><span data-stu-id="83aa3-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="83aa3-103">單行`If`陳述式包含的冒號 （:），其中之一就是隔開的多個陳述式`End`單行外控制區塊的陳述式`If`。</span><span class="sxs-lookup"><span data-stu-id="83aa3-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="83aa3-104">單行`If`陳述式不使用`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="83aa3-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="83aa3-105">**錯誤 ID:** BC32005</span><span class="sxs-lookup"><span data-stu-id="83aa3-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="83aa3-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="83aa3-106">To correct this error</span></span>  
  
- <span data-ttu-id="83aa3-107">移動單行`If`陳述式包含在控制區塊外的`End If`陳述式。</span><span class="sxs-lookup"><span data-stu-id="83aa3-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83aa3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83aa3-108">See also</span></span>

- [<span data-ttu-id="83aa3-109">If...Then...Else 陳述式</span><span class="sxs-lookup"><span data-stu-id="83aa3-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
