---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 753c92cdf2124ee7fb1b471c7bc543b6db6f3daa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="391d3-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="391d3-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="391d3-103">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="391d3-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="391d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="391d3-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="391d3-105">引數</span><span class="sxs-lookup"><span data-stu-id="391d3-105">Arguments</span></span>  
 <span data-ttu-id="391d3-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="391d3-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="391d3-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="391d3-107">Optional.</span></span> <span data-ttu-id="391d3-108">這個選項的預設值是`-utf8output-`，這表示編譯器輸出不會使用 utf-8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="391d3-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="391d3-109">指定`-utf8output`等同於指定`-utf8output+`。</span><span class="sxs-lookup"><span data-stu-id="391d3-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="391d3-110">備註</span><span class="sxs-lookup"><span data-stu-id="391d3-110">Remarks</span></span>  
 <span data-ttu-id="391d3-111">在某些國際設定，在編譯器輸出無法正確顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="391d3-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="391d3-112">在這種情況下，使用`-utf8output`和編譯器輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="391d3-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="391d3-113">`-utf8output`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="391d3-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="391d3-114">範例</span><span class="sxs-lookup"><span data-stu-id="391d3-114">Example</span></span>  
 <span data-ttu-id="391d3-115">下列程式碼編譯`In.vb`，並指示要顯示之編譯器輸出使用 utf-8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="391d3-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="391d3-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="391d3-116">See Also</span></span>  
 [<span data-ttu-id="391d3-117">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="391d3-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="391d3-118">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="391d3-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
