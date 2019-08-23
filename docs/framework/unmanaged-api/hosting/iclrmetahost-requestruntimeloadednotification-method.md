---
title: ICLRMetaHost::RequestRuntimeLoadedNotification 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 539f69c33b67ad1a8a514062c5d777deaced1599
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964999"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="2d890-102">ICLRMetaHost::RequestRuntimeLoadedNotification 方法</span><span class="sxs-lookup"><span data-stu-id="2d890-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="2d890-103">提供回呼函式, 保證會在第一次載入 common language runtime (CLR) 版本, 但尚未啟動時呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d890-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="2d890-104">這個方法會取代[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="2d890-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d890-105">語法</span><span class="sxs-lookup"><span data-stu-id="2d890-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d890-106">參數</span><span class="sxs-lookup"><span data-stu-id="2d890-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="2d890-107">在載入新的執行時間時所叫用的回呼函式。</span><span class="sxs-lookup"><span data-stu-id="2d890-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d890-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d890-108">Return Value</span></span>  
 <span data-ttu-id="2d890-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="2d890-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2d890-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d890-110">HRESULT</span></span>|<span data-ttu-id="2d890-111">描述</span><span class="sxs-lookup"><span data-stu-id="2d890-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d890-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d890-112">S_OK</span></span>|<span data-ttu-id="2d890-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="2d890-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="2d890-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="2d890-114">E_POINTER</span></span>|<span data-ttu-id="2d890-115">`pCallbackFunction` 為 null。</span><span class="sxs-lookup"><span data-stu-id="2d890-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d890-116">備註</span><span class="sxs-lookup"><span data-stu-id="2d890-116">Remarks</span></span>  
 <span data-ttu-id="2d890-117">回呼會以下列方式運作:</span><span class="sxs-lookup"><span data-stu-id="2d890-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="2d890-118">只有在第一次載入執行時間時, 才會叫用回呼。</span><span class="sxs-lookup"><span data-stu-id="2d890-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="2d890-119">不會針對相同執行時間的可重新進入負載叫用回呼。</span><span class="sxs-lookup"><span data-stu-id="2d890-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="2d890-120">對於不可重新進入的執行時間載入, 會序列化回呼函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d890-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="2d890-121">回呼函數具有下列原型:</span><span class="sxs-lookup"><span data-stu-id="2d890-121">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="2d890-122">回呼函數原型如下所示:</span><span class="sxs-lookup"><span data-stu-id="2d890-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="2d890-123">`pfnCallbackThreadSet`：</span><span class="sxs-lookup"><span data-stu-id="2d890-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="2d890-124">`pfnCallbackThreadUnset`：</span><span class="sxs-lookup"><span data-stu-id="2d890-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="2d890-125">如果主機打算載入或造成另一個執行時間以可重新進入的方式載入, 則`pfnCallbackThreadSet`必須`pfnCallbackThreadUnset`以下列方式使用回呼函式中提供的和參數:</span><span class="sxs-lookup"><span data-stu-id="2d890-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="2d890-126">`pfnCallbackThreadSet`必須由執行緒呼叫, 可能會在嘗試進行這類負載之前造成執行時間載入。</span><span class="sxs-lookup"><span data-stu-id="2d890-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="2d890-127">`pfnCallbackThreadUnset`當執行緒不會再造成這類執行時間載入 (以及從初始回呼傳回之前) 時, 必須呼叫。</span><span class="sxs-lookup"><span data-stu-id="2d890-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="2d890-128">`pfnCallbackThreadSet`和`pfnCallbackThreadUnset`都是不可重新進入的。</span><span class="sxs-lookup"><span data-stu-id="2d890-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d890-129">主應用程式不能`pfnCallbackThreadSet`在`pfnCallbackThreadUnset` `pCallbackFunction`參數的範圍之外呼叫和。</span><span class="sxs-lookup"><span data-stu-id="2d890-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d890-130">需求</span><span class="sxs-lookup"><span data-stu-id="2d890-130">Requirements</span></span>  
 <span data-ttu-id="2d890-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2d890-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d890-132">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2d890-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2d890-133">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2d890-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d890-134">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d890-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d890-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d890-135">See also</span></span>

- [<span data-ttu-id="2d890-136">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="2d890-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="2d890-137">裝載</span><span class="sxs-lookup"><span data-stu-id="2d890-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
