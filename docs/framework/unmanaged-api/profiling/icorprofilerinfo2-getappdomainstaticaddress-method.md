---
title: "ICorProfilerInfo2::GetAppDomainStaticAddress 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetAppDomainStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type: apiref
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf82d20085137e8ac55cf864a21260222fd6b514
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="e625a-102">ICorProfilerInfo2::GetAppDomainStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="e625a-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="e625a-103">取得位於指定的應用程式定義域的範圍內指定的應用程式定義域靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="e625a-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e625a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e625a-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e625a-105">參數</span><span class="sxs-lookup"><span data-stu-id="e625a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e625a-106">[in]包含要求的應用程式定義域靜態欄位之類別的類別 ID。</span><span class="sxs-lookup"><span data-stu-id="e625a-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e625a-107">[in]要求的應用程式定義域靜態欄位中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e625a-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="e625a-108">[in]應用程式定義域所要求的靜態欄位的範圍 ID。</span><span class="sxs-lookup"><span data-stu-id="e625a-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e625a-109">[out]指定應用程式定義域內的靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e625a-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e625a-110">備註</span><span class="sxs-lookup"><span data-stu-id="e625a-110">Remarks</span></span>  
 <span data-ttu-id="e625a-111">`GetAppDomainStaticAddress`方法可能會傳回下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="e625a-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="e625a-112">如果在指定的靜態欄位指派指定的內容中的位址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e625a-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="e625a-113">可能會在記憶體回收堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="e625a-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e625a-114">這些位址可能會變成記憶體回收之後, 無效，所以記憶體回收之後, 程式碼剖析工具不應該假設都有效。</span><span class="sxs-lookup"><span data-stu-id="e625a-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e625a-115">類別的類別建構函式完成之前，`GetAppDomainStaticAddress`會針對其所有靜態欄位，傳回 CORPROF_E_DATAINCOMPLETE，雖然部分的靜態欄位可能已經初始化，而且為根建立記憶體回收物件。</span><span class="sxs-lookup"><span data-stu-id="e625a-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e625a-116">需求</span><span class="sxs-lookup"><span data-stu-id="e625a-116">Requirements</span></span>  
 <span data-ttu-id="e625a-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e625a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e625a-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e625a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e625a-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e625a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e625a-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e625a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e625a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e625a-121">See Also</span></span>  
 [<span data-ttu-id="e625a-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e625a-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e625a-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="e625a-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
