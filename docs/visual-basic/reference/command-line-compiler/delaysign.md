---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 770dcad385c522a548a0c6fd3b6ef02dfbac82f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334597"
---
# <a name="-delaysign"></a><span data-ttu-id="6b4c8-102">-delaysign</span><span class="sxs-lookup"><span data-stu-id="6b4c8-102">-delaysign</span></span>
<span data-ttu-id="6b4c8-103">指定將要完整簽署還是部分簽署組件。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b4c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b4c8-104">Syntax</span></span>  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6b4c8-105">引數</span><span class="sxs-lookup"><span data-stu-id="6b4c8-105">Arguments</span></span>  
 <span data-ttu-id="6b4c8-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="6b4c8-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="6b4c8-107">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-107">Optional.</span></span> <span data-ttu-id="6b4c8-108">如果要完整簽署組件，請使用 `-delaysign-`。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-108">Use `-delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="6b4c8-109">使用`-delaysign+`如果您想要將公開金鑰放在帶正負號的雜湊的組件和保留空間。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-109">Use `-delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="6b4c8-110">預設為 `-delaysign-`。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-110">The default is `-delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b4c8-111">備註</span><span class="sxs-lookup"><span data-stu-id="6b4c8-111">Remarks</span></span>  
 <span data-ttu-id="6b4c8-112">`-delaysign`選項沒有任何作用，除非搭配[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)或是[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-112">The `-delaysign` option has no effect unless used with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="6b4c8-113">當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署該雜湊。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="6b4c8-114">所產生的數位簽章會儲存在包含資訊清單的檔案中。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="6b4c8-115">延遲簽署組件時，編譯器不會計算和儲存檔案中的簽章，但保留空間，以便可以稍後再加入簽章。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="6b4c8-116">例如，藉由使用`-delaysign+`，組織的開發人員可以將測試人員可向全域組件快取註冊及使用組件的不帶正負號的測試版本散發。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-116">For example, by using `-delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="6b4c8-117">組件上的工作完成時，負責組織的私用金鑰的人員可以完整簽署組件。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="6b4c8-118">此區隔化防止洩漏，同時讓所有開發人員使用的組件之組織的私用金鑰。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="6b4c8-119">請參閱[建立和使用強式名稱組件](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-119">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="6b4c8-120">若要在 Visual Studio 整合式的開發環境中設定-delaysign</span><span class="sxs-lookup"><span data-stu-id="6b4c8-120">To set -delaysign in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="6b4c8-121">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="6b4c8-122">在 [專案] 功能表上，按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-122">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="6b4c8-123">按一下 [簽署]索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-123">Click the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="6b4c8-124">在設定的值**僅延遲簽署** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="6b4c8-124">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b4c8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b4c8-125">See also</span></span>

- [<span data-ttu-id="6b4c8-126">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="6b4c8-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="6b4c8-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="6b4c8-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [<span data-ttu-id="6b4c8-128">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="6b4c8-128">-keycontainer</span></span>](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [<span data-ttu-id="6b4c8-129">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="6b4c8-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
