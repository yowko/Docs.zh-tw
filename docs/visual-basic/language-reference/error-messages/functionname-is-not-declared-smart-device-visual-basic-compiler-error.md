---
title: "'<functionname>' 未宣告 (智慧型裝置 - Visual Basic 編譯器錯誤)"
ms.date: 07/20/2015
f1_keywords:
- bc30766
- vbc30766
helpviewer_keywords:
- BC30766
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
ms.openlocfilehash: 5e0f6dd2da404ed988af15fadadd8ecd4a491189
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874056"
---
# <a name="functionname-is-not-declared-smart-devicevisual-basic-compiler-error"></a><span data-ttu-id="1ee2d-102">' \<functionname> ' 未宣告 (Smart Device/Visual Basic 編譯器錯誤) </span><span class="sxs-lookup"><span data-stu-id="1ee2d-102">'\<functionname>' is not declared (Smart Device/Visual Basic Compiler Error)</span></span>

<span data-ttu-id="1ee2d-103"><`functionname` 未宣告>。</span><span class="sxs-lookup"><span data-stu-id="1ee2d-103"><`functionname`> is not declared.</span></span> <span data-ttu-id="1ee2d-104">檔案 I/O 功能通常是在 `Microsoft.VisualBasic` 命名空間中，但是目標 .NET Compact Framework 版本並不支援它。</span><span class="sxs-lookup"><span data-stu-id="1ee2d-104">File I/O functionality is normally available in the `Microsoft.VisualBasic` namespace, but the targeted version of the .NET Compact Framework does not support it.</span></span>  
  
 <span data-ttu-id="1ee2d-105">**錯誤識別碼：** BC30766</span><span class="sxs-lookup"><span data-stu-id="1ee2d-105">**Error ID:** BC30766</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1ee2d-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="1ee2d-106">To correct this error</span></span>  
  
- <span data-ttu-id="1ee2d-107">使用 `System.IO` 命名空間中所定義的函式來執行檔案作業。</span><span class="sxs-lookup"><span data-stu-id="1ee2d-107">Perform file operations with functions defined in the `System.IO` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ee2d-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ee2d-108">See also</span></span>

- <xref:System.IO>
- [<span data-ttu-id="1ee2d-109">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="1ee2d-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
