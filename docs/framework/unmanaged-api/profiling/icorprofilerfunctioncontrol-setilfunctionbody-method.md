---
title: ICorProfilerFunctionControl::SetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5b6cab555144c25c5984d74d19d5e81aa1a196d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454962"
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a><span data-ttu-id="8b7bb-102">ICorProfilerFunctionControl::SetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="8b7bb-102">ICorProfilerFunctionControl::SetILFunctionBody Method</span></span>
<span data-ttu-id="8b7bb-103">取代方法的 Common Intermediate Language (CIL) 主體。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-103">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b7bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b7bb-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b7bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b7bb-105">Parameters</span></span>  
 `cbNewILMethodHeader`  
 <span data-ttu-id="8b7bb-106">[in] 新 CIL 的大小總計，包括主體後面的標頭和任何結構。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-106">[in] The total size of the new CIL, including the header and any structures that come after the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="8b7bb-107">[in] 新 CIL 標頭的指標。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-107">[in] A pointer to the new CIL header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b7bb-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="8b7bb-108">Return Value</span></span>  
 <span data-ttu-id="8b7bb-109">這個方法會傳回下列特定的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-109">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="8b7bb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b7bb-110">HRESULT</span></span>|<span data-ttu-id="8b7bb-111">描述</span><span class="sxs-lookup"><span data-stu-id="8b7bb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b7bb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b7bb-112">S_OK</span></span>|<span data-ttu-id="8b7bb-113">取代成功。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-113">The replacement was successful.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b7bb-114">備註</span><span class="sxs-lookup"><span data-stu-id="8b7bb-114">Remarks</span></span>  
 <span data-ttu-id="8b7bb-115">不同於[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法，`SetILFunctionBody`方法會管理新 CIL 主體所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-115">Unlike the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, the `SetILFunctionBody` method manages the memory required for the new CIL body.</span></span> <span data-ttu-id="8b7bb-116">這表示分析工具所提供的 CIL 主體不需要使用[IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)介面或配置特定範圍內。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-116">This means that the CIL body provided by the profiler does not have to be allocated by using the [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface or allocated within a particular range.</span></span> <span data-ttu-id="8b7bb-117">它可以配置於任何堆積上。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-117">It can be allocated on any heap.</span></span> <span data-ttu-id="8b7bb-118">分析工具可以釋放用於其 CIL 主體之後, 的記憶體`SetILFunctionBody`傳回。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-118">The profiler can free the memory used for its CIL body after `SetILFunctionBody` returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b7bb-119">需求</span><span class="sxs-lookup"><span data-stu-id="8b7bb-119">Requirements</span></span>  
 <span data-ttu-id="8b7bb-120">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b7bb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b7bb-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b7bb-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b7bb-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b7bb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b7bb-123">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b7bb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7bb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b7bb-124">See Also</span></span>  
 [<span data-ttu-id="8b7bb-125">ICorProfilerFunctionControl 介面</span><span class="sxs-lookup"><span data-stu-id="8b7bb-125">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
