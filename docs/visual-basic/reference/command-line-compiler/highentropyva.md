---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 4d88c302281097fabd0eb361d60319bc8a0daf8d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058062"
---
# <a name="-highentropyva-visual-basic"></a><span data-ttu-id="d100f-102">-highentropyva (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="d100f-102">-highentropyva (Visual Basic)</span></span>

<span data-ttu-id="d100f-103">指出64位可執行檔或由 [-platform： anycpu](platform.md) 編譯器選項標記的可執行檔，是否支援高熵位址空間配置隨機載入 (ASLR) 。</span><span class="sxs-lookup"><span data-stu-id="d100f-103">Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d100f-104">語法</span><span class="sxs-lookup"><span data-stu-id="d100f-104">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d100f-105">引數</span><span class="sxs-lookup"><span data-stu-id="d100f-105">Arguments</span></span>  

 <span data-ttu-id="d100f-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="d100f-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="d100f-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="d100f-107">Optional.</span></span> <span data-ttu-id="d100f-108">此選項預設為關閉，或指定 `-highentropyva-` 。</span><span class="sxs-lookup"><span data-stu-id="d100f-108">The option is off by default or if you specify `-highentropyva-`.</span></span> <span data-ttu-id="d100f-109">如果您指定或，就會開啟此選項 `-highentropyva` `-highentropyva+` 。</span><span class="sxs-lookup"><span data-stu-id="d100f-109">The option is on if you specify `-highentropyva` or `-highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d100f-110">備註</span><span class="sxs-lookup"><span data-stu-id="d100f-110">Remarks</span></span>  

 <span data-ttu-id="d100f-111">如果您指定此選項，當核心隨機化進程的位址空間配置作為 ASLR 的一部分時，相容的 Windows 核心版本可能會使用較高程度的熵。</span><span class="sxs-lookup"><span data-stu-id="d100f-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="d100f-112">如果核心使用較高程度的熵，可將較大量的位址配置給記憶體區域（例如堆疊和堆積）。</span><span class="sxs-lookup"><span data-stu-id="d100f-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="d100f-113">因此更難猜測特定記憶體區域的位置。</span><span class="sxs-lookup"><span data-stu-id="d100f-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="d100f-114">當此選項為 on 時，目標可執行檔及其相依的任何模組，都必須能夠處理大於 4 gb (GB 的指標值，) 當這些模組以64位進程的形式執行時。</span><span class="sxs-lookup"><span data-stu-id="d100f-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d100f-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d100f-115">See also</span></span>

- [<span data-ttu-id="d100f-116">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="d100f-116">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="d100f-117">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="d100f-117">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
