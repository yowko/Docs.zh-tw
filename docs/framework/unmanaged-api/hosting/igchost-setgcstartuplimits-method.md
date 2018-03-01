---
title: "IGCHost::SetGCStartupLimits 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d99212b1ece4d3c0ce9440ac973b8254ebca6dde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="ee6eb-102">IGCHost::SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="ee6eb-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="ee6eb-103">層代 0 設定區段的大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="ee6eb-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee6eb-104">從開始[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，您可以設定區段的大小和最大層代 0 大小值大於`DWORD`使用[igchost2:: Setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ee6eb-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee6eb-105">語法</span><span class="sxs-lookup"><span data-stu-id="ee6eb-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee6eb-106">參數</span><span class="sxs-lookup"><span data-stu-id="ee6eb-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="ee6eb-107">[in]記憶體回收系統所使用的區段大小。</span><span class="sxs-lookup"><span data-stu-id="ee6eb-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="ee6eb-108">[in]層代 0 的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ee6eb-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee6eb-109">備註</span><span class="sxs-lookup"><span data-stu-id="ee6eb-109">Remarks</span></span>  
 <span data-ttu-id="ee6eb-110">`SetGCStartupLimits`方法可能會呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="ee6eb-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="ee6eb-111">無法在稍後變更這些值。</span><span class="sxs-lookup"><span data-stu-id="ee6eb-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee6eb-112">需求</span><span class="sxs-lookup"><span data-stu-id="ee6eb-112">Requirements</span></span>  
 <span data-ttu-id="ee6eb-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee6eb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee6eb-114">**標頭：** GCHost.idl、 GCHost.h</span><span class="sxs-lookup"><span data-stu-id="ee6eb-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ee6eb-115">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ee6eb-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee6eb-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee6eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee6eb-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="ee6eb-117">See Also</span></span>  
 [<span data-ttu-id="ee6eb-118">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="ee6eb-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
