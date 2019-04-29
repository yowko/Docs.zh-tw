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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5e90055a08227ea7cb7fa1b459fe6f5f3a81fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763213"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="b0f5b-102">IGCHost2::SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="b0f5b-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="b0f5b-103">層代 0 設定區段的大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="b0f5b-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0f5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0f5b-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0f5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="b0f5b-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="b0f5b-106">[in]記憶體回收系統所使用的區段大小。</span><span class="sxs-lookup"><span data-stu-id="b0f5b-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="b0f5b-107">[in]層代 0 的大小上限。</span><span class="sxs-lookup"><span data-stu-id="b0f5b-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0f5b-108">備註</span><span class="sxs-lookup"><span data-stu-id="b0f5b-108">Remarks</span></span>  
 <span data-ttu-id="b0f5b-109">值，`SetGCStartupLimitsEx`只在主應用程式啟動之前，可以指定設定。</span><span class="sxs-lookup"><span data-stu-id="b0f5b-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="b0f5b-110">稍後無法變更這些值。</span><span class="sxs-lookup"><span data-stu-id="b0f5b-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0f5b-111">需求</span><span class="sxs-lookup"><span data-stu-id="b0f5b-111">Requirements</span></span>  
 <span data-ttu-id="b0f5b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0f5b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0f5b-113">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b0f5b-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b0f5b-114">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b0f5b-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0f5b-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0f5b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0f5b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0f5b-116">See also</span></span>

- [<span data-ttu-id="b0f5b-117">IGCHost2 介面</span><span class="sxs-lookup"><span data-stu-id="b0f5b-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
