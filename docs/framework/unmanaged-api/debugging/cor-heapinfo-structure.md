---
title: COR_HEAPINFO 結構
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 5400350e1c489ec4c2ff3cddf83a4f1a8a0c7947
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726596"
---
# <a name="cor_heapinfo-structure"></a>COR_HEAPINFO 結構

提供記憶體回收堆積的一般相關資訊，包括其是否可以列舉。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`areGCStructuresValid`|`true` 如果垃圾收集結構有效且可以列舉堆積，否則為 `false` 。|  
|`pointerSize`|目標架構上指標的大小（以位元組為單位）。|  
|`numHeaps`|進程中的邏輯垃圾收集堆積數目。|  
|`concurrent`|`TRUE` 如果啟用並行 (背景) 垃圾收集，則為，否則為 `FALSE` 。|  
|`gcType`|[CorDebugGCType](cordebuggctype-enumeration.md)列舉的成員，指出垃圾收集行程是否正在工作站或伺服器上執行。|  
  
## <a name="remarks"></a>備註  

 藉 `COR_HEAPINFO` 由呼叫 [ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) 方法來傳回結構的實例。  
  
 列舉垃圾收集堆積上的物件之前，您必須一律檢查 `areGCStructuresValid` 欄位，確定堆積處於可列舉的狀態。 如需詳細資訊，請參閱 [ICorDebugProcess5：： GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) 方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
