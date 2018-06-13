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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8215ddfd0f59f835d0b0dcd278b8cae9c12027d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422106"
---
# <a name="icordebugthread4hadunhandledexception-method"></a>ICorDebugThread4::HadUnhandledException 方法
指出執行緒是否有曾經處理的例外狀況。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
    );  
```  
  
#### <a name="parameters"></a>參數  
 `ppBlockingObjectEnum`  
 [out]之已排序列舉的位址指標[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|執行緒已自其建立後的未處理例外狀況。|  
|S_FALSE|執行緒從未安裝過處理的例外狀況。|  
  
## <a name="remarks"></a>備註  
 這個方法會指出執行緒是否有曾經處理的例外狀況。 根據時間就會觸發未處理例外狀況回呼或起始原生 JIT 附加時，這個方法保證會傳回 S_OK。 不保證， [ICorDebugThread.GetCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)方法會傳回未處理的例外狀況; 不過，它將如果處理程序已不尚未繼續取得未處理例外狀況回呼之後，或在原生 JIT 附加。 此外，它有可能 （雖然可能性不大） 有多個執行緒的未處理例外狀況在原生 JIT 附加，就會觸發的階段。 在此情況下沒有任何方式可判斷哪些例外狀況觸發 JIT 附加。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugThread4 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
