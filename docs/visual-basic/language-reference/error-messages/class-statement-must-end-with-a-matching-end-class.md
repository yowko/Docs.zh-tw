---
title: "&#39;類別 &#39;陳述式的結尾必須符合 &#39;End Class &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30481
- bc30481
helpviewer_keywords: BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e8643a0a5b55e220ca8dd53065500fe4b1e473d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a><span data-ttu-id="03316-102">&#39;類別 &#39;陳述式的結尾必須符合 &#39;End Class &#39;</span><span class="sxs-lookup"><span data-stu-id="03316-102">&#39;Class&#39; statement must end with a matching &#39;End Class&#39;</span></span>
<span data-ttu-id="03316-103">`Class`用來起始`Class`區塊，因此它只能出現在區塊中，搭配相對應的開頭`End Class`陳述式結束區塊。</span><span class="sxs-lookup"><span data-stu-id="03316-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="03316-104">您有多餘`Class`陳述式，或您有未結束您`Class`區塊`End Class`。</span><span class="sxs-lookup"><span data-stu-id="03316-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="03316-105">**錯誤 ID:** BC30481</span><span class="sxs-lookup"><span data-stu-id="03316-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="03316-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="03316-106">To correct this error</span></span>  
  
-   <span data-ttu-id="03316-107">找到並移除不必要`Class`陳述式。</span><span class="sxs-lookup"><span data-stu-id="03316-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="03316-108">結束`Class`搭配相對應的區塊`End Class`。</span><span class="sxs-lookup"><span data-stu-id="03316-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03316-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03316-109">See Also</span></span>  
 [<span data-ttu-id="03316-110">結束\<關鍵字 > 陳述式</span><span class="sxs-lookup"><span data-stu-id="03316-110">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)  
 [<span data-ttu-id="03316-111">Class 陳述式</span><span class="sxs-lookup"><span data-stu-id="03316-111">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
