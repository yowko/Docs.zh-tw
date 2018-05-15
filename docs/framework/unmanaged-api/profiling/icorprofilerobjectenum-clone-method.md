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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e8a623107e5e03ca36137c253c9bdf0a722d385
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="3e215-102">ICorProfilerObjectEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="3e215-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="3e215-103">取得這個複本的介面指標[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="3e215-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e215-104">語法</span><span class="sxs-lookup"><span data-stu-id="3e215-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3e215-105">參數</span><span class="sxs-lookup"><span data-stu-id="3e215-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="3e215-106">[out]介面指標，再依序指向的副本的指標`ICorProfilerObjectEnum`介面。</span><span class="sxs-lookup"><span data-stu-id="3e215-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="3e215-107">複本會維護其本身列舉狀態分別從這一個。</span><span class="sxs-lookup"><span data-stu-id="3e215-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="3e215-108">不過，將會與此列舉值的目前游標位置相同的複本初始資料指標位置。</span><span class="sxs-lookup"><span data-stu-id="3e215-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e215-109">需求</span><span class="sxs-lookup"><span data-stu-id="3e215-109">Requirements</span></span>  
 <span data-ttu-id="3e215-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e215-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e215-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3e215-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3e215-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e215-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e215-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e215-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e215-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e215-114">See Also</span></span>  
 [<span data-ttu-id="3e215-115">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="3e215-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
