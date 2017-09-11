---
title: "/keyfile |Microsoft 文件"
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
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
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
ms.openlocfilehash: ec63fd990b8524bbc212a33714ec8380a8c99f32
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="keyfile"></a><span data-ttu-id="b0bf3-102">/keyfile</span><span class="sxs-lookup"><span data-stu-id="b0bf3-102">/keyfile</span></span>
<span data-ttu-id="b0bf3-103">指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0bf3-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0bf3-104">Syntax</span></span>  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="b0bf3-105">引數</span><span class="sxs-lookup"><span data-stu-id="b0bf3-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="b0bf3-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-106">Required.</span></span> <span data-ttu-id="b0bf3-107">包含金鑰的檔案。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-107">File that contains the key.</span></span> <span data-ttu-id="b0bf3-108">如果檔案名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0bf3-109">備註</span><span class="sxs-lookup"><span data-stu-id="b0bf3-109">Remarks</span></span>  
 <span data-ttu-id="b0bf3-110">編譯器會將公開金鑰插入組件資訊清單，然後使用私密金鑰簽署最終組件。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="b0bf3-111">若要產生金鑰檔，請輸入`sn -k file`在命令列。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="b0bf3-112">如需詳細資訊，請參閱 [Sn.exe (強式名稱工具)](https://msdn.microsoft.com/library/k5b5tt23)。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-112">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="b0bf3-113">如果您使用編譯`/target:module`，金鑰檔的名稱是保留在模組中，併入編譯的組件時，會建立組件[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-113">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="b0bf3-114">您也可以將加密資訊給編譯器以[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-114">You can also pass your encryption information to the compiler with [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="b0bf3-115">使用[/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)如果您想要的部分簽署組件。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-115">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="b0bf3-116">您也可以指定這個選項做為自訂屬性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) 中任何 Microsoft 中繼語言模組的原始程式碼。</xref:System.Reflection.AssemblyKeyFileAttribute></span><span class="sxs-lookup"><span data-stu-id="b0bf3-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="b0bf3-117">在案例中，同時`/keyfile`和[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) （命令列選項或是自訂屬性） 中指定相同的編譯，編譯器會先嘗試金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-117">In case both `/keyfile` and [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="b0bf3-118">如果成功，組件已簽署金鑰容器中的資訊。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="b0bf3-119">如果編譯器找不到金鑰容器，則會嘗試使用指定的檔案`/keyfile`。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-119">If the compiler does not find the key container, it tries the file specified with `/keyfile`.</span></span> <span data-ttu-id="b0bf3-120">如果這個動作成功、 簽署組件金鑰檔案中的資訊以及金鑰的資訊安裝在金鑰容器 (類似於`sn -i`)，以便在下次編譯時，金鑰容器才有效。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="b0bf3-121">請注意，金鑰檔可能包含公用的金鑰。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="b0bf3-122">請參閱[建立和使用強式名稱組件](https://msdn.microsoft.com/library/xwb8f617)如需有關簽署組件。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-122">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0bf3-123">`/keyfile`選項不可以從[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]開發環境，它才可使用從命令列進行編譯。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-123">The `/keyfile` option is not available from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0bf3-124">範例</span><span class="sxs-lookup"><span data-stu-id="b0bf3-124">Example</span></span>  
 <span data-ttu-id="b0bf3-125">下列程式碼會編譯原始程式檔`Input.vb`和指定的金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="b0bf3-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0bf3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0bf3-126">See Also</span></span>  
 <span data-ttu-id="b0bf3-127">[組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="b0bf3-127">[Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="b0bf3-128"> [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="b0bf3-128"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="b0bf3-129"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="b0bf3-129"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="b0bf3-130"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="b0bf3-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
