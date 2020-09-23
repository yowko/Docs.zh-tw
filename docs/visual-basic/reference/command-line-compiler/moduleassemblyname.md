---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 9fb9287f9472d4b33eff4cb601aff5eed370b2c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065563"
---
# <a name="-moduleassemblyname"></a><span data-ttu-id="655fb-102">-moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="655fb-102">-moduleassemblyname</span></span>

<span data-ttu-id="655fb-103">指定將包含此模組的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="655fb-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="655fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="655fb-104">Syntax</span></span>  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="655fb-105">引數</span><span class="sxs-lookup"><span data-stu-id="655fb-105">Arguments</span></span>  
  
|<span data-ttu-id="655fb-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="655fb-106">Term</span></span>|<span data-ttu-id="655fb-107">定義</span><span class="sxs-lookup"><span data-stu-id="655fb-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="655fb-108">此模組所屬的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="655fb-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="655fb-109">備註</span><span class="sxs-lookup"><span data-stu-id="655fb-109">Remarks</span></span>  

 <span data-ttu-id="655fb-110">`-moduleassemblyname`只有在已指定選項時，編譯器才會處理選項 `-target:module` 。</span><span class="sxs-lookup"><span data-stu-id="655fb-110">The compiler processes the `-moduleassemblyname` option only if the `-target:module` option has been specified.</span></span> <span data-ttu-id="655fb-111">這會導致編譯器建立模組。</span><span class="sxs-lookup"><span data-stu-id="655fb-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="655fb-112">編譯器所建立的模組，只對使用選項指定的元件有效 `-moduleassemblyname` 。</span><span class="sxs-lookup"><span data-stu-id="655fb-112">The module created by the compiler is valid only for the assembly specified with the `-moduleassemblyname` option.</span></span> <span data-ttu-id="655fb-113">如果您將模組放在不同的元件中，則會發生執行階段錯誤。</span><span class="sxs-lookup"><span data-stu-id="655fb-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="655fb-114">`-moduleassemblyname`只有當下列條件成立時，才需要此選項：</span><span class="sxs-lookup"><span data-stu-id="655fb-114">The `-moduleassemblyname` option is needed only when the following are true:</span></span>  
  
- <span data-ttu-id="655fb-115">模組中的資料類型需要存取 `Friend` 參考元件中的類型。</span><span class="sxs-lookup"><span data-stu-id="655fb-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
- <span data-ttu-id="655fb-116">參考的元件已將 friend 元件存取權授與將在其中建立模組的元件。</span><span class="sxs-lookup"><span data-stu-id="655fb-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="655fb-117">如需有關建立模組的詳細資訊，請參閱 [-目標 (Visual Basic) ](target.md)。</span><span class="sxs-lookup"><span data-stu-id="655fb-117">For more information about creating a module, see [-target (Visual Basic)](target.md).</span></span> <span data-ttu-id="655fb-118">如需 friend 元件的詳細資訊，請參閱 [Friend 元件](../../../standard/assembly/friend.md)。</span><span class="sxs-lookup"><span data-stu-id="655fb-118">For more information about friend assemblies, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="655fb-119">`-moduleassemblyname`選項無法在 Visual Studio 開發環境中使用; 只有當您從命令提示字元進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="655fb-119">The `-moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="655fb-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="655fb-120">See also</span></span>

- [<span data-ttu-id="655fb-121">如何：建立多檔案元件</span><span class="sxs-lookup"><span data-stu-id="655fb-121">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="655fb-122">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="655fb-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="655fb-123">-目標 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="655fb-123">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="655fb-124">-main</span><span class="sxs-lookup"><span data-stu-id="655fb-124">-main</span></span>](main.md)
- [<span data-ttu-id="655fb-125">-reference (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="655fb-125">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="655fb-126">-addmodule</span><span class="sxs-lookup"><span data-stu-id="655fb-126">-addmodule</span></span>](addmodule.md)
- [<span data-ttu-id="655fb-127">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="655fb-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="655fb-128">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="655fb-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="655fb-129">Friend 元件</span><span class="sxs-lookup"><span data-stu-id="655fb-129">Friend Assemblies</span></span>](../../../standard/assembly/friend.md)
