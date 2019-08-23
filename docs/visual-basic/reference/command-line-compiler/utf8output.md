---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 789df84bb4011d1ad128c50a9c689d1217be6694
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937281"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="e2230-102">-utf8output (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2230-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="e2230-103">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="e2230-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2230-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2230-104">Syntax</span></span>  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2230-105">引數</span><span class="sxs-lookup"><span data-stu-id="e2230-105">Arguments</span></span>  
 <span data-ttu-id="e2230-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e2230-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e2230-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e2230-107">Optional.</span></span> <span data-ttu-id="e2230-108">這個選項的預設值是`-utf8output-`, 這表示編譯器輸出不會使用 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="e2230-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="e2230-109">指定 `-utf8output` 等同於指定 `-utf8output+`。</span><span class="sxs-lookup"><span data-stu-id="e2230-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2230-110">備註</span><span class="sxs-lookup"><span data-stu-id="e2230-110">Remarks</span></span>  
 <span data-ttu-id="e2230-111">在某些國際設定中, 編譯器輸出無法正確地顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="e2230-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="e2230-112">在這種情況下`-utf8output` , 請使用, 並將編譯器輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="e2230-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2230-113">此`-utf8output`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="e2230-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2230-114">範例</span><span class="sxs-lookup"><span data-stu-id="e2230-114">Example</span></span>  
 <span data-ttu-id="e2230-115">下列程式碼會`In.vb`編譯並指示編譯器使用 utf-8 編碼來顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="e2230-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2230-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2230-116">See also</span></span>

- [<span data-ttu-id="e2230-117">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="e2230-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e2230-118">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="e2230-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
