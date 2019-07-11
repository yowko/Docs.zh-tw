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
ms.openlocfilehash: c9104550438a2a066cdf052b8d6592e86b831194
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749993"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="64090-102">IGCHost::SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="64090-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="64090-103">層代 0 設定區段的大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="64090-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64090-104">從.NET Framework 4.5 開始，您可以設定區段的大小和最大層代 0 大小的值大於`DWORD`利用[IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="64090-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64090-105">語法</span><span class="sxs-lookup"><span data-stu-id="64090-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64090-106">參數</span><span class="sxs-lookup"><span data-stu-id="64090-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="64090-107">[in]記憶體回收系統所使用的區段大小。</span><span class="sxs-lookup"><span data-stu-id="64090-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="64090-108">[in]層代 0 的大小上限。</span><span class="sxs-lookup"><span data-stu-id="64090-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64090-109">備註</span><span class="sxs-lookup"><span data-stu-id="64090-109">Remarks</span></span>  
 <span data-ttu-id="64090-110">`SetGCStartupLimits`可能只有一次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="64090-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="64090-111">稍後無法變更這些值。</span><span class="sxs-lookup"><span data-stu-id="64090-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64090-112">需求</span><span class="sxs-lookup"><span data-stu-id="64090-112">Requirements</span></span>  
 <span data-ttu-id="64090-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64090-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64090-114">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="64090-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="64090-115">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="64090-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64090-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64090-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64090-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64090-117">See also</span></span>

- [<span data-ttu-id="64090-118">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="64090-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
