---
title: ICorProfilerInfo3::GetAppDomainsContainingModule 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5658ac87c7a938381639442216df03853f02998
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195783"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="a8e57-102">ICorProfilerInfo3::GetAppDomainsContainingModule 方法</span><span class="sxs-lookup"><span data-stu-id="a8e57-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="a8e57-103">取得已載入指定模組之應用程式定義域的識別項。</span><span class="sxs-lookup"><span data-stu-id="a8e57-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e57-104">語法</span><span class="sxs-lookup"><span data-stu-id="a8e57-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8e57-105">參數</span><span class="sxs-lookup"><span data-stu-id="a8e57-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a8e57-106">[in] 載入模組的 ID。</span><span class="sxs-lookup"><span data-stu-id="a8e57-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="a8e57-107">[in] `appDomainIds` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="a8e57-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="a8e57-108">[out] 傳回項目之總數的指標。</span><span class="sxs-lookup"><span data-stu-id="a8e57-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="a8e57-109">[out] 應用程式定義域 ID 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="a8e57-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8e57-110">備註</span><span class="sxs-lookup"><span data-stu-id="a8e57-110">Remarks</span></span>  
 <span data-ttu-id="a8e57-111">這個方法會使用呼叫端配置的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a8e57-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8e57-112">需求</span><span class="sxs-lookup"><span data-stu-id="a8e57-112">Requirements</span></span>  
 <span data-ttu-id="a8e57-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a8e57-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8e57-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8e57-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8e57-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8e57-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8e57-116">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8e57-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e57-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8e57-117">See also</span></span>

- [<span data-ttu-id="a8e57-118">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a8e57-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="a8e57-119">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="a8e57-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="a8e57-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="a8e57-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a8e57-121">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="a8e57-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
