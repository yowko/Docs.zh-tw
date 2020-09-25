---
description: -highentropyva (C# 編譯器選項)
title: -highentropyva (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /highentropyva
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
ms.openlocfilehash: f3cdeb5e63d632fecbbd94501558cc53c28a918a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173200"
---
# <a name="-highentropyva-c-compiler-options"></a><span data-ttu-id="62840-103">-highentropyva (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="62840-103">-highentropyva (C# Compiler Options)</span></span>

<span data-ttu-id="62840-104">**-highentropyva** 編譯器選項會通知 Windows 核心某一特定可執行檔是否支援高熵位址空間配置隨機載入 (ASLR)。</span><span class="sxs-lookup"><span data-stu-id="62840-104">The **-highentropyva** compiler option tells the Windows kernel whether a particular executable supports high entropy Address Space Layout Randomization (ASLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62840-105">語法</span><span class="sxs-lookup"><span data-stu-id="62840-105">Syntax</span></span>  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="62840-106">引數</span><span class="sxs-lookup"><span data-stu-id="62840-106">Arguments</span></span>  

 <span data-ttu-id="62840-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="62840-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="62840-108">此選項會指定，64 位元可執行檔或 [-platform:anycpu](./platform-compiler-option.md) 編譯器選項所標記的可執行檔支援高熵虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="62840-108">This option specifies that a 64-bit executable or an executable that is marked by the [-platform:anycpu](./platform-compiler-option.md) compiler option supports a high entropy virtual address space.</span></span> <span data-ttu-id="62840-109">此選項預設為停用。</span><span class="sxs-lookup"><span data-stu-id="62840-109">The option is disabled by default.</span></span> <span data-ttu-id="62840-110">使用 **-highentropyva+** 或 **-highentropyva** 予以啟用。</span><span class="sxs-lookup"><span data-stu-id="62840-110">Use **-highentropyva+** or **-highentropyva** to enable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62840-111">備註</span><span class="sxs-lookup"><span data-stu-id="62840-111">Remarks</span></span>  

 <span data-ttu-id="62840-112">當隨機化處理序的位址空間配置作為 ASLR 一部分時，**-highentropyva** 選項可讓相容的 Windows 核心版本使用較高程度的高熵。</span><span class="sxs-lookup"><span data-stu-id="62840-112">The **-highentropyva** option enables compatible versions of the Windows kernel to use higher degrees of entropy when randomizing the address space layout of a process as part of ASLR.</span></span> <span data-ttu-id="62840-113">使用較高程度的高熵表示可將大量位址配置到記憶體區域，例如堆疊和堆積，</span><span class="sxs-lookup"><span data-stu-id="62840-113">Using higher degrees of entropy means that a larger number of addresses can be allocated to memory regions such as stacks and heaps.</span></span> <span data-ttu-id="62840-114">因此更難猜測特定記憶體區域的位置。</span><span class="sxs-lookup"><span data-stu-id="62840-114">As a result, it is more difficult to guess the location of a particular memory region.</span></span>  
  
 <span data-ttu-id="62840-115">指定 **-highentropyva** 編譯器選項時，目標可執行檔以及作為其依據的任何模組在作為 64 位元處理序執行時，都必須能夠處理大於 4 GB 的指標值。</span><span class="sxs-lookup"><span data-stu-id="62840-115">When the **-highentropyva** compiler option is specified, the target executable and any modules that it depends on must be able to handle pointer values that are larger than 4 gigabytes (GB) when they are running as a 64-bit process.</span></span>
