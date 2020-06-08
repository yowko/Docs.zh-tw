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
ms.openlocfilehash: 3dc5f04504cca632892c16d31c92a33935b356e0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497331"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="4e16f-102">ICorProfilerInfo2::GetAppDomainStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="4e16f-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="4e16f-103">取得指定的應用程式域靜態欄位的位址，該欄位位於指定的應用程式域範圍內。</span><span class="sxs-lookup"><span data-stu-id="4e16f-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e16f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e16f-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e16f-105">參數</span><span class="sxs-lookup"><span data-stu-id="4e16f-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4e16f-106">在包含所要求應用程式域靜態欄位之類別的類別 ID。</span><span class="sxs-lookup"><span data-stu-id="4e16f-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4e16f-107">在所要求之應用程式域靜態欄位的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="4e16f-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="4e16f-108">在應用程式域的識別碼，這是要求的靜態欄位範圍。</span><span class="sxs-lookup"><span data-stu-id="4e16f-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4e16f-109">脫銷指定之應用程式域內靜態欄位位址的指標。</span><span class="sxs-lookup"><span data-stu-id="4e16f-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e16f-110">備註</span><span class="sxs-lookup"><span data-stu-id="4e16f-110">Remarks</span></span>  
 <span data-ttu-id="4e16f-111">`GetAppDomainStaticAddress`方法可能會傳回下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="4e16f-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="4e16f-112">如果未在指定的內容中指派位址給給定的靜態欄位，CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="4e16f-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="4e16f-113">可能位於垃圾收集堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="4e16f-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4e16f-114">這些位址在垃圾收集後可能會變成無效，因此在垃圾收集之後，分析工具不應假設它們是有效的。</span><span class="sxs-lookup"><span data-stu-id="4e16f-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4e16f-115">在類別的類別的函式完成之前， `GetAppDomainStaticAddress` 會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，並且會對垃圾收集物件進行根。</span><span class="sxs-lookup"><span data-stu-id="4e16f-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e16f-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="4e16f-116">Requirements</span></span>  
 <span data-ttu-id="4e16f-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e16f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e16f-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e16f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e16f-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e16f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e16f-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e16f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e16f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e16f-121">See also</span></span>

- [<span data-ttu-id="4e16f-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4e16f-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4e16f-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="4e16f-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
