---
title: "'Class' 陳述式之後必須搭配相對應的 'End Class'"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 01c231f577d21028e9ef92f37c7ac5f7f1fe2aa3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415384"
---
# <a name="class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="59be7-102">'Class' 陳述式之後必須搭配相對應的 'End Class'</span><span class="sxs-lookup"><span data-stu-id="59be7-102">'Class' statement must end with a matching 'End Class'</span></span>
<span data-ttu-id="59be7-103">`Class`是用來起始 `Class` 區塊; 因此，它只能出現在區塊開頭，並以相符 `End Class` 的語句結束區塊。</span><span class="sxs-lookup"><span data-stu-id="59be7-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="59be7-104">您有多餘的 `Class` 語句，或尚未 `Class` 使用結束區塊 `End Class` 。</span><span class="sxs-lookup"><span data-stu-id="59be7-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="59be7-105">**錯誤識別碼：** BC30481</span><span class="sxs-lookup"><span data-stu-id="59be7-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="59be7-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="59be7-106">To correct this error</span></span>  
  
- <span data-ttu-id="59be7-107">找到並移除不必要的 `Class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="59be7-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
- <span data-ttu-id="59be7-108">結束 `Class` 具有相符的區塊 `End Class` 。</span><span class="sxs-lookup"><span data-stu-id="59be7-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59be7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59be7-109">See also</span></span>

- [<span data-ttu-id="59be7-110">End \<keyword> 語句</span><span class="sxs-lookup"><span data-stu-id="59be7-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="59be7-111">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="59be7-111">Class Statement</span></span>](../statements/class-statement.md)
