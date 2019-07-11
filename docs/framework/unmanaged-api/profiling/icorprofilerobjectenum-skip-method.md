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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5818cb8d7da7415feb61532799df5fa5a16fd3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781221"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="234bd-102">ICorProfilerObjectEnum::Skip 方法</span><span class="sxs-lookup"><span data-stu-id="234bd-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="234bd-103">將這個列舉值的資料指標從其目前位置前移，以略過指定的數目的項目。</span><span class="sxs-lookup"><span data-stu-id="234bd-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="234bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="234bd-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="234bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="234bd-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="234bd-106">[in]略過的項目數目。</span><span class="sxs-lookup"><span data-stu-id="234bd-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="234bd-107">備註</span><span class="sxs-lookup"><span data-stu-id="234bd-107">Remarks</span></span>  
 <span data-ttu-id="234bd-108">此列舉值的資料指標的新位置是: （目前的位置） + `celt` 。</span><span class="sxs-lookup"><span data-stu-id="234bd-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="234bd-109">需求</span><span class="sxs-lookup"><span data-stu-id="234bd-109">Requirements</span></span>  
 <span data-ttu-id="234bd-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="234bd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="234bd-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="234bd-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="234bd-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="234bd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="234bd-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="234bd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234bd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="234bd-114">See also</span></span>

- [<span data-ttu-id="234bd-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="234bd-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
