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
ms.openlocfilehash: 1149298b4c5e521b37aae6ec48d463f395f18ae3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439566"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="88a95-102">ICorProfilerCallback2::ThreadNameChanged 方法</span><span class="sxs-lookup"><span data-stu-id="88a95-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="88a95-103">通知程式碼分析工具，執行緒的名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="88a95-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88a95-104">語法</span><span class="sxs-lookup"><span data-stu-id="88a95-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88a95-105">參數</span><span class="sxs-lookup"><span data-stu-id="88a95-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="88a95-106">在執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="88a95-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="88a95-107">在執行緒新名稱的長度。</span><span class="sxs-lookup"><span data-stu-id="88a95-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="88a95-108">在執行緒的新名稱。</span><span class="sxs-lookup"><span data-stu-id="88a95-108">[in] The new name of the thread.</span></span> <span data-ttu-id="88a95-109">名稱不是以 null 結束。</span><span class="sxs-lookup"><span data-stu-id="88a95-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88a95-110">需求</span><span class="sxs-lookup"><span data-stu-id="88a95-110">Requirements</span></span>  
 <span data-ttu-id="88a95-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="88a95-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88a95-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88a95-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88a95-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88a95-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88a95-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88a95-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88a95-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88a95-115">See also</span></span>

- [<span data-ttu-id="88a95-116">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="88a95-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="88a95-117">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="88a95-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
