---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004982"
---
# <a name="-verbose"></a><span data-ttu-id="5f211-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="5f211-102">-verbose</span></span>
<span data-ttu-id="5f211-103">使編譯器產生詳細的狀態和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="5f211-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f211-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f211-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f211-105">引數</span><span class="sxs-lookup"><span data-stu-id="5f211-105">Arguments</span></span>  
 <span data-ttu-id="5f211-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5f211-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="5f211-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="5f211-107">Optional.</span></span> <span data-ttu-id="5f211-108">指定 `-verbose` 與指定 `-verbose+` 相同，這會導致編譯器發出詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="5f211-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="5f211-109">此選項的預設值為 `-verbose-`。</span><span class="sxs-lookup"><span data-stu-id="5f211-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f211-110">備註</span><span class="sxs-lookup"><span data-stu-id="5f211-110">Remarks</span></span>  
 <span data-ttu-id="5f211-111">[@No__t-0] 選項會顯示編譯器發出之錯誤總數的相關資訊、報告模組正在載入哪些元件，以及顯示目前正在編譯的檔案。</span><span class="sxs-lookup"><span data-stu-id="5f211-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f211-112">@No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="5f211-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f211-113">範例</span><span class="sxs-lookup"><span data-stu-id="5f211-113">Example</span></span>  
 <span data-ttu-id="5f211-114">下列程式碼會編譯 `In.vb`，並指示編譯器顯示詳細狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="5f211-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f211-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f211-115">See also</span></span>

- [<span data-ttu-id="5f211-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="5f211-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5f211-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="5f211-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
