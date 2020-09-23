---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 726f3dd179aedb39b578c8580c9632182af2d5e0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085122"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="33667-102">-resource (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="33667-102">-resource (Visual Basic)</span></span>

<span data-ttu-id="33667-103">將 Managed 資源內嵌至組件中。</span><span class="sxs-lookup"><span data-stu-id="33667-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33667-104">語法</span><span class="sxs-lookup"><span data-stu-id="33667-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="33667-105">或</span><span class="sxs-lookup"><span data-stu-id="33667-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="33667-106">引數</span><span class="sxs-lookup"><span data-stu-id="33667-106">Arguments</span></span>  
  
|<span data-ttu-id="33667-107">詞彙</span><span class="sxs-lookup"><span data-stu-id="33667-107">Term</span></span>|<span data-ttu-id="33667-108">定義</span><span class="sxs-lookup"><span data-stu-id="33667-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="33667-109">必要。</span><span class="sxs-lookup"><span data-stu-id="33667-109">Required.</span></span> <span data-ttu-id="33667-110">要內嵌在輸出檔中的資源檔名稱。</span><span class="sxs-lookup"><span data-stu-id="33667-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="33667-111">依預設，在 `filename` 元件中是公用的。</span><span class="sxs-lookup"><span data-stu-id="33667-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="33667-112">以引號括住檔案名 ( "" ) 如果它包含空格。</span><span class="sxs-lookup"><span data-stu-id="33667-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="33667-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="33667-113">Optional.</span></span> <span data-ttu-id="33667-114">資源的邏輯名稱;用來載入它的名稱。</span><span class="sxs-lookup"><span data-stu-id="33667-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="33667-115">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="33667-115">The default is the name of the file.</span></span> <span data-ttu-id="33667-116">您可以選擇性地在組件資訊清單中指定資源為公用或私用，如下所示： `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="33667-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33667-117">備註</span><span class="sxs-lookup"><span data-stu-id="33667-117">Remarks</span></span>  

 <span data-ttu-id="33667-118">用 `-linkresource` 來將資源連結至元件，而不將資源檔放在輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="33667-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="33667-119">例如，如果 `filename` 是 .NET Framework 資源檔（例如 [Resgen.exe (資源檔 ](../../../framework/tools/resgen-exe-resource-file-generator.md) 產生器) 或開發環境中所建立），則可以使用命名空間中的成員進行存取 (如需 <xref:System.Resources> 詳細資訊，請參閱 <xref:System.Resources.ResourceManager>) 。</span><span class="sxs-lookup"><span data-stu-id="33667-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="33667-120">若要在執行時間存取所有其他資源，請使用下列其中一種方法： <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A> 、 <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 或 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> 。</span><span class="sxs-lookup"><span data-stu-id="33667-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="33667-121">`-resource` 的簡短形式為 `-res`。</span><span class="sxs-lookup"><span data-stu-id="33667-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="33667-122">如需如何 `-resource` 在 VISUAL STUDIO IDE 中設定的詳細資訊，請參閱 [ ( .Net) 管理應用程式資源 ](/visualstudio/ide/managing-application-resources-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="33667-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33667-123">範例</span><span class="sxs-lookup"><span data-stu-id="33667-123">Example</span></span>  

 <span data-ttu-id="33667-124">下列程式碼會編譯 `In.vb` 和附加資源檔 `Rf.resource` 。</span><span class="sxs-lookup"><span data-stu-id="33667-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="33667-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33667-125">See also</span></span>

- [<span data-ttu-id="33667-126">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="33667-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="33667-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="33667-127">-win32resource</span></span>](win32resource.md)
- [<span data-ttu-id="33667-128">-linkresource (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="33667-128">-linkresource (Visual Basic)</span></span>](linkresource.md)
- [<span data-ttu-id="33667-129">-目標 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="33667-129">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="33667-130">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="33667-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
