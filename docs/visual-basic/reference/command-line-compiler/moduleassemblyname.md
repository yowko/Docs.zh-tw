---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 479f9f639548eb81351d1df3f8f08b29b393cba1
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085023"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="b3e43-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="b3e43-102">-moduleassemblyname</span></span>
<span data-ttu-id="b3e43-103">指定將包含此模組的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="b3e43-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3e43-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3e43-104">Syntax</span></span>  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="b3e43-105">引數</span><span class="sxs-lookup"><span data-stu-id="b3e43-105">Arguments</span></span>  
  
|<span data-ttu-id="b3e43-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="b3e43-106">Term</span></span>|<span data-ttu-id="b3e43-107">定義</span><span class="sxs-lookup"><span data-stu-id="b3e43-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="b3e43-108">此模組將會是一部分的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="b3e43-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3e43-109">備註</span><span class="sxs-lookup"><span data-stu-id="b3e43-109">Remarks</span></span>  
 <span data-ttu-id="b3e43-110">編譯器處理序`-moduleassemblyname`選項才`-target:module`已指定選項。</span><span class="sxs-lookup"><span data-stu-id="b3e43-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="b3e43-111">這可讓編譯器建立模組。</span><span class="sxs-lookup"><span data-stu-id="b3e43-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="b3e43-112">編譯器所建立的模組是僅適用於具有指定的組件`-moduleassemblyname`選項。</span><span class="sxs-lookup"><span data-stu-id="b3e43-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="b3e43-113">如果您將模組放在不同的組件時，會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="b3e43-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="b3e43-114">`-moduleassemblyname`只有在下列條件成立時，才需要選項：</span><span class="sxs-lookup"><span data-stu-id="b3e43-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="b3e43-115">此模組中的資料類型必須能夠存取`Friend`參考的組件中的型別。</span><span class="sxs-lookup"><span data-stu-id="b3e43-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="b3e43-116">參考的組件具有 friend 組件存取權限授與將在其中建置模組的組件。</span><span class="sxs-lookup"><span data-stu-id="b3e43-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="b3e43-117">如需建立模組的詳細資訊，請參閱[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e43-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="b3e43-118">如需 friend 組件的詳細資訊，請參閱[Friend 組件](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="b3e43-118">For more information about friend assemblies, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3e43-119">`-moduleassemblyname`選項不是從 Visual Studio 開發環境中使用; 它是使用只有當您編譯的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="b3e43-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e43-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3e43-120">See Also</span></span>  
 [<span data-ttu-id="b3e43-121">操作說明：建置多檔案組件</span><span class="sxs-lookup"><span data-stu-id="b3e43-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="b3e43-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="b3e43-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b3e43-123">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3e43-123">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="b3e43-124">-main</span><span class="sxs-lookup"><span data-stu-id="b3e43-124">-main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="b3e43-125">-參考 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3e43-125">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="b3e43-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="b3e43-126">-addmodule</span></span>](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [<span data-ttu-id="b3e43-127">組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="b3e43-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="b3e43-128">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="b3e43-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="b3e43-129">Friend 組件</span><span class="sxs-lookup"><span data-stu-id="b3e43-129">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)
