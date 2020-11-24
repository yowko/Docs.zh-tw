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
ms.openlocfilehash: fd41463af0acac1bbe1a3d4515350905b6784f79
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685326"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="10a8e-102">ICorProfilerCallback::AssemblyLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="10a8e-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>

<span data-ttu-id="10a8e-103">通知 profiler 元件已完成載入。</span><span class="sxs-lookup"><span data-stu-id="10a8e-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10a8e-104">語法</span><span class="sxs-lookup"><span data-stu-id="10a8e-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10a8e-105">參數</span><span class="sxs-lookup"><span data-stu-id="10a8e-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="10a8e-106">\[in] 識別載入的元件。</span><span class="sxs-lookup"><span data-stu-id="10a8e-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="10a8e-107">\[in] 表示元件是否已順利載入的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="10a8e-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="10a8e-108">備註</span><span class="sxs-lookup"><span data-stu-id="10a8e-108">Remarks</span></span>  

 <span data-ttu-id="10a8e-109">在呼叫方法之前，的值對 `assemblyId` 資訊要求而言是不正確 `AssemblyLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="10a8e-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="10a8e-110">載入元件的某些部分可能會在回呼之後繼續進行 `AssemblyLoadFinished` 。</span><span class="sxs-lookup"><span data-stu-id="10a8e-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="10a8e-111">中的失敗 HRESULT `hrStatus` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="10a8e-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="10a8e-112">但是，中的成功 HRESULT `hrStatus` 只會指出載入元件的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="10a8e-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10a8e-113">需求</span><span class="sxs-lookup"><span data-stu-id="10a8e-113">Requirements</span></span>  

 <span data-ttu-id="10a8e-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10a8e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10a8e-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10a8e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10a8e-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10a8e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10a8e-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10a8e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a8e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10a8e-118">See also</span></span>

- [<span data-ttu-id="10a8e-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="10a8e-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
