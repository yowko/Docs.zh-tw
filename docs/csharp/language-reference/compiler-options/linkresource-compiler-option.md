---
title: "-linkresource (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d478c42141288cc3a1478ecf43f50c961a9d2246
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-c-compiler-options"></a><span data-ttu-id="0d47b-102">/linkresource (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="0d47b-102">/linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="0d47b-103">在輸出檔中建立 .NET Framework 資源連結。</span><span class="sxs-lookup"><span data-stu-id="0d47b-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="0d47b-104">資源檔不會新增至輸出檔。</span><span class="sxs-lookup"><span data-stu-id="0d47b-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="0d47b-105">這 一點與 [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) 選項不同；後者會將資源檔內嵌在輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="0d47b-105">This differs from the [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d47b-106">語法</span><span class="sxs-lookup"><span data-stu-id="0d47b-106">Syntax</span></span>  
  
```console  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0d47b-107">引數</span><span class="sxs-lookup"><span data-stu-id="0d47b-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="0d47b-108">您要從組件連結的目標 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="0d47b-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="0d47b-109">`identifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="0d47b-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="0d47b-110">資源的邏輯名稱；用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d47b-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="0d47b-111">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d47b-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="0d47b-112">`accessibility-modifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="0d47b-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="0d47b-113">資源的存取範圍：公用或私用。</span><span class="sxs-lookup"><span data-stu-id="0d47b-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="0d47b-114">預設值是公用。</span><span class="sxs-lookup"><span data-stu-id="0d47b-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d47b-115">備註</span><span class="sxs-lookup"><span data-stu-id="0d47b-115">Remarks</span></span>  
 <span data-ttu-id="0d47b-116">根據預設，使用 C# 編譯器建立連結資源時，這些資源在組件中為公用狀態。</span><span class="sxs-lookup"><span data-stu-id="0d47b-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="0d47b-117">若要將資源設為私用，可將 `private` 指定為存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0d47b-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="0d47b-118">您只能使用 `public` 或 `private` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0d47b-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="0d47b-119">**/linkresource** 必須使用其中一個 [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項 (**/target:module** 除外)。</span><span class="sxs-lookup"><span data-stu-id="0d47b-119">**/linkresource** requires one of the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than **/target:module**.</span></span>  
  
 <span data-ttu-id="0d47b-120">例如，如果 `filename` 是由 [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) 或是在開發環境中所建立的 .NET Framework 資源檔，就可以使用 <xref:System.Resources> 命名空間中的成員進行存取。</span><span class="sxs-lookup"><span data-stu-id="0d47b-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="0d47b-121">如需詳細資訊，請參閱<xref:System.Resources.ResourceManager?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0d47b-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0d47b-122">如需其他資源，使用`GetManifestResource`方法<xref:System.Reflection.Assembly>類別，以在執行階段存取資源。</span><span class="sxs-lookup"><span data-stu-id="0d47b-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="0d47b-123">`filename` 中指定的檔案可以為任何格式。</span><span class="sxs-lookup"><span data-stu-id="0d47b-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="0d47b-124">例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="0d47b-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="0d47b-125">下方第二個範例顯示如何執行此操作。</span><span class="sxs-lookup"><span data-stu-id="0d47b-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="0d47b-126">您可以在組件連結器中執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="0d47b-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="0d47b-127">下方第三個範例顯示如何執行此操作。</span><span class="sxs-lookup"><span data-stu-id="0d47b-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="0d47b-128">如需詳細資訊，請參閱 [Al.exe (組件連結器)](../../../framework/tools/al-exe-assembly-linker.md) 和[使用組件和全域組件快取](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="0d47b-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="0d47b-129">**/linkres** 是 **/linkresource** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="0d47b-129">**/linkres** is the short form of **/linkresource**.</span></span>  
  
 <span data-ttu-id="0d47b-130">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="0d47b-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d47b-131">範例</span><span class="sxs-lookup"><span data-stu-id="0d47b-131">Example</span></span>  
 <span data-ttu-id="0d47b-132">編譯 `in.cs` 並連結至 `rf.resource` 資源檔：</span><span class="sxs-lookup"><span data-stu-id="0d47b-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="0d47b-133">範例</span><span class="sxs-lookup"><span data-stu-id="0d47b-133">Example</span></span>  
 <span data-ttu-id="0d47b-134">將 `A.cs` 編譯為 DLL，再連結至原生 DLL N.dll，並將輸出放入全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="0d47b-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="0d47b-135">此範例的 A.dll 和 N.dll 都會位於 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="0d47b-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="0d47b-136">範例</span><span class="sxs-lookup"><span data-stu-id="0d47b-136">Example</span></span>  
 <span data-ttu-id="0d47b-137">此範例會執行與上一個範例相同的動作，但改為使用組件連結器選項。</span><span class="sxs-lookup"><span data-stu-id="0d47b-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d47b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d47b-138">See Also</span></span>  
 [<span data-ttu-id="0d47b-139">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="0d47b-139">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="0d47b-140">Al.exe (組件連結器)</span><span class="sxs-lookup"><span data-stu-id="0d47b-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="0d47b-141">使用組件和全域組件快取</span><span class="sxs-lookup"><span data-stu-id="0d47b-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="0d47b-142">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="0d47b-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
