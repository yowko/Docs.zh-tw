---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: dc4c0336c8a67a1b4e70f71ba5f5406da1fbb2ff
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972381"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="7dcfe-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="7dcfe-102">-moduleassemblyname</span></span>
<span data-ttu-id="7dcfe-103">指定將包含此模組的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dcfe-104">語法</span><span class="sxs-lookup"><span data-stu-id="7dcfe-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="7dcfe-105">引數</span><span class="sxs-lookup"><span data-stu-id="7dcfe-105">Arguments</span></span>  
  
|<span data-ttu-id="7dcfe-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="7dcfe-106">Term</span></span>|<span data-ttu-id="7dcfe-107">定義</span><span class="sxs-lookup"><span data-stu-id="7dcfe-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="7dcfe-108">此模組將成為其一部分的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dcfe-109">備註</span><span class="sxs-lookup"><span data-stu-id="7dcfe-109">Remarks</span></span>  
 <span data-ttu-id="7dcfe-110">只有在`-moduleassemblyname` `-target:module`已指定選項時，編譯器才會處理選項。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="7dcfe-111">這會導致編譯器建立模組。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="7dcfe-112">編譯器所建立的模組只對使用`-moduleassemblyname`選項指定的元件有效。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="7dcfe-113">如果您將模組放在不同的元件中，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="7dcfe-114">只有在下列條件成立時，才需要選項：`-moduleassemblyname`</span><span class="sxs-lookup"><span data-stu-id="7dcfe-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="7dcfe-115">模組中的資料類型需要存取參考元件中`Friend`的類型。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="7dcfe-116">參考的元件已將 friend 元件存取權授與要在其中建立模組的元件。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="7dcfe-117">如需有關建立模組的詳細資訊，請參閱[/target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="7dcfe-118">如需 friend 元件的詳細資訊，請參閱[Friend 元件](../../../standard/assembly/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dcfe-119">此`-moduleassemblyname`選項無法從 Visual Studio 開發環境中使用; 只有當您從命令提示字元進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="7dcfe-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dcfe-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dcfe-120">See also</span></span>

- [<span data-ttu-id="7dcfe-121">如何：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="7dcfe-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="7dcfe-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="7dcfe-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7dcfe-123">-target （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7dcfe-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="7dcfe-124">-main</span><span class="sxs-lookup"><span data-stu-id="7dcfe-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="7dcfe-125">-reference （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="7dcfe-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="7dcfe-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="7dcfe-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="7dcfe-127">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="7dcfe-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="7dcfe-128">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="7dcfe-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="7dcfe-129">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="7dcfe-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
