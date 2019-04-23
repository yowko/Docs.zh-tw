---
title: ICorProfilerInfo2::GetContextStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46fd79931e7f2f05b1b17ebca3f8cff28c152ff4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221423"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="13504-102">ICorProfilerInfo2::GetContextStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="13504-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="13504-103">取得在指定之內容的範圍中指定內容靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="13504-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13504-104">語法</span><span class="sxs-lookup"><span data-stu-id="13504-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13504-105">參數</span><span class="sxs-lookup"><span data-stu-id="13504-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="13504-106">[in]包含要求的內容靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="13504-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="13504-107">[in]要求的內容靜態欄位的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="13504-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="13504-108">[in]要求的內容靜態欄位的範圍的內容識別碼。</span><span class="sxs-lookup"><span data-stu-id="13504-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="13504-109">[out]在指定的內容內的靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="13504-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13504-110">備註</span><span class="sxs-lookup"><span data-stu-id="13504-110">Remarks</span></span>  
 <span data-ttu-id="13504-111">`GetContextStaticAddress`方法可能會傳回下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="13504-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="13504-112">如果指定的靜態欄位尚未指派指定的內容中的地址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="13504-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="13504-113">可能在記憶體回收堆積中物件的位址。</span><span class="sxs-lookup"><span data-stu-id="13504-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="13504-114">這些位址可能會變成無效記憶體回收之後，讓記憶體回收之後, 程式碼剖析工具不應該假設其有效。</span><span class="sxs-lookup"><span data-stu-id="13504-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="13504-115">類別的類別建構函式完成之前，`GetContextStaticAddress`雖然靜態欄位的一些可能已經初始化，將會傳回 CORPROF_E_DATAINCOMPLETE 所有其靜態欄位，及根廢棄項目集合物件。</span><span class="sxs-lookup"><span data-stu-id="13504-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13504-116">需求</span><span class="sxs-lookup"><span data-stu-id="13504-116">Requirements</span></span>  
 <span data-ttu-id="13504-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13504-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13504-118">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13504-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13504-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13504-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13504-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13504-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13504-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13504-121">See also</span></span>

- [<span data-ttu-id="13504-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="13504-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="13504-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="13504-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
