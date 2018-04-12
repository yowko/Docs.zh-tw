---
title: '&#39;模組 &#39;陳述式只可以發生在檔案或命名空間層級'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61fe12fbd7d20e6cd2b6bc464e7fc3293150213b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="42719-102">&#39;模組 &#39;陳述式只可以發生在檔案或命名空間層級</span><span class="sxs-lookup"><span data-stu-id="42719-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="42719-103">`Module`陳述式必須出現在原始程式檔頂端之後立即`Option`和`Imports`陳述式、 全域屬性及命名空間宣告，但所有其他宣告前面。</span><span class="sxs-lookup"><span data-stu-id="42719-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="42719-104">**錯誤 ID:** BC30617</span><span class="sxs-lookup"><span data-stu-id="42719-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42719-105">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="42719-105">To correct this error</span></span>  
  
-   <span data-ttu-id="42719-106">移動`Module`陳述式來命名空間宣告或原始檔的頂端。</span><span class="sxs-lookup"><span data-stu-id="42719-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42719-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42719-107">See Also</span></span>  
 [<span data-ttu-id="42719-108">Module 陳述式</span><span class="sxs-lookup"><span data-stu-id="42719-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
