---
title: 作法：決定組件的完整名稱
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f1dbfde5e13d771f82ab1542e02de4c72b68678
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607729"
---
# <a name="how-to-determine-an-assemblys-fully-qualified-name"></a><span data-ttu-id="5b6bd-102">作法：決定組件的完整名稱</span><span class="sxs-lookup"><span data-stu-id="5b6bd-102">How to: Determine an Assembly's Fully Qualified Name</span></span>
<span data-ttu-id="5b6bd-103">若要在全域組件快取中找到組件的完整名稱，請使用全域組件快取工具 ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md))。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-103">To discover the fully qualified name of an assembly in the global assembly cache, use the Global Assembly Cache Tool ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="5b6bd-104">請參閱[如何：檢視全域組件快取的內容](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-104">See [How to: View the Contents of the Global Assembly Cache](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>  
  
 <span data-ttu-id="5b6bd-105">對於不在全域組件快取的組件，您可以使用數種方式取得完整組件名稱：可以使用程式碼輸出資訊至主控台或至變數，或者您可使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 以檢查組件中繼資料，其中包含完整名稱。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-105">For assemblies that are not in the global assembly cache, you can get the fully qualified assembly name in a number of ways: can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
- <span data-ttu-id="5b6bd-106">如果應用程式已經載入組件時，您可以擷取 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 屬性的值來取得完整名稱。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-106">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="5b6bd-107">您可以使用此方法，不論組件是否在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-107">You can use this approach whether or not the assembly is in the GAC.</span></span> <span data-ttu-id="5b6bd-108">這個範例將提供說明。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-108">The example provides an illustration.</span></span>  
  
- <span data-ttu-id="5b6bd-109">如果您知道組件的檔案系統路徑，您可以呼叫靜態 (`Shared` 在 Visual Basic 中) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> 方法來取得完整組件名稱。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-109">If you know the assembly's file system path, you can call the static (`Shared` in Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="5b6bd-110">以下是一個簡單的範例。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-110">The following is a simple example.</span></span>  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
- <span data-ttu-id="5b6bd-111">您可以使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢查組件的中繼資料，其中包含完整名稱。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-111">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>  
  
 <span data-ttu-id="5b6bd-112">如需有關設定組件屬性的詳細資訊，如版本、文化特性及組件名稱，請參閱[設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-112">For more information about setting assembly attributes such as version, culture, and assembly name, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span> <span data-ttu-id="5b6bd-113">如需有關給予組件強式名稱的詳細資訊，請參閱[建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-113">For more information about giving an assembly a strong name, see [Creating and Using Strong-Named Assemblies](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b6bd-114">範例</span><span class="sxs-lookup"><span data-stu-id="5b6bd-114">Example</span></span>  
 <span data-ttu-id="5b6bd-115">下列程式碼範例示範如何顯示含有指定類別組件的完整名稱至主控台。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-115">The following code example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="5b6bd-116">因為它會擷取應用程式已載入組件的名稱，所以組件是否在 GAC 中並不重要。</span><span class="sxs-lookup"><span data-stu-id="5b6bd-116">Because it retrieves the name of an assembly that the app has already loaded, it does not matter whether the assembly is in the GAC.</span></span>  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5b6bd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b6bd-117">See also</span></span>

- [<span data-ttu-id="5b6bd-118">組件名稱</span><span class="sxs-lookup"><span data-stu-id="5b6bd-118">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)
- [<span data-ttu-id="5b6bd-119">建立組件</span><span class="sxs-lookup"><span data-stu-id="5b6bd-119">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="5b6bd-120">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="5b6bd-120">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="5b6bd-121">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="5b6bd-121">Global Assembly Cache</span></span>](../../../docs/framework/app-domains/gac.md)
- [<span data-ttu-id="5b6bd-122">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="5b6bd-122">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="5b6bd-123">使用組件設計程式</span><span class="sxs-lookup"><span data-stu-id="5b6bd-123">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
