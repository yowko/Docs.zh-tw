---
title: ICorProfilerInfo::GetAssemblyInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad4ebe4e1255ce13974063eef3d0a4feeb5dd92b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083048"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="59fa5-102">ICorProfilerInfo::GetAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="59fa5-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="59fa5-103">接受組件識別碼，並傳回組件的名稱及其資訊清單模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="59fa5-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59fa5-104">語法</span><span class="sxs-lookup"><span data-stu-id="59fa5-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59fa5-105">參數</span><span class="sxs-lookup"><span data-stu-id="59fa5-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="59fa5-106">[in] 組件的識別項。</span><span class="sxs-lookup"><span data-stu-id="59fa5-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="59fa5-107">[in] `szName` 的長度 (以字元為單位)。</span><span class="sxs-lookup"><span data-stu-id="59fa5-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="59fa5-108">[out] 組件名稱總字元長度的指標。</span><span class="sxs-lookup"><span data-stu-id="59fa5-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="59fa5-109">[out] 呼叫端提供的寬字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="59fa5-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="59fa5-110">函式傳回時，會包含組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="59fa5-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="59fa5-111">[out] 包含組件之應用程式定義域的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="59fa5-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="59fa5-112">[out] 組件資訊清單模組的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="59fa5-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59fa5-113">備註</span><span class="sxs-lookup"><span data-stu-id="59fa5-113">Remarks</span></span>  
 <span data-ttu-id="59fa5-114">在此方法傳回之後，您必須確認 `szName` 緩衝區的大小足以包含組件的完整檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="59fa5-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="59fa5-115">若要這樣做，請比對 `pcchName` 指向的值和 `cchName` 參數。</span><span class="sxs-lookup"><span data-stu-id="59fa5-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="59fa5-116">如果 `pcchName` 指向大於 `cchName` 的值，請配置較大的 `szName` 緩衝區，並以較大的大小來更新 `cchName`，然後再次呼叫 `GetAssemblyInfo`。</span><span class="sxs-lookup"><span data-stu-id="59fa5-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="59fa5-117">或者，您也可以先使用長度為零的 `szName` 緩衝區來呼叫 `GetAssemblyInfo`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="59fa5-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="59fa5-118">接著您就可以依據 `pcchName` 中傳回的值來調整緩衝區大小，並再次呼叫 `GetAssemblyInfo`。</span><span class="sxs-lookup"><span data-stu-id="59fa5-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59fa5-119">需求</span><span class="sxs-lookup"><span data-stu-id="59fa5-119">Requirements</span></span>  
 <span data-ttu-id="59fa5-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59fa5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59fa5-121">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="59fa5-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="59fa5-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59fa5-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="59fa5-123">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="59fa5-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="59fa5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59fa5-124">See also</span></span>

- [<span data-ttu-id="59fa5-125">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="59fa5-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="59fa5-126">分析介面</span><span class="sxs-lookup"><span data-stu-id="59fa5-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="59fa5-127">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="59fa5-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
