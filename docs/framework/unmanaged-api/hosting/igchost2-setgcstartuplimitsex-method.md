---
title: IGCHost2::SetGCStartupLimitsEx 方法
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
ms.openlocfilehash: d78f81093e61c40eaec334f957d8583eeb593f5e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134810"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="2f73c-102">IGCHost2::SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="2f73c-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="2f73c-103">設定層代0的區段大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="2f73c-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f73c-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f73c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f73c-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f73c-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="2f73c-106">在垃圾收集系統所使用的區段大小。</span><span class="sxs-lookup"><span data-stu-id="2f73c-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="2f73c-107">在層代0的大小上限。</span><span class="sxs-lookup"><span data-stu-id="2f73c-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f73c-108">備註</span><span class="sxs-lookup"><span data-stu-id="2f73c-108">Remarks</span></span>  
 <span data-ttu-id="2f73c-109">只有在啟動主機之前，才可以指定 `SetGCStartupLimitsEx` 設定的值。</span><span class="sxs-lookup"><span data-stu-id="2f73c-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="2f73c-110">之後就無法變更這些值。</span><span class="sxs-lookup"><span data-stu-id="2f73c-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f73c-111">需求</span><span class="sxs-lookup"><span data-stu-id="2f73c-111">Requirements</span></span>  
 <span data-ttu-id="2f73c-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f73c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f73c-113">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="2f73c-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="2f73c-114">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2f73c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f73c-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f73c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f73c-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f73c-116">See also</span></span>

- [<span data-ttu-id="2f73c-117">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="2f73c-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
