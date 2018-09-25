---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 97e0ccd46f413cc05b659731436bb141ee178419
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071526"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="3d26e-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d26e-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="3d26e-103">建立與 Managed 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="3d26e-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d26e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d26e-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d26e-105">引數</span><span class="sxs-lookup"><span data-stu-id="3d26e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="3d26e-106">必要。</span><span class="sxs-lookup"><span data-stu-id="3d26e-106">Required.</span></span> <span data-ttu-id="3d26e-107">要連結至組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="3d26e-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="3d26e-108">如果檔案名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="3d26e-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="3d26e-109">選擇性。</span><span class="sxs-lookup"><span data-stu-id="3d26e-109">Optional.</span></span> <span data-ttu-id="3d26e-110">資源的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="3d26e-110">The logical name for the resource.</span></span> <span data-ttu-id="3d26e-111">用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d26e-111">The name that is used to load the resource.</span></span> <span data-ttu-id="3d26e-112">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d26e-112">The default is the name of the file.</span></span> <span data-ttu-id="3d26e-113">您可以選擇性地指定檔案是否公用或私用組件資訊清單中，例如： `-linkres:filename.res,myname.res,public`。</span><span class="sxs-lookup"><span data-stu-id="3d26e-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="3d26e-114">根據預設，`filename`是公用的組件中。</span><span class="sxs-lookup"><span data-stu-id="3d26e-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d26e-115">備註</span><span class="sxs-lookup"><span data-stu-id="3d26e-115">Remarks</span></span>  
 <span data-ttu-id="3d26e-116">`-linkresource`選項不會將資源檔內嵌至輸出檔; 使用`-resource`選項來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="3d26e-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="3d26e-117">`-linkresource`選項需要其中一個`-target`以外的其他選項`-target:module`。</span><span class="sxs-lookup"><span data-stu-id="3d26e-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="3d26e-118">如果`filename`已[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]建立的資源檔，例如，藉由[Resgen.exe （資源檔產生器）](../../../framework/tools/resgen-exe-resource-file-generator.md)或在開發環境中，它可以存取使用中的成員<xref:System.Resources>命名空間。</span><span class="sxs-lookup"><span data-stu-id="3d26e-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="3d26e-119">(如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager>)。若要在執行階段存取所有其他資源，請使用 開頭的方法`GetManifestResource`在<xref:System.Reflection.Assembly>類別。</span><span class="sxs-lookup"><span data-stu-id="3d26e-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="3d26e-120">檔案名稱可以是任何檔案格式。</span><span class="sxs-lookup"><span data-stu-id="3d26e-120">The file name can be any file format.</span></span> <span data-ttu-id="3d26e-121">例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="3d26e-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="3d26e-122">`-linkresource` 的簡短形式為 `-linkres`。</span><span class="sxs-lookup"><span data-stu-id="3d26e-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d26e-123">`-linkresource`選項不是可從 Visual Studio 開發環境; 它是使用只有您在編譯時從命令列。</span><span class="sxs-lookup"><span data-stu-id="3d26e-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d26e-124">範例</span><span class="sxs-lookup"><span data-stu-id="3d26e-124">Example</span></span>  
 <span data-ttu-id="3d26e-125">下列程式碼會編譯`in.vb`以及資源檔的連結`rf.resource`。</span><span class="sxs-lookup"><span data-stu-id="3d26e-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d26e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d26e-126">See also</span></span>

- [<span data-ttu-id="3d26e-127">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="3d26e-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
- [<span data-ttu-id="3d26e-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d26e-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
- [<span data-ttu-id="3d26e-129">-資源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d26e-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
- [<span data-ttu-id="3d26e-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="3d26e-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
