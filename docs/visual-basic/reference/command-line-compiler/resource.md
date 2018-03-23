---
title: -資源 (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0de09ec0c778ac55ac7d93aa6d344e2067c46116
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="4a5c1-102">-資源 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a5c1-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="4a5c1-103">將 Managed 資源內嵌至組件中。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a5c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="4a5c1-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a5c1-105">引數</span><span class="sxs-lookup"><span data-stu-id="4a5c1-105">Arguments</span></span>  
  
|<span data-ttu-id="4a5c1-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="4a5c1-106">Term</span></span>|<span data-ttu-id="4a5c1-107">定義</span><span class="sxs-lookup"><span data-stu-id="4a5c1-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="4a5c1-108">必要。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-108">Required.</span></span> <span data-ttu-id="4a5c1-109">要內嵌至輸出檔的資源檔名稱。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="4a5c1-110">根據預設，`filename`是公用的組件中。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="4a5c1-111">將檔案名稱括在引號 ("") 如果包含空格。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="4a5c1-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-112">Optional.</span></span> <span data-ttu-id="4a5c1-113">邏輯名稱的資源;用來將其載入的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="4a5c1-114">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-114">The default is the name of the file.</span></span> <span data-ttu-id="4a5c1-115">您可以選擇性地指定的資源如同下列是公用或私用組件資訊清單中： `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="4a5c1-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a5c1-116">備註</span><span class="sxs-lookup"><span data-stu-id="4a5c1-116">Remarks</span></span>  
 <span data-ttu-id="4a5c1-117">使用`-linkresource`要將資源連結至組件，不需將資源檔放在輸出檔。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="4a5c1-118">如果`filename`是[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]建立資源檔，例如，藉由[Resgen.exe （資源檔產生器）](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ，或是在開發環境中，它可以存取與其中成員保持<xref:System.Resources>命名空間 （請參閱<xref:System.Resources.ResourceManager>如需詳細資訊)。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="4a5c1-119">若要在執行階段存取所有其他資源，請使用下列方法之一： <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>， <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>，或<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="4a5c1-120">`-resource` 的簡短形式為 `-res`。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="4a5c1-121">如需有關如何設定資訊`-resource`在 Visual Studio IDE 中，請參閱[管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a5c1-122">範例</span><span class="sxs-lookup"><span data-stu-id="4a5c1-122">Example</span></span>  
 <span data-ttu-id="4a5c1-123">下列程式碼編譯`In.vb`和附加資源檔`Rf.resource`。</span><span class="sxs-lookup"><span data-stu-id="4a5c1-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a5c1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a5c1-124">See Also</span></span>  
 [<span data-ttu-id="4a5c1-125">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="4a5c1-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4a5c1-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="4a5c1-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="4a5c1-127">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a5c1-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="4a5c1-128">-目標 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a5c1-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="4a5c1-129">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="4a5c1-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
