---
title: /keyfile
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b7f41b659399ae5a12663d4e359c02606bb6f952
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="keyfile"></a><span data-ttu-id="863b9-102">/keyfile</span><span class="sxs-lookup"><span data-stu-id="863b9-102">/keyfile</span></span>
<span data-ttu-id="863b9-103">指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。</span><span class="sxs-lookup"><span data-stu-id="863b9-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="863b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="863b9-104">Syntax</span></span>  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="863b9-105">引數</span><span class="sxs-lookup"><span data-stu-id="863b9-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="863b9-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="863b9-106">Required.</span></span> <span data-ttu-id="863b9-107">包含索引鍵的檔案。</span><span class="sxs-lookup"><span data-stu-id="863b9-107">File that contains the key.</span></span> <span data-ttu-id="863b9-108">如果檔案名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="863b9-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="863b9-109">備註</span><span class="sxs-lookup"><span data-stu-id="863b9-109">Remarks</span></span>  
 <span data-ttu-id="863b9-110">編譯器的公開金鑰插入組件資訊清單，然後使用私密金鑰簽署最終組件。</span><span class="sxs-lookup"><span data-stu-id="863b9-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="863b9-111">若要產生的金鑰檔案，請輸入`sn -k file`在命令列。</span><span class="sxs-lookup"><span data-stu-id="863b9-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="863b9-112">如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。</span><span class="sxs-lookup"><span data-stu-id="863b9-112">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="863b9-113">如果您使用編譯`/target:module`，金鑰檔的名稱是保留在模組中，而且併入編譯的組件時所建立的組件[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。</span><span class="sxs-lookup"><span data-stu-id="863b9-113">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="863b9-114">您也可以使用 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="863b9-114">You can also pass your encryption information to the compiler with [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="863b9-115">如需部分簽署的組件，請使用 [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。</span><span class="sxs-lookup"><span data-stu-id="863b9-115">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="863b9-116">您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) 的任何 Microsoft 中繼語言模組的原始程式碼中。</span><span class="sxs-lookup"><span data-stu-id="863b9-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="863b9-117">在案例同時`/keyfile`和[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)指定 （根據命令列選項或是自訂屬性） 在相同編譯中，編譯器會先嘗試使用金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="863b9-117">In case both `/keyfile` and [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="863b9-118">如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="863b9-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="863b9-119">如果編譯器找不到金鑰容器，則會嘗試使用指定的檔案`/keyfile`。</span><span class="sxs-lookup"><span data-stu-id="863b9-119">If the compiler does not find the key container, it tries the file specified with `/keyfile`.</span></span> <span data-ttu-id="863b9-120">如果此作業執行成功、 簽署組件金鑰檔案中的資訊和金鑰資訊會安裝在金鑰容器 (類似於`sn -i`)，因此在下次編譯時，金鑰容器會有效。</span><span class="sxs-lookup"><span data-stu-id="863b9-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="863b9-121">請注意，金鑰檔可能只包含公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="863b9-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="863b9-122">請參閱[Creating and using strong-named Assemblies](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。</span><span class="sxs-lookup"><span data-stu-id="863b9-122">See [Creating and Using Strong-Named Assemblies](../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="863b9-123">`/keyfile`選項不是可從[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]開發環境中，只有在從命令列編譯時，它是可用。</span><span class="sxs-lookup"><span data-stu-id="863b9-123">The `/keyfile` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="863b9-124">範例</span><span class="sxs-lookup"><span data-stu-id="863b9-124">Example</span></span>  
 <span data-ttu-id="863b9-125">下列程式碼會編譯原始程式檔`Input.vb`，並指定金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="863b9-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="863b9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="863b9-126">See Also</span></span>  
 [<span data-ttu-id="863b9-127">組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="863b9-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="863b9-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="863b9-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="863b9-129">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="863b9-129">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="863b9-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="863b9-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
