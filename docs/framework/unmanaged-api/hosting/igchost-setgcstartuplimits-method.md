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
ms.openlocfilehash: 1ae50fb3ff15097f9a6ca5839f3832bcfc58d3f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134847"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="bd887-102">IGCHost::SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="bd887-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="bd887-103">設定層代0的區段大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="bd887-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bd887-104">從 .NET Framework 4.5 開始，您可以使用[IGCHost2：： SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法，將區段大小和最大層代0大小設定為大於 `DWORD` 的值。</span><span class="sxs-lookup"><span data-stu-id="bd887-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd887-105">語法</span><span class="sxs-lookup"><span data-stu-id="bd887-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd887-106">參數</span><span class="sxs-lookup"><span data-stu-id="bd887-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="bd887-107">在垃圾收集系統所使用的區段大小。</span><span class="sxs-lookup"><span data-stu-id="bd887-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="bd887-108">在層代0的大小上限。</span><span class="sxs-lookup"><span data-stu-id="bd887-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd887-109">備註</span><span class="sxs-lookup"><span data-stu-id="bd887-109">Remarks</span></span>  
 <span data-ttu-id="bd887-110">`SetGCStartupLimits` 方法只能呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="bd887-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="bd887-111">之後就無法變更這些值。</span><span class="sxs-lookup"><span data-stu-id="bd887-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd887-112">需求</span><span class="sxs-lookup"><span data-stu-id="bd887-112">Requirements</span></span>  
 <span data-ttu-id="bd887-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd887-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd887-114">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="bd887-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="bd887-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bd887-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd887-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd887-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd887-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd887-117">See also</span></span>

- [<span data-ttu-id="bd887-118">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="bd887-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
