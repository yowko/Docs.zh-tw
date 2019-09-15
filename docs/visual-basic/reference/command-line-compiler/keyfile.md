---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 30b890cf3d523d1e33b433a1ff6109759bd9a5e3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972321"
---
# <a name="-keyfile"></a><span data-ttu-id="cdd45-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="cdd45-102">-keyfile</span></span>
<span data-ttu-id="cdd45-103">指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。</span><span class="sxs-lookup"><span data-stu-id="cdd45-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd45-104">語法</span><span class="sxs-lookup"><span data-stu-id="cdd45-104">Syntax</span></span>  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="cdd45-105">引數</span><span class="sxs-lookup"><span data-stu-id="cdd45-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="cdd45-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="cdd45-106">Required.</span></span> <span data-ttu-id="cdd45-107">包含金鑰的檔案。</span><span class="sxs-lookup"><span data-stu-id="cdd45-107">File that contains the key.</span></span> <span data-ttu-id="cdd45-108">如果檔案名包含空格，請將名稱括在引號（""）中。</span><span class="sxs-lookup"><span data-stu-id="cdd45-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdd45-109">備註</span><span class="sxs-lookup"><span data-stu-id="cdd45-109">Remarks</span></span>  
 <span data-ttu-id="cdd45-110">編譯器會將公開金鑰插入組件資訊清單中，然後使用私密金鑰簽署最終元件。</span><span class="sxs-lookup"><span data-stu-id="cdd45-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="cdd45-111">若要產生金鑰檔，請在命令列中輸入 `sn -k file`。</span><span class="sxs-lookup"><span data-stu-id="cdd45-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="cdd45-112">如需詳細資訊，請參閱[sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)）。</span><span class="sxs-lookup"><span data-stu-id="cdd45-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="cdd45-113">如果您使用進行`-target:module`編譯，則金鑰檔的名稱會保留在模組中，並併入當您使用[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)編譯元件時所建立的元件中。</span><span class="sxs-lookup"><span data-stu-id="cdd45-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="cdd45-114">您也可以使用 [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="cdd45-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="cdd45-115">如需部分簽署的組件，請使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。</span><span class="sxs-lookup"><span data-stu-id="cdd45-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="cdd45-116">您也可以在任何 Microsoft 中繼語言模組的原始程式碼<xref:System.Reflection.AssemblyKeyFileAttribute>中，將此選項指定為自訂屬性（）。</span><span class="sxs-lookup"><span data-stu-id="cdd45-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="cdd45-117">如果在相同`-keyfile`編譯中同時指定和[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) （透過命令列選項或自訂屬性），編譯器會先嘗試使用金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="cdd45-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="cdd45-118">如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="cdd45-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="cdd45-119">如果編譯器找不到金鑰容器，則會嘗試使用`-keyfile`指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="cdd45-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="cdd45-120">如果成功，則會使用金鑰檔中的資訊簽署元件，並將金鑰資訊安裝在金鑰容器中（類似于`sn -i`），如此一來，在下一次編譯時，金鑰容器將會是有效的。</span><span class="sxs-lookup"><span data-stu-id="cdd45-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="cdd45-121">請注意，金鑰檔可能只包含公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="cdd45-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="cdd45-122">如需簽署元件的詳細資訊，請參閱[建立和使用強式名稱的元件](../../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="cdd45-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdd45-123">此`-keyfile`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="cdd45-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdd45-124">範例</span><span class="sxs-lookup"><span data-stu-id="cdd45-124">Example</span></span>  
 <span data-ttu-id="cdd45-125">下列程式碼會編譯原始`Input.vb`程式檔，並指定金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="cdd45-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdd45-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdd45-126">See also</span></span>

- [<span data-ttu-id="cdd45-127">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="cdd45-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="cdd45-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="cdd45-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="cdd45-129">-reference （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="cdd45-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="cdd45-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="cdd45-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
