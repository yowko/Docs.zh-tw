---
title: "-resource (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a305f98b09d390afbeba7b55ab44ff09abc74617
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="b8540-102">-resource (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="b8540-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="b8540-103">將指定的資源內嵌到輸出檔。</span><span class="sxs-lookup"><span data-stu-id="b8540-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8540-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8540-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b8540-105">引數</span><span class="sxs-lookup"><span data-stu-id="b8540-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="b8540-106">您想要內嵌到輸出檔的 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="b8540-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="b8540-107">`identifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="b8540-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="b8540-108">資源的邏輯名稱；用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8540-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="b8540-109">預設值是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b8540-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="b8540-110">`accessibility-modifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="b8540-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="b8540-111">資源的存取範圍：公用或私用。</span><span class="sxs-lookup"><span data-stu-id="b8540-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="b8540-112">預設值是公用。</span><span class="sxs-lookup"><span data-stu-id="b8540-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8540-113">備註</span><span class="sxs-lookup"><span data-stu-id="b8540-113">Remarks</span></span>  
 <span data-ttu-id="b8540-114">使用 [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) 將資源連結至組件，而不將資源檔新增至輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="b8540-114">Use [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="b8540-115">根據預設，使用 C# 編譯器建立資源時，這些資源在組件中為公用狀態。</span><span class="sxs-lookup"><span data-stu-id="b8540-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="b8540-116">若要將資源設為私用，可將 `private` 指定為存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="b8540-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="b8540-117">不允許 `public` 或 `private` 以外的其他存取範圍。</span><span class="sxs-lookup"><span data-stu-id="b8540-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="b8540-118">例如，如果 `filename` 是由 [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) 或是在開發環境中所建立的 .NET Framework 資源檔，就可以使用 <xref:System.Resources> 命名空間中的成員進行存取。</span><span class="sxs-lookup"><span data-stu-id="b8540-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="b8540-119">如需詳細資訊，請參閱<xref:System.Resources.ResourceManager?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b8540-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b8540-120">對於其他所有資源，請使用 <xref:System.Reflection.Assembly> 類別中的 `GetManifestResource` 方法，以在執行階段存取資源。</span><span class="sxs-lookup"><span data-stu-id="b8540-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="b8540-121">**-res** 是 **-resource** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="b8540-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="b8540-122">輸出檔中資源的順序是從命令列上指定的順序決定。</span><span class="sxs-lookup"><span data-stu-id="b8540-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="b8540-123">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b8540-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="b8540-124">將資源檔新增至專案。</span><span class="sxs-lookup"><span data-stu-id="b8540-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="b8540-125">選取您想要內嵌在方案總管中的檔案。</span><span class="sxs-lookup"><span data-stu-id="b8540-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="b8540-126">在 [屬性] 視窗中，選取檔案的 [建置動作]。</span><span class="sxs-lookup"><span data-stu-id="b8540-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="b8540-127">將 [建置動作] 設定為 [內嵌資源]。</span><span class="sxs-lookup"><span data-stu-id="b8540-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="b8540-128">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.FileProperties2.BuildAction%2A>。</span><span class="sxs-lookup"><span data-stu-id="b8540-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8540-129">範例</span><span class="sxs-lookup"><span data-stu-id="b8540-129">Example</span></span>  
 <span data-ttu-id="b8540-130">編譯 `in.cs`，並附加 `rf.resource` 資源檔：</span><span class="sxs-lookup"><span data-stu-id="b8540-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8540-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8540-131">See Also</span></span>  
 [<span data-ttu-id="b8540-132">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="b8540-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="b8540-133">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="b8540-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
