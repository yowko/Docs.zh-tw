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
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005204"
---
# <a name="-rootnamespace"></a><span data-ttu-id="f682c-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="f682c-102">-rootnamespace</span></span>
<span data-ttu-id="f682c-103">指定所有類型宣告的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f682c-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f682c-104">語法</span><span class="sxs-lookup"><span data-stu-id="f682c-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="f682c-105">引數</span><span class="sxs-lookup"><span data-stu-id="f682c-105">Arguments</span></span>  
  
|<span data-ttu-id="f682c-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="f682c-106">Term</span></span>|<span data-ttu-id="f682c-107">定義</span><span class="sxs-lookup"><span data-stu-id="f682c-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="f682c-108">要用來括住目前專案之所有類型宣告的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="f682c-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f682c-109">備註</span><span class="sxs-lookup"><span data-stu-id="f682c-109">Remarks</span></span>  
 <span data-ttu-id="f682c-110">如果您使用 Visual Studio 可執行檔（Devenv）來編譯在 Visual Studio 整合式開發環境中建立的專案，請使用 `-rootnamespace` 來指定 <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f682c-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="f682c-111">如需詳細資訊，請參閱[Devenv 命令列參數](/visualstudio/ide/reference/devenv-command-line-switches)。</span><span class="sxs-lookup"><span data-stu-id="f682c-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="f682c-112">使用 common language runtime MSIL 解譯器（`Ildasm.exe`）來查看輸出檔案中的命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="f682c-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="f682c-113">在 Visual Studio 的整合式開發環境中設定-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="f682c-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f682c-114">1.在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="f682c-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f682c-115">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f682c-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f682c-116">2.按一下 [應用程式] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="f682c-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="f682c-117">3.修改 [**根命名空間**] 方塊中的值。</span><span class="sxs-lookup"><span data-stu-id="f682c-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f682c-118">範例</span><span class="sxs-lookup"><span data-stu-id="f682c-118">Example</span></span>  
 <span data-ttu-id="f682c-119">下列程式碼會編譯 `In.vb`，並將命名空間中的所有類型宣告括住 `mynamespace`。</span><span class="sxs-lookup"><span data-stu-id="f682c-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f682c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f682c-120">See also</span></span>

- [<span data-ttu-id="f682c-121">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="f682c-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f682c-122">Ildasm.exe (IL 反組譯工具)</span><span class="sxs-lookup"><span data-stu-id="f682c-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="f682c-123">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="f682c-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
