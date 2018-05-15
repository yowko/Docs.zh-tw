---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f257fce67d8e348b69404411c12ded785cfd68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-verbose"></a><span data-ttu-id="247d3-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="247d3-102">-verbose</span></span>
<span data-ttu-id="247d3-103">讓編譯器以產生詳細的狀態和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="247d3-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="247d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="247d3-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="247d3-105">引數</span><span class="sxs-lookup"><span data-stu-id="247d3-105">Arguments</span></span>  
 <span data-ttu-id="247d3-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="247d3-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="247d3-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="247d3-107">Optional.</span></span> <span data-ttu-id="247d3-108">指定`-verbose`等同於指定`-verbose+`，因而導致編譯器發出詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="247d3-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="247d3-109">這個選項的預設值是`-verbose-`。</span><span class="sxs-lookup"><span data-stu-id="247d3-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="247d3-110">備註</span><span class="sxs-lookup"><span data-stu-id="247d3-110">Remarks</span></span>  
 <span data-ttu-id="247d3-111">`-verbose`選項顯示編譯器所發出的錯誤總數的相關資訊，會報告正在載入哪些組件的模組，並顯示目前正在進行編譯的檔案。</span><span class="sxs-lookup"><span data-stu-id="247d3-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="247d3-112">`-verbose`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="247d3-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="247d3-113">範例</span><span class="sxs-lookup"><span data-stu-id="247d3-113">Example</span></span>  
 <span data-ttu-id="247d3-114">下列程式碼編譯`In.vb`和指示編譯器將會顯示詳細的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="247d3-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="247d3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="247d3-115">See Also</span></span>  
 [<span data-ttu-id="247d3-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="247d3-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="247d3-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="247d3-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
