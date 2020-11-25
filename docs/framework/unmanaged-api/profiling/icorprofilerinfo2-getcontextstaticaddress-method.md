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
ms.openlocfilehash: 067e5093cc3b141936eeec43e77e6e1a9475a8a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727116"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="073be-102">ICorProfilerInfo2::GetContextStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="073be-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>

<span data-ttu-id="073be-103">取得位於指定內容約制內之指定內容靜態欄位的位址。</span><span class="sxs-lookup"><span data-stu-id="073be-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="073be-104">語法</span><span class="sxs-lookup"><span data-stu-id="073be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="073be-105">參數</span><span class="sxs-lookup"><span data-stu-id="073be-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="073be-106">在包含所要求之內容靜態欄位的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="073be-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="073be-107">在要求的內容靜態欄位的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="073be-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="073be-108">在屬於所要求內容靜態欄位範圍的內容識別碼。</span><span class="sxs-lookup"><span data-stu-id="073be-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="073be-109">擴展指定內容中靜態欄位的位址指標。</span><span class="sxs-lookup"><span data-stu-id="073be-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="073be-110">備註</span><span class="sxs-lookup"><span data-stu-id="073be-110">Remarks</span></span>  

 <span data-ttu-id="073be-111">`GetContextStaticAddress`方法可能會傳回下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="073be-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="073be-112">如果指定的靜態欄位未在指定的內容中指派位址，則為 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="073be-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="073be-113">可能位於垃圾收集堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="073be-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="073be-114">這些位址在垃圾收集之後可能會失效，因此在垃圾收集之後，分析工具不應假設它們是有效的。</span><span class="sxs-lookup"><span data-stu-id="073be-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="073be-115">在類別的類別的函式完成之前， `GetContextStaticAddress` 將會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，並且會將垃圾收集物件的根。</span><span class="sxs-lookup"><span data-stu-id="073be-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="073be-116">需求</span><span class="sxs-lookup"><span data-stu-id="073be-116">Requirements</span></span>  

 <span data-ttu-id="073be-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="073be-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="073be-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="073be-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="073be-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="073be-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="073be-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="073be-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="073be-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="073be-121">See also</span></span>

- [<span data-ttu-id="073be-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="073be-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="073be-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="073be-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
