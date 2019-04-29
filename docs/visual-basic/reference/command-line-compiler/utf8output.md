---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 75369c3bcb19afbf98bfb80bc3e439f996d2a9d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796074"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="2826d-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2826d-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="2826d-103">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="2826d-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2826d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2826d-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2826d-105">引數</span><span class="sxs-lookup"><span data-stu-id="2826d-105">Arguments</span></span>  
 <span data-ttu-id="2826d-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2826d-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2826d-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2826d-107">Optional.</span></span> <span data-ttu-id="2826d-108">此選項的預設值是`-utf8output-`，這表示編譯器輸出不會使用 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="2826d-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="2826d-109">指定 `-utf8output` 等同於指定 `-utf8output+`。</span><span class="sxs-lookup"><span data-stu-id="2826d-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2826d-110">備註</span><span class="sxs-lookup"><span data-stu-id="2826d-110">Remarks</span></span>  
 <span data-ttu-id="2826d-111">在某些國際組態中，編譯器輸出無法正確顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="2826d-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="2826d-112">在這種情況下，使用`-utf8output`和編譯器輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="2826d-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2826d-113">`-utf8output`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="2826d-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2826d-114">範例</span><span class="sxs-lookup"><span data-stu-id="2826d-114">Example</span></span>  
 <span data-ttu-id="2826d-115">下列程式碼編譯`In.vb`，並指示顯示編譯器輸出使用 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="2826d-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2826d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2826d-116">See also</span></span>

- [<span data-ttu-id="2826d-117">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="2826d-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2826d-118">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="2826d-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
