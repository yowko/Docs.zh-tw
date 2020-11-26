---
description: -keyfile (C# 編譯器選項)
title: -keyfile (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: 5af40da18895d47933cb809d710e31a40f14513b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "91152425"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="f645d-103">-keyfile (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="f645d-103">-keyfile (C# Compiler Options)</span></span>

<span data-ttu-id="f645d-104">指定包含密碼編譯金鑰的檔名。</span><span class="sxs-lookup"><span data-stu-id="f645d-104">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f645d-105">語法</span><span class="sxs-lookup"><span data-stu-id="f645d-105">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="f645d-106">引數</span><span class="sxs-lookup"><span data-stu-id="f645d-106">Arguments</span></span>  
  
|<span data-ttu-id="f645d-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="f645d-107">Term</span></span>|<span data-ttu-id="f645d-108">定義</span><span class="sxs-lookup"><span data-stu-id="f645d-108">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="f645d-109">包含強式名稱金鑰的檔名。</span><span class="sxs-lookup"><span data-stu-id="f645d-109">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f645d-110">備註</span><span class="sxs-lookup"><span data-stu-id="f645d-110">Remarks</span></span>  

 <span data-ttu-id="f645d-111">使用此選項時，編譯器會從指定的檔案將公開金鑰插入資訊清單中，然後使用私密金鑰簽署最終組件。</span><span class="sxs-lookup"><span data-stu-id="f645d-111">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="f645d-112">若要產生金鑰檔，請在命令列鍵入 sn -k `file`。</span><span class="sxs-lookup"><span data-stu-id="f645d-112">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="f645d-113">如果您使用 **-target:module** 進行編譯，則在使用 [-addmodule](./addmodule-compiler-option.md) 編譯組件時，金鑰檔的名稱會保留在模組中並併入組件。</span><span class="sxs-lookup"><span data-stu-id="f645d-113">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="f645d-114">您也可以使用 [-keycontainer](./keycontainer-compiler-option.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="f645d-114">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="f645d-115">如需部分簽署的組件，請使用 [-delaysign](./delaysign-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="f645d-115">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="f645d-116">如果在相同編譯中同時指定 -keyfile 和 -keycontainer (藉由命令列選項或是自訂屬性指定)，編譯器會先嘗試使用金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="f645d-116">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="f645d-117">如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="f645d-117">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="f645d-118">如果編譯器找不到金鑰容器，則會嘗試使用以 -keyfile 指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="f645d-118">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="f645d-119">如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件，並將金鑰資訊安裝在金鑰容器中 (類似於 sn -i)，這樣在下次編譯時，金鑰容器就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="f645d-119">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="f645d-120">請注意，金鑰檔可能只包含公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="f645d-120">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="f645d-121">如需詳細資訊，請參閱[建立和使用強式名稱的組件](../../../standard/assembly/create-use-strong-named.md)和[延遲簽署組件](../../../standard/assembly/delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="f645d-121">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f645d-122">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="f645d-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="f645d-123">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="f645d-123">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="f645d-124">按一下 [簽署] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="f645d-124">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="f645d-125">修改 [選擇強式名稱金鑰檔] 屬性。</span><span class="sxs-lookup"><span data-stu-id="f645d-125">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="f645d-126">您可以使用 <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>，以程式設計方式存取這個編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="f645d-126">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f645d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f645d-127">See also</span></span>

- [<span data-ttu-id="f645d-128">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="f645d-128">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="f645d-129">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="f645d-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
