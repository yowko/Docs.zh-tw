---
title: 將 COM 元件公開給 .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 230853abf73a368bfcd8b88375c216fdadfc7d46
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567269"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="5720e-102">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5720e-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="5720e-103">本節摘要說明向 Managed 程式碼公開現有 COM 元件所需要的程序。</span><span class="sxs-lookup"><span data-stu-id="5720e-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="5720e-104">如需撰寫與 .NET Framework 緊密整合的 COM 伺服器的詳細資訊，請參閱[交互操作的設計考量](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="5720e-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="5720e-105">現有的 COM 元件是 Managed 程式碼中的寶貴資源，如同中介層商務應用程式或隔離功能。</span><span class="sxs-lookup"><span data-stu-id="5720e-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="5720e-106">理想的元件具有主要 Interop 組件，並能緊密貼合 COM 所加諸的程式設計標準。</span><span class="sxs-lookup"><span data-stu-id="5720e-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="5720e-107">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5720e-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="5720e-108">[匯入型別程式庫作為組件](importing-a-type-library-as-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="5720e-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="5720e-109">Common Language Runtime 需要所有類型的中繼資料，包括 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="5720e-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="5720e-110">有數種方式可以取得包含 COM 類型的組件，這些類型會匯入為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5720e-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="5720e-111">[使用受控碼中的 COM 類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="5720e-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="5720e-112">您可以檢查 COM 類型、啟動執行個體，以及使用您處理任何 Managed 類型的相同方式在 COM 物件上叫用方法。</span><span class="sxs-lookup"><span data-stu-id="5720e-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="5720e-113">[編譯 Interop 專案](compiling-an-interop-project.md)。</span><span class="sxs-lookup"><span data-stu-id="5720e-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="5720e-114">Windows SDK 提供與 Common Language Specification (CLS) 相容的數種語言編譯器，包括 Visual Basic、C# 與 C++。</span><span class="sxs-lookup"><span data-stu-id="5720e-114">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="5720e-115">[部署 Interop 應用程式](deploying-an-interop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="5720e-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="5720e-116">Interop 應用程式最適合部署為全域組件快取中具有[強式名稱](../app-domains/strong-named-assemblies.md)的已簽署組件。</span><span class="sxs-lookup"><span data-stu-id="5720e-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5720e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5720e-117">See also</span></span>

- [<span data-ttu-id="5720e-118">與 Unmanaged 程式碼互通</span><span class="sxs-lookup"><span data-stu-id="5720e-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="5720e-119">[交互操作的設計考量](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5720e-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="5720e-120">COM Interop 範例：.NET 用戶端與 COM 伺服器</span><span class="sxs-lookup"><span data-stu-id="5720e-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="5720e-121">語言獨立性以及與語言無關的元件</span><span class="sxs-lookup"><span data-stu-id="5720e-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="5720e-122">Gacutil.exe (全域組件快取工具)</span><span class="sxs-lookup"><span data-stu-id="5720e-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
