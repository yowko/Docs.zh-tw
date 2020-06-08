---
title: ICorProfilerCallback::ClassUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 86402abca5386f34256f1f44f674f1e1898ad5fd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500347"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="626e0-102">ICorProfilerCallback::ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="626e0-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="626e0-103">通知分析工具，類別正在卸載。</span><span class="sxs-lookup"><span data-stu-id="626e0-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="626e0-104">語法</span><span class="sxs-lookup"><span data-stu-id="626e0-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="626e0-105">參數</span><span class="sxs-lookup"><span data-stu-id="626e0-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="626e0-106">\[在中，識別要卸載的類別。</span><span class="sxs-lookup"><span data-stu-id="626e0-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="626e0-107">備註</span><span class="sxs-lookup"><span data-stu-id="626e0-107">Remarks</span></span>  
 <span data-ttu-id="626e0-108">在方法傳回之後，的值 `classId` 對資訊要求無效 `ClassUnloadStarted` ，這是分析工具的最後機會取得此類別的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="626e0-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="626e0-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="626e0-109">Requirements</span></span>  
 <span data-ttu-id="626e0-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="626e0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="626e0-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="626e0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="626e0-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="626e0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="626e0-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="626e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="626e0-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="626e0-114">See also</span></span>

- [<span data-ttu-id="626e0-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="626e0-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="626e0-116">ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="626e0-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
