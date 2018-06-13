---
title: ICorProfilerInfo2::GetRVAStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ee12131cfa323d4426ab06ea31be4a8dd7b4583
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455461"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="e2050-102">ICorProfilerInfo2::GetRVAStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="e2050-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="e2050-103">取得指定的相對虛擬位址 (RVA) 靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="e2050-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2050-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2050-104">Syntax</span></span>  
  
```  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2050-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2050-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e2050-106">[in]包含要求的 RVA 靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="e2050-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e2050-107">[in]要求的 RVA 靜態欄位的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e2050-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e2050-108">[out]RVA 靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e2050-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2050-109">備註</span><span class="sxs-lookup"><span data-stu-id="e2050-109">Remarks</span></span>  
 <span data-ttu-id="e2050-110">`GetRVAStaticAddress`方法可能會傳回下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="e2050-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="e2050-111">如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e2050-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="e2050-112">可能會在記憶體回收堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="e2050-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e2050-113">這些位址可能會變成記憶體回收之後, 無效，所以記憶體回收之後, 程式碼剖析工具不應該假設都有效。</span><span class="sxs-lookup"><span data-stu-id="e2050-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e2050-114">類別的類別建構函式完成之前，`GetRVAStaticAddress`會針對所有的靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然的靜態欄位的部分可能已初始化，且可能會為根建立的記憶體回收物件。</span><span class="sxs-lookup"><span data-stu-id="e2050-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2050-115">需求</span><span class="sxs-lookup"><span data-stu-id="e2050-115">Requirements</span></span>  
 <span data-ttu-id="e2050-116">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2050-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2050-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e2050-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e2050-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2050-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2050-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2050-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2050-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2050-120">See Also</span></span>  
 [<span data-ttu-id="e2050-121">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e2050-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e2050-122">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="e2050-122">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
