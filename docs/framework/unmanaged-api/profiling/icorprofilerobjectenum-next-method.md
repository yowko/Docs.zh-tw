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
ms.openlocfilehash: b6e26d1538cab30db66e887aee89b8fbae501bdb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177003"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="a55bf-102">ICorProfilerObjectEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="a55bf-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="a55bf-103">從物件的循序集合中獲取指定數量的連續物件，從枚舉器在序列中的當前位置開始。</span><span class="sxs-lookup"><span data-stu-id="a55bf-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a55bf-104">語法</span><span class="sxs-lookup"><span data-stu-id="a55bf-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a55bf-105">參數</span><span class="sxs-lookup"><span data-stu-id="a55bf-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a55bf-106">[in] 要擷取的物件數目。</span><span class="sxs-lookup"><span data-stu-id="a55bf-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="a55bf-107">[出]值陣列`ObjectID`，每個值表示檢索的物件。</span><span class="sxs-lookup"><span data-stu-id="a55bf-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a55bf-108">[out] `objects` 陣列中實際傳回之項目數目的指標。</span><span class="sxs-lookup"><span data-stu-id="a55bf-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a55bf-109">需求</span><span class="sxs-lookup"><span data-stu-id="a55bf-109">Requirements</span></span>  
 <span data-ttu-id="a55bf-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a55bf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a55bf-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a55bf-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a55bf-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a55bf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a55bf-113">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a55bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55bf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a55bf-114">See also</span></span>

- [<span data-ttu-id="a55bf-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a55bf-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
