---
description: -keycontainer (C# 編譯器選項)
title: -keycontainer (C# 編譯器選項)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: 8b11380683159b7792149558a5dd432707ba3818
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125497"
---
# <a name="-keycontainer-c-compiler-options"></a><span data-ttu-id="e1470-103">-keycontainer (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="e1470-103">-keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="e1470-104">指定密碼編譯金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1470-104">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1470-105">語法</span><span class="sxs-lookup"><span data-stu-id="e1470-105">Syntax</span></span>  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="e1470-106">引數</span><span class="sxs-lookup"><span data-stu-id="e1470-106">Arguments</span></span>  
 `string`  
 <span data-ttu-id="e1470-107">強式名稱金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="e1470-107">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1470-108">備註</span><span class="sxs-lookup"><span data-stu-id="e1470-108">Remarks</span></span>  
 <span data-ttu-id="e1470-109">使用 **-keycontainer** 選項時，編譯器會建立可共用的元件。</span><span class="sxs-lookup"><span data-stu-id="e1470-109">When the **-keycontainer** option is used, the compiler creates a sharable component.</span></span> <span data-ttu-id="e1470-110">編譯器會從指定的容器將公開金鑰插入至組件資訊清單，然後使用私密金鑰簽署最終組件。</span><span class="sxs-lookup"><span data-stu-id="e1470-110">The compiler inserts a public key from the specified container into the assembly manifest and signs the final assembly with the private key.</span></span> <span data-ttu-id="e1470-111">若要產生金鑰檔，請在命令列中輸入 `sn -k file`。</span><span class="sxs-lookup"><span data-stu-id="e1470-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="e1470-112">`sn -i` 會將金鑰組安裝於容器中。</span><span class="sxs-lookup"><span data-stu-id="e1470-112">`sn -i` installs the key pair into a container.</span></span> <span data-ttu-id="e1470-113">當編譯器在 CoreCLR 上執行時，不支援此選項。</span><span class="sxs-lookup"><span data-stu-id="e1470-113">This option is not supported when the compiler runs on CoreCLR.</span></span> <span data-ttu-id="e1470-114">若要在 CoreCLR 上建置時簽署組件，請使用 [-keyfile](keyfile-compiler-option.md) 選項。</span><span class="sxs-lookup"><span data-stu-id="e1470-114">To sign an assembly when building on CoreCLR, use the [-keyfile](keyfile-compiler-option.md) option.</span></span>
  
 <span data-ttu-id="e1470-115">如果您使用 [-target:module](./target-module-compiler-option.md) 進行編譯，則在使用 [-addmodule](./addmodule-compiler-option.md) 將這個模組編譯為組件時，金鑰檔的名稱會保留在模組中並併入組件。</span><span class="sxs-lookup"><span data-stu-id="e1470-115">If you compile with [-target:module](./target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="e1470-116">您也可以在任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼中，將這個選項指定為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="e1470-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="e1470-117">您也可以使用 [-keyfile](./keyfile-compiler-option.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="e1470-117">You can also pass your encryption information to the compiler with [-keyfile](./keyfile-compiler-option.md).</span></span> <span data-ttu-id="e1470-118">如果您想要將公開金鑰新增至資訊清單，但希望等到測試過後再簽署組件，請使用 [-delaysign](./delaysign-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="e1470-118">Use [-delaysign](./delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="e1470-119">如需詳細資訊，請參閱[建立和使用強式名稱的組件](../../../standard/assembly/create-use-strong-named.md)和[延遲簽署組件](../../../standard/assembly/delay-sign.md)。</span><span class="sxs-lookup"><span data-stu-id="e1470-119">For more information, see [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) and [Delay Signing an Assembly](../../../standard/assembly/delay-sign.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e1470-120">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="e1470-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e1470-121">Visual Studio 開發環境無法使用這個編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="e1470-121">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="e1470-122">您可以使用 <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>，以程式設計方式存取這個編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="e1470-122">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1470-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1470-123">See also</span></span>

- [<span data-ttu-id="e1470-124">C# 編譯器 -keyfile 選項</span><span class="sxs-lookup"><span data-stu-id="e1470-124">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="e1470-125">C # 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="e1470-125">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="e1470-126">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="e1470-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
