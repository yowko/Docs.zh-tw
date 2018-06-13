---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef3f922d3089eaca1762ffe35fa38cfe94baf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656310"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="2098f-102">-highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2098f-102">-highentropyva (Visual Basic)</span></span>
<span data-ttu-id="2098f-103">指出是否在 64 位元可執行檔或可執行檔標記的[/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)編譯器選項支援高熵位址空間配置隨機載入 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="2098f-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2098f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2098f-104">Syntax</span></span>  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2098f-105">引數</span><span class="sxs-lookup"><span data-stu-id="2098f-105">Arguments</span></span>  
 <span data-ttu-id="2098f-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2098f-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2098f-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2098f-107">Optional.</span></span> <span data-ttu-id="2098f-108">此選項預設為 off，或如果您指定`-highentropyva-`。</span><span class="sxs-lookup"><span data-stu-id="2098f-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="2098f-109">選項為開啟如果您指定`-highentropyva`或`-highentropyva+`。</span><span class="sxs-lookup"><span data-stu-id="2098f-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2098f-110">備註</span><span class="sxs-lookup"><span data-stu-id="2098f-110">Remarks</span></span>  
 <span data-ttu-id="2098f-111">如果您指定這個選項，因為相容版本的 Windows 核心核心隨機放置程序的位址空間配置個做為 ASLR 一部分時可以使用較高程度的高熵。</span><span class="sxs-lookup"><span data-stu-id="2098f-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="2098f-112">如果核心使用的 entropy 較高程度，更大量的位址可以配置到記憶體區域，例如堆疊和堆積。</span><span class="sxs-lookup"><span data-stu-id="2098f-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="2098f-113">因此更難猜測特定記憶體區域的位置。</span><span class="sxs-lookup"><span data-stu-id="2098f-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="2098f-114">選項時，目標可執行檔和任何模組上的相依必須能夠處理這些模組做為 64 位元處理序執行時，不大於 4 gb 的指標值。</span><span class="sxs-lookup"><span data-stu-id="2098f-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2098f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2098f-115">See Also</span></span>  
 [<span data-ttu-id="2098f-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="2098f-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2098f-117">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="2098f-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
