---
title: ICorProfilerObjectEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
ms.openlocfilehash: a1a616c1289867864eb9eb449c7d6f47f9a8352b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861290"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="30676-102">ICorProfilerObjectEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="30676-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="30676-103">取得集合中凍結物件的總數。</span><span class="sxs-lookup"><span data-stu-id="30676-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30676-104">語法</span><span class="sxs-lookup"><span data-stu-id="30676-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30676-105">參數</span><span class="sxs-lookup"><span data-stu-id="30676-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="30676-106">脫銷集合中凍結物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="30676-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="30676-107">在 .NET Framework 版本 3.5 Service Pack 1 （SP1）和更新版本中，這個方法一律會傳回零。</span><span class="sxs-lookup"><span data-stu-id="30676-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30676-108">需求</span><span class="sxs-lookup"><span data-stu-id="30676-108">Requirements</span></span>  
 <span data-ttu-id="30676-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30676-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30676-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30676-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30676-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30676-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30676-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30676-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30676-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="30676-113">See also</span></span>

- [<span data-ttu-id="30676-114">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="30676-114">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
