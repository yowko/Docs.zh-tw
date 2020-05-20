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
ms.openlocfilehash: dd1aa4089a981d82ae1403189343694a065a701d
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703659"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="1c4d8-102">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="1c4d8-102">ICLRRuntimeHost Interface</span></span>
<span data-ttu-id="1c4d8-103">提供的功能類似于 .NET Framework 第1版所提供的[ICorRuntimeHost](icorruntimehost-interface.md)介面，但有下列變更：</span><span class="sxs-lookup"><span data-stu-id="1c4d8-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="1c4d8-104">新增[SetHostControl](iclrruntimehost-sethostcontrol-method.md)方法以設定主控制項介面。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="1c4d8-105">省略所提供的一些方法 `ICorRuntimeHost` 。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c4d8-106">方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-106">Methods</span></span>  
  
|<span data-ttu-id="1c4d8-107">方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-107">Method</span></span>|<span data-ttu-id="1c4d8-108">描述</span><span class="sxs-lookup"><span data-stu-id="1c4d8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1c4d8-109">ExecuteApplication 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="1c4d8-110">在以資訊清單為基礎的 ClickOnce 部署案例中使用，以指定要在新的網域中啟動的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="1c4d8-111">ExecuteInAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="1c4d8-112">指定 <xref:System.AppDomain> 要在其中執行指定 managed 程式碼的。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="1c4d8-113">ExecuteInDefaultAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="1c4d8-114">在指定的元件中，叫用指定之類型的指定方法。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="1c4d8-115">GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-115">GetCLRControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="1c4d8-116">取得類型[ICLRControl](iclrcontrol-interface.md)的介面指標，可供裝載用來自訂 common language RUNTIME （CLR）的各個層面。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="1c4d8-117">GetCurrentAppDomainId 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="1c4d8-118">取得目前正在執行之的數值識別碼 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="1c4d8-119">SetHostControl 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="1c4d8-120">設定主控制項介面。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-120">Sets the host control interface.</span></span> <span data-ttu-id="1c4d8-121">呼叫之前，您必須 `SetHostControl` 先呼叫 `Start` 。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="1c4d8-122">Start 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="1c4d8-123">將 CLR 初始化為進程。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="1c4d8-124">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="1c4d8-125">停止執行時間的程式碼執行。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="1c4d8-126">UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1c4d8-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="1c4d8-127">卸載 <xref:System.AppDomain> 對應于指定之數位識別碼的。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c4d8-128">備註</span><span class="sxs-lookup"><span data-stu-id="1c4d8-128">Remarks</span></span>  
 <span data-ttu-id="1c4d8-129">從 .NET Framework 4 開始，請使用[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)介面來取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面的指標，然後呼叫[ICLRRuntimeInfo：： GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法來取得的指標 `ICLRRuntimeHost` 。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="1c4d8-130">在舊版的 .NET Framework 中，主機會藉 `ICLRRuntimeHost` 由呼叫[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)取得實例的指標。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="1c4d8-131">若要提供 .NET Framework 版本2.0 中所提供的任何技術的執行，您必須使用， `ICLRRuntimeHost` 而不是 `ICorRuntimeHost` 。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1c4d8-132">在呼叫[ExecuteApplication](iclrruntimehost-executeapplication-method.md)方法來啟動以資訊清單為基礎的應用程式之前，請不要呼叫[Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-132">Do not call the [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="1c4d8-133">如果 `Start` 先呼叫方法， `ExecuteApplication` 方法呼叫將會失敗。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c4d8-134">需求</span><span class="sxs-lookup"><span data-stu-id="1c4d8-134">Requirements</span></span>  
 <span data-ttu-id="1c4d8-135">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c4d8-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c4d8-136">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="1c4d8-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c4d8-137">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1c4d8-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c4d8-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c4d8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4d8-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c4d8-139">See also</span></span>

- [<span data-ttu-id="1c4d8-140">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="1c4d8-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="1c4d8-141">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="1c4d8-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="1c4d8-142">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="1c4d8-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="1c4d8-143">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="1c4d8-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="1c4d8-144">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1c4d8-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="1c4d8-145">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="1c4d8-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
