---
title: ICLRRuntimeInfo::IsLoadable 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: 9339bb974c261e62502c760dfaf45651573cbe1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136366"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="3ee74-102">ICLRRuntimeInfo::IsLoadable 方法</span><span class="sxs-lookup"><span data-stu-id="3ee74-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="3ee74-103">指出與這個介面相關聯的執行時間是否可以載入目前的進程中，並考慮可能已經載入進程的其他執行時間。</span><span class="sxs-lookup"><span data-stu-id="3ee74-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ee74-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ee74-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ee74-105">參數</span><span class="sxs-lookup"><span data-stu-id="3ee74-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="3ee74-106">[out] `true` 如果此執行時間可以載入目前的進程中，則為，否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="3ee74-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ee74-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="3ee74-107">Return Value</span></span>  
 <span data-ttu-id="3ee74-108">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="3ee74-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3ee74-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ee74-109">HRESULT</span></span>|<span data-ttu-id="3ee74-110">描述</span><span class="sxs-lookup"><span data-stu-id="3ee74-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ee74-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ee74-111">S_OK</span></span>|<span data-ttu-id="3ee74-112">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="3ee74-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="3ee74-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3ee74-113">E_POINTER</span></span>|<span data-ttu-id="3ee74-114">`pbLoadable` 為 null。</span><span class="sxs-lookup"><span data-stu-id="3ee74-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ee74-115">備註</span><span class="sxs-lookup"><span data-stu-id="3ee74-115">Remarks</span></span>  
 <span data-ttu-id="3ee74-116">如果另一個執行時間已載入進程，而且可以載入與此介面相關聯的執行時間，以進行同進程並存執行，`pbLoadable` 會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="3ee74-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="3ee74-117">如果這兩個執行時間無法並存執行同進程，`pbLoadable` 會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="3ee74-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="3ee74-118">例如，common language runtime （CLR）第4版可以在 CLR 版本2.0 或 CLR 1.1 版的相同進程中並存執行。</span><span class="sxs-lookup"><span data-stu-id="3ee74-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="3ee74-119">不過，CLR 版本1.1 和 CLR 版本2.0 無法並存執行同進程。</span><span class="sxs-lookup"><span data-stu-id="3ee74-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="3ee74-120">如果未將執行時間載入進程中，這個方法一律會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="3ee74-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ee74-121">需求</span><span class="sxs-lookup"><span data-stu-id="3ee74-121">Requirements</span></span>  
 <span data-ttu-id="3ee74-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ee74-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ee74-123">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="3ee74-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3ee74-124">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3ee74-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ee74-125">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ee74-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee74-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ee74-126">See also</span></span>

- [<span data-ttu-id="3ee74-127">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="3ee74-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="3ee74-128">裝載介面</span><span class="sxs-lookup"><span data-stu-id="3ee74-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="3ee74-129">裝載</span><span class="sxs-lookup"><span data-stu-id="3ee74-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
