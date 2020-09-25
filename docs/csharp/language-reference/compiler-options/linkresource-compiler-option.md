---
description: -linkresource (C# 編譯器選項)
title: -linkresource (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 4efa0cbf286b40ad971bad66a7acce15e553eb39
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194098"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="28bf3-103">-linkresource (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="28bf3-103">-linkresource (C# Compiler Options)</span></span>

<span data-ttu-id="28bf3-104">在輸出檔中建立 .NET 資源的連結。</span><span class="sxs-lookup"><span data-stu-id="28bf3-104">Creates a link to a .NET resource in the output file.</span></span> <span data-ttu-id="28bf3-105">資源檔不會新增至輸出檔。</span><span class="sxs-lookup"><span data-stu-id="28bf3-105">The resource file is not added to the output file.</span></span> <span data-ttu-id="28bf3-106">這點與 [-resource](./resource-compiler-option.md) 選項不同；後者會將資源檔內嵌在輸出檔案中。</span><span class="sxs-lookup"><span data-stu-id="28bf3-106">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28bf3-107">語法</span><span class="sxs-lookup"><span data-stu-id="28bf3-107">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="28bf3-108">引數</span><span class="sxs-lookup"><span data-stu-id="28bf3-108">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="28bf3-109">您要從元件連結的 .NET 資源檔。</span><span class="sxs-lookup"><span data-stu-id="28bf3-109">The .NET resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="28bf3-110">`identifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="28bf3-110">`identifier` (optional)</span></span>  
 <span data-ttu-id="28bf3-111">資源的邏輯名稱；用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="28bf3-111">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="28bf3-112">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="28bf3-112">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="28bf3-113">`accessibility-modifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="28bf3-113">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="28bf3-114">資源的存取範圍：公用或私用。</span><span class="sxs-lookup"><span data-stu-id="28bf3-114">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="28bf3-115">預設值是 public。</span><span class="sxs-lookup"><span data-stu-id="28bf3-115">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28bf3-116">備註</span><span class="sxs-lookup"><span data-stu-id="28bf3-116">Remarks</span></span>  

 <span data-ttu-id="28bf3-117">根據預設，使用 C# 編譯器建立連結資源時，這些資源在組件中為公用狀態。</span><span class="sxs-lookup"><span data-stu-id="28bf3-117">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="28bf3-118">若要將資源設為私用，可將 `private` 指定為存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="28bf3-118">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="28bf3-119">您只能使用 `public` 或 `private` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="28bf3-119">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="28bf3-120">**-linkresource** 必須使用其中一個 [-target](./target-compiler-option.md) 選項 (**-target:module** 除外)。</span><span class="sxs-lookup"><span data-stu-id="28bf3-120">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="28bf3-121">如果 `filename` 是建立的 .net 資源檔（例如 [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) 或在開發環境中），則可以使用命名空間中的成員進行存取 <xref:System.Resources> 。</span><span class="sxs-lookup"><span data-stu-id="28bf3-121">If `filename` is a .NET resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="28bf3-122">如需詳細資訊，請參閱<xref:System.Resources.ResourceManager?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="28bf3-122">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="28bf3-123">對於其他所有資源，請使用 <xref:System.Reflection.Assembly> 類別中的 `GetManifestResource` 方法，以在執行階段存取資源。</span><span class="sxs-lookup"><span data-stu-id="28bf3-123">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="28bf3-124">`filename` 中指定的檔案可以為任何格式。</span><span class="sxs-lookup"><span data-stu-id="28bf3-124">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="28bf3-125">例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="28bf3-125">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="28bf3-126">下方第二個範例顯示如何執行此操作。</span><span class="sxs-lookup"><span data-stu-id="28bf3-126">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="28bf3-127">您可以在組件連結器中執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="28bf3-127">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="28bf3-128">下方第三個範例顯示如何執行此操作。</span><span class="sxs-lookup"><span data-stu-id="28bf3-128">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="28bf3-129">如需詳細資訊，請參閱 [Al.exe (組件連結器)](../../../framework/tools/al-exe-assembly-linker.md) 和[使用組件和全域組件快取](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="28bf3-129">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="28bf3-130">**-linkres** 是 **-linkresource** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="28bf3-130">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="28bf3-131">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="28bf3-131">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28bf3-132">範例</span><span class="sxs-lookup"><span data-stu-id="28bf3-132">Example</span></span>  

 <span data-ttu-id="28bf3-133">編譯 `in.cs` 並連結至 `rf.resource` 資源檔：</span><span class="sxs-lookup"><span data-stu-id="28bf3-133">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="28bf3-134">範例</span><span class="sxs-lookup"><span data-stu-id="28bf3-134">Example</span></span>  

 <span data-ttu-id="28bf3-135">將 `A.cs` 編譯為 DLL，再連結至原生 DLL N.dll，並將輸出放入全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="28bf3-135">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="28bf3-136">此範例的 A.dll 和 N.dll 都會位於 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="28bf3-136">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="28bf3-137">範例</span><span class="sxs-lookup"><span data-stu-id="28bf3-137">Example</span></span>  

 <span data-ttu-id="28bf3-138">此範例會執行與上一個範例相同的動作，但改為使用組件連結器選項。</span><span class="sxs-lookup"><span data-stu-id="28bf3-138">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="28bf3-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28bf3-139">See also</span></span>

- [<span data-ttu-id="28bf3-140">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="28bf3-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="28bf3-141">Al.exe (元件連結器) </span><span class="sxs-lookup"><span data-stu-id="28bf3-141">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="28bf3-142">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="28bf3-142">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="28bf3-143">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="28bf3-143">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
