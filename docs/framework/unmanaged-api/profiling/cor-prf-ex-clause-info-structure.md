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
ms.openlocfilehash: fb6d2e5fc21047fea0928137f983c553f9bb2bbd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867278"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="f82e7-102">COR_PRF_EX_CLAUSE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="f82e7-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="f82e7-103">儲存特定例外狀況子句執行個體及其關聯框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f82e7-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="f82e7-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="f82e7-105">Members</span><span class="sxs-lookup"><span data-stu-id="f82e7-105">Members</span></span>  
  
|<span data-ttu-id="f82e7-106">成員</span><span class="sxs-lookup"><span data-stu-id="f82e7-106">Member</span></span>|<span data-ttu-id="f82e7-107">描述</span><span class="sxs-lookup"><span data-stu-id="f82e7-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="f82e7-108">[COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md)列舉的值，指定程式碼剛剛輸入或離開的例外狀況子句類型。</span><span class="sxs-lookup"><span data-stu-id="f82e7-108">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="f82e7-109">子句處理常式的原生進入點，例如 X86 EIP 暫存器的內容。</span><span class="sxs-lookup"><span data-stu-id="f82e7-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="f82e7-110">子句處理常式邏輯框架的指標，例如，X86 EBP 暫存器的內容。</span><span class="sxs-lookup"><span data-stu-id="f82e7-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="f82e7-111">陰影堆疊的指標。</span><span class="sxs-lookup"><span data-stu-id="f82e7-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="f82e7-112">這個值是 BSP 暫存器的內容，只適用于 IA64。</span><span class="sxs-lookup"><span data-stu-id="f82e7-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f82e7-113">備註</span><span class="sxs-lookup"><span data-stu-id="f82e7-113">Remarks</span></span>  
 <span data-ttu-id="f82e7-114">收到例外狀況通知時，可以使用[ICorProfilerInfo2：： GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)來取得即將執行或剛執行的 exception 子句（`catch`/`finally`/filter）的原生位址和框架資訊。</span><span class="sxs-lookup"><span data-stu-id="f82e7-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="f82e7-115">執行 exception 子句牽涉到來自 common language runtime （CLR）的這些回呼：</span><span class="sxs-lookup"><span data-stu-id="f82e7-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="f82e7-116">ICorProfilerCallback：： ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="f82e7-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="f82e7-117">ICorProfilerCallback：： ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="f82e7-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="f82e7-118">ICorProfilerCallback：： ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="f82e7-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="f82e7-119">ICorProfilerCallback：： ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="f82e7-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="f82e7-120">ICorProfilerCallback：： ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="f82e7-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="f82e7-121">ICorProfilerCallback：： ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="f82e7-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="f82e7-122">需求</span><span class="sxs-lookup"><span data-stu-id="f82e7-122">Requirements</span></span>  
 <span data-ttu-id="f82e7-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f82e7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82e7-124">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="f82e7-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f82e7-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f82e7-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f82e7-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82e7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82e7-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="f82e7-127">See also</span></span>

- [<span data-ttu-id="f82e7-128">分析結構</span><span class="sxs-lookup"><span data-stu-id="f82e7-128">Profiling Structures</span></span>](profiling-structures.md)
