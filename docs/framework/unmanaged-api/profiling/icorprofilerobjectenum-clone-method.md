---
title: ICorProfilerObjectEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: 8153dbd27e168e3a5bd8e5aeada955a0382aaf75
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868248"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="9e7c1-102">ICorProfilerObjectEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="9e7c1-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="9e7c1-103">取得此[ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md)介面之複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="9e7c1-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e7c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e7c1-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e7c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e7c1-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9e7c1-106">脫銷介面指標的指標，指向這個 `ICorProfilerObjectEnum` 介面的複本。</span><span class="sxs-lookup"><span data-stu-id="9e7c1-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="9e7c1-107">複製會獨立維護其本身的列舉狀態。</span><span class="sxs-lookup"><span data-stu-id="9e7c1-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="9e7c1-108">不過，複本的初始游標位置會與這個列舉值的目前資料指標位置相同。</span><span class="sxs-lookup"><span data-stu-id="9e7c1-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e7c1-109">需求</span><span class="sxs-lookup"><span data-stu-id="9e7c1-109">Requirements</span></span>  
 <span data-ttu-id="9e7c1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e7c1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e7c1-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e7c1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e7c1-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e7c1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e7c1-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e7c1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7c1-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e7c1-114">See also</span></span>

- [<span data-ttu-id="9e7c1-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9e7c1-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
