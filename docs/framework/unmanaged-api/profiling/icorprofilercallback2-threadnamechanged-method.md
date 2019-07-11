---
title: ICorProfilerCallback2::ThreadNameChanged 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ffe25cae7122e65bed6aece7b0f6b2abe82c1eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779289"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="ee889-102">ICorProfilerCallback2::ThreadNameChanged 方法</span><span class="sxs-lookup"><span data-stu-id="ee889-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="ee889-103">通知程式碼剖析工具，執行緒的名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="ee889-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee889-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee889-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee889-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee889-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ee889-106">[in]執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="ee889-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ee889-107">[in]執行緒的新名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="ee889-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="ee889-108">[in]執行緒的新名稱。</span><span class="sxs-lookup"><span data-stu-id="ee889-108">[in] The new name of the thread.</span></span> <span data-ttu-id="ee889-109">名稱不是 null 終止的。</span><span class="sxs-lookup"><span data-stu-id="ee889-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee889-110">需求</span><span class="sxs-lookup"><span data-stu-id="ee889-110">Requirements</span></span>  
 <span data-ttu-id="ee889-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee889-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee889-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee889-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee889-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee889-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee889-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee889-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee889-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee889-115">See also</span></span>

- [<span data-ttu-id="ee889-116">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ee889-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ee889-117">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="ee889-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
