---
title: 已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 7616bcdc39ab479049586534fac22f1e2d96a700
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831835"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="80286-102">已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)</span><span class="sxs-lookup"><span data-stu-id="80286-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="80286-103">不再支援單行陳述式。</span><span class="sxs-lookup"><span data-stu-id="80286-103">Line statements are no longer supported.</span></span> <span data-ttu-id="80286-104">檔案 I/O 功能可從`Microsoft.VisualBasic.FileSystem.LineInput`而且可以當做圖形功能`System.Drawing.Graphics.DrawLine`。</span><span class="sxs-lookup"><span data-stu-id="80286-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="80286-105">**錯誤 ID:** BC30830</span><span class="sxs-lookup"><span data-stu-id="80286-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="80286-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="80286-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="80286-107">如果執行檔案存取，使用`Microsoft.VisualBasic.FileSystem.LineInput`。</span><span class="sxs-lookup"><span data-stu-id="80286-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="80286-108">如果執行圖形，請使用 `System.Drawing.Graphics.Drawline`。</span><span class="sxs-lookup"><span data-stu-id="80286-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80286-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80286-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="80286-110">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="80286-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
