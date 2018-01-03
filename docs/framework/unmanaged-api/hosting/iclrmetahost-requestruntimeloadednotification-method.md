---
title: "ICLRMetaHost::RequestRuntimeLoadedNotification 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7866270d8c9234a375401dfd05b504a06ddbf4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="e5dd4-102">ICLRMetaHost::RequestRuntimeLoadedNotification 方法</span><span class="sxs-lookup"><span data-stu-id="e5dd4-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="e5dd4-103">提供保證的 common language runtime (CLR) 版本是第一次載入，但尚未啟動時要呼叫的回呼函式。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="e5dd4-104">這個方法會取代[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5dd4-105">語法</span><span class="sxs-lookup"><span data-stu-id="e5dd4-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5dd4-106">參數</span><span class="sxs-lookup"><span data-stu-id="e5dd4-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="e5dd4-107">[in]在載入新的執行階段時，會叫用回呼函式。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5dd4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e5dd4-108">Return Value</span></span>  
 <span data-ttu-id="e5dd4-109">這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e5dd4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e5dd4-110">HRESULT</span></span>|<span data-ttu-id="e5dd4-111">描述</span><span class="sxs-lookup"><span data-stu-id="e5dd4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e5dd4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e5dd4-112">S_OK</span></span>|<span data-ttu-id="e5dd4-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="e5dd4-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e5dd4-114">E_POINTER</span></span>|<span data-ttu-id="e5dd4-115">`pCallbackFunction` 為 null。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5dd4-116">備註</span><span class="sxs-lookup"><span data-stu-id="e5dd4-116">Remarks</span></span>  
 <span data-ttu-id="e5dd4-117">回呼的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="e5dd4-117">The callback works in the following way:</span></span>  
  
-   <span data-ttu-id="e5dd4-118">只有在第一次載入執行階段時，會叫用回呼。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
-   <span data-ttu-id="e5dd4-119">可重新進入相同的執行階段載入不會叫用回呼。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
-   <span data-ttu-id="e5dd4-120">不可重新進入執行階段載入的回呼函式的呼叫已序列化的。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="e5dd4-121">回呼函式具有下列原型：</span><span class="sxs-lookup"><span data-stu-id="e5dd4-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="e5dd4-122">回呼函式原型如下所示：</span><span class="sxs-lookup"><span data-stu-id="e5dd4-122">The callback function prototypes are as follows:</span></span>  
  
-   <span data-ttu-id="e5dd4-123">`pfnCallbackThreadSet`：</span><span class="sxs-lookup"><span data-stu-id="e5dd4-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
-   <span data-ttu-id="e5dd4-124">`pfnCallbackThreadUnset`：</span><span class="sxs-lookup"><span data-stu-id="e5dd4-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="e5dd4-125">如果主應用程式所要載入，或導致另一個執行階段要載入的方式可重新進入，`pfnCallbackThreadSet`和`pfnCallbackThreadUnset`會提供在回呼函式必須以下列方式使用的參數：</span><span class="sxs-lookup"><span data-stu-id="e5dd4-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
-   <span data-ttu-id="e5dd4-126">`pfnCallbackThreadSet`必須先嘗試這類載入可能會導致執行階段載入的執行緒所呼叫。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
-   <span data-ttu-id="e5dd4-127">`pfnCallbackThreadUnset`必須先呼叫時，執行緒將不會再造成執行階段負載 （和從初始回呼傳回之前）。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
-   <span data-ttu-id="e5dd4-128">`pfnCallbackThreadSet`和`pfnCallbackThreadUnset`兩者都不可重新進入。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5dd4-129">裝載應用程式不能呼叫`pfnCallbackThreadSet`和`pfnCallbackThreadUnset`範圍以外的`pCallbackFunction`參數。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5dd4-130">需求</span><span class="sxs-lookup"><span data-stu-id="e5dd4-130">Requirements</span></span>  
 <span data-ttu-id="e5dd4-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5dd4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5dd4-132">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e5dd4-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e5dd4-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e5dd4-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5dd4-134">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5dd4-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5dd4-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="e5dd4-135">See Also</span></span>  
 [<span data-ttu-id="e5dd4-136">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="e5dd4-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="e5dd4-137">裝載</span><span class="sxs-lookup"><span data-stu-id="e5dd4-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
