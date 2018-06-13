---
title: COR_PRF_EX_CLAUSE_INFO 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3cf8b8735fc10b741d13b041eedc3e96607bef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450111"
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="b85be-102">COR_PRF_EX_CLAUSE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="b85be-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="b85be-103">儲存特定例外狀況子句執行個體及其關聯框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b85be-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b85be-104">語法</span><span class="sxs-lookup"><span data-stu-id="b85be-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b85be-105">成員</span><span class="sxs-lookup"><span data-stu-id="b85be-105">Members</span></span>  
  
|<span data-ttu-id="b85be-106">成員</span><span class="sxs-lookup"><span data-stu-id="b85be-106">Member</span></span>|<span data-ttu-id="b85be-107">描述</span><span class="sxs-lookup"><span data-stu-id="b85be-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="b85be-108">值為[COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)列舉，指定例外狀況子句的程式碼輸入或留下的類型。</span><span class="sxs-lookup"><span data-stu-id="b85be-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="b85be-109">子句的處理常式的原生進入點 — 比方說，X86 EIP 暫存器的內容。</span><span class="sxs-lookup"><span data-stu-id="b85be-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="b85be-110">子句的處理常式的邏輯框架指標 — 比方說，X86 EBP 暫存器的內容。</span><span class="sxs-lookup"><span data-stu-id="b85be-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="b85be-111">陰影堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="b85be-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="b85be-112">此值是 BSP 暫存器的內容，而且只適用於 IA64。</span><span class="sxs-lookup"><span data-stu-id="b85be-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b85be-113">備註</span><span class="sxs-lookup"><span data-stu-id="b85be-113">Remarks</span></span>  
 <span data-ttu-id="b85be-114">例外狀況會收到通知， [icorprofilerinfo2:: Getnotifiedexceptionclauseinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)可以用來取得例外狀況子句的原生位址和框架資訊 (`catch` / `finally`/篩選) 是即將執行或剛執行。</span><span class="sxs-lookup"><span data-stu-id="b85be-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="b85be-115">例外狀況子句執行包含這些回呼，從 common language runtime (CLR):</span><span class="sxs-lookup"><span data-stu-id="b85be-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="b85be-116">Icorprofilercallback:: Exceptioncatcherenter</span><span class="sxs-lookup"><span data-stu-id="b85be-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="b85be-117">Icorprofilercallback:: Exceptionunwindfinallyenter</span><span class="sxs-lookup"><span data-stu-id="b85be-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="b85be-118">Icorprofilercallback:: Exceptionsearchfilterenter</span><span class="sxs-lookup"><span data-stu-id="b85be-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="b85be-119">Icorprofilercallback:: Exceptioncatcherleave</span><span class="sxs-lookup"><span data-stu-id="b85be-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="b85be-120">Icorprofilercallback:: Exceptionunwindfinallyleave</span><span class="sxs-lookup"><span data-stu-id="b85be-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="b85be-121">Icorprofilercallback:: Exceptionsearchfilterleave</span><span class="sxs-lookup"><span data-stu-id="b85be-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="b85be-122">需求</span><span class="sxs-lookup"><span data-stu-id="b85be-122">Requirements</span></span>  
 <span data-ttu-id="b85be-123">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b85be-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b85be-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b85be-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b85be-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b85be-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b85be-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b85be-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85be-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b85be-127">See Also</span></span>  
 [<span data-ttu-id="b85be-128">分析結構</span><span class="sxs-lookup"><span data-stu-id="b85be-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
