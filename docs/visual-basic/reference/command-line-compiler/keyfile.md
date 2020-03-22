---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266738"
---
# <a name="-keyfile"></a><span data-ttu-id="4261c-102">-keyfile</span><span class="sxs-lookup"><span data-stu-id="4261c-102">-keyfile</span></span>
<span data-ttu-id="4261c-103">指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。</span><span class="sxs-lookup"><span data-stu-id="4261c-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4261c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4261c-104">Syntax</span></span>  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="4261c-105">引數</span><span class="sxs-lookup"><span data-stu-id="4261c-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="4261c-106">必要。</span><span class="sxs-lookup"><span data-stu-id="4261c-106">Required.</span></span> <span data-ttu-id="4261c-107">包含金鑰的檔。</span><span class="sxs-lookup"><span data-stu-id="4261c-107">File that contains the key.</span></span> <span data-ttu-id="4261c-108">如果檔案名包含空格，則用引號 （""） 括上名稱。</span><span class="sxs-lookup"><span data-stu-id="4261c-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4261c-109">備註</span><span class="sxs-lookup"><span data-stu-id="4261c-109">Remarks</span></span>  
 <span data-ttu-id="4261c-110">編譯器將公開金鑰插入組件資訊清單，然後使用私密金鑰對最終程式集進行簽名。</span><span class="sxs-lookup"><span data-stu-id="4261c-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="4261c-111">若要產生金鑰檔，請在命令列中輸入 `sn -k file`。</span><span class="sxs-lookup"><span data-stu-id="4261c-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="4261c-112">有關詳細資訊，請參閱[Sn.exe（強式名稱工具）。](../../../framework/tools/sn-exe-strong-name-tool.md)</span><span class="sxs-lookup"><span data-stu-id="4261c-112">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="4261c-113">如果使用 編譯，`-target:module`則金鑰檔的名稱將包含在模組中，併合並[到編譯器集](../../../visual-basic/reference/command-line-compiler/addmodule.md)時創建的程式集中，</span><span class="sxs-lookup"><span data-stu-id="4261c-113">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="4261c-114">您也可以使用 [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="4261c-114">You can also pass your encryption information to the compiler with [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="4261c-115">如需部分簽署的組件，請使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。</span><span class="sxs-lookup"><span data-stu-id="4261c-115">Use [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="4261c-116">您還可以在任何 Microsoft 中間語言模組的原始程式碼中<xref:System.Reflection.AssemblyKeyFileAttribute>指定此選項為自訂屬性 （ ） 。</span><span class="sxs-lookup"><span data-stu-id="4261c-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="4261c-117">如果在同`-keyfile`一編譯中指定和[-key 容器](../../../visual-basic/reference/command-line-compiler/keycontainer.md)（通過命令列選項或自訂屬性），編譯器首先嘗試金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="4261c-117">In case both `-keyfile` and [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="4261c-118">如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="4261c-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="4261c-119">如果編譯器找不到金鑰容器，它將嘗試使用`-keyfile`指定的檔。</span><span class="sxs-lookup"><span data-stu-id="4261c-119">If the compiler does not find the key container, it tries the file specified with `-keyfile`.</span></span> <span data-ttu-id="4261c-120">如果成功，程式集將使用金鑰檔中的資訊進行簽名，並且金鑰資訊安裝在金鑰容器中（類似于`sn -i`），以便在下一次編譯時金鑰容器將有效。</span><span class="sxs-lookup"><span data-stu-id="4261c-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="4261c-121">請注意，金鑰檔可能只包含公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="4261c-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="4261c-122">有關對程式集進行簽名的詳細資訊，請參閱[創建和使用強式名稱程式集](../../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="4261c-122">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4261c-123">該`-keyfile`選項在視覺化工作室開發環境中不可用;因此，該選項在視覺化工作室開發環境中不可用。它僅在從命令列編譯時可用。</span><span class="sxs-lookup"><span data-stu-id="4261c-123">The `-keyfile` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="4261c-124">範例</span><span class="sxs-lookup"><span data-stu-id="4261c-124">Example</span></span>

<span data-ttu-id="4261c-125">以下代碼編譯原始檔案`Input.vb`並指定金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="4261c-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a><span data-ttu-id="4261c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4261c-126">See also</span></span>

- [<span data-ttu-id="4261c-127">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="4261c-127">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="4261c-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="4261c-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4261c-129">-參考（視覺基礎）</span><span class="sxs-lookup"><span data-stu-id="4261c-129">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
- [<span data-ttu-id="4261c-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="4261c-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
