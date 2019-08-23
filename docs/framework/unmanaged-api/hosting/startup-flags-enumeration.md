---
title: STARTUP_FLAGS 列舉
ms.date: 03/30/2017
api_name:
- STARTUP_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- STARTUP_FLAGS
helpviewer_keywords:
- STARTUP_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 4f043594-0c45-4bc6-988e-a6793f0d8d06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f39608b39be7d5c25b916fb20877aa73d6e5a8bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916225"
---
# <a name="startup_flags-enumeration"></a><span data-ttu-id="4a583-102">STARTUP_FLAGS 列舉</span><span class="sxs-lookup"><span data-stu-id="4a583-102">STARTUP_FLAGS Enumeration</span></span>
<span data-ttu-id="4a583-103">包含值, 表示 common language runtime (CLR) 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="4a583-103">Contains values that indicate the startup behavior of the common language runtime (CLR).</span></span> <span data-ttu-id="4a583-104">根據預設, 垃圾收集是非並行的, 而且只有基類庫會載入至網域中立區域。</span><span class="sxs-lookup"><span data-stu-id="4a583-104">By default, garbage collection is non-concurrent, and only the base class library is loaded into the domain-neutral area.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a583-105">語法</span><span class="sxs-lookup"><span data-stu-id="4a583-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    STARTUP_CONCURRENT_GC                         = 0x1,  
    STARTUP_LOADER_OPTIMIZATION_MASK              = 0x3<<1,  
    STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN     = 0x1<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN      = 0x2<<1,  
    STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST = 0x3<<1,  
  
    STARTUP_LOADER_SAFEMODE                       = 0x10,  
    STARTUP_LOADER_SETPREFERENCE                  = 0x100,  
  
    STARTUP_SERVER_GC                             = 0x1000,  
    STARTUP_HOARD_GC_VM                           = 0x2000,  
  
    STARTUP_SINGLE_VERSION_HOSTING_INTERFACE      = 0x4000,  
    STARTUP_LEGACY_IMPERSONATION                  = 0x10000,  
    STARTUP_DISABLE_COMMITTHREADSTACK             = 0x20000,  
    STARTUP_ALWAYSFLOW_IMPERSONATION              = 0x40000,  
    STARTUP_TRIM_GC_COMMIT                        = 0x80000,  
  
    STARTUP_ETW                                   = 0x100000,  
    STARTUP_ARM                                   = 0x400000  
} STARTUP_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="4a583-106">成員</span><span class="sxs-lookup"><span data-stu-id="4a583-106">Members</span></span>  
  
