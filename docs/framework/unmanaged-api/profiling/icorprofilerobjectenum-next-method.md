---
title: ICorProfilerObjectEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
ms.openlocfilehash: 0c833416cca965f2655266152c5bdf5f11624d14
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861134"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="00145-102">ICorProfilerObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="00145-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="00145-103">從序列中列舉值的目前位置開始，從物件的連續集合中取得指定的連續物件數目。</span><span class="sxs-lookup"><span data-stu-id="00145-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00145-104">語法</span><span class="sxs-lookup"><span data-stu-id="00145-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00145-105">參數</span><span class="sxs-lookup"><span data-stu-id="00145-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="00145-106">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="00145-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="00145-107">脫銷`ObjectID` 值的陣列，其中每一個都代表抓取的物件。</span><span class="sxs-lookup"><span data-stu-id="00145-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="00145-108">[out] `objects` 陣列中實際傳回之項目數目的指標。</span><span class="sxs-lookup"><span data-stu-id="00145-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00145-109">需求</span><span class="sxs-lookup"><span data-stu-id="00145-109">Requirements</span></span>  
 <span data-ttu-id="00145-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00145-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00145-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00145-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00145-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00145-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00145-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00145-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00145-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="00145-114">See also</span></span>

- [<span data-ttu-id="00145-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="00145-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
