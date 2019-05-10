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
ms.openlocfilehash: 148ca261e717b9a54192a13c317fe385b98f4ccd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651168"
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="50f4d-102">COR_PRF_EX_CLAUSE_INFO 結構</span><span class="sxs-lookup"><span data-stu-id="50f4d-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="50f4d-103">儲存特定例外狀況子句執行個體及其關聯框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="50f4d-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="50f4d-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="50f4d-105">成員</span><span class="sxs-lookup"><span data-stu-id="50f4d-105">Members</span></span>  
  
|<span data-ttu-id="50f4d-106">成員</span><span class="sxs-lookup"><span data-stu-id="50f4d-106">Member</span></span>|<span data-ttu-id="50f4d-107">描述</span><span class="sxs-lookup"><span data-stu-id="50f4d-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="50f4d-108">值為[COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)列舉，指定例外狀況子句剛才輸入的程式碼或左邊的型別。</span><span class="sxs-lookup"><span data-stu-id="50f4d-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="50f4d-109">子句處理常式的原生進入點 — 比方說，X86 EIP 暫存器的內容。</span><span class="sxs-lookup"><span data-stu-id="50f4d-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="50f4d-110">子句處理常式的邏輯框架指標 — 比方說，X86 EBP 暫存器的內容。</span><span class="sxs-lookup"><span data-stu-id="50f4d-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="50f4d-111">陰影堆疊指標。</span><span class="sxs-lookup"><span data-stu-id="50f4d-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="50f4d-112">這個值會是 BSP 暫存器的內容，而且只適用於 IA64。</span><span class="sxs-lookup"><span data-stu-id="50f4d-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50f4d-113">備註</span><span class="sxs-lookup"><span data-stu-id="50f4d-113">Remarks</span></span>  
 <span data-ttu-id="50f4d-114">當收到的例外狀況通知時， [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)可用來取得例外狀況子句的原生位址及畫面格資訊 (`catch` / `finally`/篩選)，是要執行或剛執行。</span><span class="sxs-lookup"><span data-stu-id="50f4d-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="50f4d-115">例外狀況子句執行包含 common language runtime (CLR) 從這些回呼：</span><span class="sxs-lookup"><span data-stu-id="50f4d-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="50f4d-116">ICorProfilerCallback::ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="50f4d-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="50f4d-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="50f4d-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="50f4d-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="50f4d-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="50f4d-119">ICorProfilerCallback::ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="50f4d-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="50f4d-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="50f4d-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="50f4d-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="50f4d-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="50f4d-122">需求</span><span class="sxs-lookup"><span data-stu-id="50f4d-122">Requirements</span></span>  
 <span data-ttu-id="50f4d-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50f4d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50f4d-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="50f4d-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="50f4d-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50f4d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50f4d-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50f4d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f4d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50f4d-127">See also</span></span>

- [<span data-ttu-id="50f4d-128">分析結構</span><span class="sxs-lookup"><span data-stu-id="50f4d-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
