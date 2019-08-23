---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 4281c7bf5a7972d323e1e649aaef437c7ee901ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956269"
---
# <a name="-recurse"></a><span data-ttu-id="91740-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="91740-102">-recurse</span></span>
<span data-ttu-id="91740-103">編譯指定目錄或專案目錄之所有子目錄中的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="91740-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91740-104">語法</span><span class="sxs-lookup"><span data-stu-id="91740-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="91740-105">引數</span><span class="sxs-lookup"><span data-stu-id="91740-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="91740-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="91740-106">Optional.</span></span> <span data-ttu-id="91740-107">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="91740-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="91740-108">如果未指定, 則搜尋會從專案目錄開始。</span><span class="sxs-lookup"><span data-stu-id="91740-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="91740-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="91740-109">Required.</span></span> <span data-ttu-id="91740-110">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="91740-110">The file(s) to search for.</span></span> <span data-ttu-id="91740-111">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="91740-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91740-112">備註</span><span class="sxs-lookup"><span data-stu-id="91740-112">Remarks</span></span>  
 <span data-ttu-id="91740-113">您可以在檔案名中使用萬用字元, 來編譯專案目錄中的所有相符檔案, 而`-recurse`不使用。</span><span class="sxs-lookup"><span data-stu-id="91740-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="91740-114">如果未指定輸出檔名稱, 編譯器會在第一個處理的輸入檔案上以輸出檔案名為基礎。</span><span class="sxs-lookup"><span data-stu-id="91740-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="91740-115">這通常是在按字母順序查看時所編譯的檔案清單中的第一個檔案。</span><span class="sxs-lookup"><span data-stu-id="91740-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="91740-116">基於這個理由, 最好是使用`-out`選項來指定輸出檔。</span><span class="sxs-lookup"><span data-stu-id="91740-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91740-117">此`-recurse`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="91740-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91740-118">範例</span><span class="sxs-lookup"><span data-stu-id="91740-118">Example</span></span>  
 <span data-ttu-id="91740-119">下列命令會編譯目前目錄中的所有 Visual Basic 檔案。</span><span class="sxs-lookup"><span data-stu-id="91740-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="91740-120">下列命令會編譯目錄中的所有 Visual Basic `Test\ABC`檔案和其底下的任何目錄, 然後產生`Test.ABC.dll`。</span><span class="sxs-lookup"><span data-stu-id="91740-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="91740-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91740-121">See also</span></span>

- [<span data-ttu-id="91740-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="91740-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="91740-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91740-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="91740-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="91740-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
