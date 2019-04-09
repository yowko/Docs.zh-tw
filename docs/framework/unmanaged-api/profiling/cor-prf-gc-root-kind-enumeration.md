---
title: COR_PRF_GC_ROOT_KIND 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_KIND
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_KIND
helpviewer_keywords:
- COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7dfbba3cef8afadfc6e12e53ea328c4fc7165ca0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206755"
---
# <a name="corprfgcrootkind-enumeration"></a>COR_PRF_GC_ROOT_KIND 列舉
表示，由記憶體回收根目錄的種類[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)回呼。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum {  
    COR_PRF_GC_ROOT_STACK = 1,  
    COR_PRF_GC_ROOT_FINALIZER = 2,  
    COR_PRF_GC_ROOT_HANDLE = 3,  
    COR_PRF_GC_ROOT_OTHER = 0  
} COR_PRF_GC_ROOT_KIND;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_STACK`|根目錄是在堆疊上的變數。|  
|`COR_PRF_GC_ROOT_FINALIZER`|根是完成項佇列中的項目。|  
|`COR_PRF_GC_ROOT_HANDLE`|根是記憶體回收控制代碼。|  
|`COR_PRF_GC_ROOT_OTHER`|未指定的根類型。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
