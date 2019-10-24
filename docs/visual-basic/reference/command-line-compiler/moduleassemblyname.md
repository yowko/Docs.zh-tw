---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: a612a68cffd927f3e360406cca6d9daae4f66c86
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775627"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="32c5f-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="32c5f-102">-moduleassemblyname</span></span>
<span data-ttu-id="32c5f-103">指定將包含此模組的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="32c5f-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32c5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="32c5f-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="32c5f-105">引數</span><span class="sxs-lookup"><span data-stu-id="32c5f-105">Arguments</span></span>  
  
|<span data-ttu-id="32c5f-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="32c5f-106">Term</span></span>|<span data-ttu-id="32c5f-107">定義</span><span class="sxs-lookup"><span data-stu-id="32c5f-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="32c5f-108">此模組將成為其一部分的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="32c5f-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32c5f-109">備註</span><span class="sxs-lookup"><span data-stu-id="32c5f-109">Remarks</span></span>  
 <span data-ttu-id="32c5f-110">只有在指定了 `-target:module` 選項時，編譯器才會處理 `-moduleassemblyname` 選項。</span><span class="sxs-lookup"><span data-stu-id="32c5f-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="32c5f-111">這會導致編譯器建立模組。</span><span class="sxs-lookup"><span data-stu-id="32c5f-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="32c5f-112">編譯器所建立的模組僅適用于使用 [`-moduleassemblyname`] 選項指定的元件。</span><span class="sxs-lookup"><span data-stu-id="32c5f-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="32c5f-113">如果您將模組放在不同的元件中，就會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="32c5f-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="32c5f-114">只有在下列條件成立時，才需要 `-moduleassemblyname` 選項：</span><span class="sxs-lookup"><span data-stu-id="32c5f-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="32c5f-115">模組中的資料類型需要存取參考元件中的 `Friend` 類型。</span><span class="sxs-lookup"><span data-stu-id="32c5f-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="32c5f-116">參考的元件已將 friend 元件存取權授與要在其中建立模組的元件。</span><span class="sxs-lookup"><span data-stu-id="32c5f-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="32c5f-117">如需建立模組的詳細資訊，請參閱[-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)。</span><span class="sxs-lookup"><span data-stu-id="32c5f-117">For more information about creating a module, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="32c5f-118">如需 friend 元件的詳細資訊，請參閱[Friend 元件](../../../standard/assembly/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="32c5f-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32c5f-119">Visual Studio 開發環境中無法使用 [`-moduleassemblyname`] 選項;只有當您從命令提示字元編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="32c5f-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c5f-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="32c5f-120">See also</span></span>

- [<span data-ttu-id="32c5f-121">操作說明：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="32c5f-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="32c5f-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="32c5f-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="32c5f-123">-target （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="32c5f-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="32c5f-124">-main</span><span class="sxs-lookup"><span data-stu-id="32c5f-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)
- [<span data-ttu-id="32c5f-125">-reference （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="32c5f-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="32c5f-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="32c5f-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [<span data-ttu-id="32c5f-127">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="32c5f-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="32c5f-128">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="32c5f-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="32c5f-129">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="32c5f-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
