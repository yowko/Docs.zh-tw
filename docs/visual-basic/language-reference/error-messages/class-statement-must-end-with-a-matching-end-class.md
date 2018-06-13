---
title: '&#39;類別&#39;陳述式必須搭配相對應的結束&#39;結束類別&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 7c9051b15f6d9cf37d7d0245f758905467d5bbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585511"
---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a><span data-ttu-id="3c32b-102">&#39;類別&#39;陳述式必須搭配相對應的結束&#39;結束類別&#39;</span><span class="sxs-lookup"><span data-stu-id="3c32b-102">&#39;Class&#39; statement must end with a matching &#39;End Class&#39;</span></span>
<span data-ttu-id="3c32b-103">`Class` 用來起始`Class`區塊，因此它只能出現在區塊中，搭配相對應的開頭`End Class`陳述式結束區塊。</span><span class="sxs-lookup"><span data-stu-id="3c32b-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="3c32b-104">您有多餘`Class`陳述式，或您有未結束您`Class`區塊`End Class`。</span><span class="sxs-lookup"><span data-stu-id="3c32b-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="3c32b-105">**錯誤 ID:** BC30481</span><span class="sxs-lookup"><span data-stu-id="3c32b-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3c32b-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3c32b-106">To correct this error</span></span>  
  
-   <span data-ttu-id="3c32b-107">找到並移除不必要`Class`陳述式。</span><span class="sxs-lookup"><span data-stu-id="3c32b-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="3c32b-108">結束`Class`搭配相對應的區塊`End Class`。</span><span class="sxs-lookup"><span data-stu-id="3c32b-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c32b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c32b-109">See Also</span></span>  
 [<span data-ttu-id="3c32b-110">結束\<關鍵字 > 陳述式</span><span class="sxs-lookup"><span data-stu-id="3c32b-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)  
 [<span data-ttu-id="3c32b-111">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="3c32b-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
