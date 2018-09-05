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
ms.openlocfilehash: 955efad34f816cd0445c4ebdf120d8b614f0d351
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508518"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="35e0f-102">Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="35e0f-102">Unmanaged API Reference</span></span>
<span data-ttu-id="35e0f-103">本節包含與 Managed 程式碼相關之應用程式 (例如執行階段主機、編譯器、反組譯工具、模糊化工具、偵錯工具和分析工具) 可用的 Unmanaged API 的資訊。</span><span class="sxs-lookup"><span data-stu-id="35e0f-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35e0f-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="35e0f-104">In This Section</span></span>  
 [<span data-ttu-id="35e0f-105">一般資料類型</span><span class="sxs-lookup"><span data-stu-id="35e0f-105">Common Data Types</span></span>](../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="35e0f-106">列出使用的一般資料類型 (特別是用於 Unmanaged 分析及偵錯 API 中)。</span><span class="sxs-lookup"><span data-stu-id="35e0f-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="35e0f-107">ALink</span><span class="sxs-lookup"><span data-stu-id="35e0f-107">ALink</span></span>](../../../docs/framework/unmanaged-api/alink/index.md)  
 <span data-ttu-id="35e0f-108">描述支援建立 .NET Framework 組件及未繫結模組的 ALink API。</span><span class="sxs-lookup"><span data-stu-id="35e0f-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="35e0f-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="35e0f-109">Authenticode</span></span>](../../../docs/framework/unmanaged-api/authenticode/index.md)  
 <span data-ttu-id="35e0f-110">支援 Authenticode XrML 授權的建立及驗證模組。</span><span class="sxs-lookup"><span data-stu-id="35e0f-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="35e0f-111">常數</span><span class="sxs-lookup"><span data-stu-id="35e0f-111">Constants</span></span>](../../../docs/framework/unmanaged-api/constants-unmanaged-api-reference.md)  
 <span data-ttu-id="35e0f-112">描述定義於 CorSym.idl 中的常數。</span><span class="sxs-lookup"><span data-stu-id="35e0f-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 [<span data-ttu-id="35e0f-113">自訂介面屬性</span><span class="sxs-lookup"><span data-stu-id="35e0f-113">Custom Interface Attributes</span></span>](https://msdn.microsoft.com/library/940952f9-46ad-4a1a-920f-118dc0bdcd9f)  
 <span data-ttu-id="35e0f-114">描述元件物件模型 (COM) 自訂介面屬性。</span><span class="sxs-lookup"><span data-stu-id="35e0f-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="35e0f-115">偵錯</span><span class="sxs-lookup"><span data-stu-id="35e0f-115">Debugging</span></span>](../../../docs/framework/unmanaged-api/debugging/index.md)  
 <span data-ttu-id="35e0f-116">描述偵錯 API，其其可讓偵錯工具偵錯在 Common Language Runtime (CLR) 環境中執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="35e0f-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="35e0f-117">診斷符號存放區</span><span class="sxs-lookup"><span data-stu-id="35e0f-117">Diagnostics Symbol Store</span></span>](../../../docs/framework/unmanaged-api/diagnostics/index.md)  
 <span data-ttu-id="35e0f-118">描述診斷符號儲存 API，其可讓編譯器產生供偵錯工具使用的符號資訊。</span><span class="sxs-lookup"><span data-stu-id="35e0f-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="35e0f-119">融合</span><span class="sxs-lookup"><span data-stu-id="35e0f-119">Fusion</span></span>](../../../docs/framework/unmanaged-api/fusion/index.md)  
 <span data-ttu-id="35e0f-120">描述融合 API，其可讓執行階段主機存取應用程式資源的屬性，以為應用程式找出這些資源的正確版本。</span><span class="sxs-lookup"><span data-stu-id="35e0f-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="35e0f-121">裝載</span><span class="sxs-lookup"><span data-stu-id="35e0f-121">Hosting</span></span>](../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="35e0f-122">描述裝載 API，其可讓 Unmanaged 主機將 CLR 整合至其應用程式。</span><span class="sxs-lookup"><span data-stu-id="35e0f-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="35e0f-123">中繼資料</span><span class="sxs-lookup"><span data-stu-id="35e0f-123">Metadata</span></span>](../../../docs/framework/unmanaged-api/metadata/index.md)  
 <span data-ttu-id="35e0f-124">描述中繼資料 API，其可讓編譯器之類的用戶端無需由 CLR 載入類型，即可產生或存取元件的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="35e0f-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="35e0f-125">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="35e0f-125">Profiling</span></span>](../../../docs/framework/unmanaged-api/profiling/index.md)  
 <span data-ttu-id="35e0f-126">描述分析 API，其可讓分析工具透過 CLR 監視程式的執行。</span><span class="sxs-lookup"><span data-stu-id="35e0f-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="35e0f-127">強式命名</span><span class="sxs-lookup"><span data-stu-id="35e0f-127">Strong Naming</span></span>](../../../docs/framework/unmanaged-api/strong-naming/index.md)  
 <span data-ttu-id="35e0f-128">描述強式命名 API，其可讓用戶端管理組件的強式命名簽署。</span><span class="sxs-lookup"><span data-stu-id="35e0f-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="35e0f-129">WMI 和效能計數器</span><span class="sxs-lookup"><span data-stu-id="35e0f-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="35e0f-130">說明將呼叫封裝到 Windows Management Instrumentation (WMI) 程式庫的 API。</span><span class="sxs-lookup"><span data-stu-id="35e0f-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="35e0f-131">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="35e0f-131">Tlbexp Helper Functions</span></span>](../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="35e0f-132">描述組件轉換至類型程式庫的程序期間，類型程式庫匯出工具 (Tlbexp.exe) 所使用的兩個 Helper 函式和介面。</span><span class="sxs-lookup"><span data-stu-id="35e0f-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="35e0f-133">相關章節</span><span class="sxs-lookup"><span data-stu-id="35e0f-133">Related Sections</span></span>  
 [<span data-ttu-id="35e0f-134">開發指南</span><span class="sxs-lookup"><span data-stu-id="35e0f-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
  
 [<span data-ttu-id="35e0f-135">.NET Framework 的進階閱讀</span><span class="sxs-lookup"><span data-stu-id="35e0f-135">Advanced Reading for the .NET Framework</span></span>](https://msdn.microsoft.com/library/faae8083-fecb-4514-b133-b0a5a32a7c3c)
