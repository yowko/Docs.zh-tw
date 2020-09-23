---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 8c4f753f94aedaf0a4f997a3f9b99fb3f417abf8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065680"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="0ce6f-102">-linkresource (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="0ce6f-102">-linkresource (Visual Basic)</span></span>

<span data-ttu-id="0ce6f-103">建立與 Managed 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ce6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ce6f-104">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="0ce6f-105">或</span><span class="sxs-lookup"><span data-stu-id="0ce6f-105">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0ce6f-106">引數</span><span class="sxs-lookup"><span data-stu-id="0ce6f-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="0ce6f-107">必要。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-107">Required.</span></span> <span data-ttu-id="0ce6f-108">要連結至元件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-108">The resource file to link to the assembly.</span></span> <span data-ttu-id="0ce6f-109">如果檔案名包含空格，請用引號括住名稱 ( "" ) 。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="0ce6f-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-110">Optional.</span></span> <span data-ttu-id="0ce6f-111">資源的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-111">The logical name for the resource.</span></span> <span data-ttu-id="0ce6f-112">用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-112">The name that is used to load the resource.</span></span> <span data-ttu-id="0ce6f-113">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-113">The default is the name of the file.</span></span> <span data-ttu-id="0ce6f-114">您可以選擇性地指定檔案是否在組件資訊清單中為公用或私用，例如： `-linkres:filename.res,myname.res,public` 。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="0ce6f-115">依預設，在 `filename` 元件中是公用的。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-115">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ce6f-116">備註</span><span class="sxs-lookup"><span data-stu-id="0ce6f-116">Remarks</span></span>  

 <span data-ttu-id="0ce6f-117">`-linkresource`選項不會將資源檔內嵌在輸出檔中，請使用 `-resource` 選項來執行此動作。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="0ce6f-118">`-linkresource`選項需要的 `-target` 選項之一除外 `-target:module` 。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="0ce6f-119">例如，如果 `filename` 是 .NET Framework 資源檔（例如，由 [Resgen.exe (資源檔 ](../../../framework/tools/resgen-exe-resource-file-generator.md) 產生器) 或在開發環境中所建立），則可以使用命名空間中的成員進行存取 <xref:System.Resources> 。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="0ce6f-120"> (如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager> 。 ) 若要在執行時間存取所有其他資源，請使用在類別中以開頭的方法 `GetManifestResource` <xref:System.Reflection.Assembly> 。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="0ce6f-121">檔案名可以是任何檔案格式。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-121">The file name can be any file format.</span></span> <span data-ttu-id="0ce6f-122">例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="0ce6f-123">`-linkresource` 的簡短形式為 `-linkres`。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-123">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ce6f-124">`-linkresource`選項無法在 Visual Studio 開發環境中使用; 只有當您從命令列進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ce6f-125">範例</span><span class="sxs-lookup"><span data-stu-id="0ce6f-125">Example</span></span>  

 <span data-ttu-id="0ce6f-126">下列程式碼會編譯 `in.vb` 並連結至資源檔 `rf.resource` 。</span><span class="sxs-lookup"><span data-stu-id="0ce6f-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ce6f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ce6f-127">See also</span></span>

- [<span data-ttu-id="0ce6f-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="0ce6f-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0ce6f-129">-目標 (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="0ce6f-129">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="0ce6f-130">-resource (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="0ce6f-130">-resource (Visual Basic)</span></span>](resource.md)
- [<span data-ttu-id="0ce6f-131">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="0ce6f-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
