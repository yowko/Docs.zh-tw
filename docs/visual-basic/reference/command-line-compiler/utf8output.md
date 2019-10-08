---
title: -utf8output （Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: adcb518cbe8397549c3ae3b3a8ca9f0ecf9dc38e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004663"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="f5e76-102">-utf8output （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="f5e76-102">-utf8output (Visual Basic)</span></span>
<span data-ttu-id="f5e76-103">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="f5e76-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5e76-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5e76-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f5e76-105">引數</span><span class="sxs-lookup"><span data-stu-id="f5e76-105">Arguments</span></span>  
 <span data-ttu-id="f5e76-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f5e76-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="f5e76-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f5e76-107">Optional.</span></span> <span data-ttu-id="f5e76-108">此選項的預設值為 `-utf8output-`，這表示編譯器輸出不會使用 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="f5e76-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="f5e76-109">指定 `-utf8output` 等同於指定 `-utf8output+`。</span><span class="sxs-lookup"><span data-stu-id="f5e76-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5e76-110">備註</span><span class="sxs-lookup"><span data-stu-id="f5e76-110">Remarks</span></span>  
 <span data-ttu-id="f5e76-111">在某些國際設定中，編譯器輸出無法正確地顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="f5e76-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="f5e76-112">在這種情況下，請使用 `-utf8output`，並將編譯器輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="f5e76-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f5e76-113">@No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="f5e76-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5e76-114">範例</span><span class="sxs-lookup"><span data-stu-id="f5e76-114">Example</span></span>  
 <span data-ttu-id="f5e76-115">下列程式碼會編譯 `In.vb`，並指示編譯器使用 UTF-8 編碼來顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="f5e76-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5e76-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5e76-116">See also</span></span>

- [<span data-ttu-id="f5e76-117">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f5e76-117">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f5e76-118">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="f5e76-118">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
