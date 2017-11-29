---
title: /utf8output (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 23c7c308865a6b6afb07443a42090fff3d9e2efb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="utf8output-visual-basic"></a><span data-ttu-id="83c14-102">/utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83c14-102">/utf8output (Visual Basic)</span></span>
<span data-ttu-id="83c14-103">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="83c14-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c14-104">語法</span><span class="sxs-lookup"><span data-stu-id="83c14-104">Syntax</span></span>  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="83c14-105">引數</span><span class="sxs-lookup"><span data-stu-id="83c14-105">Arguments</span></span>  
 <span data-ttu-id="83c14-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="83c14-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="83c14-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="83c14-107">Optional.</span></span> <span data-ttu-id="83c14-108">這個選項的預設值是`/utf8output-`，這表示編譯器輸出不會使用 utf-8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83c14-108">The default for this option is `/utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="83c14-109">指定`/utf8output`等同於指定`/utf8output+`。</span><span class="sxs-lookup"><span data-stu-id="83c14-109">Specifying `/utf8output` is the same as specifying `/utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83c14-110">備註</span><span class="sxs-lookup"><span data-stu-id="83c14-110">Remarks</span></span>  
 <span data-ttu-id="83c14-111">在某些國際設定，在編譯器輸出無法正確顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="83c14-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="83c14-112">在這種情況下，使用`/utf8output`和編譯器輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="83c14-112">In such situations, use `/utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83c14-113">`/utf8output`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="83c14-113">The `/utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83c14-114">範例</span><span class="sxs-lookup"><span data-stu-id="83c14-114">Example</span></span>  
 <span data-ttu-id="83c14-115">下列程式碼編譯`In.vb`，並指示要顯示之編譯器輸出使用 utf-8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="83c14-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="83c14-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83c14-116">See Also</span></span>  
 [<span data-ttu-id="83c14-117">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="83c14-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="83c14-118">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="83c14-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
