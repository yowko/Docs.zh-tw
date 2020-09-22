---
title: 已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 4ca1538dbde0d585b7b421d60cde4531c00e9145
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873840"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="be40c-102">已不再支援 'Line' 陳述式 (Visual Basic 編譯器錯誤)</span><span class="sxs-lookup"><span data-stu-id="be40c-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>

<span data-ttu-id="be40c-103">不再支援行語句。</span><span class="sxs-lookup"><span data-stu-id="be40c-103">Line statements are no longer supported.</span></span> <span data-ttu-id="be40c-104">檔案 i/o 功能可供使用 `Microsoft.VisualBasic.FileSystem.LineInput` ，而且圖形功能也可供使用 `System.Drawing.Graphics.DrawLine` 。</span><span class="sxs-lookup"><span data-stu-id="be40c-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="be40c-105">**錯誤識別碼：** BC30830</span><span class="sxs-lookup"><span data-stu-id="be40c-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="be40c-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="be40c-106">To correct this error</span></span>  
  
1. <span data-ttu-id="be40c-107">如果執行檔案存取，請使用 `Microsoft.VisualBasic.FileSystem.LineInput` 。</span><span class="sxs-lookup"><span data-stu-id="be40c-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="be40c-108">如果執行圖形，請使用 `System.Drawing.Graphics.Drawline`。</span><span class="sxs-lookup"><span data-stu-id="be40c-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be40c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be40c-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="be40c-110">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="be40c-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
