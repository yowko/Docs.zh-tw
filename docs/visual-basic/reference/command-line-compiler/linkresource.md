---
title: "/linkresource (Visual Basic) |Microsoft 文件"
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
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8d4d2d2fdacef0c830414790efa544a96c35fd3c
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="45ac6-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45ac6-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="45ac6-103">建立與 Managed 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="45ac6-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ac6-104">語法</span><span class="sxs-lookup"><span data-stu-id="45ac6-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="45ac6-105">引數</span><span class="sxs-lookup"><span data-stu-id="45ac6-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="45ac6-106">必要項。</span><span class="sxs-lookup"><span data-stu-id="45ac6-106">Required.</span></span> <span data-ttu-id="45ac6-107">要連結至組件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="45ac6-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="45ac6-108">如果檔案名稱包含空格，將名稱括在引號 ("")。</span><span class="sxs-lookup"><span data-stu-id="45ac6-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="45ac6-109">選擇項。</span><span class="sxs-lookup"><span data-stu-id="45ac6-109">Optional.</span></span> <span data-ttu-id="45ac6-110">資源的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="45ac6-110">The logical name for the resource.</span></span> <span data-ttu-id="45ac6-111">用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="45ac6-111">The name that is used to load the resource.</span></span> <span data-ttu-id="45ac6-112">預設為檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="45ac6-112">The default is the name of the file.</span></span> <span data-ttu-id="45ac6-113">您可以選擇性地指定檔案是否公用或私用組件資訊清單中，例如︰ `/linkres:filename.res,myname.res,public`。</span><span class="sxs-lookup"><span data-stu-id="45ac6-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="45ac6-114">根據預設，`filename`是公用的組件中。</span><span class="sxs-lookup"><span data-stu-id="45ac6-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45ac6-115">備註</span><span class="sxs-lookup"><span data-stu-id="45ac6-115">Remarks</span></span>  
 <span data-ttu-id="45ac6-116">`/linkresource`選項不會在輸出檔案中內嵌資源檔，使用`/resource`選項來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="45ac6-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="45ac6-117">`/linkresource`選項需要其中`/target`以外的其他選項`/target:module`。</span><span class="sxs-lookup"><span data-stu-id="45ac6-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="45ac6-118">如果`filename`是[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]建立資源檔，例如，由[Resgen.exe （資源檔產生器）](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)或在開發環境中，它可以存取與其中成員保持<xref:System.Resources>命名空間。</xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="45ac6-118">If `filename` is a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="45ac6-119">(如需詳細資訊，請參閱<xref:System.Resources.ResourceManager>。)</xref:System.Resources.ResourceManager>若要在執行階段存取所有其他資源，請使用 開頭的方法`GetManifestResource`中<xref:System.Reflection.Assembly>類別。</xref:System.Reflection.Assembly></span><span class="sxs-lookup"><span data-stu-id="45ac6-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="45ac6-120">檔案名稱可以是任何檔案格式。</span><span class="sxs-lookup"><span data-stu-id="45ac6-120">The file name can be any file format.</span></span> <span data-ttu-id="45ac6-121">例如，您可能要產生的組件中，原生 DLL 部分，以便安裝到全域組件快取和從組件中的 managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="45ac6-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="45ac6-122">簡短形式`/linkresource`是`/linkres`。</span><span class="sxs-lookup"><span data-stu-id="45ac6-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45ac6-123">`/linkresource`選項不可以從 Visual Studio 開發環境，可僅當您編譯從命令列。</span><span class="sxs-lookup"><span data-stu-id="45ac6-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45ac6-124">範例</span><span class="sxs-lookup"><span data-stu-id="45ac6-124">Example</span></span>  
 <span data-ttu-id="45ac6-125">下列程式碼編譯`In.vb`和連結的資源檔`Rf.resource`。</span><span class="sxs-lookup"><span data-stu-id="45ac6-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="45ac6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45ac6-126">See Also</span></span>  
 <span data-ttu-id="45ac6-127">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="45ac6-127">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="45ac6-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="45ac6-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="45ac6-129"> [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) </span><span class="sxs-lookup"><span data-stu-id="45ac6-129"> [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) </span></span>  
<span data-ttu-id="45ac6-130"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="45ac6-130"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
