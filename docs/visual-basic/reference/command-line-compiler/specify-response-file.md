---
title: '@ (指定回應檔) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: 6b993a6399eec4e203821109db153aadf246cbac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838114"
---
# <a name="-specify-response-file-visual-basic"></a><span data-ttu-id="639e4-102">@ (指定回應檔) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="639e4-102">@ (Specify Response File) (Visual Basic)</span></span>
<span data-ttu-id="639e4-103">指定包含編譯器選項的檔案和要編譯的原始程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="639e4-103">Specifies a file that contains compiler options and source-code files to compile.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="639e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="639e4-104">Syntax</span></span>  
  
```  
@response_file  
```  
  
## <a name="arguments"></a><span data-ttu-id="639e4-105">引數</span><span class="sxs-lookup"><span data-stu-id="639e4-105">Arguments</span></span>  
 `response_file`  
 <span data-ttu-id="639e4-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="639e4-106">Required.</span></span> <span data-ttu-id="639e4-107">列出編譯器選項或原始程式檔編譯的檔案。</span><span class="sxs-lookup"><span data-stu-id="639e4-107">A file that lists compiler options or source-code files to compile.</span></span> <span data-ttu-id="639e4-108">將檔案名稱括在引號 ("") 如果它包含空格。</span><span class="sxs-lookup"><span data-stu-id="639e4-108">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="639e4-109">備註</span><span class="sxs-lookup"><span data-stu-id="639e4-109">Remarks</span></span>  
 <span data-ttu-id="639e4-110">編譯器會處理編譯器選項和原始程式碼檔，如同它們已在命令列上指定回應檔中指定。</span><span class="sxs-lookup"><span data-stu-id="639e4-110">The compiler processes the compiler options and source-code files specified in a response file as if they had been specified on the command line.</span></span>  
  
 <span data-ttu-id="639e4-111">若要指定一個以上的回應檔案在編譯中，指定多個回應檔選項，如下所示。</span><span class="sxs-lookup"><span data-stu-id="639e4-111">To specify more than one response file in a compilation, specify multiple response-file options, such as the following.</span></span>  
  
```  
@file1.rsp @file2.rsp  
```  
  
 <span data-ttu-id="639e4-112">在回應檔案、 多個編譯器選項和原始程式碼檔可以出現在一行上。</span><span class="sxs-lookup"><span data-stu-id="639e4-112">In a response file, multiple compiler options and source-code files can appear on one line.</span></span> <span data-ttu-id="639e4-113">單一編譯器選項規格必須出現在一行 （無法跨越多行）。</span><span class="sxs-lookup"><span data-stu-id="639e4-113">A single compiler-option specification must appear on one line (cannot span multiple lines).</span></span> <span data-ttu-id="639e4-114">回應檔案可以有開頭的註解`#`符號。</span><span class="sxs-lookup"><span data-stu-id="639e4-114">Response files can have comments that begin with the `#` symbol.</span></span>  
  
 <span data-ttu-id="639e4-115">您可以結合一或多個回應檔中指定選項在命令列上指定的選項。</span><span class="sxs-lookup"><span data-stu-id="639e4-115">You can combine options specified on the command line with options specified in one or more response files.</span></span> <span data-ttu-id="639e4-116">當它遇到它們，編譯器會處理命令選項。</span><span class="sxs-lookup"><span data-stu-id="639e4-116">The compiler processes the command options as it encounters them.</span></span> <span data-ttu-id="639e4-117">因此，命令列引數可以覆寫回應檔中先前列出的選項。</span><span class="sxs-lookup"><span data-stu-id="639e4-117">Therefore, command-line arguments can override previously listed options in response files.</span></span> <span data-ttu-id="639e4-118">相反地，回應檔中的選項會覆寫在命令列上或其他回應檔中先前所列的選項。</span><span class="sxs-lookup"><span data-stu-id="639e4-118">Conversely, options in a response file override options listed previously on the command line or in other response files.</span></span>  
  
 <span data-ttu-id="639e4-119">Visual Basic 提供 Vbc.rsp 檔案，位於與 Vbc.exe 檔案相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="639e4-119">Visual Basic provides the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="639e4-120">依預設會包括 Vbc.rsp 檔案，除非`-noconfig`選項使用。</span><span class="sxs-lookup"><span data-stu-id="639e4-120">The Vbc.rsp file is included by default unless the `-noconfig` option is used.</span></span> <span data-ttu-id="639e4-121">如需詳細資訊，請參閱 < [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)。</span><span class="sxs-lookup"><span data-stu-id="639e4-121">For more information, see [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="639e4-122">`@`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="639e4-122">The `@` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="639e4-123">範例</span><span class="sxs-lookup"><span data-stu-id="639e4-123">Example</span></span>  
 <span data-ttu-id="639e4-124">下列幾行是從範例回應檔案。</span><span class="sxs-lookup"><span data-stu-id="639e4-124">The following lines are from a sample response file.</span></span>  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a><span data-ttu-id="639e4-125">範例</span><span class="sxs-lookup"><span data-stu-id="639e4-125">Example</span></span>  
 <span data-ttu-id="639e4-126">下列範例示範如何使用`@`包含名為回應檔選項`File1.rsp`。</span><span class="sxs-lookup"><span data-stu-id="639e4-126">The following example demonstrates how to use the `@` option with the response file named `File1.rsp`.</span></span>  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="639e4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="639e4-127">See also</span></span>

- [<span data-ttu-id="639e4-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="639e4-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="639e4-129">-noconfig</span><span class="sxs-lookup"><span data-stu-id="639e4-129">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="639e4-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="639e4-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
