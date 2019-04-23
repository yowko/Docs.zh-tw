---
title: Unmanaged API 參考
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd84d84706a0d61f26b576b7300fae87fbe602e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984161"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="db3a9-102">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="db3a9-102">Unmanaged API Reference</span></span>
<span data-ttu-id="db3a9-103">本節包含與 Managed 程式碼相關之應用程式 (例如執行階段主機、編譯器、反組譯工具、模糊化工具、偵錯工具和分析工具) 可用的 Unmanaged API 的資訊。</span><span class="sxs-lookup"><span data-stu-id="db3a9-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="db3a9-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="db3a9-104">In This Section</span></span>  
 [<span data-ttu-id="db3a9-105">一般資料類型</span><span class="sxs-lookup"><span data-stu-id="db3a9-105">Common Data Types</span></span>](../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="db3a9-106">列出使用的一般資料類型 (特別是用於 Unmanaged 分析及偵錯 API 中)。</span><span class="sxs-lookup"><span data-stu-id="db3a9-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="db3a9-107">ALink</span><span class="sxs-lookup"><span data-stu-id="db3a9-107">ALink</span></span>](../../../docs/framework/unmanaged-api/alink/index.md)  
 <span data-ttu-id="db3a9-108">描述支援建立 .NET Framework 組件及未繫結模組的 ALink API。</span><span class="sxs-lookup"><span data-stu-id="db3a9-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="db3a9-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="db3a9-109">Authenticode</span></span>](../../../docs/framework/unmanaged-api/authenticode/index.md)  
 <span data-ttu-id="db3a9-110">支援 Authenticode XrML 授權的建立及驗證模組。</span><span class="sxs-lookup"><span data-stu-id="db3a9-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="db3a9-111">常數</span><span class="sxs-lookup"><span data-stu-id="db3a9-111">Constants</span></span>](../../../docs/framework/unmanaged-api/constants-unmanaged-api-reference.md)  
 <span data-ttu-id="db3a9-112">描述定義於 CorSym.idl 中的常數。</span><span class="sxs-lookup"><span data-stu-id="db3a9-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="db3a9-113">[自訂介面屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="db3a9-113">[Custom Interface Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="db3a9-114">描述元件物件模型 (COM) 自訂介面屬性。</span><span class="sxs-lookup"><span data-stu-id="db3a9-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="db3a9-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="db3a9-115">Debugging</span></span>](../../../docs/framework/unmanaged-api/debugging/index.md)  
 <span data-ttu-id="db3a9-116">描述偵錯 API，其其可讓偵錯工具偵錯在 Common Language Runtime (CLR) 環境中執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="db3a9-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="db3a9-117">診斷符號存放區</span><span class="sxs-lookup"><span data-stu-id="db3a9-117">Diagnostics Symbol Store</span></span>](../../../docs/framework/unmanaged-api/diagnostics/index.md)  
 <span data-ttu-id="db3a9-118">描述診斷符號儲存 API，其可讓編譯器產生供偵錯工具使用的符號資訊。</span><span class="sxs-lookup"><span data-stu-id="db3a9-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="db3a9-119">融合</span><span class="sxs-lookup"><span data-stu-id="db3a9-119">Fusion</span></span>](../../../docs/framework/unmanaged-api/fusion/index.md)  
 <span data-ttu-id="db3a9-120">描述融合 API，其可讓執行階段主機存取應用程式資源的屬性，以為應用程式找出這些資源的正確版本。</span><span class="sxs-lookup"><span data-stu-id="db3a9-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="db3a9-121">裝載</span><span class="sxs-lookup"><span data-stu-id="db3a9-121">Hosting</span></span>](../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="db3a9-122">描述裝載 API，其可讓 Unmanaged 主機將 CLR 整合至其應用程式。</span><span class="sxs-lookup"><span data-stu-id="db3a9-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="db3a9-123">中繼資料</span><span class="sxs-lookup"><span data-stu-id="db3a9-123">Metadata</span></span>](../../../docs/framework/unmanaged-api/metadata/index.md)  
 <span data-ttu-id="db3a9-124">描述中繼資料 API，其可讓編譯器之類的用戶端無需由 CLR 載入類型，即可產生或存取元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="db3a9-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="db3a9-125">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="db3a9-125">Profiling</span></span>](../../../docs/framework/unmanaged-api/profiling/index.md)  
 <span data-ttu-id="db3a9-126">描述分析 API，其可讓分析工具透過 CLR 監視程式的執行。</span><span class="sxs-lookup"><span data-stu-id="db3a9-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="db3a9-127">強式命名</span><span class="sxs-lookup"><span data-stu-id="db3a9-127">Strong Naming</span></span>](../../../docs/framework/unmanaged-api/strong-naming/index.md)  
 <span data-ttu-id="db3a9-128">描述強式命名 API，其可讓用戶端管理組件的強式命名簽署。</span><span class="sxs-lookup"><span data-stu-id="db3a9-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="db3a9-129">WMI 和效能計數器</span><span class="sxs-lookup"><span data-stu-id="db3a9-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="db3a9-130">說明將呼叫封裝到 Windows Management Instrumentation (WMI) 程式庫的 API。</span><span class="sxs-lookup"><span data-stu-id="db3a9-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="db3a9-131">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="db3a9-131">Tlbexp Helper Functions</span></span>](../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="db3a9-132">描述組件轉換至類型程式庫的程序期間，類型程式庫匯出工具 (Tlbexp.exe) 所使用的兩個 Helper 函式和介面。</span><span class="sxs-lookup"><span data-stu-id="db3a9-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="db3a9-133">相關章節</span><span class="sxs-lookup"><span data-stu-id="db3a9-133">Related Sections</span></span>  
 [<span data-ttu-id="db3a9-134">開發指南</span><span class="sxs-lookup"><span data-stu-id="db3a9-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
