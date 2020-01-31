---
title: ICorDebugThread4::HadUnhandledException 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.HadUnhandledException Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::HadUnhandledException
helpviewer_keywords:
- ICorDebugThread4::HadUnhandledException method [.NET Framework debugging]
- HadUnhandledException method [.NET Framework debugging]
ms.assetid: 05558daa-39e2-4c38-aeaf-e2aec4a09468
topic_type:
- apiref
ms.openlocfilehash: f558a4c94afeb69f58605958ddcb91e4be772c39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791342"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException 方法
指出執行緒是否曾經有未處理的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
## <a name="parameters"></a>參數  
 `ppBlockingObjectEnum`  
 脫銷[CorDebugBlockingObject](cordebugblockingobject-structure.md)結構的已排序列舉之位址的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|執行緒在建立之後有未處理的例外狀況。|  
|S_FALSE|執行緒從未發生未處理的例外狀況。|  
  
## <a name="remarks"></a>備註  
 這個方法會指出執行緒是否曾經有未處理的例外狀況。 在觸發未處理的例外狀況回呼或起始原生 JIT 附加時，會保證此方法會傳回 S_OK。 不保證[ICorDebugThread 的 GetCurrentException](icordebugthread-getcurrentexception-method.md)方法會傳回未處理的例外狀況;不過，如果在取得未處理的例外狀況回呼或原生 JIT 附加之後，進程尚未繼續，就會發生此情況。 此外，觸發原生 JIT 附加時，有可能（但不太可能）有一個以上的執行緒具有未處理的例外狀況。 在這種情況下，無法判斷哪個例外狀況觸發了 JIT 附加。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugThread4 介面](icordebugthread4-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
