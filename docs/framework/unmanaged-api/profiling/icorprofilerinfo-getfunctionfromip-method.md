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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a9f6e63a1f24043ac502d139f735cada599df4f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780675"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="29b3a-102">ICorProfilerInfo::GetFunctionFromIP 方法</span><span class="sxs-lookup"><span data-stu-id="29b3a-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="29b3a-103">對應的 managed 程式碼指令指標`FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="29b3a-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="29b3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29b3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="29b3a-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="29b3a-106">[in]在 managed 程式碼指令指標。</span><span class="sxs-lookup"><span data-stu-id="29b3a-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="29b3a-107">[out]傳回的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="29b3a-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b3a-108">需求</span><span class="sxs-lookup"><span data-stu-id="29b3a-108">Requirements</span></span>  
 <span data-ttu-id="29b3a-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29b3a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29b3a-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="29b3a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29b3a-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29b3a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29b3a-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29b3a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b3a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29b3a-113">See also</span></span>

- [<span data-ttu-id="29b3a-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="29b3a-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
