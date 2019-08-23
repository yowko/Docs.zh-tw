---
title: '@ (指定回應檔) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: b84d50334e56305c27c5c0bc54578ba871a28365
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937288"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="60337-102">@ (指定回應檔) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60337-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="60337-103">指定檔案, 其中包含要編譯的編譯器選項和原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="60337-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60337-104">語法</span><span class="sxs-lookup"><span data-stu-id="60337-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="60337-105">引數</span><span class="sxs-lookup"><span data-stu-id="60337-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="60337-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="60337-106">Required.</span></span> <span data-ttu-id="60337-107">列出要編譯之編譯器選項或原始程式碼檔案的檔案。</span><span class="sxs-lookup"><span data-stu-id="60337-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="60337-108">將檔案名括在引號 ("") 中 (如果它包含空格)。</span><span class="sxs-lookup"><span data-stu-id="60337-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60337-109">備註</span><span class="sxs-lookup"><span data-stu-id="60337-109">Remarks</span></span>  
 <span data-ttu-id="60337-110">編譯器會處理在回應檔中指定的編譯器選項和原始程式碼檔, 如同已在命令列上指定。</span><span class="sxs-lookup"><span data-stu-id="60337-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="60337-111">若要在編譯中指定一個以上的回應檔, 請指定多個回應檔案選項, 如下所示。</span><span class="sxs-lookup"><span data-stu-id="60337-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="60337-112">在回應檔中, 多個編譯器選項和原始程式碼檔可能會出現在一行上。</span><span class="sxs-lookup"><span data-stu-id="60337-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="60337-113">單一編譯器選項規格必須出現在一行 (不能跨越多行)。</span><span class="sxs-lookup"><span data-stu-id="60337-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="60337-114">回應檔可以有以`#`符號開頭的批註。</span><span class="sxs-lookup"><span data-stu-id="60337-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="60337-115">您可以結合在命令列上指定的選項與一個或多個回應檔中指定的選項。</span><span class="sxs-lookup"><span data-stu-id="60337-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="60337-116">編譯器會在遇到命令選項時進行處理。</span><span class="sxs-lookup"><span data-stu-id="60337-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="60337-117">因此, 命令列引數可以覆寫回應檔中先前列出的選項。</span><span class="sxs-lookup"><span data-stu-id="60337-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="60337-118">相反地, 回應檔中的選項會覆寫先前在命令列或其他回應檔中列出的選項。</span><span class="sxs-lookup"><span data-stu-id="60337-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="60337-119">Visual Basic 提供 Vbc .rsp 檔案, 該檔案位於與 Vbc 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="60337-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="60337-120">除非使用`-noconfig`選項, 否則預設會包含 Vbc 檔案。</span><span class="sxs-lookup"><span data-stu-id="60337-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="60337-121">如需詳細資訊, 請參閱[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)。</span><span class="sxs-lookup"><span data-stu-id="60337-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60337-122">此`@`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="60337-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60337-123">範例</span><span class="sxs-lookup"><span data-stu-id="60337-123">Example</span></span>  
 <span data-ttu-id="60337-124">下列幾行來自範例回應檔。</span><span class="sxs-lookup"><span data-stu-id="60337-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="60337-125">範例</span><span class="sxs-lookup"><span data-stu-id="60337-125">Example</span></span>  
 <span data-ttu-id="60337-126">下列範例示範如何搭配使用`@`選項與名為`File1.rsp`的回應檔。</span><span class="sxs-lookup"><span data-stu-id="60337-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="60337-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60337-127">See also</span></span>

- [<span data-ttu-id="60337-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="60337-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="60337-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="60337-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="60337-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="60337-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
