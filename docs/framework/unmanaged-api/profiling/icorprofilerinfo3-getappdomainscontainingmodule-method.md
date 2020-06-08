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
ms.openlocfilehash: 8615deb2e42b039120d97b3eb5af23beb31b0808
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502843"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="d71ce-102">ICorProfilerInfo3::GetAppDomainsContainingModule 方法</span><span class="sxs-lookup"><span data-stu-id="d71ce-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="d71ce-103">取得已載入指定模組之應用程式定義域的識別項。</span><span class="sxs-lookup"><span data-stu-id="d71ce-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="d71ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d71ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="d71ce-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="d71ce-106">[in] 載入模組的 ID。</span><span class="sxs-lookup"><span data-stu-id="d71ce-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="d71ce-107">[in] `appDomainIds` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="d71ce-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="d71ce-108">[out] 傳回項目之總數的指標。</span><span class="sxs-lookup"><span data-stu-id="d71ce-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="d71ce-109">[out] 應用程式定義域 ID 值的陣列。</span><span class="sxs-lookup"><span data-stu-id="d71ce-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d71ce-110">備註</span><span class="sxs-lookup"><span data-stu-id="d71ce-110">Remarks</span></span>  
 <span data-ttu-id="d71ce-111">這個方法會使用呼叫端配置的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d71ce-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d71ce-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="d71ce-112">Requirements</span></span>  
 <span data-ttu-id="d71ce-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d71ce-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d71ce-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d71ce-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d71ce-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d71ce-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d71ce-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d71ce-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71ce-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d71ce-117">See also</span></span>

- [<span data-ttu-id="d71ce-118">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="d71ce-118">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="d71ce-119">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="d71ce-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d71ce-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="d71ce-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d71ce-121">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="d71ce-121">Profiling</span></span>](index.md)
