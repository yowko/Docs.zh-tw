---
title: -resource (C# 編譯器選項)
ms.date: 07/20/2015
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
ms.openlocfilehash: 056207185f89aa219faf1b721598d372394e1061
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725697"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="f9b77-102">-resource (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="f9b77-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="f9b77-103">將指定的資源內嵌到輸出檔。</span><span class="sxs-lookup"><span data-stu-id="f9b77-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b77-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9b77-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9b77-105">引數</span><span class="sxs-lookup"><span data-stu-id="f9b77-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="f9b77-106">您想要內嵌到輸出檔的 .NET Framework 資源檔。</span><span class="sxs-lookup"><span data-stu-id="f9b77-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="f9b77-107">`identifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="f9b77-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="f9b77-108">資源的邏輯名稱；用來載入資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9b77-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="f9b77-109">預設值是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="f9b77-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="f9b77-110">`accessibility-modifier` (選擇性)</span><span class="sxs-lookup"><span data-stu-id="f9b77-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="f9b77-111">資源的存取範圍：公用或私用。</span><span class="sxs-lookup"><span data-stu-id="f9b77-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="f9b77-112">預設值是公用。</span><span class="sxs-lookup"><span data-stu-id="f9b77-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9b77-113">備註</span><span class="sxs-lookup"><span data-stu-id="f9b77-113">Remarks</span></span>  
 <span data-ttu-id="f9b77-114">使用 [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) 將資源連結至組件，而不將資源檔新增至輸出檔案。</span><span class="sxs-lookup"><span data-stu-id="f9b77-114">Use [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="f9b77-115">根據預設，使用 C# 編譯器建立資源時，這些資源在組件中為公用狀態。</span><span class="sxs-lookup"><span data-stu-id="f9b77-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="f9b77-116">若要將資源設為私用，可將 `private` 指定為存取範圍修飾詞。</span><span class="sxs-lookup"><span data-stu-id="f9b77-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="f9b77-117">不允許 `public` 或 `private` 以外的其他存取範圍。</span><span class="sxs-lookup"><span data-stu-id="f9b77-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="f9b77-118">例如，如果 `filename` 是由 [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) 或是在開發環境中所建立的 .NET Framework 資源檔，就可以使用 <xref:System.Resources> 命名空間中的成員進行存取。</span><span class="sxs-lookup"><span data-stu-id="f9b77-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="f9b77-119">如需詳細資訊，請參閱<xref:System.Resources.ResourceManager?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="f9b77-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9b77-120">對於其他所有資源，請使用 <xref:System.Reflection.Assembly> 類別中的 `GetManifestResource` 方法，以在執行階段存取資源。</span><span class="sxs-lookup"><span data-stu-id="f9b77-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="f9b77-121">**-res** 是 **-resource** 的簡短形式。</span><span class="sxs-lookup"><span data-stu-id="f9b77-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="f9b77-122">輸出檔中資源的順序是從命令列上指定的順序決定。</span><span class="sxs-lookup"><span data-stu-id="f9b77-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f9b77-123">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="f9b77-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="f9b77-124">將資源檔新增至專案。</span><span class="sxs-lookup"><span data-stu-id="f9b77-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="f9b77-125">選取您想要內嵌在方案總管中的檔案。</span><span class="sxs-lookup"><span data-stu-id="f9b77-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="f9b77-126">在 [屬性] 視窗中，選取檔案的 [建置動作]。</span><span class="sxs-lookup"><span data-stu-id="f9b77-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="f9b77-127">將 [建置動作] 設定為 [內嵌資源]。</span><span class="sxs-lookup"><span data-stu-id="f9b77-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="f9b77-128">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.FileProperties2.BuildAction%2A>。</span><span class="sxs-lookup"><span data-stu-id="f9b77-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b77-129">範例</span><span class="sxs-lookup"><span data-stu-id="f9b77-129">Example</span></span>  
 <span data-ttu-id="f9b77-130">編譯 `in.cs`，並附加 `rf.resource` 資源檔：</span><span class="sxs-lookup"><span data-stu-id="f9b77-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9b77-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9b77-131">See also</span></span>

- [<span data-ttu-id="f9b77-132">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="f9b77-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="f9b77-133">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="f9b77-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
