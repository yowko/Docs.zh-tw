---
title: IGCHost::SetGCStartupLimits 方法
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6962b52925ab5b70a8b34c6d3720bb45c85b24c0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473886"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="515f9-102">IGCHost::SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="515f9-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="515f9-103">層代 0 設定區段的大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="515f9-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="515f9-104">開頭[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以設定區段的大小和最大層代 0 大小值大於`DWORD`利用[IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="515f9-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="515f9-105">語法</span><span class="sxs-lookup"><span data-stu-id="515f9-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="515f9-106">參數</span><span class="sxs-lookup"><span data-stu-id="515f9-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="515f9-107">[in]記憶體回收系統所使用的區段大小。</span><span class="sxs-lookup"><span data-stu-id="515f9-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="515f9-108">[in]層代 0 的大小上限。</span><span class="sxs-lookup"><span data-stu-id="515f9-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="515f9-109">備註</span><span class="sxs-lookup"><span data-stu-id="515f9-109">Remarks</span></span>  
 <span data-ttu-id="515f9-110">`SetGCStartupLimits`可能只有一次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="515f9-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="515f9-111">稍後無法變更這些值。</span><span class="sxs-lookup"><span data-stu-id="515f9-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="515f9-112">需求</span><span class="sxs-lookup"><span data-stu-id="515f9-112">Requirements</span></span>  
 <span data-ttu-id="515f9-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="515f9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="515f9-114">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="515f9-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="515f9-115">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="515f9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="515f9-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="515f9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515f9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="515f9-117">See also</span></span>
- [<span data-ttu-id="515f9-118">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="515f9-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
