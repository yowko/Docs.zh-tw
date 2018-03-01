---
title: "ICorProfilerObjectEnum::GetCount 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b7675749a132cffe284d73bab3dba91f6ff7a3fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="9e92e-102">ICorProfilerObjectEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="9e92e-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="9e92e-103">取得集合中的已凍結的物件總數。</span><span class="sxs-lookup"><span data-stu-id="9e92e-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e92e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e92e-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e92e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e92e-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="9e92e-106">[out]集合中已凍結的物件數目指標。</span><span class="sxs-lookup"><span data-stu-id="9e92e-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="9e92e-107">這個方法一律會傳回零，在.NET Framework 3.5 版 Service Pack 1 (SP1) 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="9e92e-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e92e-108">需求</span><span class="sxs-lookup"><span data-stu-id="9e92e-108">Requirements</span></span>  
 <span data-ttu-id="9e92e-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e92e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e92e-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e92e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e92e-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e92e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e92e-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e92e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e92e-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e92e-113">See Also</span></span>  
 [<span data-ttu-id="9e92e-114">ICorProfilerObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="9e92e-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
