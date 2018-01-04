---
title: "COR_PRF_GC_ROOT_KIND 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_ROOT_KIND
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_ROOT_KIND
helpviewer_keywords: COR_PRF_GC_ROOT_KIND enumeration [.NET Framework profiling]
ms.assetid: b9fb1c03-417f-41d4-aed4-02cb4ade8def
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 537b39384d04e7a0080a22c6894cc2f6965b0bbc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcrootkind-enumeration"></a>COR_PRF_GC_ROOT_KIND 列舉
表示所公開的記憶體回收根目錄的種類[icorprofilercallback2:: Rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)回呼。  
  
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
|`COR_PRF_GC_ROOT_FINALIZER`|根目錄是完成項佇列中的項目。|  
|`COR_PRF_GC_ROOT_HANDLE`|根目錄是記憶體回收控制代碼。|  
|`COR_PRF_GC_ROOT_OTHER`|未指定的根類型。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [分析列舉](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
