---
title: "ICorProfilerInfo::GetModuleInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8309b57f2940805e23010feac17b6d37f1a58af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="c6427-102">ICorProfilerInfo::GetModuleInfo 方法</span><span class="sxs-lookup"><span data-stu-id="c6427-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="c6427-103">根據模組 ID，傳回模組的檔案名稱和模組的父組件 ID。</span><span class="sxs-lookup"><span data-stu-id="c6427-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6427-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6427-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6427-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6427-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c6427-106">[in] 將被擷取資訊的模組 ID。</span><span class="sxs-lookup"><span data-stu-id="c6427-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="c6427-107">[out] 載入模組的基底位址。</span><span class="sxs-lookup"><span data-stu-id="c6427-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c6427-108">[in] `szName` 傳回緩衝區的長度 (以字元為單位)。</span><span class="sxs-lookup"><span data-stu-id="c6427-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c6427-109">[out] 所傳回的模組檔案名稱之總字元長度的指標。</span><span class="sxs-lookup"><span data-stu-id="c6427-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="c6427-110">[out] 呼叫端提供的寬字元緩衝區。</span><span class="sxs-lookup"><span data-stu-id="c6427-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="c6427-111">當方法傳回時，這個緩衝區會包含模組的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c6427-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="c6427-112">[out] 模組父組件之 ID 的指標。</span><span class="sxs-lookup"><span data-stu-id="c6427-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6427-113">備註</span><span class="sxs-lookup"><span data-stu-id="c6427-113">Remarks</span></span>  
 <span data-ttu-id="c6427-114">若為動態模組，則 `szName` 參數為空字串，且基底位址為 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="c6427-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="c6427-115">雖然`GetModuleInfo`可以呼叫方法，只要有模組 ID，無法使用的父組件的識別碼，直到分析工具收到[icorprofilercallback:: Moduleattachedtoassembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="c6427-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="c6427-116">當 `GetModuleInfo` 傳回時，您必須確認 `szName` 緩衝區的大小足以包含模組的完整檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c6427-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="c6427-117">若要執行這項作業，請比較 `pcchName` 指向的值和 `cchName` 參數的值。</span><span class="sxs-lookup"><span data-stu-id="c6427-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="c6427-118">如果 `pcchName` 指向大於 `cchName` 的值，請配置較大的 `szName` 緩衝區，並以較大的大小來更新 `cchName`，然後再次呼叫 `GetModuleInfo`。</span><span class="sxs-lookup"><span data-stu-id="c6427-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="c6427-119">此外，您可以先使用長度為零的 `szName` 緩衝區來呼叫 `GetModuleInfo`，以取得正確的緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="c6427-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="c6427-120">接著您就可以將緩衝區大小設定為 `pcchName` 中傳回的值，並再次呼叫 `GetModuleInfo`。</span><span class="sxs-lookup"><span data-stu-id="c6427-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6427-121">需求</span><span class="sxs-lookup"><span data-stu-id="c6427-121">Requirements</span></span>  
 <span data-ttu-id="c6427-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6427-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6427-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c6427-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6427-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6427-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6427-125">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6427-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6427-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="c6427-126">See Also</span></span>  
 [<span data-ttu-id="c6427-127">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c6427-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c6427-128">分析介面</span><span class="sxs-lookup"><span data-stu-id="c6427-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c6427-129">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="c6427-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [<span data-ttu-id="c6427-130">GetModuleInfo2 方法</span><span class="sxs-lookup"><span data-stu-id="c6427-130">GetModuleInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
