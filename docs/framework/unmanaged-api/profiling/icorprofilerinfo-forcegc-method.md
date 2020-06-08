---
title: ICorProfilerInfo::ForceGC 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 9bc6619f3ef383c7bf60a310a87f056cfc43cddf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498670"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="97433-102">ICorProfilerInfo::ForceGC 方法</span><span class="sxs-lookup"><span data-stu-id="97433-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="97433-103">強制在 common language runtime （CLR）中進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="97433-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97433-104">語法</span><span class="sxs-lookup"><span data-stu-id="97433-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="97433-105">備註</span><span class="sxs-lookup"><span data-stu-id="97433-105">Remarks</span></span>  
 <span data-ttu-id="97433-106">`ForceGC`方法只能從從未執行 managed 程式碼，且在其堆疊上沒有任何 profiler 回呼的執行緒中呼叫。</span><span class="sxs-lookup"><span data-stu-id="97433-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="97433-107">最方便的執行方式是在分析工具內建立另一個執行緒，以在 `ForceGC` 收到信號時呼叫。</span><span class="sxs-lookup"><span data-stu-id="97433-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97433-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="97433-108">Requirements</span></span>  
 <span data-ttu-id="97433-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97433-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97433-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97433-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97433-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97433-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97433-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97433-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97433-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97433-113">See also</span></span>

- [<span data-ttu-id="97433-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="97433-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
