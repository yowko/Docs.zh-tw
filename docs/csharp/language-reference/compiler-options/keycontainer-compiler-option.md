---
title: "-keycontainer (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keycontainer
dev_langs:
- CSharp
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: 35d3793f5052bb3ad047a3748465d8a01a4fe0f3
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="keycontainer-c-compiler-options"></a><span data-ttu-id="66926-102">/keycontainer (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="66926-102">/keycontainer (C# Compiler Options)</span></span>
<span data-ttu-id="66926-103">指定密碼編譯金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="66926-103">Specifies the name of the cryptographic key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66926-104">語法</span><span class="sxs-lookup"><span data-stu-id="66926-104">Syntax</span></span>  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a><span data-ttu-id="66926-105">引數</span><span class="sxs-lookup"><span data-stu-id="66926-105">Arguments</span></span>  
 `string`  
 <span data-ttu-id="66926-106">強式名稱金鑰容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="66926-106">The name of the strong name key container.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66926-107">備註</span><span class="sxs-lookup"><span data-stu-id="66926-107">Remarks</span></span>  
 <span data-ttu-id="66926-108">使用 **/keycontainer** 選項時，編譯器會將公開金鑰從指定的容器插入資訊清單，並使用私密金鑰簽署最終組件，藉此建立可共用的元件。</span><span class="sxs-lookup"><span data-stu-id="66926-108">When the **/keycontainer** option is used, the compiler creates a sharable component by inserting a public key from the specified container into the assembly manifest and signing the final assembly with the private key.</span></span> <span data-ttu-id="66926-109">若要產生金鑰檔，請在命令列鍵入 sn -k `file`。</span><span class="sxs-lookup"><span data-stu-id="66926-109">To generate a key file, type sn -k `file` at the command line.</span></span> <span data-ttu-id="66926-110">sn-i 會將金鑰組安裝在容器中。</span><span class="sxs-lookup"><span data-stu-id="66926-110">sn -i installs the key pair into a container.</span></span>  
  
 <span data-ttu-id="66926-111">如果您使用 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 進行編譯，則在使用 [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) 將這個模組編譯為組件時，金鑰檔的名稱會保留在模組中並併入組件。</span><span class="sxs-lookup"><span data-stu-id="66926-111">If you compile with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), the name of the key file is held in the module and incorporated into the assembly when you compile this module into an assembly with [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="66926-112">您也可以在任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼中，將這個選項指定為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>)。</span><span class="sxs-lookup"><span data-stu-id="66926-112">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="66926-113">您也可以使用 [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="66926-113">You can also pass your encryption information to the compiler with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).</span></span> <span data-ttu-id="66926-114">如果您想要將公開金鑰新增至資訊清單，但希望等到測試過後再簽署組件，請使用 [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="66926-114">Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) if you want the public key added to the assembly manifest but want to delay signing the assembly until it has been tested.</span></span>  
  
 <span data-ttu-id="66926-115">如需詳細資訊，請參閱[建立和使用強式名稱的組件](https://msdn.microsoft.com/library/xwb8f617)和[延遲簽署組件](../../../framework/app-domains/delay-sign-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="66926-115">For more information, see [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="66926-116">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="66926-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="66926-117">Visual Studio 開發環境無法使用這個編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="66926-117">This compiler option is not available in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="66926-118">您可以使用 <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>，以程式設計方式存取這個編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="66926-118">You can programmatically access this compiler option with <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66926-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66926-119">See Also</span></span>  
 <span data-ttu-id="66926-120">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="66926-120">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="66926-121"> [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span><span class="sxs-lookup"><span data-stu-id="66926-121"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span></span>
