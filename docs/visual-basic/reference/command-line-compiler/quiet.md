---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: 32f82eb428c1d3bc427a10b9ca7a1a5feb9e339a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816534"
---
# <a name="-quiet"></a><span data-ttu-id="10387-102">-quiet</span><span class="sxs-lookup"><span data-stu-id="10387-102">-quiet</span></span>
<span data-ttu-id="10387-103">防止編譯器顯示語法相關錯誤和警告的程式碼。</span><span class="sxs-lookup"><span data-stu-id="10387-103">Prevents the compiler from displaying code for syntax-related errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10387-104">語法</span><span class="sxs-lookup"><span data-stu-id="10387-104">Syntax</span></span>  
  
```  
-quiet  
```  
  
## <a name="remarks"></a><span data-ttu-id="10387-105">備註</span><span class="sxs-lookup"><span data-stu-id="10387-105">Remarks</span></span>  
 <span data-ttu-id="10387-106">`-quiet` 預設為非作用中。</span><span class="sxs-lookup"><span data-stu-id="10387-106">By default, `-quiet` is not in effect.</span></span> <span data-ttu-id="10387-107">當編譯器報告語法相關錯誤或警告時，它也會輸出從來源程式碼行。</span><span class="sxs-lookup"><span data-stu-id="10387-107">When the compiler reports a syntax-related error or warning, it also outputs the line from source code.</span></span> <span data-ttu-id="10387-108">剖析編譯器輸出的應用程式，它可能會更方便的編譯器輸出的診斷文字項目。</span><span class="sxs-lookup"><span data-stu-id="10387-108">For applications that parse compiler output, it may be more convenient for the compiler to output only the text of the diagnostic.</span></span>  
  
 <span data-ttu-id="10387-109">在下列範例中，`Module1`輸出錯誤包含原始程式碼，而不需要編譯時`-quiet`。</span><span class="sxs-lookup"><span data-stu-id="10387-109">In the following example, `Module1` outputs an error that includes source code when compiled without `-quiet`.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        x()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="10387-110">輸出：</span><span class="sxs-lookup"><span data-stu-id="10387-110">Output:</span></span>  
 
```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
``` 
 <span data-ttu-id="10387-111">以編譯`-quiet`，編譯器只會輸出下列：</span><span class="sxs-lookup"><span data-stu-id="10387-111">Compiled with `-quiet`, the compiler outputs only the following:</span></span>  
  
 `E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.`  
  
> [!NOTE]
>  <span data-ttu-id="10387-112">`-quiet`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="10387-112">The `-quiet` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10387-113">範例</span><span class="sxs-lookup"><span data-stu-id="10387-113">Example</span></span>  
 <span data-ttu-id="10387-114">下列程式碼編譯`T2.vb`並不會顯示語法相關的編譯器診斷的程式碼：</span><span class="sxs-lookup"><span data-stu-id="10387-114">The following code compiles `T2.vb` and does not display code for syntax-related compiler diagnostics:</span></span>  
  
```  
vbc -quiet t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="10387-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10387-115">See also</span></span>

- [<span data-ttu-id="10387-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="10387-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="10387-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="10387-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
