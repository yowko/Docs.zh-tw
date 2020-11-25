---
title: .NET Framework 4 和 4.5 中新增的 CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: 6ee3b8cdf348a5eade3903e2d26b4f9b93886305
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706810"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a><span data-ttu-id="155bc-102">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="155bc-102">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>

<span data-ttu-id="155bc-103">本節描述非受控主機可用來將 .NET Framework 4、.NET Framework 4.5 和更新版本中的 common language runtime (CLR) 整合至其應用程式的介面。</span><span class="sxs-lookup"><span data-stu-id="155bc-103">This section describes interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) in the .NET Framework 4, .NET Framework 4.5, and later versions into their applications.</span></span> <span data-ttu-id="155bc-104">這些介面會提供方法，讓主機在進程中設定和載入執行時間。</span><span class="sxs-lookup"><span data-stu-id="155bc-104">These interfaces provide methods for a host to configure and load the runtime into a process.</span></span>  
  
 <span data-ttu-id="155bc-105">從 .NET Framework 4 開始，所有裝載介面都有下列特性：</span><span class="sxs-lookup"><span data-stu-id="155bc-105">Starting with the .NET Framework 4, all hosting interfaces have the following characteristics:</span></span>  
  
- <span data-ttu-id="155bc-106">它們使用存留期管理 (`AddRef` 和 `Release`) ，封裝 (隱含內容) 和 `QueryInterface` COM。</span><span class="sxs-lookup"><span data-stu-id="155bc-106">They use lifetime management (`AddRef` and `Release`), encapsulation (implicit context) and `QueryInterface` from COM.</span></span>  
  
- <span data-ttu-id="155bc-107">它們不會使用、或等 COM `BSTR` 類型 `SAFEARRAY` `VARIANT` 。</span><span class="sxs-lookup"><span data-stu-id="155bc-107">They do not use COM types such as `BSTR`, `SAFEARRAY`, or `VARIANT`.</span></span>  
  
- <span data-ttu-id="155bc-108">沒有使用 [CoCreateInstance 函數](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的單元模型、匯總或登錄啟用。</span><span class="sxs-lookup"><span data-stu-id="155bc-108">There are no apartment models, aggregation, or registry activation that use the [CoCreateInstance function](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="155bc-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="155bc-109">In This Section</span></span>  

 [<span data-ttu-id="155bc-110">ICLRAppDomainResourceMonitor 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-110">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)  
 <span data-ttu-id="155bc-111">提供可檢查應用程式域的記憶體和 CPU 使用量的方法。</span><span class="sxs-lookup"><span data-stu-id="155bc-111">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
 [<span data-ttu-id="155bc-112">ICLRDomainManager 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-112">ICLRDomainManager Interface</span></span>](iclrdomainmanager-interface.md)  
 <span data-ttu-id="155bc-113">讓主機指定將用來初始化預設應用程式域的應用程式域管理員，以及指定初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="155bc-113">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
 [<span data-ttu-id="155bc-114">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-114">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)  
 <span data-ttu-id="155bc-115">提供 [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) 方法，此方法可讓主控制項將垃圾收集區段的大小以及垃圾收集系統層代0的大小上限設定為大於 `DWORD` 的值。</span><span class="sxs-lookup"><span data-stu-id="155bc-115">Provides the [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) method, which enables a host to set the size of the garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than `DWORD`.</span></span>  
  
 [<span data-ttu-id="155bc-116">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-116">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)  
 <span data-ttu-id="155bc-117">提供方法來傳回特定版本的 CLR、列出所有已安裝的 Clr、列出所有同進程執行時間、傳回啟用介面，以及探索用來編譯元件的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="155bc-117">Provides methods that return a specific version of the CLR, list all installed CLRs, list all in-process runtimes, return the activation interface, and discover the CLR version used to compile an assembly.</span></span>  
  
 [<span data-ttu-id="155bc-118">ICLRMetaHostPolicy 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-118">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)  
 <span data-ttu-id="155bc-119">提供 [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) 方法，此方法會根據原則準則、managed 元件、版本和設定檔提供 CLR 介面。</span><span class="sxs-lookup"><span data-stu-id="155bc-119">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method that provides a CLR interface based on policy criteria, managed assembly, version, and configuration file.</span></span>  
  
 [<span data-ttu-id="155bc-120">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-120">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)  
 <span data-ttu-id="155bc-121">提供方法來傳回特定執行時間的相關資訊，包括版本、目錄和載入狀態。</span><span class="sxs-lookup"><span data-stu-id="155bc-121">Provides methods that return information about a specific runtime, including version, directory, and load status.</span></span>  
  
 [<span data-ttu-id="155bc-122">ICLRStrongName 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)  
 <span data-ttu-id="155bc-123">提供基本的全域靜態函式來簽署具有強式名稱的元件。</span><span class="sxs-lookup"><span data-stu-id="155bc-123">Provides basic global static functions for signing assemblies with strong names.</span></span> <span data-ttu-id="155bc-124">所有 [ICLRStrongName](iclrstrongname-interface.md) 方法都會傳回標準 COM hresult。</span><span class="sxs-lookup"><span data-stu-id="155bc-124">All the [ICLRStrongName](iclrstrongname-interface.md) methods return standard COM HRESULTs.</span></span>  
  
 [<span data-ttu-id="155bc-125">ICLRStrongName2 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-125">ICLRStrongName2 Interface</span></span>](iclrstrongname2-interface.md)  
 <span data-ttu-id="155bc-126">提供使用安全雜湊演算法的 SHA-1 群組來建立強式名稱的功能， (SHA-256、SHA-384 和 SHA-512) 。</span><span class="sxs-lookup"><span data-stu-id="155bc-126">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
 [<span data-ttu-id="155bc-127">ICLRTask2 介面</span><span class="sxs-lookup"><span data-stu-id="155bc-127">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)  
 <span data-ttu-id="155bc-128">提供 [ICLRTask 介面](iclrtask-interface.md)的所有功能;此外，還提供可讓執行緒中止在目前線程上延遲的方法。</span><span class="sxs-lookup"><span data-stu-id="155bc-128">Provides all the functionality of the [ICLRTask Interface](iclrtask-interface.md); in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="155bc-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="155bc-129">Related Sections</span></span>  

 [<span data-ttu-id="155bc-130">已被取代的 CLR 裝載介面和 Coclass</span><span class="sxs-lookup"><span data-stu-id="155bc-130">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="155bc-131">描述 .NET Framework 版本1.0 和1.1 提供的裝載介面。</span><span class="sxs-lookup"><span data-stu-id="155bc-131">Describes the hosting interfaces provided with the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="155bc-132">CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="155bc-132">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="155bc-133">描述 .NET Framework 版本2.0、3.0 和3.5 所提供的裝載介面。</span><span class="sxs-lookup"><span data-stu-id="155bc-133">Describes the hosting interfaces provided with the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
 [<span data-ttu-id="155bc-134">裝載</span><span class="sxs-lookup"><span data-stu-id="155bc-134">Hosting</span></span>](index.md)  
 <span data-ttu-id="155bc-135">介紹 .NET Framework 中的裝載。</span><span class="sxs-lookup"><span data-stu-id="155bc-135">Introduces hosting in the .NET Framework.</span></span>
