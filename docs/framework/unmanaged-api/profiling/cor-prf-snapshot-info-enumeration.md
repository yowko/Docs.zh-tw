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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa85fb2cebb47ecbd7b0f091cb79f6ea0936b1cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598996"
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="f5148-102">COR_PRF_SNAPSHOT_INFO 列舉</span><span class="sxs-lookup"><span data-stu-id="f5148-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="f5148-103">指定要傳遞的資料與分析工具的每個呼叫堆疊快照的備份多少[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f5148-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5148-104">語法</span><span class="sxs-lookup"><span data-stu-id="f5148-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f5148-105">成員</span><span class="sxs-lookup"><span data-stu-id="f5148-105">Members</span></span>  
  
|<span data-ttu-id="f5148-106">成員</span><span class="sxs-lookup"><span data-stu-id="f5148-106">Members</span></span>|<span data-ttu-id="f5148-107">描述</span><span class="sxs-lookup"><span data-stu-id="f5148-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="f5148-108">指出，必須針對所有傳遞值`StackSnapshotCallback`參數，除了`context`參數。</span><span class="sxs-lookup"><span data-stu-id="f5148-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="f5148-109">指出，必須針對所有傳遞值`StackSnapshotCallback`參數，包括`context`參數。</span><span class="sxs-lookup"><span data-stu-id="f5148-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="f5148-110">表示將會使用更簡單、 替代的堆疊查核行程演算法。</span><span class="sxs-lookup"><span data-stu-id="f5148-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5148-111">備註</span><span class="sxs-lookup"><span data-stu-id="f5148-111">Remarks</span></span>  
 <span data-ttu-id="f5148-112">所提供的值`COR_PRF_SNAPSHOT_INFO`列舉型別傳遞做為參數[DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f5148-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5148-113">需求</span><span class="sxs-lookup"><span data-stu-id="f5148-113">Requirements</span></span>  
 <span data-ttu-id="f5148-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5148-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5148-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5148-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5148-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5148-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5148-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5148-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5148-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5148-118">See also</span></span>

- [<span data-ttu-id="f5148-119">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="f5148-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="f5148-120">分析列舉</span><span class="sxs-lookup"><span data-stu-id="f5148-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
