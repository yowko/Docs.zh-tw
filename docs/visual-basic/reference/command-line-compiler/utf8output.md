---
title: -utf8output
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 2faebb7870cbc019d479215563261f331f9fddcf
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085070"
---
# <a name="-utf8output-visual-basic"></a><span data-ttu-id="d70a2-102">-utf8output (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="d70a2-102">-utf8output (Visual Basic)</span></span>

<span data-ttu-id="d70a2-103">使用 UTF-8 編碼顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="d70a2-103">Displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="d70a2-104">Syntax</span></span>  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d70a2-105">引數</span><span class="sxs-lookup"><span data-stu-id="d70a2-105">Arguments</span></span>  

 <span data-ttu-id="d70a2-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d70a2-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d70a2-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d70a2-107">Optional.</span></span> <span data-ttu-id="d70a2-108">這個選項的預設值是 `-utf8output-` ，這表示編譯器輸出不會使用 utf-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="d70a2-108">The default for this option is `-utf8output-`, which means compiler output does not use UTF-8 encoding.</span></span> <span data-ttu-id="d70a2-109">指定 `-utf8output` 等同於指定 `-utf8output+`。</span><span class="sxs-lookup"><span data-stu-id="d70a2-109">Specifying `-utf8output` is the same as specifying `-utf8output+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d70a2-110">備註</span><span class="sxs-lookup"><span data-stu-id="d70a2-110">Remarks</span></span>  

 <span data-ttu-id="d70a2-111">在某些國際設定中，無法在主控台中正確顯示編譯器輸出。</span><span class="sxs-lookup"><span data-stu-id="d70a2-111">In some international configurations, compiler output cannot be displayed correctly in the console.</span></span> <span data-ttu-id="d70a2-112">在這種情況下，請使用 `-utf8output` 並將編譯器輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="d70a2-112">In such situations, use `-utf8output` and redirect compiler output to a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d70a2-113">`-utf8output`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="d70a2-113">The `-utf8output` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d70a2-114">範例</span><span class="sxs-lookup"><span data-stu-id="d70a2-114">Example</span></span>  

 <span data-ttu-id="d70a2-115">下列程式碼會編譯 `In.vb` 並指示編譯器使用 utf-8 編碼來顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="d70a2-115">The following code compiles `In.vb` and directs the compiler to display output using UTF-8 encoding.</span></span>  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d70a2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d70a2-116">See also</span></span>

- [<span data-ttu-id="d70a2-117">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="d70a2-117">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d70a2-118">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="d70a2-118">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
