---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13bce09ca9fd1ae9ebb919a9245d8ccf87fbde1d
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44368741"
---
# <a name="-rootnamespace"></a><span data-ttu-id="f0edf-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="f0edf-102">-rootnamespace</span></span>
<span data-ttu-id="f0edf-103">指定所有類型宣告的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f0edf-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0edf-104">語法</span><span class="sxs-lookup"><span data-stu-id="f0edf-104">Syntax</span></span>  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="f0edf-105">引數</span><span class="sxs-lookup"><span data-stu-id="f0edf-105">Arguments</span></span>  
  
|<span data-ttu-id="f0edf-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f0edf-106">Term</span></span>|<span data-ttu-id="f0edf-107">定義</span><span class="sxs-lookup"><span data-stu-id="f0edf-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="f0edf-108">在用來括住目前專案的所有類型宣告的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="f0edf-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0edf-109">備註</span><span class="sxs-lookup"><span data-stu-id="f0edf-109">Remarks</span></span>  
 <span data-ttu-id="f0edf-110">如果您使用 Visual Studio 可執行檔 (Devenv.exe) 編譯所建立的專案在 Visual Studio 整合式的開發環境，請使用`-rootnamespace`指定的值<xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="f0edf-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="f0edf-111">請參閱[Devenv 命令列參數](/visualstudio/ide/reference/devenv-command-line-switches)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f0edf-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="f0edf-112">使用 common language runtime MSIL 反組譯 (`Ildasm.exe`) 若要檢視輸出檔案中的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="f0edf-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="f0edf-113">若要在 Visual Studio 整合式的開發環境中設定-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="f0edf-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f0edf-114">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="f0edf-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f0edf-115">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f0edf-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f0edf-116">2.按一下 [應用程式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f0edf-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="f0edf-117">3.修改中的值**根命名空間** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="f0edf-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f0edf-118">範例</span><span class="sxs-lookup"><span data-stu-id="f0edf-118">Example</span></span>  
 <span data-ttu-id="f0edf-119">下列程式碼會編譯`In.vb`而命名空間中含括所有類型宣告`mynamespace`。</span><span class="sxs-lookup"><span data-stu-id="f0edf-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0edf-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0edf-120">See also</span></span>

- [<span data-ttu-id="f0edf-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f0edf-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
- [<span data-ttu-id="f0edf-122">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="f0edf-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)  
- [<span data-ttu-id="f0edf-123">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="f0edf-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
