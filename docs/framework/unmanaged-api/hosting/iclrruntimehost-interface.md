---
title: ICLRRuntimeHost 介面
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f159c0b57f2087b608fac8cbc9b9c64ceb063a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965997"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="2b41b-102">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="2b41b-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="2b41b-103">提供的功能類似于 .NET Framework 第1版所提供的[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)介面, 但有下列變更:</span><span class="sxs-lookup"><span data-stu-id="2b41b-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="2b41b-104">新增[SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)方法以設定主控制項介面。</span><span class="sxs-lookup"><span data-stu-id="2b41b-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="2b41b-105">省略所提供`ICorRuntimeHost`的一些方法。</span><span class="sxs-lookup"><span data-stu-id="2b41b-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b41b-106">方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-106">Methods</span></span>  
  
|<span data-ttu-id="2b41b-107">方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-107">Method</span></span>|<span data-ttu-id="2b41b-108">描述</span><span class="sxs-lookup"><span data-stu-id="2b41b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b41b-109">ExecuteApplication 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="2b41b-110">在以資訊清單為基礎的 ClickOnce 部署案例中使用, 以指定要在新的網域中啟動的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2b41b-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="2b41b-111">ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="2b41b-112">指定要<xref:System.AppDomain>在其中執行指定 managed 程式碼的。</span><span class="sxs-lookup"><span data-stu-id="2b41b-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="2b41b-113">ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="2b41b-114">在指定的元件中, 叫用指定之類型的指定方法。</span><span class="sxs-lookup"><span data-stu-id="2b41b-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="2b41b-115">GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="2b41b-116">取得類型[ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)的介面指標, 可供裝載用來自訂 common language RUNTIME (CLR) 的各個層面。</span><span class="sxs-lookup"><span data-stu-id="2b41b-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="2b41b-117">GetCurrentAppDomainId 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="2b41b-118">取得目前正在執行之的<xref:System.AppDomain>數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="2b41b-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="2b41b-119">SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="2b41b-120">設定主控制項介面。</span><span class="sxs-lookup"><span data-stu-id="2b41b-120">Sets the host control interface.</span></span> <span data-ttu-id="2b41b-121">`SetHostControl` 呼叫`Start`之前, 您必須先呼叫。</span><span class="sxs-lookup"><span data-stu-id="2b41b-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="2b41b-122">Start 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="2b41b-123">將 CLR 初始化為進程。</span><span class="sxs-lookup"><span data-stu-id="2b41b-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="2b41b-124">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="2b41b-125">停止執行時間的程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="2b41b-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="2b41b-126">UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="2b41b-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="2b41b-127"><xref:System.AppDomain>卸載對應于指定之數位識別碼的。</span><span class="sxs-lookup"><span data-stu-id="2b41b-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b41b-128">備註</span><span class="sxs-lookup"><span data-stu-id="2b41b-128">Remarks</span></span>  
 <span data-ttu-id="2b41b-129">從 .NET Framework 4 開始, 請使用[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)介面來取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面的指標, 然後呼叫[ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法`ICLRRuntimeHost`來取得的指標。</span><span class="sxs-lookup"><span data-stu-id="2b41b-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="2b41b-130">在舊版的 .NET Framework 中, 主機會藉由呼叫`ICLRRuntimeHost` [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)取得實例的指標。</span><span class="sxs-lookup"><span data-stu-id="2b41b-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="2b41b-131">若要提供 .NET Framework 版本2.0 中所提供的任何技術的執行, 您必須使用`ICLRRuntimeHost` , `ICorRuntimeHost`而不是。</span><span class="sxs-lookup"><span data-stu-id="2b41b-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2b41b-132">在呼叫[ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)方法來啟動以資訊清單為基礎的應用程式之前, 請不要呼叫[Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="2b41b-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="2b41b-133">如果先呼叫`ExecuteApplication`方法,方法呼叫將會失敗。 `Start`</span><span class="sxs-lookup"><span data-stu-id="2b41b-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b41b-134">需求</span><span class="sxs-lookup"><span data-stu-id="2b41b-134">Requirements</span></span>  
 <span data-ttu-id="2b41b-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b41b-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b41b-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2b41b-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2b41b-137">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2b41b-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b41b-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b41b-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b41b-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b41b-139">See also</span></span>

- [<span data-ttu-id="2b41b-140">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="2b41b-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="2b41b-141">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="2b41b-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="2b41b-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="2b41b-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="2b41b-143">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="2b41b-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="2b41b-144">裝載介面</span><span class="sxs-lookup"><span data-stu-id="2b41b-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2b41b-145">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="2b41b-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
