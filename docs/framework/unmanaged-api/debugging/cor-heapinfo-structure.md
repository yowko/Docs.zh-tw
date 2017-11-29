---
title: "COR_HEAPINFO 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_HEAPINFO
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_HEAPINFO
helpviewer_keywords: COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e316b964e3e983f50b81228709623e162529b05c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="corheapinfo-structure"></a>COR_HEAPINFO 結構
提供記憶體回收堆積的一般相關資訊，包括其是否可以列舉。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`areGCStructuresValid`|`true`如果記憶體回收結構有效且可以列舉堆積。，否則， `false`。|  
|`pointerSize`|以位元組為單位的目標架構上的指標大小。|  
|`numHeaps`|邏輯記憶體回收堆積中的處理序數目。|  
|`concurrent`|`TRUE`如果同時啟用 （背景） 記憶體回收。否則， `FALSE`。|  
|`gcType`|成員[CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)列舉，指出是否在工作站或伺服器上執行記憶體回收行程。|  
  
## <a name="remarks"></a>備註  
 執行個體`COR_HEAPINFO`結構由呼叫[icordebugprocess5:: Getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法。  
  
 之前列舉的物件在記憶體回收堆積上的，您必須一律檢查`areGCStructuresValid`欄位，以確保在堆積中的可列舉的狀態。 如需詳細資訊，請參閱[icordebugprocess5:: Getgcheapinformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
