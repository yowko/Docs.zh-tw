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
ms.openlocfilehash: 4b8018bb84dea08987d91f351b1ab0d9f3b48c56
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503896"
---
# <a name="icorruntimehost-interface"></a><span data-ttu-id="d341d-102">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="d341d-102">ICorRuntimeHost Interface</span></span>
<span data-ttu-id="d341d-103">提供的方法可讓主機明確啟動和停止 common language runtime （CLR）、建立和設定應用程式域、存取預設網域，以及列舉在進程中執行的所有網域。</span><span class="sxs-lookup"><span data-stu-id="d341d-103">Provides methods that enable the host to start and stop the common language runtime (CLR) explicitly, to create and configure application domains, to access the default domain, and to enumerate all domains running in the process.</span></span>  
  
 <span data-ttu-id="d341d-104">在 .NET Framework 版本2.0 中，此介面已由[ICLRRuntimeHost](iclrruntimehost-interface.md)所取代。</span><span class="sxs-lookup"><span data-stu-id="d341d-104">In the .NET Framework version 2.0, this interface is superceded by [ICLRRuntimeHost](iclrruntimehost-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d341d-105">方法</span><span class="sxs-lookup"><span data-stu-id="d341d-105">Methods</span></span>  
  
|<span data-ttu-id="d341d-106">方法</span><span class="sxs-lookup"><span data-stu-id="d341d-106">Method</span></span>|<span data-ttu-id="d341d-107">描述</span><span class="sxs-lookup"><span data-stu-id="d341d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d341d-108">CloseEnum 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-108">CloseEnum Method</span></span>](icorruntimehost-closeenum-method.md)|<span data-ttu-id="d341d-109">將網域列舉值重設回定義域清單的開頭。</span><span class="sxs-lookup"><span data-stu-id="d341d-109">Resets a domain enumerator back to the beginning of the domain list.</span></span>|  
|[<span data-ttu-id="d341d-110">CreateDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-110">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)|<span data-ttu-id="d341d-111">建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="d341d-111">Creates an application domain.</span></span> <span data-ttu-id="d341d-112">呼叫端會接收類型的介面指標 <xref:System._AppDomain> ，類型為的實例 <xref:System.AppDomain?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d341d-112">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>|  
|[<span data-ttu-id="d341d-113">CreateDomainEx 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-113">CreateDomainEx Method</span></span>](icorruntimehost-createdomainex-method.md)|<span data-ttu-id="d341d-114">建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="d341d-114">Creates an application domain.</span></span> <span data-ttu-id="d341d-115">這個方法可讓呼叫端傳遞 IAppDomainSetup 實例，以設定傳回之實例的其他功能 <xref:System._AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="d341d-115">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>|  
|[<span data-ttu-id="d341d-116">CreateDomainSetup 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-116">CreateDomainSetup Method</span></span>](icorruntimehost-createdomainsetup-method.md)|<span data-ttu-id="d341d-117">取得實例之類型的介面指標 `IAppDomainSetup` <xref:System.AppDomainSetup> 。</span><span class="sxs-lookup"><span data-stu-id="d341d-117">Gets an interface pointer of type `IAppDomainSetup` to an <xref:System.AppDomainSetup> instance.</span></span> <span data-ttu-id="d341d-118">`IAppDomainSetup`提供方法來設定應用程式域的各個層面，然後再建立。</span><span class="sxs-lookup"><span data-stu-id="d341d-118">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>|  
|[<span data-ttu-id="d341d-119">CreateEvidence 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-119">CreateEvidence Method</span></span>](icorruntimehost-createevidence-method.md)|<span data-ttu-id="d341d-120">取得類型的介面指標 <xref:System.Security.Principal.IIdentity> ，可讓主機建立要傳遞至[CreateDomain](icorruntimehost-createdomain-method.md)或[CreateDomainEx](icorruntimehost-createdomainex-method.md)的安全性辨識項。</span><span class="sxs-lookup"><span data-stu-id="d341d-120">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity>, which allows the host to create security evidence to pass to [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md).</span></span>|  
|[<span data-ttu-id="d341d-121">CreateLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-121">CreateLogicalThreadState Method</span></span>](icorruntimehost-createlogicalthreadstate-method.md)|<span data-ttu-id="d341d-122">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="d341d-122">Do not use.</span></span>|  
|[<span data-ttu-id="d341d-123">CurrentDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-123">CurrentDomain Method</span></span>](icorruntimehost-currentdomain-method.md)|<span data-ttu-id="d341d-124">取得類型的介面指標 <xref:System._AppDomain> ，表示在目前線程上載入的網域。</span><span class="sxs-lookup"><span data-stu-id="d341d-124">Gets an interface pointer of type <xref:System._AppDomain> that represents the domain loaded on the current thread.</span></span>|  
|[<span data-ttu-id="d341d-125">DeleteLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-125">DeleteLogicalThreadState Method</span></span>](icorruntimehost-deletelogicalthreadstate-method.md)|<span data-ttu-id="d341d-126">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="d341d-126">Do not use.</span></span>|  
|[<span data-ttu-id="d341d-127">EnumDomains 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-127">EnumDomains Method</span></span>](icorruntimehost-enumdomains-method.md)|<span data-ttu-id="d341d-128">取得目前進程中之定義域的列舉值。</span><span class="sxs-lookup"><span data-stu-id="d341d-128">Gets an enumerator for the domains in the current process.</span></span>|  
|[<span data-ttu-id="d341d-129">GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-129">GetConfiguration Method</span></span>](icorruntimehost-getconfiguration-method.md)|<span data-ttu-id="d341d-130">取得物件，讓主機指定 CLR 的回呼設定。</span><span class="sxs-lookup"><span data-stu-id="d341d-130">Gets an object that allows the host to specify the callback configuration of the CLR.</span></span>|  
|[<span data-ttu-id="d341d-131">GetDefaultDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-131">GetDefaultDomain Method</span></span>](icorruntimehost-getdefaultdomain-method.md)|<span data-ttu-id="d341d-132">取得類型的介面指標 <xref:System._AppDomain> ，表示目前進程的預設網域。</span><span class="sxs-lookup"><span data-stu-id="d341d-132">Gets an interface pointer of type <xref:System._AppDomain> that represents the default domain for the current process.</span></span>|  
|[<span data-ttu-id="d341d-133">LocksHeldByLogicalThread 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-133">LocksHeldByLogicalThread Method</span></span>](icorruntimehost-locksheldbylogicalthread-method.md)|<span data-ttu-id="d341d-134">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="d341d-134">Do not use.</span></span>|  
|[<span data-ttu-id="d341d-135">MapFile 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-135">MapFile Method</span></span>](icorruntimehost-mapfile-method.md)|<span data-ttu-id="d341d-136">將指定的檔案對應到記憶體中。</span><span class="sxs-lookup"><span data-stu-id="d341d-136">Maps the specified file into memory.</span></span> <span data-ttu-id="d341d-137">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="d341d-137">This method is obsolete.</span></span>|  
|[<span data-ttu-id="d341d-138">NextDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-138">NextDomain Method</span></span>](icorruntimehost-nextdomain-method.md)|<span data-ttu-id="d341d-139">取得列舉中下一個網域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="d341d-139">Gets an interface pointer to the next domain in the enumeration.</span></span>|  
|[<span data-ttu-id="d341d-140">Start 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-140">Start Method</span></span>](icorruntimehost-start-method.md)|<span data-ttu-id="d341d-141">啟動 CLR。</span><span class="sxs-lookup"><span data-stu-id="d341d-141">Starts the CLR.</span></span>|  
|[<span data-ttu-id="d341d-142">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-142">Stop Method</span></span>](icorruntimehost-stop-method.md)|<span data-ttu-id="d341d-143">在執行時間中停止執行目前進程的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d341d-143">Stops the execution of code in the runtime for the current process.</span></span>|  
|[<span data-ttu-id="d341d-144">SwitchInLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-144">SwitchInLogicalThreadState Method</span></span>](icorruntimehost-switchinlogicalthreadstate-method.md)|<span data-ttu-id="d341d-145">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="d341d-145">Do not use.</span></span>|  
|[<span data-ttu-id="d341d-146">SwitchOutLogicalThreadState 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-146">SwitchOutLogicalThreadState Method</span></span>](icorruntimehost-switchoutlogicalthreadstate-method.md)|<span data-ttu-id="d341d-147">請勿使用。</span><span class="sxs-lookup"><span data-stu-id="d341d-147">Do not use.</span></span>|  
|[<span data-ttu-id="d341d-148">UnloadDomain 方法</span><span class="sxs-lookup"><span data-stu-id="d341d-148">UnloadDomain Method</span></span>](icorruntimehost-unloaddomain-method.md)|<span data-ttu-id="d341d-149">從目前的進程中卸載指定的應用程式域。</span><span class="sxs-lookup"><span data-stu-id="d341d-149">Unloads the specified application domain from the current process.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d341d-150">規格需求</span><span class="sxs-lookup"><span data-stu-id="d341d-150">Requirements</span></span>  
 <span data-ttu-id="d341d-151">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d341d-151">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d341d-152">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d341d-152">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d341d-153">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d341d-153">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d341d-154">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="d341d-154">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d341d-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d341d-155">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="d341d-156">Hosting</span><span class="sxs-lookup"><span data-stu-id="d341d-156">Hosting</span></span>](index.md)
- [<span data-ttu-id="d341d-157">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="d341d-157">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- <span data-ttu-id="d341d-158">[執行階段主應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d341d-158">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
- [<span data-ttu-id="d341d-159">裝載介面</span><span class="sxs-lookup"><span data-stu-id="d341d-159">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="d341d-160">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="d341d-160">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
