---
title: .NET Framework 4 和 4.5 中新增的 CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: 8484b47549f83795778420048d610e2d1626d87b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899724"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="141d3-102">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="141d3-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>
<span data-ttu-id="141d3-103">本節說明非受控主機可用來將 .NET Framework 4、.NET Framework 4.5 和更新版本中的 common language runtime （CLR）整合到其應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="141d3-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="141d3-104">這些介面會提供方法，讓主機設定並將執行時間載入進程中。</span><span class="sxs-lookup"><span data-stu-id="141d3-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="141d3-105">從 .NET Framework 4 開始，所有的裝載介面都具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="141d3-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="141d3-106">它們會使用存留期管理（`AddRef` 和 `Release`）、封裝（隱含內容）和 COM `QueryInterface`。</span><span class="sxs-lookup"><span data-stu-id="141d3-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="141d3-107">它們不會使用 COM 類型，例如 `BSTR`、`SAFEARRAY`或 `VARIANT`。</span><span class="sxs-lookup"><span data-stu-id="141d3-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="141d3-108">沒有使用[CoCreateInstance 函數](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的單元模型、匯總或登錄啟用。</span><span class="sxs-lookup"><span data-stu-id="141d3-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="141d3-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="141d3-109">In This Section</span></span>  
 [<span data-ttu-id="141d3-110">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-110">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="141d3-111">提供可檢查應用程式域記憶體和 CPU 使用量的方法。</span><span class="sxs-lookup"><span data-stu-id="141d3-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="141d3-112">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-112">ICLRDomainManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 <span data-ttu-id="141d3-113">可讓主機指定將用來初始化預設應用程式域的應用程式網域管理員，以及指定初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="141d3-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="141d3-114">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-114">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 <span data-ttu-id="141d3-115">提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法，可讓主機將垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限設定為大於 `DWORD`的值。</span><span class="sxs-lookup"><span data-stu-id="141d3-115">Provides the [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="141d3-116">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-116">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 <span data-ttu-id="141d3-117">提供的方法會傳回 CLR 的特定版本、列出所有已安裝的 CLRs、列出所有內含式執行時間、傳回啟用介面，以及探索用來編譯元件的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="141d3-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="141d3-118">ICLRMetaHostPolicy 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-118">ICLRMetaHostPolicy Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="141d3-119">提供[GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法，以根據原則準則、managed 元件、版本和設定檔來提供 CLR 介面。</span><span class="sxs-lookup"><span data-stu-id="141d3-119">Provides the [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="141d3-120">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-120">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 <span data-ttu-id="141d3-121">提供傳回特定執行時間相關資訊的方法，包括版本、目錄和載入狀態。</span><span class="sxs-lookup"><span data-stu-id="141d3-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="141d3-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 <span data-ttu-id="141d3-123">提供基本的全域靜態函式，以強式名稱簽署元件。</span><span class="sxs-lookup"><span data-stu-id="141d3-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="141d3-124">所有的[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)方法都會傳回標準 COM hresult。</span><span class="sxs-lookup"><span data-stu-id="141d3-124">All the [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="141d3-125">ICLRStrongName2 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-125">ICLRStrongName2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 <span data-ttu-id="141d3-126">提供使用 SHA-2 安全雜湊演算法（SHA-256、SHA-384 和 SHA-512）群組建立強式名稱的功能。</span><span class="sxs-lookup"><span data-stu-id="141d3-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="141d3-127">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="141d3-127">ICLRTask2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 <span data-ttu-id="141d3-128">提供[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)的所有功能;此外，也提供可讓執行緒中止在目前線程上延遲的方法。</span><span class="sxs-lookup"><span data-stu-id="141d3-128">Provides all the functionality of the [ICLRTask Interface](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="141d3-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="141d3-129">Related Sections</span></span>  
 [<span data-ttu-id="141d3-130">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="141d3-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="141d3-131">描述 .NET Framework 版本1.0 和1.1 所提供的主控介面。</span><span class="sxs-lookup"><span data-stu-id="141d3-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="141d3-132">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="141d3-132">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="141d3-133">描述 .NET Framework 版本2.0、3.0 和3.5 所提供的主控介面。</span><span class="sxs-lookup"><span data-stu-id="141d3-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="141d3-134">裝載</span><span class="sxs-lookup"><span data-stu-id="141d3-134">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="141d3-135">引進了 .NET Framework 中的裝載。</span><span class="sxs-lookup"><span data-stu-id="141d3-135">Introduces hosting in the .NET Framework.</span></span>
