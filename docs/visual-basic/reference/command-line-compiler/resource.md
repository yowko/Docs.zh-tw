---
title: "/resource (Visual Basic) |Microsoft 文件"
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
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: 19
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
ms.openlocfilehash: 2278902f96f7b6349e91a9803f58c3caa89f4f33
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="resource-visual-basic"></a><span data-ttu-id="be26c-102">/resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be26c-102">/resource (Visual Basic)</span></span>
<span data-ttu-id="be26c-103">將 Managed 資源內嵌至組件中。</span><span class="sxs-lookup"><span data-stu-id="be26c-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be26c-104">語法</span><span class="sxs-lookup"><span data-stu-id="be26c-104">Syntax</span></span>  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="be26c-105">引數</span><span class="sxs-lookup"><span data-stu-id="be26c-105">Arguments</span></span>  
  
|<span data-ttu-id="be26c-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="be26c-106">Term</span></span>|<span data-ttu-id="be26c-107">定義</span><span class="sxs-lookup"><span data-stu-id="be26c-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="be26c-108">必要項。</span><span class="sxs-lookup"><span data-stu-id="be26c-108">Required.</span></span> <span data-ttu-id="be26c-109">資源檔嵌入至輸出檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="be26c-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="be26c-110">根據預設，`filename`是公用的組件中。</span><span class="sxs-lookup"><span data-stu-id="be26c-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="be26c-111">將檔案名稱括在引號 ("") 如果它包含空格。</span><span class="sxs-lookup"><span data-stu-id="be26c-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="be26c-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="be26c-112">Optional.</span></span> <span data-ttu-id="be26c-113">資源; 的邏輯名稱用來載入它的名稱。</span><span class="sxs-lookup"><span data-stu-id="be26c-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="be26c-114">預設為檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="be26c-114">The default is the name of the file.</span></span> <span data-ttu-id="be26c-115">您可以選擇性地指定資源是否公用或私用組件資訊清單中，使用下列︰ `/res:``filename.res`，`myname.res`，`public`</span><span class="sxs-lookup"><span data-stu-id="be26c-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `/res:``filename.res`,`myname.res`,`public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be26c-116">備註</span><span class="sxs-lookup"><span data-stu-id="be26c-116">Remarks</span></span>  
 <span data-ttu-id="be26c-117">使用`/linkresource`資源連結到組件不需將資源檔放在輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="be26c-117">Use `/linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="be26c-118">如果`filename`是[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]建立資源檔，例如，由[Resgen.exe （資源檔產生器）](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)或在開發環境中，它可以存取與其中成員保持<xref:System.Resources>命名空間 (請參閱<xref:System.Resources.ResourceManager>如需詳細資訊)。</xref:System.Resources.ResourceManager> </xref:System.Resources></span><span class="sxs-lookup"><span data-stu-id="be26c-118">If `filename` is a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="be26c-119">若要在執行階段存取所有其他資源，請使用下列方法之一︰ <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>， <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>，或<xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</xref:System.Reflection.Assembly.GetManifestResourceStream%2A> </xref:System.Reflection.Assembly.GetManifestResourceNames%2A> </xref:System.Reflection.Assembly.GetManifestResourceInfo%2A></span><span class="sxs-lookup"><span data-stu-id="be26c-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="be26c-120">簡短形式`/resource`是`/res`。</span><span class="sxs-lookup"><span data-stu-id="be26c-120">The short form of `/resource` is `/res`.</span></span>  
  
 <span data-ttu-id="be26c-121">如需有關如何設定資訊`/resource`在 Visual Studio IDE 中，請參閱[管理應用程式資源 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="be26c-121">For information about how to set `/resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be26c-122">範例</span><span class="sxs-lookup"><span data-stu-id="be26c-122">Example</span></span>  
 <span data-ttu-id="be26c-123">下列程式碼編譯`In.vb`會附加至資源檔和`Rf.resource`。</span><span class="sxs-lookup"><span data-stu-id="be26c-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="be26c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be26c-124">See Also</span></span>  
 <span data-ttu-id="be26c-125">[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="be26c-125">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="be26c-126"> [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) </span><span class="sxs-lookup"><span data-stu-id="be26c-126"> [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) </span></span>  
<span data-ttu-id="be26c-127"> [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) </span><span class="sxs-lookup"><span data-stu-id="be26c-127"> [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) </span></span>  
<span data-ttu-id="be26c-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="be26c-128"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="be26c-129"> [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="be26c-129"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
