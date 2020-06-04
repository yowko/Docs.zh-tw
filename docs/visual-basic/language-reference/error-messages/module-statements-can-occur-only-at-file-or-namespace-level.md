---
title: "'Module' 陳述式只可以發生在檔案或命名空間層級"
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: d01c30571fc34e142300ac8706c56d5e99175fcf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397203"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="ec517-102">'Module' 陳述式只可以發生在檔案或命名空間層級</span><span class="sxs-lookup"><span data-stu-id="ec517-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="ec517-103">`Module`語句必須出現在原始程式檔的頂端，緊接在 `Option` 和 `Imports` 語句、全域屬性、命名空間宣告，但在其他所有宣告之前。</span><span class="sxs-lookup"><span data-stu-id="ec517-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="ec517-104">**錯誤識別碼：** BC30617</span><span class="sxs-lookup"><span data-stu-id="ec517-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ec517-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="ec517-105">To correct this error</span></span>  
  
- <span data-ttu-id="ec517-106">將 `Module` 陳述式移至命名空間宣告或原始程式檔的上方。</span><span class="sxs-lookup"><span data-stu-id="ec517-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec517-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec517-107">See also</span></span>

- [<span data-ttu-id="ec517-108">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="ec517-108">Module Statement</span></span>](../statements/module-statement.md)
