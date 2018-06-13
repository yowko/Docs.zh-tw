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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5f23950eea94cde0655d364ad0c6701e04a7c1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453843"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="94dd0-102">ICorProfilerObjectEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="94dd0-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="94dd0-103">取得集合中的已凍結的物件總數。</span><span class="sxs-lookup"><span data-stu-id="94dd0-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94dd0-104">語法</span><span class="sxs-lookup"><span data-stu-id="94dd0-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94dd0-105">參數</span><span class="sxs-lookup"><span data-stu-id="94dd0-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="94dd0-106">[out]集合中已凍結的物件數目指標。</span><span class="sxs-lookup"><span data-stu-id="94dd0-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="94dd0-107">這個方法一律會傳回零，在.NET Framework 3.5 版 Service Pack 1 (SP1) 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="94dd0-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94dd0-108">需求</span><span class="sxs-lookup"><span data-stu-id="94dd0-108">Requirements</span></span>  
 <span data-ttu-id="94dd0-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94dd0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94dd0-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="94dd0-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="94dd0-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94dd0-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94dd0-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94dd0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94dd0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94dd0-113">See Also</span></span>  
 [<span data-ttu-id="94dd0-114">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="94dd0-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
