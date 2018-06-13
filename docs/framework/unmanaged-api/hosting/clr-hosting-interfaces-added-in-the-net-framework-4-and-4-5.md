---
title: .NET Framework 4 和 4.5 中新增的 CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 982f5780a40dd8cbce02ec33f7e6f77589cd3717
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435792"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="526e2-102">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="526e2-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="526e2-103">本節說明 unmanaged 介面主機可用於將 common language runtime (CLR) 整合在[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]， [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，及至其應用程式的更新版本。</span><span class="sxs-lookup"><span data-stu-id="526e2-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], and later versions into their applications.</span></span> <span data-ttu-id="526e2-104">這些介面提供主應用程式設定和執行階段載入處理序的方法。</span><span class="sxs-lookup"><span data-stu-id="526e2-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="526e2-105">從開始[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]、 所有裝載介面具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="526e2-105">Starting with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], all hosting interfaces have the following characteristics:</span></span>  
  
-   <span data-ttu-id="526e2-106">他們使用生命週期管理 (`AddRef`和`Release`)，封裝 （隱含的內容） 和`QueryInterface`從 com 存取。</span><span class="sxs-lookup"><span data-stu-id="526e2-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
-   <span data-ttu-id="526e2-107">那里請不要使用 COM 類型例如`BSTR`， `SAFEARRAY`，或`VARIANT`。</span><span class="sxs-lookup"><span data-stu-id="526e2-107">There do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
-   <span data-ttu-id="526e2-108">使用沒有 apartment 模型、 彙總，或登錄啟動[CoCreateInstance 函式](http://go.microsoft.com/fwlink/?LinkId=142894)。</span><span class="sxs-lookup"><span data-stu-id="526e2-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](http://go.microsoft.com/fwlink/?LinkId=142894).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="526e2-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="526e2-109">In This Section</span></span>  
 [<span data-ttu-id="526e2-110">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="526e2-111">提供方法，檢查應用程式定義域的記憶體和 CPU 使用量。</span><span class="sxs-lookup"><span data-stu-id="526e2-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="526e2-112">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="526e2-113">可讓主應用程式指定將用於初始化預設應用程式定義域，並指定初始化屬性的應用程式定義域管理員。</span><span class="sxs-lookup"><span data-stu-id="526e2-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="526e2-114">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="526e2-115">提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法，可讓主應用程式設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大值大於`DWORD`。</span><span class="sxs-lookup"><span data-stu-id="526e2-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="526e2-116">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="526e2-117">提供方法，傳回特定版本的 CLR，列出所有已安裝的 Clr、 列出所有的同處理序執行階段，傳回啟用介面，而探索用來編譯組件的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="526e2-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="526e2-118">ICLRMetaHostPolicy 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="526e2-119">提供[GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)提供 CLR 介面的方法為基礎原則的條件、 managed 組件、 版本和組態檔。</span><span class="sxs-lookup"><span data-stu-id="526e2-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="526e2-120">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="526e2-121">提供方法，傳回特定的執行階段，包括版本、 目錄和負載狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="526e2-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="526e2-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="526e2-123">提供基本的全域靜態函式簽署組件具有強式名稱。</span><span class="sxs-lookup"><span data-stu-id="526e2-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="526e2-124">所有[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)方法會傳回標準的 COM Hresult。</span><span class="sxs-lookup"><span data-stu-id="526e2-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="526e2-125">ICLRStrongName2 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="526e2-126">提供建立強式名稱使用 sha-2 群組 （sha-256、 sha-384 和 sha-512） 的安全雜湊演算法的能力。</span><span class="sxs-lookup"><span data-stu-id="526e2-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="526e2-127">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="526e2-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="526e2-128">提供的所有功能[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); 此外，都提供方法，讓執行緒中止目前的執行緒上延遲。</span><span class="sxs-lookup"><span data-stu-id="526e2-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="526e2-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="526e2-129">Related Sections</span></span>  
 [<span data-ttu-id="526e2-130">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="526e2-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="526e2-131">描述裝載隨附.NET framework 1.0 和 1.1 版的介面。</span><span class="sxs-lookup"><span data-stu-id="526e2-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="526e2-132">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="526e2-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="526e2-133">描述.NET framework 2.0、 3.0 和 3.5 所隨附的裝載介面。</span><span class="sxs-lookup"><span data-stu-id="526e2-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="526e2-134">裝載</span><span class="sxs-lookup"><span data-stu-id="526e2-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="526e2-135">導入了.NET Framework 中的裝載。</span><span class="sxs-lookup"><span data-stu-id="526e2-135">Introduces hosting in the .NET Framework.</span></span>
