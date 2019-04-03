---
title: "'Class' 陳述式之後必須搭配相對應的 'End Class'"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 0619db618abd562bda86836bdd41bbcd6caee0f9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836502"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="cbae9-102">'Class' 陳述式之後必須搭配相對應的 'End Class'</span><span class="sxs-lookup"><span data-stu-id="cbae9-102">'Class' statement must end with a matching 'End Class'</span></span>
<span data-ttu-id="cbae9-103">`Class` 用來起始`Class`區塊，因此它只能出現在區塊中，搭配相對應的開頭`End Class`結束區塊的陳述式。</span><span class="sxs-lookup"><span data-stu-id="cbae9-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="cbae9-104">您有多餘`Class`陳述式，或您有未結束您`Class`含有區塊`End Class`。</span><span class="sxs-lookup"><span data-stu-id="cbae9-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="cbae9-105">**錯誤 ID:** BC30481</span><span class="sxs-lookup"><span data-stu-id="cbae9-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cbae9-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="cbae9-106">To correct this error</span></span>  
  
-   <span data-ttu-id="cbae9-107">找到並移除不必要的 `Class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="cbae9-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="cbae9-108">結束`Class`搭配相對應的區塊`End Class`。</span><span class="sxs-lookup"><span data-stu-id="cbae9-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbae9-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbae9-109">See also</span></span>

- [<span data-ttu-id="cbae9-110">結束\<關鍵字 > 陳述式</span><span class="sxs-lookup"><span data-stu-id="cbae9-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
- [<span data-ttu-id="cbae9-111">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="cbae9-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
