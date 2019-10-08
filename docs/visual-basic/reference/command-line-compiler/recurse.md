---
title: -recurse
ms.date: 03/13/2018
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
ms.openlocfilehash: 71613af0f1c319801296180d49dbacfedf0ceca4
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005257"
---
# <a name="-recurse"></a><span data-ttu-id="01f41-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="01f41-102">-recurse</span></span>
<span data-ttu-id="01f41-103">編譯指定目錄或專案目錄之所有子目錄中的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="01f41-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f41-104">語法</span><span class="sxs-lookup"><span data-stu-id="01f41-104">Syntax</span></span>  
  
```console  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="01f41-105">引數</span><span class="sxs-lookup"><span data-stu-id="01f41-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="01f41-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="01f41-106">Optional.</span></span> <span data-ttu-id="01f41-107">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="01f41-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="01f41-108">如果未指定，則搜尋會從專案目錄開始。</span><span class="sxs-lookup"><span data-stu-id="01f41-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="01f41-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="01f41-109">Required.</span></span> <span data-ttu-id="01f41-110">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="01f41-110">The file(s) to search for.</span></span> <span data-ttu-id="01f41-111">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="01f41-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01f41-112">備註</span><span class="sxs-lookup"><span data-stu-id="01f41-112">Remarks</span></span>  
 <span data-ttu-id="01f41-113">您可以在檔案名中使用萬用字元，來編譯專案目錄中的所有相符檔案，而不使用 `-recurse`。</span><span class="sxs-lookup"><span data-stu-id="01f41-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="01f41-114">如果未指定輸出檔名稱，編譯器會在第一個處理的輸入檔案上以輸出檔案名為基礎。</span><span class="sxs-lookup"><span data-stu-id="01f41-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="01f41-115">這通常是在按字母順序查看時所編譯的檔案清單中的第一個檔案。</span><span class="sxs-lookup"><span data-stu-id="01f41-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="01f41-116">基於這個理由，最好使用 `-out` 選項來指定輸出檔。</span><span class="sxs-lookup"><span data-stu-id="01f41-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01f41-117">@No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="01f41-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01f41-118">範例</span><span class="sxs-lookup"><span data-stu-id="01f41-118">Example</span></span>  
 <span data-ttu-id="01f41-119">下列命令會編譯目前目錄中的所有 Visual Basic 檔案。</span><span class="sxs-lookup"><span data-stu-id="01f41-119">The following command compiles all Visual Basic files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="01f41-120">下列命令會編譯 `Test\ABC` 目錄中的所有 Visual Basic 檔案和其底下的任何目錄，然後產生 `Test.ABC.dll`。</span><span class="sxs-lookup"><span data-stu-id="01f41-120">The following command compiles all Visual Basic files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="01f41-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01f41-121">See also</span></span>

- [<span data-ttu-id="01f41-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="01f41-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="01f41-123">-out （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="01f41-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)
- [<span data-ttu-id="01f41-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="01f41-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
