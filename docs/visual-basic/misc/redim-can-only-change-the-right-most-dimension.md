---
title: "&#39;ReDim &#39;只能變更最右側的維度"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 989a06f94824dfd051d1a7d2e7749dbb8c8e11a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="28c34-102">&#39;ReDim &#39;只能變更最右側的維度</span><span class="sxs-lookup"><span data-stu-id="28c34-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="28c34-103">`ReDim` 陳述式嘗試使用 `Preserve` 關鍵字來變更不是最後一個維度的陣列的維度。</span><span class="sxs-lookup"><span data-stu-id="28c34-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="28c34-104">使用 `Preserve`時，您只能調整陣列的最後一個維度。</span><span class="sxs-lookup"><span data-stu-id="28c34-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="28c34-105">對於所有其他維度，您必須指定與現有陣列相同的大小。</span><span class="sxs-lookup"><span data-stu-id="28c34-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28c34-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="28c34-106">To correct this error</span></span>  
  
-   <span data-ttu-id="28c34-107">請移除 `Preserve` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="28c34-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c34-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28c34-108">See Also</span></span>  
 [<span data-ttu-id="28c34-109">Visual Basic 中的陣列</span><span class="sxs-lookup"><span data-stu-id="28c34-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="28c34-110">在 Visual Basic 中的陣列維度</span><span class="sxs-lookup"><span data-stu-id="28c34-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="28c34-111">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="28c34-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="28c34-112">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="28c34-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="28c34-113">保留-刪除</span><span class="sxs-lookup"><span data-stu-id="28c34-113">Preserve - delete</span></span>](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
