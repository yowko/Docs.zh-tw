---
title: ICorDebugVirtualUnwinder::Next 方法
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4bacbd9ef11f6f6cb6d9952290c00f1b8ce50aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder::Next 方法
進入呼叫端的內容。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a>參數  
 無。  
  
## <a name="return-value"></a>傳回值  
 如果成功發生回溯，會傳回 `S_OK`，如果因為沒有更多框架，而無法完成回溯，則傳回 `CORDBG_S_AT_END_OF_STACK`。  
  
 如果傳回失敗的 HRESULT，ICorDebug 應用程式開發介面會傳回 `CORDBG_E_DATA_TARGET_ERROR`。  
  
## <a name="remarks"></a>備註  
 堆疊查核器應該會確保其繼續進行，以致於最後呼叫 `Next` 時，會傳回失敗 HRESULT 或 `CORDBG_S_AT_END_OF_STACK`。 傳回`S_OK`無限期地可能會造成無限迴圈。  
  
> [!NOTE]
>  本方法只適用於 .NET 原生。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugMemoryBuffer 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
