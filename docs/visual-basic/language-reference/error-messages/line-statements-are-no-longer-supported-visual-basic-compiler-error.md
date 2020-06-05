---
title: 已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: a3d243f39f3fc45ca6b1ba0d26892d4c3db56f59
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397294"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="83f6b-102">已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)</span><span class="sxs-lookup"><span data-stu-id="83f6b-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="83f6b-103">已不再支援行語句。</span><span class="sxs-lookup"><span data-stu-id="83f6b-103">Line statements are no longer supported.</span></span> <span data-ttu-id="83f6b-104">檔案 i/o 功能可供使用 `Microsoft.VisualBasic.FileSystem.LineInput` ，而且圖形功能可作為提供 `System.Drawing.Graphics.DrawLine` 。</span><span class="sxs-lookup"><span data-stu-id="83f6b-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="83f6b-105">**錯誤識別碼：** BC30830</span><span class="sxs-lookup"><span data-stu-id="83f6b-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="83f6b-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="83f6b-106">To correct this error</span></span>  
  
1. <span data-ttu-id="83f6b-107">如果要執行檔案存取，請使用 `Microsoft.VisualBasic.FileSystem.LineInput` 。</span><span class="sxs-lookup"><span data-stu-id="83f6b-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="83f6b-108">如果執行圖形，請使用 `System.Drawing.Graphics.Drawline`。</span><span class="sxs-lookup"><span data-stu-id="83f6b-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f6b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83f6b-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="83f6b-110">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="83f6b-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
