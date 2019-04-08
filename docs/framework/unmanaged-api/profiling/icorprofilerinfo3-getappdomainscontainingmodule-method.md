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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195783"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="6c089-102">ICorProfilerInfo3::GetAppDomainsContainingModule 方法</span><span class="sxs-lookup"><span data-stu-id="6c089-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="6c089-103">取得已載入指定模組之應用程式定義域的識別項。</span><span class="sxs-lookup"><span data-stu-id="6c089-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c089-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c089-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c089-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c089-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="6c089-106">[in] 載入模組的 ID。</span><span class="sxs-lookup"><span data-stu-id="6c089-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="6c089-107">[in] `appDomainIds` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="6c089-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="6c089-108">[out] 傳回項目之總數的指標。</span><span class="sxs-lookup"><span data-stu-id="6c089-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="6c089-109">[out] 應用程式定義域 ID 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="6c089-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c089-110">備註</span><span class="sxs-lookup"><span data-stu-id="6c089-110">Remarks</span></span>  
 <span data-ttu-id="6c089-111">這個方法會使用呼叫端配置的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6c089-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c089-112">需求</span><span class="sxs-lookup"><span data-stu-id="6c089-112">Requirements</span></span>  
 <span data-ttu-id="6c089-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c089-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c089-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c089-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c089-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c089-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6c089-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6c089-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6c089-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c089-117">See also</span></span>

- [<span data-ttu-id="6c089-118">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="6c089-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="6c089-119">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="6c089-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="6c089-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="6c089-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6c089-121">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="6c089-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
