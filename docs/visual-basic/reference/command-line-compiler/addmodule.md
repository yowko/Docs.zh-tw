---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2db122acc03056a9cb6f355119d4c4e6da6ed175
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097783"
---
# <a name="-addmodule"></a><span data-ttu-id="c12a3-102">-addmodule</span><span class="sxs-lookup"><span data-stu-id="c12a3-102">-addmodule</span></span>

<span data-ttu-id="c12a3-103">讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。</span><span class="sxs-lookup"><span data-stu-id="c12a3-103">Causes the compiler to make all type information from the specified file(s) available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c12a3-104">語法</span><span class="sxs-lookup"><span data-stu-id="c12a3-104">Syntax</span></span>  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="c12a3-105">引數</span><span class="sxs-lookup"><span data-stu-id="c12a3-105">Arguments</span></span>  

 `fileList`  
 <span data-ttu-id="c12a3-106">必要。</span><span class="sxs-lookup"><span data-stu-id="c12a3-106">Required.</span></span> <span data-ttu-id="c12a3-107">包含中繼資料但不包含組件資訊清單的檔案清單（以逗號分隔）。</span><span class="sxs-lookup"><span data-stu-id="c12a3-107">Comma-delimited list of files that contain metadata but do not contain assembly manifests.</span></span> <span data-ttu-id="c12a3-108">包含空格的檔案名應以引號括住 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="c12a3-108">File names containing spaces should be surrounded by quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c12a3-109">備註</span><span class="sxs-lookup"><span data-stu-id="c12a3-109">Remarks</span></span>  

 <span data-ttu-id="c12a3-110">參數所列出的檔案 `fileList` 必須以 `-target:module` 選項建立，或與另一個編譯器的相等 `-target:module` 。</span><span class="sxs-lookup"><span data-stu-id="c12a3-110">The files listed by the `fileList` parameter must be created with the `-target:module` option, or with another compiler's equivalent to `-target:module`.</span></span>  
  
 <span data-ttu-id="c12a3-111">所有新增的模組都 `-addmodule` 必須與執行時間的輸出檔案位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="c12a3-111">All modules added with `-addmodule` must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="c12a3-112">也就是說，您可以在編譯時期指定任何目錄中的模組，但模組在執行時間必須在應用程式目錄中。</span><span class="sxs-lookup"><span data-stu-id="c12a3-112">That is, you can specify a module in any directory at compile time, but the module must be in the application directory at run time.</span></span> <span data-ttu-id="c12a3-113">如果不是，您會收到 <xref:System.TypeLoadException> 錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c12a3-113">If it is not, you get a <xref:System.TypeLoadException> error.</span></span>  
  
 <span data-ttu-id="c12a3-114">如果您指定 (以隱含或明確的方式) 任何[目標 (Visual Basic) ](target.md) 選項 `-target:module` `-addmodule` ，則您傳遞給的檔案 `-addmodule` 會成為專案元件的一部分。</span><span class="sxs-lookup"><span data-stu-id="c12a3-114">If you specify (implicitly or explicitly) any[-target (Visual Basic)](target.md) option other than `-target:module` with `-addmodule`, the files you pass to `-addmodule` become part of the project's assembly.</span></span> <span data-ttu-id="c12a3-115">需要元件，才能執行包含一或多個新增之檔案的輸出檔 `-addmodule` 。</span><span class="sxs-lookup"><span data-stu-id="c12a3-115">An assembly is required to run an output file that has one or more files added with `-addmodule`.</span></span>  
  
 <span data-ttu-id="c12a3-116">使用 [-reference (Visual Basic) ](reference.md) 從包含元件的檔案匯入中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c12a3-116">Use [-reference (Visual Basic)](reference.md) to import metadata from a file that contains an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c12a3-117">`-addmodule`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="c12a3-117">The `-addmodule` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c12a3-118">範例</span><span class="sxs-lookup"><span data-stu-id="c12a3-118">Example</span></span>  

 <span data-ttu-id="c12a3-119">下列程式碼會建立模組。</span><span class="sxs-lookup"><span data-stu-id="c12a3-119">The following code creates a module.</span></span>  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 <span data-ttu-id="c12a3-120">下列程式碼會匯入模組的類型。</span><span class="sxs-lookup"><span data-stu-id="c12a3-120">The following code imports the module's types.</span></span>  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 <span data-ttu-id="c12a3-121">當您執行時 `t1` ，它會輸出 `802` 。</span><span class="sxs-lookup"><span data-stu-id="c12a3-121">When you run `t1`, it outputs `802`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c12a3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c12a3-122">See also</span></span>

- [<span data-ttu-id="c12a3-123">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="c12a3-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c12a3-124">-目標 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="c12a3-124">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="c12a3-125">-reference (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="c12a3-125">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="c12a3-126">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="c12a3-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
