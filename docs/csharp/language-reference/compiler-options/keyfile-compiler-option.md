---
title: -keyfile (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /keyfile
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
ms.openlocfilehash: eef843c87b8f1993c3419b261894a6df31096294
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606882"
---
# <a name="-keyfile-c-compiler-options"></a><span data-ttu-id="81739-102">-keyfile (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="81739-102">-keyfile (C# Compiler Options)</span></span>
<span data-ttu-id="81739-103">指定包含密碼編譯金鑰的檔名。</span><span class="sxs-lookup"><span data-stu-id="81739-103">Specifies the filename containing the cryptographic key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81739-104">語法</span><span class="sxs-lookup"><span data-stu-id="81739-104">Syntax</span></span>  
  
```console  
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="81739-105">引數</span><span class="sxs-lookup"><span data-stu-id="81739-105">Arguments</span></span>  
  
|<span data-ttu-id="81739-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="81739-106">Term</span></span>|<span data-ttu-id="81739-107">定義</span><span class="sxs-lookup"><span data-stu-id="81739-107">Definition</span></span>|  
|----------|----------------|  
|`file`|<span data-ttu-id="81739-108">包含強式名稱金鑰的檔名。</span><span class="sxs-lookup"><span data-stu-id="81739-108">The name of the file containing the strong name key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81739-109">備註</span><span class="sxs-lookup"><span data-stu-id="81739-109">Remarks</span></span>  
 <span data-ttu-id="81739-110">使用此選項時，編譯器會從指定的檔案將公開金鑰插入資訊清單中，然後使用私密金鑰簽署最終組件。</span><span class="sxs-lookup"><span data-stu-id="81739-110">When this option is used, the compiler inserts the public key from the specified file into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="81739-111">若要產生金鑰檔，請在命令列鍵入 sn -k `file`。</span><span class="sxs-lookup"><span data-stu-id="81739-111">To generate a key file, type sn -k `file` at the command line.</span></span>  
  
 <span data-ttu-id="81739-112">如果您使用 **-target:module** 進行編譯，則在使用 [-addmodule](./addmodule-compiler-option.md) 編譯組件時，金鑰檔的名稱會保留在模組中並併入組件。</span><span class="sxs-lookup"><span data-stu-id="81739-112">If you compile with **-target:module**, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="81739-113">您也可以使用 [-keycontainer](./keycontainer-compiler-option.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="81739-113">You can also pass your encryption information to the compiler with [-keycontainer](./keycontainer-compiler-option.md).</span></span> <span data-ttu-id="81739-114">如需部分簽署的組件，請使用 [-delaysign](./delaysign-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="81739-114">Use [-delaysign](./delaysign-compiler-option.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="81739-115">如果在相同編譯中同時指定 -keyfile 和 -keycontainer (藉由命令列選項或是自訂屬性指定)，編譯器會先嘗試使用金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="81739-115">In case both -keyfile and -keycontainer are specified (either by command line option or by custom attribute) in the same compilation, the compiler will first try the key container.</span></span> <span data-ttu-id="81739-116">如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="81739-116">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="81739-117">如果編譯器找不到金鑰容器，則會嘗試使用以 -keyfile 指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="81739-117">If the compiler does not find the key container, it will try the file specified with -keyfile.</span></span> <span data-ttu-id="81739-118">如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件，並將金鑰資訊安裝在金鑰容器中 (類似於 sn -i)，這樣在下次編譯時，金鑰容器就會是有效的。</span><span class="sxs-lookup"><span data-stu-id="81739-118">If that succeeds, the assembly is signed with the information in the key file and the key information will be installed in the key container (similar to sn -i) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="81739-119">請注意，金鑰檔可能只包含公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="81739-119">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="81739-120">如需詳細資訊，請參閱[建立和使用強式名稱的組件](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)和[延遲簽署組件](../../../framework/app-domains/delay-sign-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="81739-120">For more information, see [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="81739-121">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="81739-121">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="81739-122">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="81739-122">Open the **Properties** page for the project.</span></span>  
  
2. <span data-ttu-id="81739-123">按一下 [簽署]  屬性頁。</span><span class="sxs-lookup"><span data-stu-id="81739-123">Click the **Signing** property page.</span></span>  
  
3. <span data-ttu-id="81739-124">修改 [選擇強式名稱金鑰檔]  屬性。</span><span class="sxs-lookup"><span data-stu-id="81739-124">Modify the **Choose a strong name key file** property.</span></span>  
  
 <span data-ttu-id="81739-125">您可以使用 <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>，以程式設計方式存取這個編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="81739-125">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81739-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81739-126">See also</span></span>

- [<span data-ttu-id="81739-127">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="81739-127">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="81739-128">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="81739-128">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
