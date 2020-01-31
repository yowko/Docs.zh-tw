---
title: ICorProfilerObjectEnum::Skip 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
ms.openlocfilehash: 096489fcdc9d604e003386501c22967b45ba6d7f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861095"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="7054e-102">ICorProfilerObjectEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="7054e-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="7054e-103">將此列舉值的資料指標從其目前位置前移，以略過指定數目的元素。</span><span class="sxs-lookup"><span data-stu-id="7054e-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7054e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7054e-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7054e-105">參數</span><span class="sxs-lookup"><span data-stu-id="7054e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7054e-106">在要略過的元素數目。</span><span class="sxs-lookup"><span data-stu-id="7054e-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7054e-107">備註</span><span class="sxs-lookup"><span data-stu-id="7054e-107">Remarks</span></span>  
 <span data-ttu-id="7054e-108">這個列舉值的資料指標的新位置是：（目前位置） + `celt`。</span><span class="sxs-lookup"><span data-stu-id="7054e-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7054e-109">需求</span><span class="sxs-lookup"><span data-stu-id="7054e-109">Requirements</span></span>  
 <span data-ttu-id="7054e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7054e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7054e-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7054e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7054e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7054e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7054e-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7054e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7054e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7054e-114">See also</span></span>

- [<span data-ttu-id="7054e-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="7054e-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
