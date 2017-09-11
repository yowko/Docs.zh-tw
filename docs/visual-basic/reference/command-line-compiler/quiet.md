---
title: "/quiet |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
dev_langs:
- VB
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bc21be8982fea52bf25d0bedeec2b78eee1e705f
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="quiet"></a><span data-ttu-id="1a6b8-102">/quiet</span><span class="sxs-lookup"><span data-stu-id="1a6b8-102">/quiet</span></span>
<span data-ttu-id="1a6b8-103">防止編譯器顯示語法相關錯誤和警告的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1a6b8-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a6b8-104">語法</span><span class="sxs-lookup"><span data-stu-id="1a6b8-104">Syntax</span></span>  
  
```  
/quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="1a6b8-105">備註</span><span class="sxs-lookup"><span data-stu-id="1a6b8-105">Remarks</span></span>  
 <span data-ttu-id="1a6b8-106">`/quiet` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="1a6b8-106">By default, `/quiet` is not in effect.</span></span> <span data-ttu-id="1a6b8-107">當編譯器報告與語法相關的錯誤或警告時，它也會輸出原始程式碼中的一行。</span><span class="sxs-lookup"><span data-stu-id="1a6b8-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="1a6b8-108">對於剖析編譯器輸出的應用程式，可能會更方便編譯器輸出的診斷文字。</span><span class="sxs-lookup"><span data-stu-id="1a6b8-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="1a6b8-109">在下列範例中，`Module1`輸出錯誤包含原始程式碼，而不需要編譯時`/quiet`。</span><span class="sxs-lookup"><span data-stu-id="1a6b8-109">In the following example, `Module1` outputs an error that includes source code when compiled without `/quiet`.</span></span>  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="1a6b8-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="1a6b8-110">Output:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 <span data-ttu-id="1a6b8-111">以編譯`/quiet`，編譯器只會輸出下列︰</span><span class="sxs-lookup"><span data-stu-id="1a6b8-111">Compiled with `/quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="1a6b8-112">`/quiet`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="1a6b8-112">The `/quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a6b8-113">範例</span><span class="sxs-lookup"><span data-stu-id="1a6b8-113">Example</span></span>  
 <span data-ttu-id="1a6b8-114">下列程式碼編譯`T2.vb`並不會顯示與語法相關編譯器診斷程式碼︰</span><span class="sxs-lookup"><span data-stu-id="1a6b8-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a6b8-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a6b8-115">See Also</span></span>  
 <span data-ttu-id="1a6b8-116">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="1a6b8-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="1a6b8-117"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="1a6b8-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
