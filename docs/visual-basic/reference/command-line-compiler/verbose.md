---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: f6d896fb0d41a8fa3ed613d29bc3fca2bd14cc5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796087"
---
# <a name="-verbose"></a><span data-ttu-id="57795-102">-verbose</span><span class="sxs-lookup"><span data-stu-id="57795-102">-verbose</span></span>
<span data-ttu-id="57795-103">可讓編譯器產生詳細的狀態和錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="57795-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57795-104">語法</span><span class="sxs-lookup"><span data-stu-id="57795-104">Syntax</span></span>  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="57795-105">引數</span><span class="sxs-lookup"><span data-stu-id="57795-105">Arguments</span></span>  
 <span data-ttu-id="57795-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="57795-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="57795-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="57795-107">Optional.</span></span> <span data-ttu-id="57795-108">指定`-verbose`等同於指定`-verbose+`，因而導致編譯器發出詳細訊息。</span><span class="sxs-lookup"><span data-stu-id="57795-108">Specifying `-verbose` is the same as specifying `-verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="57795-109">此選項的預設值是`-verbose-`。</span><span class="sxs-lookup"><span data-stu-id="57795-109">The default for this option is `-verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57795-110">備註</span><span class="sxs-lookup"><span data-stu-id="57795-110">Remarks</span></span>  
 <span data-ttu-id="57795-111">`-verbose`選項會顯示編譯器所發出的錯誤總數的相關資訊、 報表組件正在載入的模組，並顯示目前正在進行編譯的檔案。</span><span class="sxs-lookup"><span data-stu-id="57795-111">The `-verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57795-112">`-verbose`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="57795-112">The `-verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57795-113">範例</span><span class="sxs-lookup"><span data-stu-id="57795-113">Example</span></span>  
 <span data-ttu-id="57795-114">下列程式碼編譯`In.vb`和指示編譯器將會顯示詳細資訊的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="57795-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="57795-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57795-115">See also</span></span>

- [<span data-ttu-id="57795-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="57795-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="57795-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="57795-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
