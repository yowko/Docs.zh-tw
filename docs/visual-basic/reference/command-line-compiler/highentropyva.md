---
title: "/highentropyva (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
caps.latest.revision: 12
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
ms.openlocfilehash: ef482f142e07e96eabf93bd2223b0d24f351553b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="highentropyva-visual-basic"></a><span data-ttu-id="b9de0-102">/highentropyva (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9de0-102">/highentropyva (Visual Basic)</span></span>
<span data-ttu-id="b9de0-103">指出是否在 64 位元可執行檔或可執行檔標記的[/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md)編譯器選項支援高熵位址空間配置隨機載入 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="b9de0-103">Indicates whether a 64-bit executable or an executable that's marked by the [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9de0-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9de0-104">Syntax</span></span>  
  
```  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b9de0-105">引數</span><span class="sxs-lookup"><span data-stu-id="b9de0-105">Arguments</span></span>  
 <span data-ttu-id="b9de0-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b9de0-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="b9de0-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="b9de0-107">Optional.</span></span> <span data-ttu-id="b9de0-108">此選項預設為關閉，或如果您指定`/highentropyva-`。</span><span class="sxs-lookup"><span data-stu-id="b9de0-108">The option is off by default or if you specify `/highentropyva-`.</span></span> <span data-ttu-id="b9de0-109">此選項為開啟如果您指定`/highentropyva`或`/highentropyva+`。</span><span class="sxs-lookup"><span data-stu-id="b9de0-109">The option is on if you specify `/highentropyva` or `/highentropyva+`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9de0-110">備註</span><span class="sxs-lookup"><span data-stu-id="b9de0-110">Remarks</span></span>  
 <span data-ttu-id="b9de0-111">如果您指定這個選項時，Windows 核心的相容版本可以使用較高程度的高熵核心隨機放置程序的位址空間配置個做為 ASLR 一部分時。</span><span class="sxs-lookup"><span data-stu-id="b9de0-111">If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="b9de0-112">如果核心使用較高程度的高熵，大量位址可以配置到記憶體區域，例如堆疊和堆積。</span><span class="sxs-lookup"><span data-stu-id="b9de0-112">If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="b9de0-113">因此更難猜測特定記憶體區域的位置。</span><span class="sxs-lookup"><span data-stu-id="b9de0-113">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="b9de0-114">在選項設為目標的可執行檔和任何模組上時它相依必須能夠處理這些模組會做為 64 位元處理序執行時，會大於 4 gb 的指標值。</span><span class="sxs-lookup"><span data-stu-id="b9de0-114">When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9de0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9de0-115">See Also</span></span>  
 <span data-ttu-id="b9de0-116">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="b9de0-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="b9de0-117"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="b9de0-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
