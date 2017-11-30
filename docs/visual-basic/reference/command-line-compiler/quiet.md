---
title: /quiet
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b816cadb9d805d57a14e9b5df553654dd8167af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="quiet"></a><span data-ttu-id="c2108-102">/quiet</span><span class="sxs-lookup"><span data-stu-id="c2108-102">/quiet</span></span>
<span data-ttu-id="c2108-103">防止編譯器顯示語法相關錯誤和警告的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2108-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2108-104">語法</span><span class="sxs-lookup"><span data-stu-id="c2108-104">Syntax</span></span>  
  
```  
/quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="c2108-105">備註</span><span class="sxs-lookup"><span data-stu-id="c2108-105">Remarks</span></span>  
 <span data-ttu-id="c2108-106">`/quiet` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="c2108-106">By default, `/quiet` is not in effect.</span></span> <span data-ttu-id="c2108-107">當編譯器報告語法相關錯誤或警告時，它也會輸出從來源程式碼行。</span><span class="sxs-lookup"><span data-stu-id="c2108-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="c2108-108">剖析編譯器輸出的應用程式，可能更方便編譯器輸出的診斷文字。</span><span class="sxs-lookup"><span data-stu-id="c2108-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="c2108-109">在下列範例中，`Module1`輸出錯誤包含原始碼時將不會編譯`/quiet`。</span><span class="sxs-lookup"><span data-stu-id="c2108-109">In the following example, `Module1` outputs an error that includes source code when compiled without `/quiet`.</span></span>  
  
```  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c2108-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="c2108-110">Output:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
 `x`  
  
 `~`  
  
 <span data-ttu-id="c2108-111">以編譯`/quiet`，編譯器只會輸出下列：</span><span class="sxs-lookup"><span data-stu-id="c2108-111">Compiled with `/quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="c2108-112">`/quiet`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="c2108-112">The `/quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2108-113">範例</span><span class="sxs-lookup"><span data-stu-id="c2108-113">Example</span></span>  
 <span data-ttu-id="c2108-114">下列程式碼編譯`T2.vb`並不會顯示語法相關編譯器診斷程式碼：</span><span class="sxs-lookup"><span data-stu-id="c2108-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc /quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2108-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2108-115">See Also</span></span>  
 [<span data-ttu-id="c2108-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="c2108-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c2108-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="c2108-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
