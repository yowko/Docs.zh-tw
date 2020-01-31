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
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867018"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="69e16-102">COR_PRF_SNAPSHOT_INFO 列舉</span><span class="sxs-lookup"><span data-stu-id="69e16-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="69e16-103">指定在每次呼叫分析工具的[StackSnapshotCallback](stacksnapshotcallback-function.md)函數時，要傳回多少資料給堆疊快照集。</span><span class="sxs-lookup"><span data-stu-id="69e16-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69e16-104">語法</span><span class="sxs-lookup"><span data-stu-id="69e16-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="69e16-105">Members</span><span class="sxs-lookup"><span data-stu-id="69e16-105">Members</span></span>  
  
|<span data-ttu-id="69e16-106">Members</span><span class="sxs-lookup"><span data-stu-id="69e16-106">Members</span></span>|<span data-ttu-id="69e16-107">描述</span><span class="sxs-lookup"><span data-stu-id="69e16-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="69e16-108">表示必須傳遞所有 `StackSnapshotCallback` 參數的值，但 `context` 參數除外。</span><span class="sxs-lookup"><span data-stu-id="69e16-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="69e16-109">表示必須傳遞所有 `StackSnapshotCallback` 參數的值，包括 `context` 參數。</span><span class="sxs-lookup"><span data-stu-id="69e16-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="69e16-110">表示將使用更簡單的替代堆疊流覽演算法。</span><span class="sxs-lookup"><span data-stu-id="69e16-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69e16-111">備註</span><span class="sxs-lookup"><span data-stu-id="69e16-111">Remarks</span></span>  
 <span data-ttu-id="69e16-112">`COR_PRF_SNAPSHOT_INFO` 列舉所提供的值會當做參數傳遞給[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="69e16-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69e16-113">需求</span><span class="sxs-lookup"><span data-stu-id="69e16-113">Requirements</span></span>  
 <span data-ttu-id="69e16-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69e16-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69e16-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="69e16-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69e16-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69e16-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69e16-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69e16-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e16-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="69e16-118">See also</span></span>

- [<span data-ttu-id="69e16-119">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="69e16-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="69e16-120">分析列舉</span><span class="sxs-lookup"><span data-stu-id="69e16-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
