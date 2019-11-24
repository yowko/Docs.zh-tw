---
title: COR_PRF_SNAPSHOT_INFO 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 6ade4f7877e39a8307a36f3a3268f79e8b4d44fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427265"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="1b8c8-102">COR_PRF_SNAPSHOT_INFO 列舉</span><span class="sxs-lookup"><span data-stu-id="1b8c8-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="1b8c8-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span><span class="sxs-lookup"><span data-stu-id="1b8c8-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b8c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b8c8-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="1b8c8-105">Members</span><span class="sxs-lookup"><span data-stu-id="1b8c8-105">Members</span></span>  
  
|<span data-ttu-id="1b8c8-106">Members</span><span class="sxs-lookup"><span data-stu-id="1b8c8-106">Members</span></span>|<span data-ttu-id="1b8c8-107">描述</span><span class="sxs-lookup"><span data-stu-id="1b8c8-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="1b8c8-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span><span class="sxs-lookup"><span data-stu-id="1b8c8-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="1b8c8-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span><span class="sxs-lookup"><span data-stu-id="1b8c8-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="1b8c8-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span><span class="sxs-lookup"><span data-stu-id="1b8c8-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b8c8-111">備註</span><span class="sxs-lookup"><span data-stu-id="1b8c8-111">Remarks</span></span>  
 <span data-ttu-id="1b8c8-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="1b8c8-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b8c8-113">需求</span><span class="sxs-lookup"><span data-stu-id="1b8c8-113">Requirements</span></span>  
 <span data-ttu-id="1b8c8-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b8c8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b8c8-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b8c8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b8c8-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b8c8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b8c8-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b8c8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b8c8-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="1b8c8-118">See also</span></span>

- [<span data-ttu-id="1b8c8-119">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="1b8c8-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="1b8c8-120">分析列舉</span><span class="sxs-lookup"><span data-stu-id="1b8c8-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
