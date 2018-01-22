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
ms.openlocfilehash: 752e0e54c48b3b348a477787e5e911f1b1777667
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="5c529-102">&#39;ReDim &#39;只能變更最右側的維度</span><span class="sxs-lookup"><span data-stu-id="5c529-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="5c529-103">`ReDim` 陳述式嘗試使用 `Preserve` 關鍵字來變更不是最後一個維度的陣列的維度。</span><span class="sxs-lookup"><span data-stu-id="5c529-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="5c529-104">使用 `Preserve`時，您只能調整陣列的最後一個維度。</span><span class="sxs-lookup"><span data-stu-id="5c529-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="5c529-105">對於所有其他維度，您必須指定與現有陣列相同的大小。</span><span class="sxs-lookup"><span data-stu-id="5c529-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c529-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="5c529-106">To correct this error</span></span>  
  
-   <span data-ttu-id="5c529-107">請移除 `Preserve` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5c529-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c529-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="5c529-108">See Also</span></span>  
 [<span data-ttu-id="5c529-109">Visual Basic 中的陣列</span><span class="sxs-lookup"><span data-stu-id="5c529-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="5c529-110">在 Visual Basic 中的陣列維度</span><span class="sxs-lookup"><span data-stu-id="5c529-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="5c529-111">ReDim 陳述式</span><span class="sxs-lookup"><span data-stu-id="5c529-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="5c529-112">Dim 陳述式</span><span class="sxs-lookup"><span data-stu-id="5c529-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="5c529-113">保留-刪除</span><span class="sxs-lookup"><span data-stu-id="5c529-113">Preserve - delete</span></span>](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
