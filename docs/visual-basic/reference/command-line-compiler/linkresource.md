---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="a3278-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3278-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="a3278-103">建立與 Managed 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="a3278-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3278-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3278-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a3278-105">引數</span><span class="sxs-lookup"><span data-stu-id="a3278-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="a3278-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="a3278-106">Required.</span></span> <span data-ttu-id="a3278-107">要連結至組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="a3278-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="a3278-108">如果檔案名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="a3278-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="a3278-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a3278-109">Optional.</span></span> <span data-ttu-id="a3278-110">資源的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="a3278-110">The logical name for the resource.</span></span> <span data-ttu-id="a3278-111">用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3278-111">The name that is used to load the resource.</span></span> <span data-ttu-id="a3278-112">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="a3278-112">The default is the name of the file.</span></span> <span data-ttu-id="a3278-113">您可以選擇性地指定檔案是否公用或私用組件資訊清單中，例如： `/linkres:filename.res,myname.res,public`。</span><span class="sxs-lookup"><span data-stu-id="a3278-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="a3278-114">根據預設，`filename`是公用的組件中。</span><span class="sxs-lookup"><span data-stu-id="a3278-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3278-115">備註</span><span class="sxs-lookup"><span data-stu-id="a3278-115">Remarks</span></span>  
 <span data-ttu-id="a3278-116">`/linkresource`選項不會在輸出檔中內嵌資源檔; 使用`/resource`選項來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="a3278-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="a3278-117">`/linkresource`選項需要一個`/target`選項以外`/target:module`。</span><span class="sxs-lookup"><span data-stu-id="a3278-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="a3278-118">如果`filename`是[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]建立資源檔，例如，藉由[Resgen.exe （資源檔產生器）](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ，或是在開發環境中，它可以存取與其中成員保持<xref:System.Resources>命名空間。</span><span class="sxs-lookup"><span data-stu-id="a3278-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="a3278-119">(如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager>)。若要在執行階段存取所有其他資源，可使用的方式開頭`GetManifestResource`中<xref:System.Reflection.Assembly>類別。</span><span class="sxs-lookup"><span data-stu-id="a3278-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="a3278-120">檔案名稱可以是任何檔案格式。</span><span class="sxs-lookup"><span data-stu-id="a3278-120">The file name can be any file format.</span></span> <span data-ttu-id="a3278-121">例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="a3278-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="a3278-122">`/linkresource` 的簡短形式為 `/linkres`。</span><span class="sxs-lookup"><span data-stu-id="a3278-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3278-123">`/linkresource`選項不可以從 Visual Studio 開發環境，則可以使用只有當您編譯從命令列。</span><span class="sxs-lookup"><span data-stu-id="a3278-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3278-124">範例</span><span class="sxs-lookup"><span data-stu-id="a3278-124">Example</span></span>  
 <span data-ttu-id="a3278-125">下列程式碼編譯`In.vb`以及資源檔連結`Rf.resource`。</span><span class="sxs-lookup"><span data-stu-id="a3278-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3278-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3278-126">See Also</span></span>  
 [<span data-ttu-id="a3278-127">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a3278-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a3278-128">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3278-128">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="a3278-129">/resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3278-129">/resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [<span data-ttu-id="a3278-130">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="a3278-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
