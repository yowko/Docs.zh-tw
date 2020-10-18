---
title: "'<functionname>' 未宣告 (智慧型裝置 - Visual Basic 編譯器錯誤)"
ms.date: 07/20/2015
f1_keywords:
- bc30766
- vbc30766
helpviewer_keywords:
- BC30766
ms.assetid: 13918600-6087-40d7-8134-32aa9d3bfda4
ms.openlocfilehash: 1c57e1aaea2eb52133d37b782f8fa0ddd96943a9
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163398"
---
# <a name="bc30766-functionname-is-not-declared-smart-devicevisual-basic-compiler-error"></a><span data-ttu-id="01176-102">BC30766： ' \<functionname> ' 未宣告 (Smart Device/Visual Basic 編譯器錯誤) </span><span class="sxs-lookup"><span data-stu-id="01176-102">BC30766: '\<functionname>' is not declared (Smart Device/Visual Basic Compiler Error)</span></span>

<span data-ttu-id="01176-103"><`functionname` 未宣告>。</span><span class="sxs-lookup"><span data-stu-id="01176-103"><`functionname`> is not declared.</span></span> <span data-ttu-id="01176-104">檔案 I/O 功能通常是在 `Microsoft.VisualBasic` 命名空間中，但是目標 .NET Compact Framework 版本並不支援它。</span><span class="sxs-lookup"><span data-stu-id="01176-104">File I/O functionality is normally available in the `Microsoft.VisualBasic` namespace, but the targeted version of the .NET Compact Framework does not support it.</span></span>

 <span data-ttu-id="01176-105">**錯誤識別碼：** BC30766</span><span class="sxs-lookup"><span data-stu-id="01176-105">**Error ID:** BC30766</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="01176-106">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="01176-106">To correct this error</span></span>

- <span data-ttu-id="01176-107">使用 `System.IO` 命名空間中所定義的函式來執行檔案作業。</span><span class="sxs-lookup"><span data-stu-id="01176-107">Perform file operations with functions defined in the `System.IO` namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="01176-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01176-108">See also</span></span>

- <xref:System.IO>
- [<span data-ttu-id="01176-109">使用 Visual Basic 存取檔案</span><span class="sxs-lookup"><span data-stu-id="01176-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
