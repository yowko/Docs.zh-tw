---
title: "'Module' 陳述式只可以發生在檔案或命名空間層級"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bf0239422fb5a98e4670aea407f684753d3a7ea4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825439"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="5bc8a-102">'Module' 陳述式只可以發生在檔案或命名空間層級</span><span class="sxs-lookup"><span data-stu-id="5bc8a-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="5bc8a-103">`Module` 陳述式必須出現在原始程式檔頂端之後立即`Option`和`Imports`陳述式、 全域屬性和命名空間宣告，但所有其他宣告前面。</span><span class="sxs-lookup"><span data-stu-id="5bc8a-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="5bc8a-104">**錯誤 ID:** BC30617</span><span class="sxs-lookup"><span data-stu-id="5bc8a-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5bc8a-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5bc8a-105">To correct this error</span></span>  
  
-   <span data-ttu-id="5bc8a-106">將 `Module` 陳述式移至命名空間宣告或原始程式檔的上方。</span><span class="sxs-lookup"><span data-stu-id="5bc8a-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc8a-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bc8a-107">See also</span></span>

- [<span data-ttu-id="5bc8a-108">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="5bc8a-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
