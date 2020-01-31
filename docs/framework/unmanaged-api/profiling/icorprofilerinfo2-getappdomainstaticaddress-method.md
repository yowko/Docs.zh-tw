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
ms.openlocfilehash: 05d8c44655d8670194035c336bd62ae5d53bfec3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862959"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="2f9b7-102">ICorProfilerInfo2::GetAppDomainStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="2f9b7-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="2f9b7-103">取得指定的應用程式域靜態欄位的位址，該欄位位於指定的應用程式域範圍內。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f9b7-104">語法</span><span class="sxs-lookup"><span data-stu-id="2f9b7-104">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f9b7-105">參數</span><span class="sxs-lookup"><span data-stu-id="2f9b7-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2f9b7-106">在包含所要求應用程式域靜態欄位之類別的類別 ID。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="2f9b7-107">在所要求之應用程式域靜態欄位的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="2f9b7-108">在應用程式域的識別碼，這是要求的靜態欄位範圍。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="2f9b7-109">脫銷指定之應用程式域內靜態欄位位址的指標。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f9b7-110">備註</span><span class="sxs-lookup"><span data-stu-id="2f9b7-110">Remarks</span></span>  
 <span data-ttu-id="2f9b7-111">`GetAppDomainStaticAddress` 方法可能會傳回下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="2f9b7-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="2f9b7-112">如果未在指定的內容中指派位址給給定的靜態欄位，CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="2f9b7-113">可能位於垃圾收集堆積中之物件的位址。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="2f9b7-114">這些位址在垃圾收集後可能會變成無效，因此在垃圾收集之後，分析工具不應假設它們是有效的。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="2f9b7-115">在類別的類別的函式完成之前，`GetAppDomainStaticAddress` 將會傳回其所有靜態欄位的 CORPROF_E_DATAINCOMPLETE，雖然某些靜態欄位可能已經初始化，並且會對垃圾收集物件進行根。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f9b7-116">需求</span><span class="sxs-lookup"><span data-stu-id="2f9b7-116">Requirements</span></span>  
 <span data-ttu-id="2f9b7-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f9b7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f9b7-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f9b7-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f9b7-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f9b7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f9b7-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f9b7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f9b7-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f9b7-121">See also</span></span>

- [<span data-ttu-id="2f9b7-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="2f9b7-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="2f9b7-123">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="2f9b7-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
