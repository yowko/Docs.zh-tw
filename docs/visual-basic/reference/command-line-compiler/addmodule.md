---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 3e5c94cce8b16649854050855800ac1bf2fc6572
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580573"
---
# <a name="-addmodule"></a><span data-ttu-id="6f160-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="6f160-102">-addmodule</span></span>
<span data-ttu-id="6f160-103">讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="6f160-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f160-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f160-104">Syntax</span></span>  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="6f160-105">引數</span><span class="sxs-lookup"><span data-stu-id="6f160-105">Arguments</span></span>  
 `fileList`  
 <span data-ttu-id="6f160-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="6f160-106">Required.</span></span> <span data-ttu-id="6f160-107">檔案所含的中繼資料，但不是包含組件資訊清單的逗號分隔清單。</span><span class="sxs-lookup"><span data-stu-id="6f160-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="6f160-108">應該以引號括住包含空格的檔案名稱 ("")。</span><span class="sxs-lookup"><span data-stu-id="6f160-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f160-109">備註</span><span class="sxs-lookup"><span data-stu-id="6f160-109">Remarks</span></span>  
 <span data-ttu-id="6f160-110">依列出的檔案`fileList`參數必須以建立`-target:module`選項，或使用其他編譯器相當於`-target:module`。</span><span class="sxs-lookup"><span data-stu-id="6f160-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="6f160-111">加上的所有模組`-addmodule`必須位於執行階段的輸出檔相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="6f160-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="6f160-112">也就是您可以在任何目錄中指定模組，在編譯時期，但該模組在執行階段時，必須在應用程式目錄中。</span><span class="sxs-lookup"><span data-stu-id="6f160-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="6f160-113">如果不是，您會取得<xref:System.TypeLoadException>時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6f160-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="6f160-114">如果您指定 （隱含或明確） 任何[-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外的其他選項`-target:module`與`-addmodule`，您將傳遞至檔案`-addmodule`成為專案的組件的一部分。</span><span class="sxs-lookup"><span data-stu-id="6f160-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="6f160-115">組件，才能執行輸出檔案，其中具有一個或多個檔案加`-addmodule`。</span><span class="sxs-lookup"><span data-stu-id="6f160-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="6f160-116">使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)從包含的組件檔案匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6f160-116">Use [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f160-117">`-addmodule`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="6f160-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f160-118">範例</span><span class="sxs-lookup"><span data-stu-id="6f160-118">Example</span></span>  
 <span data-ttu-id="6f160-119">下列程式碼會建立模組。</span><span class="sxs-lookup"><span data-stu-id="6f160-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 <span data-ttu-id="6f160-120">下列程式碼匯入模組的類型。</span><span class="sxs-lookup"><span data-stu-id="6f160-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 <span data-ttu-id="6f160-121">當您執行`t1`，它會輸出`802`。</span><span class="sxs-lookup"><span data-stu-id="6f160-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f160-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f160-122">See also</span></span>
- [<span data-ttu-id="6f160-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="6f160-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6f160-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f160-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="6f160-125">-參考 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f160-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="6f160-126">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="6f160-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
