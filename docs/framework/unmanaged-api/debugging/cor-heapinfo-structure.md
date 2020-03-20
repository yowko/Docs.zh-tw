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
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179314"
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
|`areGCStructuresValid`|`true`如果垃圾回收結構有效，並且可以枚舉堆;如果垃圾回收結構有效，則為堆。否則， `false`.|  
|`pointerSize`|目標體系結構上指標的大小（以位元組為單位）。|  
|`numHeaps`|進程中的邏輯垃圾回收堆數。|  
|`concurrent`|`TRUE`如果啟用併發（後臺）垃圾回收;如果啟用了併發（後臺）垃圾回收;否則， `FALSE`.|  
|`gcType`|[CorDebugGCType](cordebuggctype-enumeration.md)枚舉的成員，用於指示垃圾回收器是在工作站上運行還是伺服器上運行。|  
  
## <a name="remarks"></a>備註  
 結構的`COR_HEAPINFO`實例通過調用[ICorDebugProcess5：：：getGCHeap資訊](icordebugprocess5-getgcheapinformation-method.md)方法返回。  
  
 在枚舉垃圾回收堆上的物件之前，必須始終檢查該`areGCStructuresValid`欄位以確保堆處於枚舉狀態。 有關詳細資訊，請參閱[ICorDebugProcess5：：getGCHeap資訊](icordebugprocess5-getgcheapinformation-method.md)方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
