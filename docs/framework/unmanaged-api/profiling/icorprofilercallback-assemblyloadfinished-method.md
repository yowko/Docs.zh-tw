---
title: ICorProfilerCallback::AssemblyLoadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: 15ce195af0c0e8f8777f6e5d02043e17e32308da
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866640"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="abb16-102">ICorProfilerCallback::AssemblyLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="abb16-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="abb16-103">通知分析工具元件已完成載入。</span><span class="sxs-lookup"><span data-stu-id="abb16-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb16-104">語法</span><span class="sxs-lookup"><span data-stu-id="abb16-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abb16-105">參數</span><span class="sxs-lookup"><span data-stu-id="abb16-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="abb16-106">中的 \[] 識別已載入的元件。</span><span class="sxs-lookup"><span data-stu-id="abb16-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="abb16-107">\[in]） HRESULT，指出元件是否已成功載入。</span><span class="sxs-lookup"><span data-stu-id="abb16-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="abb16-108">備註</span><span class="sxs-lookup"><span data-stu-id="abb16-108">Remarks</span></span>  
 <span data-ttu-id="abb16-109">在呼叫 `AssemblyLoadFinished` 方法之前，`assemblyId` 的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="abb16-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="abb16-110">載入元件的某些部分可能會在 `AssemblyLoadFinished` 回呼之後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="abb16-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="abb16-111">`hrStatus` 中的失敗 HRESULT 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="abb16-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="abb16-112">不過，`hrStatus` 中的成功 HRESULT 只會指出載入元件的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="abb16-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb16-113">需求</span><span class="sxs-lookup"><span data-stu-id="abb16-113">Requirements</span></span>  
 <span data-ttu-id="abb16-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abb16-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abb16-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abb16-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abb16-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abb16-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abb16-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abb16-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb16-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="abb16-118">See also</span></span>

- [<span data-ttu-id="abb16-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="abb16-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
