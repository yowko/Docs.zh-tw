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
ms.openlocfilehash: ba02373aae33baf77b72323fabf1f6ca1fe4eecf
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490239"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="9d1ef-102">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="9d1ef-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="9d1ef-103">提供的功能類似於[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) .NET Framework 第 1 版，以下列變更所提供的介面：</span><span class="sxs-lookup"><span data-stu-id="9d1ef-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="9d1ef-104">新增[SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)來設定主應用程式控制項介面的方法。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="9d1ef-105">略過其中所提供的一些方法`ICorRuntimeHost`。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d1ef-106">方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-106">Methods</span></span>  
  
|<span data-ttu-id="9d1ef-107">方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-107">Method</span></span>|<span data-ttu-id="9d1ef-108">描述</span><span class="sxs-lookup"><span data-stu-id="9d1ef-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d1ef-109">ExecuteApplication 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="9d1ef-110">用於以指定要啟動新的網域中的應用程式的資訊清單為基礎的 ClickOnce 部署案例。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="9d1ef-111">ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="9d1ef-112">指定<xref:System.AppDomain>要執行指定的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="9d1ef-113">ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="9d1ef-114">叫用指定的型別，指定的組件中的指定的方法。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="9d1ef-115">GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="9d1ef-116">取得類型的介面指標[ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)主機可用於自訂的 common language runtime (CLR) 的層面。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="9d1ef-117">GetCurrentAppDomainId 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="9d1ef-118">取得的數值識別碼<xref:System.AppDomain>，目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="9d1ef-119">SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="9d1ef-120">設定主控件控制介面。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-120">Sets the host control interface.</span></span> <span data-ttu-id="9d1ef-121">您必須呼叫`SetHostControl`再呼叫`Start`。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="9d1ef-122">Start 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="9d1ef-123">初始化 CLR 程序。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="9d1ef-124">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="9d1ef-125">執行階段中停止執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="9d1ef-126">UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="9d1ef-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="9d1ef-127">卸載<xref:System.AppDomain>，其對應於指定的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d1ef-128">備註</span><span class="sxs-lookup"><span data-stu-id="9d1ef-128">Remarks</span></span>  
 <span data-ttu-id="9d1ef-129">從.NET Framework 4 開始，使用[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)介面，以取得的指標[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面，並接著呼叫[iclrruntimeinfo:: Getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法來取得變數的指標， `ICLRRuntimeHost`。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="9d1ef-130">在舊版的.NET Framework 中，主應用程式取得的指標`ICLRRuntimeHost`藉由呼叫的執行個體[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或是[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="9d1ef-131">若要提供的任何.NET Framework 2.0 版中提供的技術實作，您必須使用`ICLRRuntimeHost`而不是`ICorRuntimeHost`。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d1ef-132">請勿呼叫[開始](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法，再呼叫[ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)方法，以啟用資訊清單為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="9d1ef-133">如果`Start`首先，呼叫方法`ExecuteApplication`方法呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d1ef-134">需求</span><span class="sxs-lookup"><span data-stu-id="9d1ef-134">Requirements</span></span>  
 <span data-ttu-id="9d1ef-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d1ef-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d1ef-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d1ef-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d1ef-137">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9d1ef-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d1ef-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d1ef-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d1ef-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d1ef-139">See also</span></span>

- [<span data-ttu-id="9d1ef-140">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="9d1ef-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9d1ef-141">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="9d1ef-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9d1ef-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="9d1ef-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9d1ef-143">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="9d1ef-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9d1ef-144">裝載介面</span><span class="sxs-lookup"><span data-stu-id="9d1ef-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="9d1ef-145">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="9d1ef-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
