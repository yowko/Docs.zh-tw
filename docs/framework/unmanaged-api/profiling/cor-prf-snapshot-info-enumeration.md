---
title: "COR_PRF_SNAPSHOT_INFO 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SNAPSHOT_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SNAPSHOT_INFO
helpviewer_keywords: COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a9c854360881426f2fc7fc9e401da1dc93b9bd84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="a496f-102">COR_PRF_SNAPSHOT_INFO 列舉</span><span class="sxs-lookup"><span data-stu-id="a496f-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="a496f-103">指定要傳遞的資料量隨同堆疊中的快照集每次呼叫程式碼剖析工具[StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="a496f-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a496f-104">語法</span><span class="sxs-lookup"><span data-stu-id="a496f-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a496f-105">成員</span><span class="sxs-lookup"><span data-stu-id="a496f-105">Members</span></span>  
  
|<span data-ttu-id="a496f-106">Members</span><span class="sxs-lookup"><span data-stu-id="a496f-106">Members</span></span>|<span data-ttu-id="a496f-107">說明</span><span class="sxs-lookup"><span data-stu-id="a496f-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="a496f-108">表示值必須針對所有傳遞`StackSnapshotCallback`參數，除了`context`參數。</span><span class="sxs-lookup"><span data-stu-id="a496f-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="a496f-109">表示值必須針對所有傳遞`StackSnapshotCallback`參數，包括`context`參數。</span><span class="sxs-lookup"><span data-stu-id="a496f-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="a496f-110">表示將會使用更簡單、 替代的堆疊查核行程演算法。</span><span class="sxs-lookup"><span data-stu-id="a496f-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a496f-111">備註</span><span class="sxs-lookup"><span data-stu-id="a496f-111">Remarks</span></span>  
 <span data-ttu-id="a496f-112">所提供的值`COR_PRF_SNAPSHOT_INFO`列舉型別會當做參數傳遞給[DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a496f-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a496f-113">需求</span><span class="sxs-lookup"><span data-stu-id="a496f-113">Requirements</span></span>  
 <span data-ttu-id="a496f-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a496f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a496f-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a496f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a496f-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a496f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a496f-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a496f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a496f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a496f-118">See Also</span></span>  
 [<span data-ttu-id="a496f-119">DoStackSnapshot 方法</span><span class="sxs-lookup"><span data-stu-id="a496f-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="a496f-120">分析列舉</span><span class="sxs-lookup"><span data-stu-id="a496f-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
