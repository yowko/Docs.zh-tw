---
title: ICorDebugProcess8 介面
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: 00c432374eeb82692492b8e6b10472f13bc44d6e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732511"
---
# <a name="icordebugprocess8-interface"></a>ICorDebugProcess8 介面

[在 .NET Framework 4.6 和更新版本中支援]  
  
 以邏輯方式擴充 ICorDebugProcess 介面，以啟用或停用特定類型的 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外狀況回呼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnableExceptionCallbacksOutsideOfMyCode 方法](icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|啟用或停用特定類型的 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 例外狀況回呼。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
