---
title: "'Class' 陳述式之後必須搭配相對應的 'End Class'"
ms.date: 07/20/2015
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
ms.openlocfilehash: 6889e97aad913f6911ce438892752542de0d10f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163190"
---
# <a name="bc30481-class-statement-must-end-with-a-matching-end-class"></a><span data-ttu-id="d9f87-102">BC30481： ' Class ' 語句之後必須搭配相對應的 ' End Class '</span><span class="sxs-lookup"><span data-stu-id="d9f87-102">BC30481: 'Class' statement must end with a matching 'End Class'</span></span>

<span data-ttu-id="d9f87-103">`Class` 用來起始 `Class` 區塊; 因此，它只能出現在區塊的開頭，且相符的 `End Class` 語句會結束區塊。</span><span class="sxs-lookup"><span data-stu-id="d9f87-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="d9f87-104">可能是您有多餘的 `Class` 語句，或尚未結束您 `Class` 的區塊 `End Class` 。</span><span class="sxs-lookup"><span data-stu-id="d9f87-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>

 <span data-ttu-id="d9f87-105">**錯誤識別碼：** BC30481</span><span class="sxs-lookup"><span data-stu-id="d9f87-105">**Error ID:** BC30481</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d9f87-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="d9f87-106">To correct this error</span></span>

- <span data-ttu-id="d9f87-107">找到並移除不必要的 `Class` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d9f87-107">Locate and remove the unnecessary `Class` statement.</span></span>

- <span data-ttu-id="d9f87-108">使用相符的來結束 `Class` 區塊 `End Class` 。</span><span class="sxs-lookup"><span data-stu-id="d9f87-108">Conclude the `Class` block with a matching `End Class`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9f87-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9f87-109">See also</span></span>

- [<span data-ttu-id="d9f87-110">End \<keyword> 語句</span><span class="sxs-lookup"><span data-stu-id="d9f87-110">End \<keyword> Statement</span></span>](../statements/end-keyword-statement.md)
- [<span data-ttu-id="d9f87-111">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="d9f87-111">Class Statement</span></span>](../statements/class-statement.md)
