---
title: "/addmodule |Microsoft 文件"
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
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2db0db5b5dd94f03e67d8680624e2a4ad23587f7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="addmodule"></a><span data-ttu-id="6a5af-102">/addmodule</span><span class="sxs-lookup"><span data-stu-id="6a5af-102">/addmodule</span></span>
<span data-ttu-id="6a5af-103">讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="6a5af-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a5af-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a5af-104">Syntax</span></span>  
  
```  
/addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="6a5af-105">引數</span><span class="sxs-lookup"><span data-stu-id="6a5af-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="6a5af-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="6a5af-106">Required.</span></span> <span data-ttu-id="6a5af-107">檔案所含的中繼資料，但不是包含組件資訊清單的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="6a5af-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="6a5af-108">應該以引號括住包含空格的檔案名稱 ("")。</span><span class="sxs-lookup"><span data-stu-id="6a5af-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a5af-109">備註</span><span class="sxs-lookup"><span data-stu-id="6a5af-109">Remarks</span></span>  
 <span data-ttu-id="6a5af-110">所列出的檔案`fileList`參數必須與建立`/target:module`選項，或以其他編譯器相當於`/target:module`。</span><span class="sxs-lookup"><span data-stu-id="6a5af-110">The files listed by the `fileList` parameter must be created with the `/target:module` option, or with another compiler's equivalent to `/target:module`.</span></span>  
  
 <span data-ttu-id="6a5af-111">加上的所有模組`/addmodule`必須位於相同的目錄和輸出檔在執行階段。</span><span class="sxs-lookup"><span data-stu-id="6a5af-111">All modules added with `/addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="6a5af-112">也就是說，您可以在任何目錄指定模組在編譯時期，但該模組在執行階段時，必須在應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="6a5af-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="6a5af-113">如果不是，您收到<xref:System.TypeLoadException>錯誤。</xref:System.TypeLoadException></span><span class="sxs-lookup"><span data-stu-id="6a5af-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="6a5af-114">如果您指定 （隱含或明確） 任何[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外的其他選項`/target:module`與`/addmodule`，傳遞至檔案`/addmodule`成為專案的組件的一部分。</span><span class="sxs-lookup"><span data-stu-id="6a5af-114">If you specify (implicitly or explicitly) any[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `/target:module` with `/addmodule`, the files you pass to `/addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="6a5af-115">組件，才可執行的輸出檔，都有一個或多個檔案加入`/addmodule`。</span><span class="sxs-lookup"><span data-stu-id="6a5af-115">An assembly is required to run an output file that has one or more files added with `/addmodule`.</span></span>  
  
 <span data-ttu-id="6a5af-116">使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)從包含組件檔案匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6a5af-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a5af-117">`/addmodule`選項不是從 Visual Studio 開發環境中使用，可從命令列編譯時，才。</span><span class="sxs-lookup"><span data-stu-id="6a5af-117">The `/addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a5af-118">範例</span><span class="sxs-lookup"><span data-stu-id="6a5af-118">Example</span></span>  
 <span data-ttu-id="6a5af-119">下列程式碼會建立模組。</span><span class="sxs-lookup"><span data-stu-id="6a5af-119">The following code creates a module.</span></span>  
  
 <span data-ttu-id="6a5af-120">[!code-vb[VbVbalrCompiler #&47;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6a5af-120">[!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]</span></span>  
  
 <span data-ttu-id="6a5af-121">下列程式碼會匯入模組的型別。</span><span class="sxs-lookup"><span data-stu-id="6a5af-121">The following code imports the module's types.</span></span>  
  
 <span data-ttu-id="6a5af-122">[!code-vb[VbVbalrCompiler #&48;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6a5af-122">[!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]</span></span>  
  
 <span data-ttu-id="6a5af-123">當您執行`t1`，它會輸出`802`。</span><span class="sxs-lookup"><span data-stu-id="6a5af-123">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5af-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a5af-124">See Also</span></span>  
 <span data-ttu-id="6a5af-125">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="6a5af-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="6a5af-126"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="6a5af-126"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="6a5af-127"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="6a5af-127"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="6a5af-128"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="6a5af-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
