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
ms.openlocfilehash: ac40e203cf7d32c1fe30c9915bac3171139403e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723277"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="87f45-102">ICLRMetaHost::RequestRuntimeLoadedNotification 方法</span><span class="sxs-lookup"><span data-stu-id="87f45-102">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>

<span data-ttu-id="87f45-103">提供回呼函式，保證在第一次載入 common language runtime (CLR) 版本，但尚未啟動時，會呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="87f45-103">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="87f45-104">這個方法會取代 [LockClrVersion](lockclrversion-function.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="87f45-104">This method supersedes the [LockClrVersion](lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f45-105">語法</span><span class="sxs-lookup"><span data-stu-id="87f45-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87f45-106">參數</span><span class="sxs-lookup"><span data-stu-id="87f45-106">Parameters</span></span>  

 `pCallbackFunction`  
 <span data-ttu-id="87f45-107">在載入新執行時間時叫用的回呼函數。</span><span class="sxs-lookup"><span data-stu-id="87f45-107">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87f45-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="87f45-108">Return Value</span></span>  

 <span data-ttu-id="87f45-109">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="87f45-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="87f45-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87f45-110">HRESULT</span></span>|<span data-ttu-id="87f45-111">描述</span><span class="sxs-lookup"><span data-stu-id="87f45-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87f45-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="87f45-112">S_OK</span></span>|<span data-ttu-id="87f45-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="87f45-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="87f45-114">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="87f45-114">E_POINTER</span></span>|<span data-ttu-id="87f45-115">`pCallbackFunction` 為 null。</span><span class="sxs-lookup"><span data-stu-id="87f45-115">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87f45-116">備註</span><span class="sxs-lookup"><span data-stu-id="87f45-116">Remarks</span></span>  

 <span data-ttu-id="87f45-117">回呼的運作方式如下：</span><span class="sxs-lookup"><span data-stu-id="87f45-117">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="87f45-118">只有在第一次載入執行時間時，才會叫用回呼。</span><span class="sxs-lookup"><span data-stu-id="87f45-118">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="87f45-119">針對相同執行時間的可重新進入載入，不會叫用回呼。</span><span class="sxs-lookup"><span data-stu-id="87f45-119">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="87f45-120">針對非重新進入執行時間載入，會序列化回呼函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="87f45-120">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="87f45-121">回呼函數具有下列原型：</span><span class="sxs-lookup"><span data-stu-id="87f45-121">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="87f45-122">回呼函數原型如下所示：</span><span class="sxs-lookup"><span data-stu-id="87f45-122">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="87f45-123">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="87f45-123">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="87f45-124">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="87f45-124">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="87f45-125">如果主機打算載入或導致另一個執行時間以重新進入的方式載入，則在回呼函式中 `pfnCallbackThreadSet` 提供的和 `pfnCallbackThreadUnset` 參數必須以下列方式使用：</span><span class="sxs-lookup"><span data-stu-id="87f45-125">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="87f45-126">`pfnCallbackThreadSet` 必須由可能會導致執行時間載入的執行緒呼叫，然後再嘗試這類載入。</span><span class="sxs-lookup"><span data-stu-id="87f45-126">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="87f45-127">`pfnCallbackThreadUnset` 當執行緒不再造成執行時間載入 (，以及從初始回呼) 傳回之前，都必須呼叫。</span><span class="sxs-lookup"><span data-stu-id="87f45-127">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="87f45-128">`pfnCallbackThreadSet` 和 `pfnCallbackThreadUnset` 都是不可重新進入的。</span><span class="sxs-lookup"><span data-stu-id="87f45-128">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87f45-129">主機應用程式不得在 `pfnCallbackThreadSet` `pfnCallbackThreadUnset` 參數的範圍之外呼叫和 `pCallbackFunction` 。</span><span class="sxs-lookup"><span data-stu-id="87f45-129">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f45-130">需求</span><span class="sxs-lookup"><span data-stu-id="87f45-130">Requirements</span></span>  

 <span data-ttu-id="87f45-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87f45-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f45-132">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="87f45-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="87f45-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="87f45-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87f45-134">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87f45-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f45-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87f45-135">See also</span></span>

- [<span data-ttu-id="87f45-136">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="87f45-136">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="87f45-137">裝載</span><span class="sxs-lookup"><span data-stu-id="87f45-137">Hosting</span></span>](index.md)
