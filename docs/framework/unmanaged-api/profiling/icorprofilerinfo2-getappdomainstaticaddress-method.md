---
title: ICorProfilerInfo2::GetAppDomainStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2095f02cb23c3580b0a1109e8f0da669f61adabc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789385"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="e8876-102">ICorProfilerInfo2::GetAppDomainStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="e8876-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="e8876-103">取得在指定的應用程式定義域的範圍中指定的應用程式定義域靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="e8876-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8876-104">語法</span><span class="sxs-lookup"><span data-stu-id="e8876-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8876-105">參數</span><span class="sxs-lookup"><span data-stu-id="e8876-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e8876-106">[in]包含要求的應用程式定義域靜態欄位的類別類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="e8876-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e8876-107">[in]要求的應用程式定義域靜態欄位的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e8876-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="e8876-108">[in]應用程式定義域所要求的靜態欄位的範圍識別碼。</span><span class="sxs-lookup"><span data-stu-id="e8876-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e8876-109">[out]指定的應用程式網域內的靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="e8876-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8876-110">備註</span><span class="sxs-lookup"><span data-stu-id="e8876-110">Remarks</span></span>  
 <span data-ttu-id="e8876-111">`GetAppDomainStaticAddress`方法可能會傳回下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="e8876-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="e8876-112">如果指定的靜態欄位尚未指派指定的內容中的地址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e8876-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="e8876-113">可能在記憶體回收堆積中物件的位址。</span><span class="sxs-lookup"><span data-stu-id="e8876-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e8876-114">這些位址可能會變成無效記憶體回收之後，讓記憶體回收之後, 程式碼剖析工具不應該假設其有效。</span><span class="sxs-lookup"><span data-stu-id="e8876-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e8876-115">類別的類別建構函式完成之前，`GetAppDomainStaticAddress`雖然靜態欄位的一些可能已經初始化，將會傳回 CORPROF_E_DATAINCOMPLETE 所有其靜態欄位，及根廢棄項目集合物件。</span><span class="sxs-lookup"><span data-stu-id="e8876-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8876-116">需求</span><span class="sxs-lookup"><span data-stu-id="e8876-116">Requirements</span></span>  
 <span data-ttu-id="e8876-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8876-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8876-118">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e8876-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e8876-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8876-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8876-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8876-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8876-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8876-121">See also</span></span>

- [<span data-ttu-id="e8876-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e8876-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e8876-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="e8876-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
