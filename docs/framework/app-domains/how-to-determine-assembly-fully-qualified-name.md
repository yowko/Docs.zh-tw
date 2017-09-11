---
title: "如何：決定組件的完整名稱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 673c836ea761c24e2627e97ab3bcb5dd3c35d141
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a><span data-ttu-id="d1c3c-102">如何：決定組件的完整名稱</span><span class="sxs-lookup"><span data-stu-id="d1c3c-102">How to: Determine an Assembly&#39;s Fully Qualified Name</span></span>
<span data-ttu-id="d1c3c-103">若要在全域組件快取中找到組件的完整名稱，請使用全域組件快取工具 ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md))。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="d1c3c-104">請參閱[如何：檢視全域組件快取的內容](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="d1c3c-105">對於不在全域組件快取的組件，您可以使用數種方式取得完整組件名稱：可以使用程式碼輸出資訊至主控台或至變數，或者您可使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 以檢查組件中繼資料，其中包含完整名稱。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
-   <span data-ttu-id="d1c3c-106">如果應用程式已經載入組件時，您可以擷取 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName> 屬性的值來取得完整名稱。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName> property to get the fully qualified name.</span></span> <span data-ttu-id="d1c3c-107">您可以使用此方法，不論組件是否在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="d1c3c-108">這個範例將提供說明。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-108">The example provides an illustration.</span></span>  
  
-   <span data-ttu-id="d1c3c-109">如果您知道組件的檔案系統路徑，您可以呼叫靜態 (`Shared` 在 Visual Basic 中) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=fullName> 方法來取得完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=fullName> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="d1c3c-110">以下是一個簡單的範例。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-110">The following is a simple example.</span></span>  
  
     <span data-ttu-id="d1c3c-111">[!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]  [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="d1c3c-111">[!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]  [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]</span></span>  
  
-   <span data-ttu-id="d1c3c-112">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢查組件的中繼資料，其中包含完整名稱。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-112">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="d1c3c-113">如需有關設定組件屬性的詳細資訊，如版本、文化特性及組件名稱，請參閱[設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="d1c3c-114">如需有關給予組件強式名稱的詳細資訊，請參閱[建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-114">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1c3c-115">範例</span><span class="sxs-lookup"><span data-stu-id="d1c3c-115">Example</span></span>  
 <span data-ttu-id="d1c3c-116">下列程式碼範例示範如何顯示含有指定類別組件的完整名稱至主控台。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-116">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="d1c3c-117">因為它會擷取應用程式已載入組件的名稱，所以組件是否在 GAC 中並不重要。</span><span class="sxs-lookup"><span data-stu-id="d1c3c-117">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 <span data-ttu-id="d1c3c-118">[!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)] [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)] [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="d1c3c-118">[!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)] [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)] [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c3c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c3c-119">See Also</span></span>  
 <span data-ttu-id="d1c3c-120">[組件名稱](../../../docs/framework/app-domains/assembly-names.md) </span><span class="sxs-lookup"><span data-stu-id="d1c3c-120">[Assembly Names](../../../docs/framework/app-domains/assembly-names.md) </span></span>  
 <span data-ttu-id="d1c3c-121">[建立組件](../../../docs/framework/app-domains/create-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="d1c3c-121">[Creating Assemblies](../../../docs/framework/app-domains/create-assemblies.md) </span></span>  
 <span data-ttu-id="d1c3c-122">[建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="d1c3c-122">[Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md) </span></span>  
 <span data-ttu-id="d1c3c-123">[全域組件快取](../../../docs/framework/app-domains/gac.md) </span><span class="sxs-lookup"><span data-stu-id="d1c3c-123">[Global Assembly Cache](../../../docs/framework/app-domains/gac.md) </span></span>  
 <span data-ttu-id="d1c3c-124">[執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="d1c3c-124">[How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span></span>  
 [<span data-ttu-id="d1c3c-125">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="d1c3c-125">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)

