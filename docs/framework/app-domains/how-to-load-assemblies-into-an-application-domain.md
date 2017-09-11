---
title: "如何：將組件載入應用程式定義域"
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
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
caps.latest.revision: 16
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 75642ff3beb4462faa9068db76c89f3cb5f75ab8
ms.openlocfilehash: c319da0f8e6f3cdfb83e659a778136d668699834
ms.contentlocale: zh-tw
ms.lasthandoff: 08/10/2017

---
# <a name="how-to-load-assemblies-into-an-application-domain"></a><span data-ttu-id="5b30a-102">如何：將組件載入應用程式定義域</span><span class="sxs-lookup"><span data-stu-id="5b30a-102">How to: Load Assemblies into an Application Domain</span></span>
<span data-ttu-id="5b30a-103">有數種方式可以將組件載入應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="5b30a-103">There are several ways to load an assembly into an application domain.</span></span> <span data-ttu-id="5b30a-104">建議的方法是使用 <xref:System.Reflection.Assembly?displayProperty=fullName> 類別的 `static` (在 Visual Basic 中為 `Shared`) <xref:System.Reflection.Assembly.Load%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="5b30a-104">The recommended way is to use the `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.Load%2A> method of the <xref:System.Reflection.Assembly?displayProperty=fullName> class.</span></span> <span data-ttu-id="5b30a-105">其他可以載入組件的方式包括：</span><span class="sxs-lookup"><span data-stu-id="5b30a-105">Other ways assemblies can be loaded include:</span></span>  
  
-   <span data-ttu-id="5b30a-106"><xref:System.Reflection.Assembly> 類別的 <xref:System.Reflection.Assembly.LoadFrom%2A> 方法會載入已指定其檔案位置的組件。</span><span class="sxs-lookup"><span data-stu-id="5b30a-106">The <xref:System.Reflection.Assembly.LoadFrom%2A> method of the <xref:System.Reflection.Assembly> class loads an assembly given its file location.</span></span> <span data-ttu-id="5b30a-107">使用這種方法載入組件會使用不同的載入內容。</span><span class="sxs-lookup"><span data-stu-id="5b30a-107">Loading assemblies with this method uses a different load context.</span></span>  
  
-   <span data-ttu-id="5b30a-108"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> 和 <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> 方法將組件載入僅限反映的內容。</span><span class="sxs-lookup"><span data-stu-id="5b30a-108">The <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> and <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> methods load an assembly into the reflection-only context.</span></span> <span data-ttu-id="5b30a-109">可以檢查但不會執行載入此內容的組件，以允許檢查以其他平台為目標的組件。</span><span class="sxs-lookup"><span data-stu-id="5b30a-109">Assemblies loaded into this context can be examined but not executed, allowing the examination of assemblies that target other platforms.</span></span> <span data-ttu-id="5b30a-110">請參閱[如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)。</span><span class="sxs-lookup"><span data-stu-id="5b30a-110">See [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b30a-111">僅限反映的內容是 .NET Framework 2.0 版的新功能。</span><span class="sxs-lookup"><span data-stu-id="5b30a-111">The reflection-only context is new in the .NET Framework version 2.0.</span></span>  
  
-   <span data-ttu-id="5b30a-112"><xref:System.AppDomain> 類別的 <xref:System.AppDomain.CreateInstance%2A> 和 <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> 這類方法可以將組件載入應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="5b30a-112">Methods such as <xref:System.AppDomain.CreateInstance%2A> and <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> of the <xref:System.AppDomain> class can load assemblies into an application domain.</span></span>  
  
-   <span data-ttu-id="5b30a-113"><xref:System.Type> 類別的 <xref:System.Type.GetType%2A> 方法可以載入組件。</span><span class="sxs-lookup"><span data-stu-id="5b30a-113">The <xref:System.Type.GetType%2A> method of the <xref:System.Type> class can load assemblies.</span></span>  
  
-   <span data-ttu-id="5b30a-114"><xref:System.AppDomain?displayProperty=fullName> 類別的 <xref:System.AppDomain.Load%2A> 方法可以載入組件，但主要用於 COM 互通性。</span><span class="sxs-lookup"><span data-stu-id="5b30a-114">The <xref:System.AppDomain.Load%2A> method of the <xref:System.AppDomain?displayProperty=fullName> class can load assemblies, but is primarily used for COM interoperability.</span></span> <span data-ttu-id="5b30a-115">它不應該用來將組件載入其呼叫所在應用程式定義域以外的應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="5b30a-115">It should not be used to load assemblies into an application domain other than the application domain from which it is called.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b30a-116">從 .NET Framework 2.0 版開始，執行階段不會載入使用 .NET Framework 版本所編譯的組件，而這個版本的版本號碼高於目前載入的執行階段。</span><span class="sxs-lookup"><span data-stu-id="5b30a-116">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="5b30a-117">這適用於版本號碼的主要與次要元件組合。</span><span class="sxs-lookup"><span data-stu-id="5b30a-117">This applies to the combination of the major and minor components of the version number.</span></span>  
  
 <span data-ttu-id="5b30a-118">您可以指定在應用程式定義域之間共用所載入組件之 Just-In-Time (JIT) 編譯程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="5b30a-118">You can specify the way the just-in-time (JIT) compiled code from loaded assemblies is shared between application domains.</span></span> <span data-ttu-id="5b30a-119">如需詳細資訊，請參閱[應用程式定義域和組件](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)。</span><span class="sxs-lookup"><span data-stu-id="5b30a-119">For more information, see [Application Domains and Assemblies](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b30a-120">範例</span><span class="sxs-lookup"><span data-stu-id="5b30a-120">Example</span></span>  
 <span data-ttu-id="5b30a-121">下列程式碼會將名為 "example.exe" 或 "example.dll" 的組件載入目前應用程式定義域、從組件取得名為 `Example` 的類型、取得適用於該類型且名為 `MethodA` 的無參數方法，並且執行方法。</span><span class="sxs-lookup"><span data-stu-id="5b30a-121">The following code loads an assembly named "example.exe" or "example.dll" into the current application domain, gets a type named `Example` from the assembly, gets a parameterless method named `MethodA` for that type, and executes the method.</span></span> <span data-ttu-id="5b30a-122">如需從載入的組件取得資訊的完整討論，請參閱[動態載入和使用類型](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5b30a-122">For a complete discussion on obtaining information from a loaded assembly, see [Dynamically Loading and Using Types](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
 <span data-ttu-id="5b30a-123">[!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)] [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)] [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="5b30a-123">[!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)] [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)] [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b30a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b30a-124">See Also</span></span>  
 <span data-ttu-id="5b30a-125"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A></span><span class="sxs-lookup"><span data-stu-id="5b30a-125"><xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A></span></span>   
 <span data-ttu-id="5b30a-126">[使用應用程式定義域設計程式](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span><span class="sxs-lookup"><span data-stu-id="5b30a-126">[Programming with Application Domains](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131) </span></span>  
 <span data-ttu-id="5b30a-127">[反映](../../../docs/framework/reflection-and-codedom/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="5b30a-127">[Reflection](../../../docs/framework/reflection-and-codedom/reflection.md) </span></span>  
 <span data-ttu-id="5b30a-128">[使用應用程式定義域](../../../docs/framework/app-domains/use.md) </span><span class="sxs-lookup"><span data-stu-id="5b30a-128">[Using Application Domains](../../../docs/framework/app-domains/use.md) </span></span>  
 <span data-ttu-id="5b30a-129">[如何：將組件載入僅限反映的內容](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md) </span><span class="sxs-lookup"><span data-stu-id="5b30a-129">[How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md) </span></span>  
 [<span data-ttu-id="5b30a-130">應用程式定義域和組件</span><span class="sxs-lookup"><span data-stu-id="5b30a-130">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)

