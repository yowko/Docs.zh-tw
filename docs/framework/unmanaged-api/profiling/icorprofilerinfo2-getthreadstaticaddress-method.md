---
title: ICorProfilerInfo2::GetThreadStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: 3df6e4decf1c4641116dee5fab3ca83189b427c0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496759"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="943da-102">ICorProfilerInfo2::GetThreadStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="943da-102">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>
<span data-ttu-id="943da-103">取得指定的執行緒靜態欄位的位址，該欄位位於指定之執行緒的範圍內。</span><span class="sxs-lookup"><span data-stu-id="943da-103">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943da-104">語法</span><span class="sxs-lookup"><span data-stu-id="943da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="943da-105">參數</span><span class="sxs-lookup"><span data-stu-id="943da-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="943da-106">在包含所要求的執行緒靜態欄位之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="943da-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="943da-107">在所要求之執行緒靜態欄位的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="943da-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="943da-108">在做為要求的靜態欄位範圍之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="943da-108">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="943da-109">脫銷位於指定執行緒內之靜態欄位位址的指標。</span><span class="sxs-lookup"><span data-stu-id="943da-109">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="943da-110">備註</span><span class="sxs-lookup"><span data-stu-id="943da-110">Remarks</span></span>  
 <span data-ttu-id="943da-111">`GetThreadStaticAddress`方法可能會傳回下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="943da-111">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="943da-112">如果未在指定的內容中指派位址給給定的靜態欄位，CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="943da-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="943da-113">可能位於垃圾收集堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="943da-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="943da-114">在垃圾收集之後，這些位址可能會變成無效，因此垃圾收集分析工具不應假設它們是有效的。</span><span class="sxs-lookup"><span data-stu-id="943da-114">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="943da-115">在類別的類別的函式完成之前， `GetThreadStaticAddress` 會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，並且會對垃圾收集物件進行根。</span><span class="sxs-lookup"><span data-stu-id="943da-115">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="943da-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="943da-116">Requirements</span></span>  
 <span data-ttu-id="943da-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="943da-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="943da-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="943da-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="943da-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="943da-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="943da-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="943da-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="943da-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="943da-121">See also</span></span>

- [<span data-ttu-id="943da-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="943da-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="943da-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="943da-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
