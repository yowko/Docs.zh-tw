---
title: "CorDebugRecordFormat 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugRecordFormat
api_location: mscordbi.dll
api_type: COM
ms.assetid: d680c1c0-16ab-4ccc-9444-39cf8e0e05ee
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eaf962250d97f031eaa60b7cc0b15622897aad3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugrecordformat-enumeration"></a>CorDebugRecordFormat 列舉
描述包含原生例外狀況偵錯事件相關資訊之位元組陣列中的資料格式。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugRecordFormat {  
    FORMAT_WINDOWS_EXCEPTIONRECORD32 = 1,  
    FORMAT_WINDOWS_EXCEPTIONRECORD64 = 2,  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD32`|這份資料是 32 位元 Windows 例外狀況記錄。|  
|`FORMAT_WINDOWS_EXCEPTIONRECORD64`|這份資料是 64 位元 Windows 例外狀況記錄。|  
  
## <a name="remarks"></a>備註  
 成員`CorDebugRecordFormat`列舉會傳遞至[DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法，以表示中的位元組陣列格式其`pRecord`引數。  
  
> [!NOTE]
>  這個列舉僅適用於 .NET 原生偵錯案例。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
