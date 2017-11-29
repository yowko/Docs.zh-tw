---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6b5da8e5eacacde9de5bdc54ef2d5e4d7f0d2653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="rootnamespace"></a><span data-ttu-id="ccf62-102">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="ccf62-102">/rootnamespace</span></span>
<span data-ttu-id="ccf62-103">指定所有類型宣告的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ccf62-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf62-104">語法</span><span class="sxs-lookup"><span data-stu-id="ccf62-104">Syntax</span></span>  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="ccf62-105">引數</span><span class="sxs-lookup"><span data-stu-id="ccf62-105">Arguments</span></span>  
  
|<span data-ttu-id="ccf62-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="ccf62-106">Term</span></span>|<span data-ttu-id="ccf62-107">定義</span><span class="sxs-lookup"><span data-stu-id="ccf62-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="ccf62-108">在用來括住目前專案的所有類型宣告的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="ccf62-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccf62-109">備註</span><span class="sxs-lookup"><span data-stu-id="ccf62-109">Remarks</span></span>  
 <span data-ttu-id="ccf62-110">如果您使用 Visual Studio 可執行檔 (Devenv.exe) 來編譯所建立的專案在 Visual Studio 整合式的開發環境中，使用`/rootnamespace`指定的值<xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ccf62-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `/rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="ccf62-111">請參閱[Devenv 命令列參數](/visualstudio/ide/reference/devenv-command-line-switches)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ccf62-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="ccf62-112">使用 common language runtime MSIL 反組譯工具 (`Ildasm.exe`) 若要檢視輸出檔中的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="ccf62-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="ccf62-113">在 Visual Studio 中設定 /rootnamespace 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="ccf62-113">To set /rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ccf62-114">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="ccf62-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ccf62-115">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="ccf62-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="ccf62-116">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="ccf62-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="ccf62-117">2.按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ccf62-117">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="ccf62-118">3.修改中的值**根命名空間**方塊。</span><span class="sxs-lookup"><span data-stu-id="ccf62-118">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ccf62-119">範例</span><span class="sxs-lookup"><span data-stu-id="ccf62-119">Example</span></span>  
 <span data-ttu-id="ccf62-120">下列程式碼編譯`In.vb`封入命名空間中的所有型別宣告和`mynamespace`。</span><span class="sxs-lookup"><span data-stu-id="ccf62-120">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccf62-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccf62-121">See Also</span></span>  
 [<span data-ttu-id="ccf62-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="ccf62-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ccf62-123">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="ccf62-123">Ildasm.exe (IL Disassembler)</span></span>](https://msdn.microsoft.com/library/f7dy01k1)  
 [<span data-ttu-id="ccf62-124">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="ccf62-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
