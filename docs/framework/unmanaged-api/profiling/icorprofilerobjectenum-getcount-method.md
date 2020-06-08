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
ms.openlocfilehash: 4c867a9e263f022fc6f8d90a883562e2560ad1b2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494653"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="bfcee-102">ICorProfilerObjectEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="bfcee-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="bfcee-103">取得集合中凍結物件的總數。</span><span class="sxs-lookup"><span data-stu-id="bfcee-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfcee-104">語法</span><span class="sxs-lookup"><span data-stu-id="bfcee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfcee-105">參數</span><span class="sxs-lookup"><span data-stu-id="bfcee-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="bfcee-106">脫銷集合中凍結物件數目的指標。</span><span class="sxs-lookup"><span data-stu-id="bfcee-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="bfcee-107">在 .NET Framework 版本 3.5 Service Pack 1 （SP1）和更新版本中，這個方法一律會傳回零。</span><span class="sxs-lookup"><span data-stu-id="bfcee-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfcee-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="bfcee-108">Requirements</span></span>  
 <span data-ttu-id="bfcee-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfcee-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfcee-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bfcee-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bfcee-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfcee-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfcee-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfcee-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfcee-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfcee-113">See also</span></span>

- [<span data-ttu-id="bfcee-114">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="bfcee-114">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
