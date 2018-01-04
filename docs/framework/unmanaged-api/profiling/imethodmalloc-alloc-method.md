---
title: "IMethodMalloc::Alloc 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMethodMalloc.Alloc
api_location: mscorwks.dll
api_type: COM
f1_keywords: IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26998e8b2e8648b4fb175f188540e7bc33c580c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc 方法
嘗試為新的 Microsoft intermediate language (MSIL) 函式主體配置指定的記憶體數量。  
  
## <a name="syntax"></a>語法  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a>參數  
 `cb`  
 [in]方法主體所配置的位元組數目。  
  
## <a name="remarks"></a>備註  
 配置的記憶體會開始在大於這個配置器相關聯之模組的基底位址的位址。 換句話說，每個配置器建立特定的模組，並會嘗試從其基底的位址配置記憶體的正數的位移。 如果`Alloc`無法配置所要求的位元組在大於模組的基底位址的位址數目會傳回 E_OUTOFMEMORY，不論實際可用的記憶體空間的數量。  
  
 `Alloc`方法應用於搭配[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** WindSee[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [IMethodMalloc 介面](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
