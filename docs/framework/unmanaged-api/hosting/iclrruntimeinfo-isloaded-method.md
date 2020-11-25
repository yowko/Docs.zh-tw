---
title: ICLRRuntimeInfo::IsLoaded 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 66ae74deba9ceab9d1ea6b2c0b96a87bf44f32ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714922"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="554b4-102">ICLRRuntimeInfo::IsLoaded 方法</span><span class="sxs-lookup"><span data-stu-id="554b4-102">ICLRRuntimeInfo::IsLoaded Method</span></span>

<span data-ttu-id="554b4-103">指出與 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面相關聯的 common language RUNTIME (CLR) 是否會載入至進程。</span><span class="sxs-lookup"><span data-stu-id="554b4-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="554b4-104">您也可以在不啟動的情況下載入執行時間。</span><span class="sxs-lookup"><span data-stu-id="554b4-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="554b4-105">語法</span><span class="sxs-lookup"><span data-stu-id="554b4-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="554b4-106">參數</span><span class="sxs-lookup"><span data-stu-id="554b4-106">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="554b4-107">在進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="554b4-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="554b4-108">[out] `true` 如果 CLR 已載入至進程，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="554b4-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="554b4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="554b4-109">Return Value</span></span>  

 <span data-ttu-id="554b4-110">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="554b4-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="554b4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="554b4-111">HRESULT</span></span>|<span data-ttu-id="554b4-112">描述</span><span class="sxs-lookup"><span data-stu-id="554b4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="554b4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="554b4-113">S_OK</span></span>|<span data-ttu-id="554b4-114">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="554b4-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="554b4-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="554b4-115">E_POINTER</span></span>|<span data-ttu-id="554b4-116">`pbLoaded` 為 null。</span><span class="sxs-lookup"><span data-stu-id="554b4-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="554b4-117">備註</span><span class="sxs-lookup"><span data-stu-id="554b4-117">Remarks</span></span>  

 <span data-ttu-id="554b4-118">這個方法與下列函式和介面具有回溯相容性：</span><span class="sxs-lookup"><span data-stu-id="554b4-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="554b4-119">.NET Framework 第1版裝載 API) 中 ([ICorRuntimeHost](icorruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="554b4-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="554b4-120">.NET Framework 2.0 裝載 API) 中 ([ICLRRuntimeHost](iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="554b4-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="554b4-121">已淘汰的函式 `CorBindTo*` (在 .NET Framework 2.0 裝載 API) 中看到已被 [取代的 CLR 裝載](deprecated-clr-hosting-functions.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="554b4-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="554b4-122">主機可以呼叫其中一個已被取代的函式（ `CorBindTo*` 例如 [CorBindToRuntime](corbindtoruntime-function.md) 函式），以具現化特定的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="554b4-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="554b4-123">然後，主機可以呼叫 [ICLRMetaHost：： GetRuntime](iclrmetahost-getruntime-method.md) 方法，並指定相同的版本號碼來取得 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="554b4-123">The host could then call the [ICLRMetaHost::GetRuntime](iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="554b4-124">如果主機接著在 `IsLoaded` 傳回的 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面上呼叫方法，則 `pbLoaded` 會傳回， `true` 否則會傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="554b4-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="554b4-125">需求</span><span class="sxs-lookup"><span data-stu-id="554b4-125">Requirements</span></span>  

 <span data-ttu-id="554b4-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="554b4-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="554b4-127">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="554b4-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="554b4-128">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="554b4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="554b4-129">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="554b4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554b4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="554b4-130">See also</span></span>

- [<span data-ttu-id="554b4-131">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="554b4-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="554b4-132">裝載介面</span><span class="sxs-lookup"><span data-stu-id="554b4-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="554b4-133">裝載</span><span class="sxs-lookup"><span data-stu-id="554b4-133">Hosting</span></span>](index.md)
