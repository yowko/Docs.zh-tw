---
title: IMethodMalloc::Alloc 方法
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54c38f9a9abc9a02ba4d84c9a41b2ef6b1f7cb69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528559"
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
 配置的記憶體會開始在大於此配置器相關聯的模組的基底位址的位址。 換句話說，每個配置器會建立針對特定的模組，並會嘗試從其基底的位址配置記憶體中的正面的位移。 如果`Alloc`無法配置要求的位元組位置大於模組的基底位址的位址數目則會傳回 E_OUTOFMEMORY，不論實際的記憶體可用的空間量。  
  
 `Alloc`方法應該用於搭配[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** WindSee[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [IMethodMalloc 介面](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
