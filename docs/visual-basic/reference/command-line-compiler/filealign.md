---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 809b7ad005b6bb5f127f84425b5d2beb980df471
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058127"
---
# <a name="-filealign"></a><span data-ttu-id="dde8c-102">-filealign</span><span class="sxs-lookup"><span data-stu-id="dde8c-102">-filealign</span></span>

<span data-ttu-id="dde8c-103">指定要對齊輸出檔案區段的位置。</span><span class="sxs-lookup"><span data-stu-id="dde8c-103">Specifies where to align the sections of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dde8c-104">語法</span><span class="sxs-lookup"><span data-stu-id="dde8c-104">Syntax</span></span>  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="dde8c-105">引數</span><span class="sxs-lookup"><span data-stu-id="dde8c-105">Arguments</span></span>  

 `number`  
 <span data-ttu-id="dde8c-106">必要。</span><span class="sxs-lookup"><span data-stu-id="dde8c-106">Required.</span></span> <span data-ttu-id="dde8c-107">值，指定輸出檔案中區段的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="dde8c-107">A value that specifies the alignment of sections in the output file.</span></span> <span data-ttu-id="dde8c-108">有效值為 512、1024、2048、4096 和 8192。</span><span class="sxs-lookup"><span data-stu-id="dde8c-108">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="dde8c-109">這些值是以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="dde8c-109">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dde8c-110">備註</span><span class="sxs-lookup"><span data-stu-id="dde8c-110">Remarks</span></span>  

 <span data-ttu-id="dde8c-111">您可以使用 `-filealign` 選項來指定輸出檔案中區段的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="dde8c-111">You can use the `-filealign` option to specify the alignment of sections in your output file.</span></span> <span data-ttu-id="dde8c-112">區段是可攜式可執行檔中的連續記憶體區塊， (PE) 包含程式碼或資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="dde8c-112">Sections are blocks of contiguous memory in a Portable Executable (PE) file that contains either code or data.</span></span> <span data-ttu-id="dde8c-113">此 `-filealign` 選項可讓您以非標準的對齊方式編譯應用程式; 大部分的開發人員都不需要使用此選項。</span><span class="sxs-lookup"><span data-stu-id="dde8c-113">The `-filealign` option lets you compile your application with a nonstandard alignment; most developers do not need to use this option.</span></span>  
  
 <span data-ttu-id="dde8c-114">每個區段都會對齊屬於值倍數的界限 `-filealign` 。</span><span class="sxs-lookup"><span data-stu-id="dde8c-114">Each section is aligned on a boundary that is a multiple of the `-filealign` value.</span></span> <span data-ttu-id="dde8c-115">沒有固定預設值。</span><span class="sxs-lookup"><span data-stu-id="dde8c-115">There is no fixed default.</span></span> <span data-ttu-id="dde8c-116">如果 `-filealign` 未指定，編譯器會在編譯時期選取預設值。</span><span class="sxs-lookup"><span data-stu-id="dde8c-116">If `-filealign` is not specified, the compiler picks a default at compile time.</span></span>  
  
 <span data-ttu-id="dde8c-117">藉由指定區段大小，您可以變更輸出檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="dde8c-117">By specifying the section size, you can change the size of the output file.</span></span> <span data-ttu-id="dde8c-118">修改區段大小對執行於較小裝置上的程式而言可能很有用。</span><span class="sxs-lookup"><span data-stu-id="dde8c-118">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dde8c-119">`-filealign`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="dde8c-119">The `-filealign` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dde8c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dde8c-120">See also</span></span>

- [<span data-ttu-id="dde8c-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="dde8c-121">Visual Basic Command-Line Compiler</span></span>](index.md)
