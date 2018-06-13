---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d682533f96b5fb56430a0826d37a9794dc8c5d8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655306"
---
# <a name="-keycontainer"></a><span data-ttu-id="a3df1-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="a3df1-102">-keycontainer</span></span>
<span data-ttu-id="a3df1-103">指定金鑰組的金鑰容器名稱，為組件提供強式名稱。</span><span class="sxs-lookup"><span data-stu-id="a3df1-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3df1-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3df1-104">Syntax</span></span>  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3df1-105">引數</span><span class="sxs-lookup"><span data-stu-id="a3df1-105">Arguments</span></span>  
  
|<span data-ttu-id="a3df1-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="a3df1-106">Term</span></span>|<span data-ttu-id="a3df1-107">定義</span><span class="sxs-lookup"><span data-stu-id="a3df1-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="a3df1-108">必要。</span><span class="sxs-lookup"><span data-stu-id="a3df1-108">Required.</span></span> <span data-ttu-id="a3df1-109">包含索引鍵的容器檔案。</span><span class="sxs-lookup"><span data-stu-id="a3df1-109">Container file that contains the key.</span></span> <span data-ttu-id="a3df1-110">將檔案名稱括在引號 ("") 如果名稱包含空格。</span><span class="sxs-lookup"><span data-stu-id="a3df1-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3df1-111">備註</span><span class="sxs-lookup"><span data-stu-id="a3df1-111">Remarks</span></span>  
 <span data-ttu-id="a3df1-112">藉由將公開金鑰插入組件資訊清單，並使用私密金鑰簽署最終組件，編譯器會建立可共用的元件。</span><span class="sxs-lookup"><span data-stu-id="a3df1-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="a3df1-113">若要產生的金鑰檔案，請輸入`sn -k``file`在命令列。</span><span class="sxs-lookup"><span data-stu-id="a3df1-113">To generate a key file, type `sn -k``file` at the command line.</span></span> <span data-ttu-id="a3df1-114">`-i`選項會安裝至容器的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="a3df1-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="a3df1-115">如需詳細資訊，請參閱 [Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))。</span><span class="sxs-lookup"><span data-stu-id="a3df1-115">For more information, see [Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="a3df1-116">如果您使用編譯`-target:module`，金鑰檔的名稱是保留在模組中，而且併入編譯的組件時所建立的組件[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。</span><span class="sxs-lookup"><span data-stu-id="a3df1-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="a3df1-117">您也可以在任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼中，將這個選項指定為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="a3df1-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="a3df1-118">您也可以使用 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="a3df1-118">You can also pass your encryption information to the compiler with [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md).</span></span> <span data-ttu-id="a3df1-119">如需部分簽署的組件，請使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。</span><span class="sxs-lookup"><span data-stu-id="a3df1-119">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="a3df1-120">請參閱[Creating and using strong-named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。</span><span class="sxs-lookup"><span data-stu-id="a3df1-120">See [Creating and Using Strong-Named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3df1-121">`-keycontainer`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。</span><span class="sxs-lookup"><span data-stu-id="a3df1-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3df1-122">範例</span><span class="sxs-lookup"><span data-stu-id="a3df1-122">Example</span></span>  
 <span data-ttu-id="a3df1-123">下列程式碼會編譯原始程式檔`Input.vb`和指定的金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="a3df1-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3df1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3df1-124">See Also</span></span>  
 [<span data-ttu-id="a3df1-125">組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="a3df1-125">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="a3df1-126">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a3df1-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a3df1-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="a3df1-127">-keyfile</span></span>](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="a3df1-128">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="a3df1-128">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
