---
title: "/utf8output (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
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
ms.openlocfilehash: 45361fb1dca34f2cdc849184d0e316b27d9545b6
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="utf8output-visual-basic"></a><span data-ttu-id="c6788-102">/utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6788-102">/utf8output (Visual Basic)</span></span>
<span data-ttu-id="c6788-103">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="c6788-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6788-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6788-104">Syntax</span></span>  
  
```  
/utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c6788-105">引數</span><span class="sxs-lookup"><span data-stu-id="c6788-105">Arguments</span></span>  
 <span data-ttu-id="c6788-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c6788-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c6788-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="c6788-107">Optional.</span></span> <span data-ttu-id="c6788-108">此選項的預設值是`/utf8output-`，這表示編譯器輸出不會使用 utf-8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c6788-108">The default for this option is `/utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="c6788-109">指定`/utf8output`等同於指定`/utf8output+`。</span><span class="sxs-lookup"><span data-stu-id="c6788-109">Specifying `/utf8output` is the same as specifying `/utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6788-110">備註</span><span class="sxs-lookup"><span data-stu-id="c6788-110">Remarks</span></span>  
 <span data-ttu-id="c6788-111">在某些國際設定，編譯器輸出無法正確顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="c6788-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="c6788-112">在這種情況下，使用`/utf8output`和編譯器輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="c6788-112">In such situations, use `/utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6788-113">`/utf8output`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="c6788-113">The `/utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6788-114">範例</span><span class="sxs-lookup"><span data-stu-id="c6788-114">Example</span></span>  
 <span data-ttu-id="c6788-115">下列程式碼編譯`In.vb`，並指示編譯器顯示輸出使用 utf-8 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="c6788-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```  
vbc /utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6788-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6788-116">See Also</span></span>  
 <span data-ttu-id="c6788-117">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="c6788-117">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="c6788-118"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="c6788-118"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
