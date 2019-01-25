---
title: ICorRuntimeHost 介面
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41dc37751e2dcf26eea887e84423179512c53614
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653511"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="871fe-102">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="871fe-102">ICorRuntimeHost Interface</span></span>
<span data-ttu-id="871fe-103">提供方法，讓主應用程式啟動，並明確地停止 common language runtime (CLR)，來建立及設定應用程式定義域，若要存取預設網域，並列舉處理序中執行的所有網域。</span><span class="sxs-lookup"><span data-stu-id="871fe-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="871fe-104">在.NET Framework 2.0 版中，此介面已被取代[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="871fe-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="871fe-105">方法</span><span class="sxs-lookup"><span data-stu-id="871fe-105">Methods</span></span>  
  
|<span data-ttu-id="871fe-106">方法</span><span class="sxs-lookup"><span data-stu-id="871fe-106">Method</span></span>|<span data-ttu-id="871fe-107">描述</span><span class="sxs-lookup"><span data-stu-id="871fe-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="871fe-108">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-108">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|<span data-ttu-id="871fe-109">將網域列舉值重設回網域清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="871fe-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="871fe-110">CreateDomain 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-110">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|<span data-ttu-id="871fe-111">建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="871fe-111">Creates an application domain.</span></span> <span data-ttu-id="871fe-112">呼叫端會收到類型的介面指標<xref:System._AppDomain>型別的執行個體<xref:System.AppDomain?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="871fe-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="871fe-113">CreateDomainEx 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-113">CreateDomainEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|<span data-ttu-id="871fe-114">建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="871fe-114">Creates an application domain.</span></span> <span data-ttu-id="871fe-115">這個方法可讓呼叫端傳遞 IAppDomainSetup 執行個體來設定傳回的其他功能<xref:System._AppDomain>執行個體。</span><span class="sxs-lookup"><span data-stu-id="871fe-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="871fe-116">CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-116">CreateDomainSetup Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="871fe-117">取得類型的介面指標`IAppDomainSetup`至<xref:System.AppDomainSetup>執行個體。</span><span class="sxs-lookup"><span data-stu-id="871fe-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="871fe-118">`IAppDomainSetup` 提供方法來設定應用程式定義域的層面，才能建立。</span><span class="sxs-lookup"><span data-stu-id="871fe-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="871fe-119">CreateEvidence 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-119">CreateEvidence Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|<span data-ttu-id="871fe-120">取得類型的介面指標<xref:System.Security.Principal.IIdentity>，可讓主應用程式建立安全性辨識項，要傳遞給[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或是[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)。</span><span class="sxs-lookup"><span data-stu-id="871fe-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="871fe-121">CreateLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-121">CreateLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="871fe-122">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="871fe-122">Do not use.</span></span>|  
|[<span data-ttu-id="871fe-123">CurrentDomain 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-123">CurrentDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|<span data-ttu-id="871fe-124">取得類型的介面指標<xref:System._AppDomain>，代表目前執行緒上所載入的網域。</span><span class="sxs-lookup"><span data-stu-id="871fe-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="871fe-125">DeleteLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-125">DeleteLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="871fe-126">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="871fe-126">Do not use.</span></span>|  
|[<span data-ttu-id="871fe-127">EnumDomains 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-127">EnumDomains Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|<span data-ttu-id="871fe-128">取得目前的處理序中的網域列舉值。</span><span class="sxs-lookup"><span data-stu-id="871fe-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="871fe-129">GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-129">GetConfiguration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="871fe-130">取得物件，可讓主機指定的 clr 的回撥設定。</span><span class="sxs-lookup"><span data-stu-id="871fe-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="871fe-131">GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-131">GetDefaultDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="871fe-132">取得類型的介面指標<xref:System._AppDomain>，代表為目前的處理序的預設網域。</span><span class="sxs-lookup"><span data-stu-id="871fe-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="871fe-133">LocksHeldByLogicalThread 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-133">LocksHeldByLogicalThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="871fe-134">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="871fe-134">Do not use.</span></span>|  
|[<span data-ttu-id="871fe-135">MapFile 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-135">MapFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|<span data-ttu-id="871fe-136">將指定的檔案對應到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="871fe-136">Maps the specified file into memory.</span></span> <span data-ttu-id="871fe-137">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="871fe-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="871fe-138">NextDomain 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-138">NextDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|<span data-ttu-id="871fe-139">取得列舉型別中的下一個網域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="871fe-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="871fe-140">Start 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-140">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|<span data-ttu-id="871fe-141">啟動 CLR。</span><span class="sxs-lookup"><span data-stu-id="871fe-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="871fe-142">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-142">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|<span data-ttu-id="871fe-143">停止目前的處理序的執行階段中的程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="871fe-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="871fe-144">SwitchInLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-144">SwitchInLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="871fe-145">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="871fe-145">Do not use.</span></span>|  
|[<span data-ttu-id="871fe-146">SwitchOutLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-146">SwitchOutLogicalThreadState Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="871fe-147">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="871fe-147">Do not use.</span></span>|  
|[<span data-ttu-id="871fe-148">UnloadDomain 方法</span><span class="sxs-lookup"><span data-stu-id="871fe-148">UnloadDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="871fe-149">卸載指定的應用程式定義域，從目前的處理序。</span><span class="sxs-lookup"><span data-stu-id="871fe-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="871fe-150">需求</span><span class="sxs-lookup"><span data-stu-id="871fe-150">Requirements</span></span>  
 <span data-ttu-id="871fe-151">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="871fe-151">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="871fe-152">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="871fe-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="871fe-153">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="871fe-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="871fe-154">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="871fe-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871fe-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="871fe-155">See also</span></span>
- <xref:System.AppDomain>
- [<span data-ttu-id="871fe-156">裝載</span><span class="sxs-lookup"><span data-stu-id="871fe-156">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [<span data-ttu-id="871fe-157">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="871fe-157">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="871fe-158">執行階段主應用程式</span><span class="sxs-lookup"><span data-stu-id="871fe-158">Runtime Hosts</span></span>](https://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)
- [<span data-ttu-id="871fe-159">裝載介面</span><span class="sxs-lookup"><span data-stu-id="871fe-159">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="871fe-160">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="871fe-160">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
