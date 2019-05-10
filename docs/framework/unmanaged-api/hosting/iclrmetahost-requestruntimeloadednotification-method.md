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
ms.openlocfilehash: 87afb19736a484d24bde56cc34854dcd26c6b53b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755705"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="0eca9-102">ICLRMetaHost::RequestRuntimeLoadedNotification 方法</span><span class="sxs-lookup"><span data-stu-id="0eca9-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>
<span data-ttu-id="0eca9-103">提供保證的 common language runtime (CLR) 版本是第一次載入，但尚未開始時要呼叫的回呼函式。</span><span class="sxs-lookup"><span data-stu-id="0eca9-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="0eca9-104">這個方法會取代[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="0eca9-104">This method supersedes the [LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eca9-105">語法</span><span class="sxs-lookup"><span data-stu-id="0eca9-105">Syntax</span></span>  
  
```  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eca9-106">參數</span><span class="sxs-lookup"><span data-stu-id="0eca9-106">Parameters</span></span>  
 `pCallbackFunction`  
 <span data-ttu-id="0eca9-107">[in]已載入新的執行階段時，會叫用回呼函式。</span><span class="sxs-lookup"><span data-stu-id="0eca9-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eca9-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="0eca9-108">Return Value</span></span>  
 <span data-ttu-id="0eca9-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="0eca9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0eca9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0eca9-110">HRESULT</span></span>|<span data-ttu-id="0eca9-111">描述</span><span class="sxs-lookup"><span data-stu-id="0eca9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0eca9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0eca9-112">S_OK</span></span>|<span data-ttu-id="0eca9-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="0eca9-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="0eca9-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0eca9-114">E_POINTER</span></span>|<span data-ttu-id="0eca9-115">`pCallbackFunction` 為 null。</span><span class="sxs-lookup"><span data-stu-id="0eca9-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0eca9-116">備註</span><span class="sxs-lookup"><span data-stu-id="0eca9-116">Remarks</span></span>  
 <span data-ttu-id="0eca9-117">回呼的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="0eca9-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="0eca9-118">只有在第一次載入執行階段時，會叫用回呼。</span><span class="sxs-lookup"><span data-stu-id="0eca9-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="0eca9-119">回呼不會叫用相同的執行階段的可重新進入的負載。</span><span class="sxs-lookup"><span data-stu-id="0eca9-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="0eca9-120">不可重新進入執行階段載入的序列化回呼函式的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0eca9-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="0eca9-121">回呼函式具有下列原型：</span><span class="sxs-lookup"><span data-stu-id="0eca9-121">The callback function has the following prototype:</span></span>  
  
```  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="0eca9-122">回呼函式原型如下所示：</span><span class="sxs-lookup"><span data-stu-id="0eca9-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="0eca9-123">`pfnCallbackThreadSet`：</span><span class="sxs-lookup"><span data-stu-id="0eca9-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="0eca9-124">`pfnCallbackThreadUnset`：</span><span class="sxs-lookup"><span data-stu-id="0eca9-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="0eca9-125">如果主機想要載入，或導致另一個執行階段要載入的方式可重新進入，則`pfnCallbackThreadSet`和`pfnCallbackThreadUnset`參數所提供的回呼函式必須使用方式如下：</span><span class="sxs-lookup"><span data-stu-id="0eca9-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="0eca9-126">`pfnCallbackThreadSet` 必須由之前嘗試這類載入可能會導致執行階段載入的執行緒呼叫。</span><span class="sxs-lookup"><span data-stu-id="0eca9-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="0eca9-127">`pfnCallbackThreadUnset` 必須先呼叫時，執行緒將不會再造成執行階段負載 （以及從初始的回呼傳回之前）。</span><span class="sxs-lookup"><span data-stu-id="0eca9-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="0eca9-128">`pfnCallbackThreadSet` 和`pfnCallbackThreadUnset`兩者都是不可重新進入。</span><span class="sxs-lookup"><span data-stu-id="0eca9-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0eca9-129">裝載應用程式必須呼叫`pfnCallbackThreadSet`並`pfnCallbackThreadUnset`的範圍外`pCallbackFunction`參數。</span><span class="sxs-lookup"><span data-stu-id="0eca9-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eca9-130">需求</span><span class="sxs-lookup"><span data-stu-id="0eca9-130">Requirements</span></span>  
 <span data-ttu-id="0eca9-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0eca9-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eca9-132">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0eca9-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0eca9-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0eca9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0eca9-134">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eca9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eca9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0eca9-135">See also</span></span>

- [<span data-ttu-id="0eca9-136">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="0eca9-136">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [<span data-ttu-id="0eca9-137">裝載</span><span class="sxs-lookup"><span data-stu-id="0eca9-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
