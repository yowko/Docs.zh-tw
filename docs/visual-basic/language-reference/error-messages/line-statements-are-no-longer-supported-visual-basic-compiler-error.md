---
title: "&#39;行 &#39;陳述式已不再支援 （Visual Basic 編譯器錯誤）"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords: BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d2db5dc786749360dfcf6789f12b5659d5713fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="f8595-102">&#39;行 &#39;陳述式已不再支援 （Visual Basic 編譯器錯誤）</span><span class="sxs-lookup"><span data-stu-id="f8595-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="f8595-103">不再支援單行陳述式。</span><span class="sxs-lookup"><span data-stu-id="f8595-103">Line statements are no longer supported.</span></span> <span data-ttu-id="f8595-104">檔案 I/O 功能可做為`Microsoft.VisualBasic.FileSystem.LineInput`和圖形功能是做為`System.Drawing.Graphics.DrawLine`。</span><span class="sxs-lookup"><span data-stu-id="f8595-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="f8595-105">**錯誤 ID:** BC30830</span><span class="sxs-lookup"><span data-stu-id="f8595-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f8595-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="f8595-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f8595-107">如果執行檔案存取，請使用`Microsoft.VisualBasic.FileSystem.LineInput`。</span><span class="sxs-lookup"><span data-stu-id="f8595-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="f8595-108">如果執行圖形，請使用`System.Drawing.Graphics.Drawline`。</span><span class="sxs-lookup"><span data-stu-id="f8595-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8595-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8595-109">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [<span data-ttu-id="f8595-110">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="f8595-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
