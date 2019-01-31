---
title: "'Module' 陳述式只可以發生在檔案或命名空間層級"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 0820763cce9cc27f9a379ed5e766e0691a75f36b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271261"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="063fb-102">'Module' 陳述式只可以發生在檔案或命名空間層級</span><span class="sxs-lookup"><span data-stu-id="063fb-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="063fb-103">`Module` 陳述式必須出現在原始程式檔頂端之後立即`Option`和`Imports`陳述式、 全域屬性和命名空間宣告，但所有其他宣告前面。</span><span class="sxs-lookup"><span data-stu-id="063fb-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="063fb-104">**錯誤 ID:** BC30617</span><span class="sxs-lookup"><span data-stu-id="063fb-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="063fb-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="063fb-105">To correct this error</span></span>  
  
-   <span data-ttu-id="063fb-106">將 `Module` 陳述式移至命名空間宣告或原始程式檔的上方。</span><span class="sxs-lookup"><span data-stu-id="063fb-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="063fb-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="063fb-107">See also</span></span>
- [<span data-ttu-id="063fb-108">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="063fb-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
