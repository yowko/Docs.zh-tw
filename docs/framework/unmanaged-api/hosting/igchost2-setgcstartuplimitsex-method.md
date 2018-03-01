---
title: "IGCHost2::SetGCStartupLimitsEx 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f8ed2b2aa43fcf925b6202ab339209904e7c53af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="20c5e-102">IGCHost2::SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="20c5e-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="20c5e-103">層代 0 設定區段的大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="20c5e-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20c5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="20c5e-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20c5e-105">參數</span><span class="sxs-lookup"><span data-stu-id="20c5e-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="20c5e-106">[in]記憶體回收系統所使用的區段大小。</span><span class="sxs-lookup"><span data-stu-id="20c5e-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="20c5e-107">[in]層代 0 的大小上限。</span><span class="sxs-lookup"><span data-stu-id="20c5e-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20c5e-108">備註</span><span class="sxs-lookup"><span data-stu-id="20c5e-108">Remarks</span></span>  
 <span data-ttu-id="20c5e-109">值，`SetGCStartupLimitsEx`可以指定只在主應用程式啟動之前。</span><span class="sxs-lookup"><span data-stu-id="20c5e-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="20c5e-110">無法在稍後變更這些值。</span><span class="sxs-lookup"><span data-stu-id="20c5e-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20c5e-111">需求</span><span class="sxs-lookup"><span data-stu-id="20c5e-111">Requirements</span></span>  
 <span data-ttu-id="20c5e-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="20c5e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20c5e-113">**標頭：** GCHost.idl、 GCHost.h</span><span class="sxs-lookup"><span data-stu-id="20c5e-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="20c5e-114">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="20c5e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20c5e-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20c5e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c5e-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="20c5e-116">See Also</span></span>  
 [<span data-ttu-id="20c5e-117">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="20c5e-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
