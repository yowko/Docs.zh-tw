---
title: -filealign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26ff29f00f00d3ea5dbbd0bbf01df4d7858771d0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-filealign"></a><span data-ttu-id="4b675-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="4b675-102">-filealign</span></span>
<span data-ttu-id="4b675-103">指定要對齊輸出檔案區段的位置。</span><span class="sxs-lookup"><span data-stu-id="4b675-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b675-104">語法</span><span class="sxs-lookup"><span data-stu-id="4b675-104">Syntax</span></span>  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="4b675-105">引數</span><span class="sxs-lookup"><span data-stu-id="4b675-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="4b675-106">必要。</span><span class="sxs-lookup"><span data-stu-id="4b675-106">Required.</span></span> <span data-ttu-id="4b675-107">值，指定輸出檔案區段的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="4b675-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="4b675-108">有效值為 512、1024、2048、4096 和 8192。</span><span class="sxs-lookup"><span data-stu-id="4b675-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="4b675-109">這些值是以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="4b675-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b675-110">備註</span><span class="sxs-lookup"><span data-stu-id="4b675-110">Remarks</span></span>  
 <span data-ttu-id="4b675-111">您可以使用`-filealign`選項來指定輸出檔案區段的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="4b675-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="4b675-112">區段是包含程式碼或資料的可攜式執行檔 (PE) 檔案中的連續記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="4b675-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="4b675-113">`-filealign`選項可讓您編譯您的應用程式與標準的對齊方式; 大部分的開發人員不需要使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="4b675-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="4b675-114">每個區段對齊的倍數界限`-filealign`值。</span><span class="sxs-lookup"><span data-stu-id="4b675-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="4b675-115">沒有固定預設值。</span><span class="sxs-lookup"><span data-stu-id="4b675-115">There is no fixed default.</span></span> <span data-ttu-id="4b675-116">如果`-filealign`未指定，則編譯器會在編譯時期挑選預設值。</span><span class="sxs-lookup"><span data-stu-id="4b675-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="4b675-117">藉由指定區段大小，您可以變更輸出檔的大小。</span><span class="sxs-lookup"><span data-stu-id="4b675-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="4b675-118">修改區段大小對執行於較小裝置上的程式而言可能很有用。</span><span class="sxs-lookup"><span data-stu-id="4b675-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b675-119">`-filealign`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="4b675-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b675-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b675-120">See Also</span></span>  
 [<span data-ttu-id="4b675-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="4b675-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