|<span data-ttu-id="4a583-107">成員</span><span class="sxs-lookup"><span data-stu-id="4a583-107">Member</span></span>|<span data-ttu-id="4a583-108">描述</span><span class="sxs-lookup"><span data-stu-id="4a583-108">Description</span></span>|  
|------------|-----------------|  
|`STARTUP_CONCURRENT_GC`|<span data-ttu-id="4a583-109">指定應該使用並行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="4a583-109">Specifies that concurrent garbage collection should be used.</span></span> <span data-ttu-id="4a583-110">如果呼叫者要求在單處理器機器上進行伺服器組建和並行垃圾收集, 則會改為執行工作站組建和非並行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="4a583-110">If the caller asks for the server build and concurrent garbage collection on a single-processor machine, the workstation build and non-concurrent garbage collection are run instead.</span></span> <span data-ttu-id="4a583-111">**注意：** 在執行 Intel Itanium 架構 (先前稱為 IA-64) 的64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="4a583-111">**Note:**  Concurrent garbage collection is not supported in applications that are running the WOW64 x86 emulator on 64-bit systems that implement the Intel Itanium architecture (formerly called IA-64).</span></span> <span data-ttu-id="4a583-112">如需在64位 Windows 系統上使用 WOW64 的詳細資訊, 請參閱執行[32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。</span><span class="sxs-lookup"><span data-stu-id="4a583-112">For more information about using WOW64 on 64-bit Windows systems, see [Running 32-bit Applications](/windows/desktop/WinProg64/running-32-bit-applications).</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MASK`|<span data-ttu-id="4a583-113">指定應該進行載入器優化。</span><span class="sxs-lookup"><span data-stu-id="4a583-113">Specifies that loader optimization shall occur.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`|<span data-ttu-id="4a583-114">指定不將任何元件載入為網域中性。</span><span class="sxs-lookup"><span data-stu-id="4a583-114">Specifies that no assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`|<span data-ttu-id="4a583-115">指定將所有元件載入為網域中性。</span><span class="sxs-lookup"><span data-stu-id="4a583-115">Specifies that all assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`|<span data-ttu-id="4a583-116">指定將所有強式名稱的元件載入為網域中性。</span><span class="sxs-lookup"><span data-stu-id="4a583-116">Specifies that all strong-named assemblies are loaded as domain-neutral.</span></span>|  
|`STARTUP_LOADER_SAFEMODE`|<span data-ttu-id="4a583-117">指定 CLR 版本原則將不會套用至傳入的版本。</span><span class="sxs-lookup"><span data-stu-id="4a583-117">Specifies that CLR version policy will not be applied to the version passed in.</span></span> <span data-ttu-id="4a583-118">將會載入指定之 CLR 的確切版本。</span><span class="sxs-lookup"><span data-stu-id="4a583-118">The exact version specified of the CLR will be loaded.</span></span> <span data-ttu-id="4a583-119">填充碼不會評估原則來判斷最新的相容版本。</span><span class="sxs-lookup"><span data-stu-id="4a583-119">The shim does not evaluate policy to determine the latest compatible version.</span></span>|  
|`STARTUP_LOADER_SETPREFERENCE`|<span data-ttu-id="4a583-120">指定慣用的執行時間將會設定, 但不會實際啟動。</span><span class="sxs-lookup"><span data-stu-id="4a583-120">Specifies that the preferred runtime will be set, but not actually started.</span></span>|  
|`STARTUP_SERVER_GC`|<span data-ttu-id="4a583-121">指定將使用伺服器垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="4a583-121">Specifies that the server garbage collection will be used.</span></span>|  
|`STARTUP_HOARD_GC_VM`|<span data-ttu-id="4a583-122">指定垃圾收集會保留使用的虛擬位址。</span><span class="sxs-lookup"><span data-stu-id="4a583-122">Specifies that garbage collection will keep the virtual address used.</span></span>|  
|`STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`|<span data-ttu-id="4a583-123">指定不允許混用主控介面。</span><span class="sxs-lookup"><span data-stu-id="4a583-123">Specifies that mixing a hosting interface will not be allowed.</span></span>|  
|`STARTUP_LEGACY_IMPERSONATION`|<span data-ttu-id="4a583-124">指定模擬預設不應流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="4a583-124">Specifies that impersonation should not flow across asynchronous points by default.</span></span>|  
|`STARTUP_DISABLE_COMMITTHREADSTACK`|<span data-ttu-id="4a583-125">指定當執行緒開始執行時, 不應認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="4a583-125">Specifies that the full thread stack should not be committed when the thread starts running.</span></span>|  
|`STARTUP_ALWAYSFLOW_IMPERSONATION`|<span data-ttu-id="4a583-126">指定透過平台叫用達成的 managed 模擬和模擬會流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="4a583-126">Specifies that managed impersonations and impersonations achieved through platform invoke will flow across asynchronous points.</span></span> <span data-ttu-id="4a583-127">根據預設, 只有受管理的模擬會流經非同步點。</span><span class="sxs-lookup"><span data-stu-id="4a583-127">By default, only managed impersonations will flow across asynchronous points.</span></span>|  
|`STARTUP_TRIM_GC_COMMIT`|<span data-ttu-id="4a583-128">指定當系統記憶體不足時, 垃圾收集會使用較少的認可空間。</span><span class="sxs-lookup"><span data-stu-id="4a583-128">Specifies that garbage collection will use less committed space when system memory is low.</span></span> <span data-ttu-id="4a583-129">請`gcTrimCommitOnLowMemory`參閱[共用 Web 裝載的優化](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md)。</span><span class="sxs-lookup"><span data-stu-id="4a583-129">See `gcTrimCommitOnLowMemory` in [Optimization for Shared Web Hosting](../../../standard/garbage-collection/optimization-for-shared-web-hosting.md).</span></span>|  
|`STARTUP_ETW`|<span data-ttu-id="4a583-130">指定針對 common language runtime 事件啟用 Windows 事件追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="4a583-130">Specifies that event tracing for Windows (ETW) is enabled for common language runtime events.</span></span> <span data-ttu-id="4a583-131">從 Windows Vista 開始, 一律會啟用事件追蹤, 因此此旗標沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="4a583-131">Beginning with Windows Vista, event tracing is always enabled, so this flag has no effect.</span></span> <span data-ttu-id="4a583-132">請參閱[控制 .NET Framework 記錄](../../../../docs/framework/performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="4a583-132">See [Controlling .NET Framework Logging](../../../../docs/framework/performance/controlling-logging.md).</span></span>|  
|`STARTUP_ARM`|<span data-ttu-id="4a583-133">指定啟用應用程式域資源監視。</span><span class="sxs-lookup"><span data-stu-id="4a583-133">Specifies that application domain resource monitoring is enabled.</span></span> <span data-ttu-id="4a583-134">請參閱[ \<屬性和appDomainResourceMonitoring > 元素。](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4a583-134">See the <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> property and [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a583-135">需求</span><span class="sxs-lookup"><span data-stu-id="4a583-135">Requirements</span></span>  
 <span data-ttu-id="4a583-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4a583-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a583-137">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a583-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a583-138">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a583-138">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a583-139">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a583-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a583-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a583-140">See also</span></span>

- [<span data-ttu-id="4a583-141">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="4a583-141">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
