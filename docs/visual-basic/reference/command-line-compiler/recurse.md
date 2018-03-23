---
title: -recurse
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb1cc114c2882aa82787f94a271dd7684c716b01
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-recurse"></a><span data-ttu-id="8ab09-102">-recurse</span><span class="sxs-lookup"><span data-stu-id="8ab09-102">-recurse</span></span>
<span data-ttu-id="8ab09-103">編譯指定的目錄或專案目錄的子目錄中的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="8ab09-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ab09-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ab09-104">Syntax</span></span>  
  
```  
-recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8ab09-105">引數</span><span class="sxs-lookup"><span data-stu-id="8ab09-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="8ab09-106">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8ab09-106">Optional.</span></span> <span data-ttu-id="8ab09-107">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="8ab09-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="8ab09-108">如果未指定，則會在專案目錄中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="8ab09-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="8ab09-109">必要。</span><span class="sxs-lookup"><span data-stu-id="8ab09-109">Required.</span></span> <span data-ttu-id="8ab09-110">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="8ab09-110">The file(s) to search for.</span></span> <span data-ttu-id="8ab09-111">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8ab09-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ab09-112">備註</span><span class="sxs-lookup"><span data-stu-id="8ab09-112">Remarks</span></span>  
 <span data-ttu-id="8ab09-113">您也可以在檔案名稱中使用萬用字元，編譯專案目錄中所有相符的檔案，而不使用`-recurse`。</span><span class="sxs-lookup"><span data-stu-id="8ab09-113">You can use wildcards in a file name to compile all matching files in the project directory without using `-recurse`.</span></span> <span data-ttu-id="8ab09-114">如果沒有任何輸出檔案名稱指定時，編譯器會根據處理第一個輸入檔的輸出檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="8ab09-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="8ab09-115">這通常是在編譯時依字母順序檢視檔清單中的第一個檔案。</span><span class="sxs-lookup"><span data-stu-id="8ab09-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="8ab09-116">基於這個理由，建議您最好以指定輸出檔案使用`-out`選項。</span><span class="sxs-lookup"><span data-stu-id="8ab09-116">For this reason, it is best to specify an output file using the `-out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ab09-117">`-recurse`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="8ab09-117">The `-recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab09-118">範例</span><span class="sxs-lookup"><span data-stu-id="8ab09-118">Example</span></span>  
 <span data-ttu-id="8ab09-119">下列命令會將所有[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]目前目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="8ab09-119">The following command compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the current directory.</span></span>  
  
```console
vbc *.vb  
```  
  
 <span data-ttu-id="8ab09-120">下列命令會將所有[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]檔案`Test\ABC`目錄和任何目錄下方，然後產生`Test.ABC.dll`。</span><span class="sxs-lookup"><span data-stu-id="8ab09-120">The following command compiles all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```console
vbc -target:library -out:Test.ABC.dll -recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ab09-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ab09-121">See Also</span></span>  
 [<span data-ttu-id="8ab09-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="8ab09-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="8ab09-123">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ab09-123">-out (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/out.md)  
 [<span data-ttu-id="8ab09-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="8ab09-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
