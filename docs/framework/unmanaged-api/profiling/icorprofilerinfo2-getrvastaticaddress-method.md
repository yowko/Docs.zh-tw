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
ms.openlocfilehash: ca64d4f5932fb4a0c0486fee5ca1017a6d3adaf2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868625"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="e917c-102">ICorProfilerInfo2::GetRVAStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="e917c-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>
<span data-ttu-id="e917c-103">取得指定的相對虛擬位址（RVA）靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="e917c-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e917c-104">語法</span><span class="sxs-lookup"><span data-stu-id="e917c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e917c-105">參數</span><span class="sxs-lookup"><span data-stu-id="e917c-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e917c-106">在包含所要求之 RVA 靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="e917c-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="e917c-107">在所要求之 RVA 靜態欄位的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="e917c-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="e917c-108">脫銷RVA-靜態欄位位址的指標。</span><span class="sxs-lookup"><span data-stu-id="e917c-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e917c-109">備註</span><span class="sxs-lookup"><span data-stu-id="e917c-109">Remarks</span></span>  
 <span data-ttu-id="e917c-110">`GetRVAStaticAddress` 方法可能會傳回下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="e917c-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="e917c-111">如果未在指定的內容中指派位址給給定的靜態欄位，CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e917c-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="e917c-112">可能位於垃圾收集堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="e917c-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="e917c-113">這些位址在垃圾收集後可能會變成無效，因此在垃圾收集之後，分析工具不應假設它們是有效的。</span><span class="sxs-lookup"><span data-stu-id="e917c-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="e917c-114">在類別的類別的函式完成之前，`GetRVAStaticAddress` 會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，而且可能是根的垃圾收集物件。</span><span class="sxs-lookup"><span data-stu-id="e917c-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e917c-115">需求</span><span class="sxs-lookup"><span data-stu-id="e917c-115">Requirements</span></span>  
 <span data-ttu-id="e917c-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e917c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e917c-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e917c-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e917c-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e917c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e917c-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e917c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e917c-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="e917c-120">See also</span></span>

- [<span data-ttu-id="e917c-121">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e917c-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e917c-122">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="e917c-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
