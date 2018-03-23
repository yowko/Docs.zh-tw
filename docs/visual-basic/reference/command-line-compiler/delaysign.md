---
title: -delaysign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d659e97f3b3a360456a1fcdaa9756934bb096334
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-delaysign"></a><span data-ttu-id="e2b77-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="e2b77-102">-delaysign</span></span>
<span data-ttu-id="e2b77-103">指定將要完整簽署還是部分簽署組件。</span><span class="sxs-lookup"><span data-stu-id="e2b77-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2b77-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2b77-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2b77-105">引數</span><span class="sxs-lookup"><span data-stu-id="e2b77-105">Arguments</span></span>  
 <span data-ttu-id="e2b77-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e2b77-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e2b77-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e2b77-107">Optional.</span></span> <span data-ttu-id="e2b77-108">如果要完整簽署組件，請使用 `-delaysign-`。</span><span class="sxs-lookup"><span data-stu-id="e2b77-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="e2b77-109">使用`-delaysign+`如果您想要將公開金鑰放入帶正負號的雜湊的組件和保留空間。</span><span class="sxs-lookup"><span data-stu-id="e2b77-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="e2b77-110">預設值為 `-delaysign-`。</span><span class="sxs-lookup"><span data-stu-id="e2b77-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2b77-111">備註</span><span class="sxs-lookup"><span data-stu-id="e2b77-111">Remarks</span></span>  
 <span data-ttu-id="e2b77-112">`-delaysign`選項沒有任何作用，除非搭配[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)或[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。</span><span class="sxs-lookup"><span data-stu-id="e2b77-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="e2b77-113">當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署該雜湊。</span><span class="sxs-lookup"><span data-stu-id="e2b77-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="e2b77-114">所產生的數位簽章會儲存在包含資訊清單的檔案中。</span><span class="sxs-lookup"><span data-stu-id="e2b77-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="e2b77-115">延遲簽署組件時，編譯器不會不會計算並儲存檔案中的簽章，但保留空間，以便稍後再加入簽章。</span><span class="sxs-lookup"><span data-stu-id="e2b77-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="e2b77-116">例如，藉由使用`-delaysign+`，組織中的開發人員可以將不帶正負號的測試組件版本的測試人員可以向全域組件快取，並使用發佈。</span><span class="sxs-lookup"><span data-stu-id="e2b77-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="e2b77-117">組件上的工作完成時，負責組織的私用金鑰的人員可以完整簽署組件。</span><span class="sxs-lookup"><span data-stu-id="e2b77-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="e2b77-118">此劃分防止洩漏，同時允許使用組件的所有開發人員組織的私用金鑰。</span><span class="sxs-lookup"><span data-stu-id="e2b77-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="e2b77-119">請參閱[Creating and using strong-named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。</span><span class="sxs-lookup"><span data-stu-id="e2b77-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="e2b77-120">在 Visual Studio 整合式的開發環境中設定-delaysign</span><span class="sxs-lookup"><span data-stu-id="e2b77-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="e2b77-121">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="e2b77-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e2b77-122">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e2b77-122">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="e2b77-123">按一下 [簽署]索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e2b77-123">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="e2b77-124">設定中的值**延遲簽署只能**方塊。</span><span class="sxs-lookup"><span data-stu-id="e2b77-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b77-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2b77-125">See Also</span></span>  
 [<span data-ttu-id="e2b77-126">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="e2b77-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e2b77-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="e2b77-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="e2b77-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="e2b77-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [<span data-ttu-id="e2b77-129">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="e2b77-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
