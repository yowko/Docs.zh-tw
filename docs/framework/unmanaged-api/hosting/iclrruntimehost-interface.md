---
title: "ICLRRuntimeHost 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost
helpviewer_keywords: ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type: apiref
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 332db2680ca23f34893a6c50c5311d73838bc1e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="414e8-102">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="414e8-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="414e8-103">提供的功能類似於[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)介面提供在.NET Framework 第 1 版有下列變更：</span><span class="sxs-lookup"><span data-stu-id="414e8-103">Provides functionality similar to that of the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
-   <span data-ttu-id="414e8-104">新增[SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)設定主控制項介面的方法。</span><span class="sxs-lookup"><span data-stu-id="414e8-104">The addition of the [SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
-   <span data-ttu-id="414e8-105">提供的一些方法省略`ICorRuntimeHost`。</span><span class="sxs-lookup"><span data-stu-id="414e8-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="414e8-106">方法</span><span class="sxs-lookup"><span data-stu-id="414e8-106">Methods</span></span>  
  
|<span data-ttu-id="414e8-107">方法</span><span class="sxs-lookup"><span data-stu-id="414e8-107">Method</span></span>|<span data-ttu-id="414e8-108">說明</span><span class="sxs-lookup"><span data-stu-id="414e8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="414e8-109">ExecuteApplication 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-109">ExecuteApplication Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="414e8-110">在資訊清單為主的 ClickOnce 部署案例中用來指定要啟動新的網域中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="414e8-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="414e8-111">ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-111">ExecuteInAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="414e8-112">指定<xref:System.AppDomain>，以執行指定的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="414e8-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="414e8-113">ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-113">ExecuteInDefaultAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="414e8-114">叫用指定的組件中的指定類型的指定的方法。</span><span class="sxs-lookup"><span data-stu-id="414e8-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="414e8-115">GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="414e8-116">取得類型的介面指標[ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)主機可用於自訂的 common language runtime (CLR) 層面。</span><span class="sxs-lookup"><span data-stu-id="414e8-116">Gets an interface pointer of type [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="414e8-117">GetCurrentAppDomainId 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-117">GetCurrentAppDomainId Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="414e8-118">取得的數值識別碼<xref:System.AppDomain>，目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="414e8-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="414e8-119">SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-119">SetHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="414e8-120">設定主機控制項介面。</span><span class="sxs-lookup"><span data-stu-id="414e8-120">Sets the host control interface.</span></span> <span data-ttu-id="414e8-121">您必須呼叫`SetHostControl`之前先呼叫`Start`。</span><span class="sxs-lookup"><span data-stu-id="414e8-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="414e8-122">Start 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-122">Start Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|<span data-ttu-id="414e8-123">初始化 CLR 程序。</span><span class="sxs-lookup"><span data-stu-id="414e8-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="414e8-124">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-124">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|<span data-ttu-id="414e8-125">停止執行的程式碼執行階段。</span><span class="sxs-lookup"><span data-stu-id="414e8-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="414e8-126">UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="414e8-126">UnloadAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="414e8-127">卸載<xref:System.AppDomain>對應於指定的數值識別項。</span><span class="sxs-lookup"><span data-stu-id="414e8-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="414e8-128">備註</span><span class="sxs-lookup"><span data-stu-id="414e8-128">Remarks</span></span>  
 <span data-ttu-id="414e8-129">從開始[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，使用[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)介面，以取得指標[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面，並接著呼叫[iclrruntimeinfo:: Getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法來取得指向`ICLRRuntimeHost`。</span><span class="sxs-lookup"><span data-stu-id="414e8-129">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="414e8-130">在舊版的.NET Framework 中，主機會取得的指標`ICLRRuntimeHost`藉由呼叫的執行個體[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="414e8-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="414e8-131">若要提供的任何.NET Framework 2.0 版中提供的技術實作，您必須使用`ICLRRuntimeHost`而不是`ICorRuntimeHost`。</span><span class="sxs-lookup"><span data-stu-id="414e8-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="414e8-132">請勿呼叫[啟動](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法之前先呼叫[ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)方法來啟動資訊清單為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="414e8-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="414e8-133">如果`Start`首先，呼叫方法`ExecuteApplication`方法呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="414e8-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="414e8-134">需求</span><span class="sxs-lookup"><span data-stu-id="414e8-134">Requirements</span></span>  
 <span data-ttu-id="414e8-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="414e8-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="414e8-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="414e8-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="414e8-137">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="414e8-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="414e8-138">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="414e8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="414e8-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="414e8-139">See Also</span></span>  
 [<span data-ttu-id="414e8-140">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="414e8-140">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="414e8-141">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="414e8-141">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="414e8-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="414e8-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="414e8-143">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="414e8-143">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="414e8-144">裝載介面</span><span class="sxs-lookup"><span data-stu-id="414e8-144">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="414e8-145">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="414e8-145">CLRRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
