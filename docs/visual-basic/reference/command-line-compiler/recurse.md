---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 1edb648ec574c0052b7b8314f4ada710c8b0fe01
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183330"
---
# <a name="-recurse"></a><span data-ttu-id="16326-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="16326-102">-recurse</span></span>
<span data-ttu-id="16326-103">編譯指定的目錄或專案目錄中的所有子目錄中的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="16326-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16326-104">語法</span><span class="sxs-lookup"><span data-stu-id="16326-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="16326-105">引數</span><span class="sxs-lookup"><span data-stu-id="16326-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="16326-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="16326-106">Optional.</span></span> <span data-ttu-id="16326-107">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="16326-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="16326-108">如果未指定，則會在專案目錄中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="16326-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="16326-109">必要。</span><span class="sxs-lookup"><span data-stu-id="16326-109">Required.</span></span> <span data-ttu-id="16326-110">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="16326-110">The file(s) to search for.</span></span> <span data-ttu-id="16326-111">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="16326-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16326-112">備註</span><span class="sxs-lookup"><span data-stu-id="16326-112">Remarks</span></span>  
 <span data-ttu-id="16326-113">您可以在 檔案名稱使用萬用字元，來編譯專案目錄中的所有相符檔案，而不需使用`-recurse`。</span><span class="sxs-lookup"><span data-stu-id="16326-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="16326-114">如果不指定任何輸出檔案名稱，編譯器會根據處理的第一個輸入檔案的輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="16326-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="16326-115">這通常是依字母順序檢視時所編譯檔的清單中的第一個檔案。</span><span class="sxs-lookup"><span data-stu-id="16326-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="16326-116">基於這個理由，最好是指定輸出檔案使用`-out`選項。</span><span class="sxs-lookup"><span data-stu-id="16326-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16326-117">`-recurse`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="16326-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16326-118">範例</span><span class="sxs-lookup"><span data-stu-id="16326-118">Example</span></span>  
 <span data-ttu-id="16326-119">下列命令會編譯目前目錄中的所有 Visual Basic 檔案。</span><span class="sxs-lookup"><span data-stu-id="16326-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="16326-120">下列命令會編譯中的所有 Visual Basic 檔案`Test\ABC`目錄和其下的任何目錄，然後產生`Test.ABC.dll`。</span><span class="sxs-lookup"><span data-stu-id="16326-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="16326-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16326-121">See Also</span></span>  
 [<span data-ttu-id="16326-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="16326-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="16326-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16326-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="16326-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="16326-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
