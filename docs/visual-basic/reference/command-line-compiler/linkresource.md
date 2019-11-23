---
title: -linkresource （Visual Basic）
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: dee5384696d543442f3280b9fdb535a7d9b6f863
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005496"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="2e909-102">-linkresource （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2e909-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="2e909-103">建立與 Managed 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="2e909-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e909-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e909-104">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="2e909-105">或</span><span class="sxs-lookup"><span data-stu-id="2e909-105">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e909-106">引數</span><span class="sxs-lookup"><span data-stu-id="2e909-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="2e909-107">必要。</span><span class="sxs-lookup"><span data-stu-id="2e909-107">Required.</span></span> <span data-ttu-id="2e909-108">要連結至元件的資源檔。</span><span class="sxs-lookup"><span data-stu-id="2e909-108">The resource file to link to the assembly.</span></span> <span data-ttu-id="2e909-109">如果檔案名包含空格，請將名稱括在引號（""）中。</span><span class="sxs-lookup"><span data-stu-id="2e909-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="2e909-110">選擇性。</span><span class="sxs-lookup"><span data-stu-id="2e909-110">Optional.</span></span> <span data-ttu-id="2e909-111">資源的邏輯名稱。</span><span class="sxs-lookup"><span data-stu-id="2e909-111">The logical name for the resource.</span></span> <span data-ttu-id="2e909-112">用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="2e909-112">The name that is used to load the resource.</span></span> <span data-ttu-id="2e909-113">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="2e909-113">The default is the name of the file.</span></span> <span data-ttu-id="2e909-114">（選擇性）您可以在組件資訊清單中指定檔案是否為公用或私用，例如： `-linkres:filename.res,myname.res,public`。</span><span class="sxs-lookup"><span data-stu-id="2e909-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="2e909-115">根據預設，`filename` 在元件中是公用的。</span><span class="sxs-lookup"><span data-stu-id="2e909-115">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e909-116">備註</span><span class="sxs-lookup"><span data-stu-id="2e909-116">Remarks</span></span>  
 <span data-ttu-id="2e909-117">`-linkresource` 選項不會將資源檔內嵌在輸出檔案中;使用 [`-resource`] 選項來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="2e909-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="2e909-118">`-linkresource` 選項需要 `-target:module`以外的其中一個 `-target` 選項。</span><span class="sxs-lookup"><span data-stu-id="2e909-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="2e909-119">例如，如果 `filename` 是由[resgen.exe （資源檔](../../../framework/tools/resgen-exe-resource-file-generator.md)產生器）或在開發環境中建立的 .NET Framework 資源檔，則可以使用 <xref:System.Resources> 命名空間中的成員進行存取。</span><span class="sxs-lookup"><span data-stu-id="2e909-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="2e909-120">（如需詳細資訊，請參閱 <xref:System.Resources.ResourceManager>）。若要在執行時間存取所有其他資源，請在 <xref:System.Reflection.Assembly> 類別中使用以 `GetManifestResource` 開頭的方法。</span><span class="sxs-lookup"><span data-stu-id="2e909-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="2e909-121">檔案名可以是任何檔案格式。</span><span class="sxs-lookup"><span data-stu-id="2e909-121">The file name can be any file format.</span></span> <span data-ttu-id="2e909-122">例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="2e909-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="2e909-123">`-linkresource` 的簡短形式為 `-linkres`。</span><span class="sxs-lookup"><span data-stu-id="2e909-123">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e909-124">Visual Studio 開發環境中無法使用 [`-linkresource`] 選項。只有當您從命令列編譯時，才可以使用它。</span><span class="sxs-lookup"><span data-stu-id="2e909-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e909-125">範例</span><span class="sxs-lookup"><span data-stu-id="2e909-125">Example</span></span>  
 <span data-ttu-id="2e909-126">下列程式碼會編譯 `in.vb` 和連結至資源檔 `rf.resource`。</span><span class="sxs-lookup"><span data-stu-id="2e909-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e909-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e909-127">See also</span></span>

- [<span data-ttu-id="2e909-128">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="2e909-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2e909-129">-target （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2e909-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="2e909-130">-資源（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="2e909-130">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="2e909-131">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="2e909-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
