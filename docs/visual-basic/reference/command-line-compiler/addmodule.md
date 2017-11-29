---
title: /addmodule
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fff292605e125776ae25e667d4813d770ed0a0aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule"></a><span data-ttu-id="da135-102">/addmodule</span><span class="sxs-lookup"><span data-stu-id="da135-102">/addmodule</span></span>
<span data-ttu-id="da135-103">讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="da135-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da135-104">語法</span><span class="sxs-lookup"><span data-stu-id="da135-104">Syntax</span></span>  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="da135-105">引數</span><span class="sxs-lookup"><span data-stu-id="da135-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="da135-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="da135-106">Required.</span></span> <span data-ttu-id="da135-107">包含中繼資料但不包含組件資訊清單檔案的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="da135-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="da135-108">應該以引號括住包含空格的檔案名稱 ("")。</span><span class="sxs-lookup"><span data-stu-id="da135-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da135-109">備註</span><span class="sxs-lookup"><span data-stu-id="da135-109">Remarks</span></span>  
 <span data-ttu-id="da135-110">所列出的檔案`fileList`參數必須以建立`/target:module`選項，或其他編譯器等同於`/target:module`。</span><span class="sxs-lookup"><span data-stu-id="da135-110">The files listed by the `fileList` parameter must be created with the `/target:module` option, or with another compiler's equivalent to `/target:module`.</span></span>  
  
 <span data-ttu-id="da135-111">使用新增的所有模組`/addmodule`必須位於執行階段的輸出檔相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="da135-111">All modules added with `/addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="da135-112">也就是說，您可以在編譯時期，任一目錄中指定的模組，但該模組在執行階段時，必須在應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="da135-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="da135-113">如果不是，您會取得<xref:System.TypeLoadException>錯誤。</span><span class="sxs-lookup"><span data-stu-id="da135-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="da135-114">如果您指定 （隱含或明確） 任何[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)選項以外`/target:module`與`/addmodule`，您將傳遞至檔案`/addmodule`成為專案的組件的一部分。</span><span class="sxs-lookup"><span data-stu-id="da135-114">If you specify (implicitly or explicitly) any[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `/target:module` with `/addmodule`, the files you pass to `/addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="da135-115">組件，才能執行的輸出檔，具有一個或多個檔案加入`/addmodule`。</span><span class="sxs-lookup"><span data-stu-id="da135-115">An assembly is required to run an output file that has one or more files added with `/addmodule`.</span></span>  
  
 <span data-ttu-id="da135-116">使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)從包含組件檔案匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="da135-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da135-117">`/addmodule`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="da135-117">The `/addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da135-118">範例</span><span class="sxs-lookup"><span data-stu-id="da135-118">Example</span></span>  
 <span data-ttu-id="da135-119">下列程式碼會建立模組。</span><span class="sxs-lookup"><span data-stu-id="da135-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="da135-120">下列程式碼會匯入模組的類型。</span><span class="sxs-lookup"><span data-stu-id="da135-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="da135-121">當您執行`t1`，它會輸出`802`。</span><span class="sxs-lookup"><span data-stu-id="da135-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da135-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da135-122">See Also</span></span>  
 [<span data-ttu-id="da135-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="da135-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="da135-124">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da135-124">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="da135-125">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da135-125">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="da135-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="da135-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
