---
title: ICorProfilerInfo::GetFunctionFromIP 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromIP
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromIP
helpviewer_keywords:
- GetFunctionFromIP method [.NET Framework profiling]
- ICorProfilerInfo::GetFunctionFromIP method [.NET Framework profiling]
ms.assetid: f069802a-198f-46dd-9f09-4f77adffc9ba
topic_type:
- apiref
ms.openlocfilehash: 14b152474cd71dc3ff7b59c94b6ec4fa0cd7ce0c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439206"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="dd386-102">ICorProfilerInfo::GetFunctionFromIP 方法</span><span class="sxs-lookup"><span data-stu-id="dd386-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="dd386-103">Maps a managed code instruction pointer to a `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="dd386-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd386-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd386-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd386-105">參數</span><span class="sxs-lookup"><span data-stu-id="dd386-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="dd386-106">[in] The instruction pointer in managed code.</span><span class="sxs-lookup"><span data-stu-id="dd386-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="dd386-107">[out] The returned function ID.</span><span class="sxs-lookup"><span data-stu-id="dd386-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd386-108">需求</span><span class="sxs-lookup"><span data-stu-id="dd386-108">Requirements</span></span>  
 <span data-ttu-id="dd386-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dd386-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd386-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd386-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd386-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd386-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd386-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd386-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd386-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd386-113">See also</span></span>

- [<span data-ttu-id="dd386-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="dd386-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
