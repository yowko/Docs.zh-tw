---
title: "/recurse |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /recurse compiler option [Visual Basic]
- -recurse compiler option [Visual Basic]
- recurse compiler option [Visual Basic]
ms.assetid: 84a0b670-33ae-44c4-a46a-b90388809317
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
ms.openlocfilehash: 9ceb2f3bc9e4d0f1088258f504b7a49c58a29e35
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="recurse"></a><span data-ttu-id="8f548-102">/recurse</span><span class="sxs-lookup"><span data-stu-id="8f548-102">/recurse</span></span>
<span data-ttu-id="8f548-103">編譯原始程式碼檔指定的目錄或專案目錄中的所有子目錄中。</span><span class="sxs-lookup"><span data-stu-id="8f548-103">Compiles source-code files in all child directories of either the specified directory or the project directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f548-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f548-104">Syntax</span></span>  
  
```  
/recurse:[dir\]file  
```  
  
## <a name="arguments"></a><span data-ttu-id="8f548-105">引數</span><span class="sxs-lookup"><span data-stu-id="8f548-105">Arguments</span></span>  
 `dir`  
 <span data-ttu-id="8f548-106">選擇項。</span><span class="sxs-lookup"><span data-stu-id="8f548-106">Optional.</span></span> <span data-ttu-id="8f548-107">您想要開始搜尋的目錄。</span><span class="sxs-lookup"><span data-stu-id="8f548-107">The directory in which you want the search to begin.</span></span> <span data-ttu-id="8f548-108">如果未指定，則會在專案目錄中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="8f548-108">If not specified, the search begins in the project directory.</span></span>  
  
 `file`  
 <span data-ttu-id="8f548-109">必要項。</span><span class="sxs-lookup"><span data-stu-id="8f548-109">Required.</span></span> <span data-ttu-id="8f548-110">要搜尋的檔案。</span><span class="sxs-lookup"><span data-stu-id="8f548-110">The file(s) to search for.</span></span> <span data-ttu-id="8f548-111">允許萬用字元。</span><span class="sxs-lookup"><span data-stu-id="8f548-111">Wildcard characters are allowed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f548-112">備註</span><span class="sxs-lookup"><span data-stu-id="8f548-112">Remarks</span></span>  
 <span data-ttu-id="8f548-113">您也可以在檔案名稱中使用萬用字元，編譯專案目錄中所有相符的檔案，而不需使用`/recurse`。</span><span class="sxs-lookup"><span data-stu-id="8f548-113">You can use wildcards in a file name to compile all matching files in the project directory without using `/recurse`.</span></span> <span data-ttu-id="8f548-114">如果沒有指定輸出檔名是，編譯器來建立輸出檔名稱，第一個處理的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="8f548-114">If no output file name is specified, the compiler bases the output file name on the first input file processed.</span></span> <span data-ttu-id="8f548-115">這通常是在編譯時依字母順序檢視檔案清單中的第一個檔案。</span><span class="sxs-lookup"><span data-stu-id="8f548-115">This is generally the first file in the list of files compiled when viewed alphabetically.</span></span> <span data-ttu-id="8f548-116">基於這個理由，最好指定輸出檔使用`/out`選項。</span><span class="sxs-lookup"><span data-stu-id="8f548-116">For this reason, it is best to specify an output file using the `/out` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f548-117">`/recurse`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="8f548-117">The `/recurse` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f548-118">範例</span><span class="sxs-lookup"><span data-stu-id="8f548-118">Example</span></span>  
 <span data-ttu-id="8f548-119">下列程式碼編譯所有[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]目前目錄中的檔案。</span><span class="sxs-lookup"><span data-stu-id="8f548-119">The following code compiles all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the current directory.</span></span>  
  
```  
vbc *.vb  
```  
  
 <span data-ttu-id="8f548-120">下列程式碼編譯所有[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]檔案中`Test\ABC`目錄和其下，任何目錄，然後產生`Test.ABC.dll`。</span><span class="sxs-lookup"><span data-stu-id="8f548-120">The following code compiles all [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] files in the `Test\ABC` directory and any directories below it, and then generates `Test.ABC.dll`.</span></span>  
  
```  
vbc /target:library /out:Test.ABC.dll /recurse:Test\ABC\*.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f548-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f548-121">See Also</span></span>  
 <span data-ttu-id="8f548-122">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="8f548-122">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="8f548-123"> [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md) </span><span class="sxs-lookup"><span data-stu-id="8f548-123"> [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md) </span></span>  
<span data-ttu-id="8f548-124"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="8f548-124"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
