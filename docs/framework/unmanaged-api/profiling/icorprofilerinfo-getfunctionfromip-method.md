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
ms.openlocfilehash: cd1f3982fe1439135bf96579370a5a798c61dd2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863773"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="74b12-102">ICorProfilerInfo::GetFunctionFromIP 方法</span><span class="sxs-lookup"><span data-stu-id="74b12-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="74b12-103">將 managed 程式碼指令指標對應至 `FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="74b12-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b12-104">語法</span><span class="sxs-lookup"><span data-stu-id="74b12-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74b12-105">參數</span><span class="sxs-lookup"><span data-stu-id="74b12-105">Parameters</span></span>

- `ip`

  <span data-ttu-id="74b12-106">中的 \[] managed 程式碼中的指令指標。</span><span class="sxs-lookup"><span data-stu-id="74b12-106">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="74b12-107">\[out] 傳回的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="74b12-107">\[out] The returned function ID.</span></span>

## <a name="requirements"></a><span data-ttu-id="74b12-108">需求</span><span class="sxs-lookup"><span data-stu-id="74b12-108">Requirements</span></span>  
 <span data-ttu-id="74b12-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74b12-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74b12-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74b12-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74b12-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74b12-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74b12-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74b12-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b12-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="74b12-113">See also</span></span>

- [<span data-ttu-id="74b12-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="74b12-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
