---
title: ICorDebugDebugEvent::GetEventKind 方法
ms.date: 03/30/2017
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bbc9581db839d9c0a48362eac2108f43665b0fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdebugeventgeteventkind-method"></a>ICorDebugDebugEvent::GetEventKind 方法
指出這個 `ICorDebugDebugEvent` 物件所代表的事件類型。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a>參數  
 pDebugEventKind  
 指標[CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)列舉的成員，表示事件類型。  
  
## <a name="remarks"></a>備註  
 根據 `pDebugEventKind` 的值，您可以呼叫 `QueryInterface` 以取得包含其他資料的更精確偵錯事件介面。  
  
> [!NOTE]
>  本方法只適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugDebugEvent 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
