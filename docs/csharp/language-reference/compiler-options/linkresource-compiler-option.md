---
title: "-linkresource (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /linkresource
dev_langs:
- CSharp
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: 6fdbeab3960b9cfed1fe2e05183cee123c508507
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="linkresource-c-compiler-options"></a><span data-ttu-id="442b9-102">/linkresource (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="442b9-102">/linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="442b9-103">在輸出檔中建立 .NET Framework 資源連結。</span><span class="sxs-lookup"><span data-stu-id="442b9-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="442b9-104">資源檔不會新增至輸出檔。</span><span class="sxs-lookup"><span data-stu-id="442b9-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="442b9-105">這 一點與 [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) 選項不同；後者會將資源檔內嵌在輸出檔中。</span><span class="sxs-lookup"><span data-stu-id="442b9-105">This differs from the [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="442b9-106">語法</span><span class="sxs-lookup"><span data-stu-id="442b9-106">Syntax</span></span>  
  
```console  
/linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="442b9-107">引數</span><span class="sxs-lookup"><span data-stu-id="442b9-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="442b9-108">您要從組件連結的目標 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="442b9-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="442b9-109">`identifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="442b9-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="442b9-110">資源的邏輯名稱；用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="442b9-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="442b9-111">預設值是檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="442b9-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="442b9-112">`accessibility-modifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="442b9-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="442b9-113">資源的存取範圍：公用或私用。</span><span class="sxs-lookup"><span data-stu-id="442b9-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="442b9-114">預設值是公用。</span><span class="sxs-lookup"><span data-stu-id="442b9-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="442b9-115">備註</span><span class="sxs-lookup"><span data-stu-id="442b9-115">Remarks</span></span>  
 <span data-ttu-id="442b9-116">根據預設，使用 C# 編譯器建立連結資源時，這些資源在組件中為公用狀態。</span><span class="sxs-lookup"><span data-stu-id="442b9-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="442b9-117">若要將資源設為私用，可將 `private` 指定為存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="442b9-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="442b9-118">您只能使用 `public` 或 `private` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="442b9-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="442b9-119">**/linkresource** 必須使用其中一個 [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項 (**/target:module** 除外)。</span><span class="sxs-lookup"><span data-stu-id="442b9-119">**/linkresource** requires one of the [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than **/target:module**.</span></span>  
  
 <span data-ttu-id="442b9-120">例如，如果 `filename` 是由 [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) 或是在開發環境中所建立的 .NET Framework 資源檔，就可以使用 <xref:System.Resources> 命名空間中的成員進行存取。</span><span class="sxs-lookup"><span data-stu-id="442b9-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="442b9-121">如需詳細資訊，請參閱<xref:System.Resources.ResourceManager?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="442b9-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=fullName>.</span></span> <span data-ttu-id="442b9-122">至於其他所有資源，請使用 <xref:System.Reflection.Assembly> 類別中的 `GetManifestResource`* 方法在執行階段存取資源。</span><span class="sxs-lookup"><span data-stu-id="442b9-122">For all other resources, use the `GetManifestResource`* methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="442b9-123">`filename` 中指定的檔案可以為任何格式。</span><span class="sxs-lookup"><span data-stu-id="442b9-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="442b9-124">例如，您可能需要產生組件的原生 DLL 部分，以便安裝到全域組件快取中，並從組件的 Managed 程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="442b9-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="442b9-125">下方第二個範例顯示如何執行此操作。</span><span class="sxs-lookup"><span data-stu-id="442b9-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="442b9-126">您可以在組件連結器中執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="442b9-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="442b9-127">下方第三個範例顯示如何執行此操作。</span><span class="sxs-lookup"><span data-stu-id="442b9-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="442b9-128">如需詳細資訊，請參閱 [Al.exe (組件連結器)](https://msdn.microsoft.com/library/c405shex) 和[使用組件和全域組件快取](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="442b9-128">For more information, see [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="442b9-129">**/linkres** 是 **/linkresource** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="442b9-129">**/linkres** is the short form of **/linkresource**.</span></span>  
  
 <span data-ttu-id="442b9-130">Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。</span><span class="sxs-lookup"><span data-stu-id="442b9-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="442b9-131">範例</span><span class="sxs-lookup"><span data-stu-id="442b9-131">Example</span></span>  
 <span data-ttu-id="442b9-132">編譯 `in.cs` 並連結至 `rf.resource` 資源檔：</span><span class="sxs-lookup"><span data-stu-id="442b9-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="442b9-133">範例</span><span class="sxs-lookup"><span data-stu-id="442b9-133">Example</span></span>  
 <span data-ttu-id="442b9-134">將 `A.cs` 編譯為 DLL，再連結至原生 DLL N.dll，並將輸出放入全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="442b9-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="442b9-135">此範例的 A.dll 和 N.dll 都會位於 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="442b9-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="442b9-136">範例</span><span class="sxs-lookup"><span data-stu-id="442b9-136">Example</span></span>  
 <span data-ttu-id="442b9-137">此範例會執行與上一個範例相同的動作，但改為使用組件連結器選項。</span><span class="sxs-lookup"><span data-stu-id="442b9-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="442b9-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="442b9-138">See Also</span></span>  
 <span data-ttu-id="442b9-139">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="442b9-139">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="442b9-140"> [Al.exe (組件連結器)](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="442b9-140"> [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
<span data-ttu-id="442b9-141"> [使用組件和全域組件快取](../../../framework/app-domains/working-with-assemblies-and-the-gac.md) </span><span class="sxs-lookup"><span data-stu-id="442b9-141"> [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md) </span></span>  
<span data-ttu-id="442b9-142"> [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span><span class="sxs-lookup"><span data-stu-id="442b9-142"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span></span>
