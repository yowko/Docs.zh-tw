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
# <a name="-verbose"></a><span data-ttu-id="f77cd-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="f77cd-102">-verbose</span></span>
<span data-ttu-id="f77cd-103">使編譯器產生詳細的狀態和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="f77cd-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f77cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="f77cd-104">Syntax</span></span>  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f77cd-105">引數</span><span class="sxs-lookup"><span data-stu-id="f77cd-105">Arguments</span></span>  
 <span data-ttu-id="f77cd-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f77cd-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="f77cd-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f77cd-107">Optional.</span></span> <span data-ttu-id="f77cd-108">指定`-verbose`與指定`-verbose+`相同，這會導致編譯器發出詳細資訊訊息。</span><span class="sxs-lookup"><span data-stu-id="f77cd-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="f77cd-109">此選項的預設值為`-verbose-`。</span><span class="sxs-lookup"><span data-stu-id="f77cd-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f77cd-110">備註</span><span class="sxs-lookup"><span data-stu-id="f77cd-110">Remarks</span></span>  
 <span data-ttu-id="f77cd-111">`-verbose`選項會顯示編譯器發出之錯誤總數的相關資訊、報告模組正在載入哪些元件，以及顯示目前正在編譯的檔案。</span><span class="sxs-lookup"><span data-stu-id="f77cd-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f77cd-112">此`-verbose`選項無法在 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="f77cd-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f77cd-113">範例</span><span class="sxs-lookup"><span data-stu-id="f77cd-113">Example</span></span>  
 <span data-ttu-id="f77cd-114">下列程式碼會`In.vb`編譯並指示編譯器顯示詳細的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="f77cd-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f77cd-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f77cd-115">See also</span></span>

- [<span data-ttu-id="f77cd-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f77cd-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f77cd-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="f77cd-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
