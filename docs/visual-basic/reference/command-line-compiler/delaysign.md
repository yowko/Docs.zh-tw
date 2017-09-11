---
title: "/delaysign |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bcc819e08ca7731d91dc77dc831060bcf00a4425
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="delaysign"></a><span data-ttu-id="226e9-102">/delaysign</span><span class="sxs-lookup"><span data-stu-id="226e9-102">/delaysign</span></span>
<span data-ttu-id="226e9-103">指定將要完整簽署還是部分簽署組件。</span><span class="sxs-lookup"><span data-stu-id="226e9-103">Specifies whether the assembly will be fully or partially signed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="226e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="226e9-104">Syntax</span></span>  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="226e9-105">引數</span><span class="sxs-lookup"><span data-stu-id="226e9-105">Arguments</span></span>  
 <span data-ttu-id="226e9-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="226e9-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="226e9-107">選擇項。</span><span class="sxs-lookup"><span data-stu-id="226e9-107">Optional.</span></span> <span data-ttu-id="226e9-108">如果要完整簽署組件，請使用 `/delaysign-`。</span><span class="sxs-lookup"><span data-stu-id="226e9-108">Use `/delaysign-` if you want a fully signed assembly.</span></span> <span data-ttu-id="226e9-109">使用`/delaysign+`如果您想要的公開金鑰置於帶正負號的雜湊的組件和保留空間。</span><span class="sxs-lookup"><span data-stu-id="226e9-109">Use `/delaysign+` if you want to place the public key in the assembly and reserve space for the signed hash.</span></span> <span data-ttu-id="226e9-110">預設為 `/delaysign-`。</span><span class="sxs-lookup"><span data-stu-id="226e9-110">The default is `/delaysign-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="226e9-111">備註</span><span class="sxs-lookup"><span data-stu-id="226e9-111">Remarks</span></span>  
 <span data-ttu-id="226e9-112">`/delaysign`選項沒有任何作用，除非搭配[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)或[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。</span><span class="sxs-lookup"><span data-stu-id="226e9-112">The `/delaysign` option has no effect unless used with [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) or [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span>  
  
 <span data-ttu-id="226e9-113">當您要求完整簽署組件時，編譯器會雜湊包含資訊清單 （組件中繼資料），並使用私密金鑰簽署雜湊的檔案。</span><span class="sxs-lookup"><span data-stu-id="226e9-113">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="226e9-114">所產生的數位簽章會儲存在包含資訊清單的檔案中。</span><span class="sxs-lookup"><span data-stu-id="226e9-114">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="226e9-115">延遲簽署組件時，編譯器不會不會計算並儲存檔案中的簽章，但會保留空間，以便可以稍後再加入簽章。</span><span class="sxs-lookup"><span data-stu-id="226e9-115">When an assembly is delay signed, the compiler does not compute and store the signature but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="226e9-116">例如，藉由使用`/delaysign+`，組織中的開發人員可以散發不帶正負號的測試組件版本的軟體測試人員可以向全域組件快取，並使用。</span><span class="sxs-lookup"><span data-stu-id="226e9-116">For example, by using `/delaysign+`, a developer in an organization can distribute unsigned test versions of an assembly that testers can register with the global assembly cache and use.</span></span> <span data-ttu-id="226e9-117">組件上的工作完成時，負責組織的私用金鑰的人員可以完整簽署組件。</span><span class="sxs-lookup"><span data-stu-id="226e9-117">When work on the assembly is completed, the person responsible for the organization's private key can fully sign the assembly.</span></span> <span data-ttu-id="226e9-118">此區隔化防止洩漏，同時允許使用組件的所有開發人員組織的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="226e9-118">This compartmentalization protects the organization's private key from disclosure, while allowing all developers to work on the assemblies.</span></span>  
  
 <span data-ttu-id="226e9-119">請參閱[建立和使用強式名稱組件](https://msdn.microsoft.com/library/xwb8f617)如需有關簽署組件。</span><span class="sxs-lookup"><span data-stu-id="226e9-119">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="226e9-120">在 Visual Studio 中設定 /delaysign 整合式開發環境</span><span class="sxs-lookup"><span data-stu-id="226e9-120">To set /delaysign in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="226e9-121">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="226e9-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="226e9-122">在**專案**] 功能表上，按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="226e9-122">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="226e9-123">如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。</span><span class="sxs-lookup"><span data-stu-id="226e9-123">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="226e9-124">按一下 [**簽署**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="226e9-124">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="226e9-125">在設定的值**延遲簽署只**方塊。</span><span class="sxs-lookup"><span data-stu-id="226e9-125">Set the value in the **Delay sign only** box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="226e9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="226e9-126">See Also</span></span>  
 <span data-ttu-id="226e9-127">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="226e9-127">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="226e9-128"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span><span class="sxs-lookup"><span data-stu-id="226e9-128"> [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) </span></span>  
<span data-ttu-id="226e9-129"> [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) </span><span class="sxs-lookup"><span data-stu-id="226e9-129"> [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) </span></span>  
<span data-ttu-id="226e9-130"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="226e9-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
