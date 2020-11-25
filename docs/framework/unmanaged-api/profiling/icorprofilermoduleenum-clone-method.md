---
title: ICorProfilerModuleEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
ms.openlocfilehash: ae9f6b7865a80e3edc4cae8fd1298e5eed864377
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722826"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="50e25-102">ICorProfilerModuleEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="50e25-102">ICorProfilerModuleEnum::Clone Method</span></span>

<span data-ttu-id="50e25-103">取得這個 [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) 介面複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="50e25-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e25-104">語法</span><span class="sxs-lookup"><span data-stu-id="50e25-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50e25-105">參數</span><span class="sxs-lookup"><span data-stu-id="50e25-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="50e25-106">擴展指向介面指標的指標，該指標會指向這個 [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) 介面的複本。</span><span class="sxs-lookup"><span data-stu-id="50e25-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="50e25-107">列舉值的複本會從這個列舉值分開維護自己的列舉狀態。</span><span class="sxs-lookup"><span data-stu-id="50e25-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="50e25-108">不過，複本的初始游標位置與此列舉值的目前資料指標位置相同。</span><span class="sxs-lookup"><span data-stu-id="50e25-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e25-109">需求</span><span class="sxs-lookup"><span data-stu-id="50e25-109">Requirements</span></span>  

 <span data-ttu-id="50e25-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50e25-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e25-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50e25-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50e25-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50e25-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50e25-113">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e25-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e25-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50e25-114">See also</span></span>

- [<span data-ttu-id="50e25-115">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="50e25-115">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="50e25-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="50e25-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
