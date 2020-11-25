---
title: CorDebugRecordFormat 列舉
ms.date: 03/30/2017
api_name:
- CorDebugRecordFormat
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type:
- apiref
ms.openlocfilehash: b3a22d7b32eb258263d373ae91b3fb7fbc9aae99
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696384"
---
# <a name="cordebugrecordformat-enumeration"></a>CorDebugRecordFormat 列舉

描述包含原生例外狀況偵錯事件相關資訊之位元組陣列中的資料格式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|這份資料是 32 位元 Windows 例外狀況記錄。|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|這份資料是 64 位元 Windows 例外狀況記錄。|  
  
## <a name="remarks"></a>備註  

 列舉的成員 `CorDebugRecordFormat` 會傳遞至 [DecodeEvent](icordebugprocess6-decodeevent-method.md) 方法，以在其引數中指出位元組陣列的格式 `pRecord` 。  
  
> [!NOTE]
> 這個列舉僅適用於 .NET Native 偵錯案例。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
