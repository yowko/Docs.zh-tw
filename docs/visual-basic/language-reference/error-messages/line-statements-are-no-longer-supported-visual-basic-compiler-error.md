---
title: 已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: c7a3e6bcd0db268a0e0acfc74c570e26f89cff6a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339069"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="9bcf5-102">已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)</span><span class="sxs-lookup"><span data-stu-id="9bcf5-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="9bcf5-103">不再支援單行陳述式。</span><span class="sxs-lookup"><span data-stu-id="9bcf5-103">Line statements are no longer supported.</span></span> <span data-ttu-id="9bcf5-104">檔案 I/O 功能可從`Microsoft.VisualBasic.FileSystem.LineInput`而且可以當做圖形功能`System.Drawing.Graphics.DrawLine`。</span><span class="sxs-lookup"><span data-stu-id="9bcf5-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="9bcf5-105">**錯誤 ID:** BC30830</span><span class="sxs-lookup"><span data-stu-id="9bcf5-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9bcf5-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="9bcf5-106">To correct this error</span></span>  
  
1. <span data-ttu-id="9bcf5-107">如果執行檔案存取，使用`Microsoft.VisualBasic.FileSystem.LineInput`。</span><span class="sxs-lookup"><span data-stu-id="9bcf5-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="9bcf5-108">如果執行圖形，請使用 `System.Drawing.Graphics.Drawline`。</span><span class="sxs-lookup"><span data-stu-id="9bcf5-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bcf5-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bcf5-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="9bcf5-110">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="9bcf5-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
