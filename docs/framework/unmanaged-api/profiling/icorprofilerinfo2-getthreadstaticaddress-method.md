---
title: "ICorProfilerInfo2::GetThreadStaticAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetThreadStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type: apiref
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25deb36e935649c9a10d87872407c9a0d490239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="cb32d-102">ICorProfilerInfo2::GetThreadStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="cb32d-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="cb32d-103">取得指定執行緒的範圍內指定執行緒靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="cb32d-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb32d-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb32d-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb32d-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb32d-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="cb32d-106">[in]包含要求的執行緒靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb32d-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="cb32d-107">[in]要求的執行緒靜態欄位中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="cb32d-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="cb32d-108">[in]要求的靜態欄位的資料範圍的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="cb32d-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="cb32d-109">[out]內指定執行緒靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="cb32d-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb32d-110">備註</span><span class="sxs-lookup"><span data-stu-id="cb32d-110">Remarks</span></span>  
 <span data-ttu-id="cb32d-111">`GetThreadStaticAddress`方法可能會傳回下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="cb32d-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="cb32d-112">如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="cb32d-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="cb32d-113">可能會在記憶體回收堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="cb32d-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="cb32d-114">記憶體回收之後，這些位址可能會失效之後在記憶體回收集合程式碼剖析工具不應該假設都有效。</span><span class="sxs-lookup"><span data-stu-id="cb32d-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="cb32d-115">類別的類別建構函式完成之前，`GetThreadStaticAddress`會針對其所有靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然部分的靜態欄位可能已經初始化，而且為根建立記憶體回收物件。</span><span class="sxs-lookup"><span data-stu-id="cb32d-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb32d-116">需求</span><span class="sxs-lookup"><span data-stu-id="cb32d-116">Requirements</span></span>  
 <span data-ttu-id="cb32d-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb32d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb32d-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb32d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb32d-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb32d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb32d-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb32d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb32d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb32d-121">See Also</span></span>  
 [<span data-ttu-id="cb32d-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="cb32d-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="cb32d-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="cb32d-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
