---
title: CorDebugDecodeEventFlagsWindows 列舉
ms.date: 03/30/2017
api_name:
- CorDebugDecodeEventFlagsWindows
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aa6cf962-30ae-4cfd-8895-826deeb46a54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa8bbcf4d8e5aadee6a4250d23842187d6c2af09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugdecodeeventflagswindows-enumeration"></a>CorDebugDecodeEventFlagsWindows 列舉
提供 Windows 平台上之偵錯事件的其他資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugDecodeEventFlagsWindows {  
    IS_FIRST_CHANCE = 1,  
} CorDebugDecodeEventFlagsWindows;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`IS_FIRST_CHANCE`|表示偵錯事件是第一個可能發生的例外狀況。|  
  
## <a name="remarks"></a>備註  
 [Icordebugprocess6:: Decodeevent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)方法包含`dwFlags`參數提供偵錯事件相關的其他資訊，而且其值相依於目標架構。 `CorDebugDecodeEventFlagsWindows` 列舉可搭配 Windows 平台上的偵錯事件使用。  
  
> [!NOTE]
>  這個列舉僅適用於 .NET 原生偵錯案例。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
