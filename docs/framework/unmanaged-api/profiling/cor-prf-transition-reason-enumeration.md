---
title: COR_PRF_TRANSITION_REASON 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867040"
---
# <a name="cor_prf_transition_reason-enumeration"></a>COR_PRF_TRANSITION_REASON 列舉
指出從 Managed 程式碼轉換為 Unmanaged 程式碼 (反之亦然) 的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|轉換是因為函式的呼叫所造成。|  
|`COR_PRF_TRANSITION_RETURN`|轉換是因為從函式傳回。|  
  
## <a name="remarks"></a>備註  
 當轉換發生時，分析工具會收到[ICorProfilerCallback：： ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md)或[ICorProfilerCallback：： UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md)回呼，其中任一項都會提供 `COR_PRF_TRANSITION_REASON` 列舉的值，以指出轉換的原因。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
