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
ms.openlocfilehash: fba01c1dfdea83b2580f45b7dbcef91fb7b73fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452900"
---
# <a name="icorprofilerinfogetfunctionfromip-method"></a><span data-ttu-id="e8999-102">ICorProfilerInfo::GetFunctionFromIP 方法</span><span class="sxs-lookup"><span data-stu-id="e8999-102">ICorProfilerInfo::GetFunctionFromIP Method</span></span>
<span data-ttu-id="e8999-103">對應的 managed 程式碼指令指標`FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="e8999-103">Maps a managed code instruction pointer to a `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8999-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8999-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromIP(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8999-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8999-105">Parameters</span></span>  
 `ip`  
 <span data-ttu-id="e8999-106">[in]指令指標在 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8999-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="e8999-107">[out]傳回的函式 id。</span><span class="sxs-lookup"><span data-stu-id="e8999-107">[out] The returned function ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8999-108">需求</span><span class="sxs-lookup"><span data-stu-id="e8999-108">Requirements</span></span>  
 <span data-ttu-id="e8999-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8999-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8999-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8999-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8999-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8999-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8999-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8999-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8999-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8999-113">See Also</span></span>  
 [<span data-ttu-id="e8999-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e8999-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
