---
title: ICorDebugManagedCallback3::CustomNotification 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3.CustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3::CustomNotification
helpviewer_keywords:
- ICorDebugManagedCallback3::CustomNotification method [.NET Framework debugging]
- CustomNotification method [.NET Framework debugging]
ms.assetid: 5e5422ac-afa1-403d-a894-2d7348673e38
topic_type:
- apiref
ms.openlocfilehash: 078f90387a475559067d402610ec264f4076ae01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793257"
---
# <a name="icordebugmanagedcallback3customnotification-method"></a>ICorDebugManagedCallback3::CustomNotification 方法
表示已引發自訂偵錯工具通知。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CustomNotification(ICorDebugThread *    pThread,  
                           ICorDebugAppDomain * pAppDomain);  
```  
  
## <a name="parameters"></a>參數  
 `pThread`  
 在引發通知之執行緒的指標。  
  
 `pAppDomain`  
 在應用程式域的指標，其中包含引發通知的執行緒。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此方法已順利完成。|  
  
## <a name="exceptions"></a>例外狀況  
  
## <a name="remarks"></a>備註  
 後續呼叫[ICorDebugThread4：： GetCurrentCustomDebuggerNotification](icordebugthread4-getcurrentcustomdebuggernotification-method.md)方法，會抓取傳遞給 <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> 方法的 thread 物件。 執行緒物件的類型必須先前已藉由呼叫[ICorDebugProcess3：： SetEnableCustomNotification](icordebugprocess3-setenablecustomnotification-method.md)方法來啟用。 偵錯工具可以從 thread 物件的欄位讀取特定類型的參數，並可將回應儲存到欄位中。  
  
 [ICorDebug](icordebug-interface.md)介面不會對通知類型或其內容施加任何原則，而通知的語義會嚴格成為偵錯工具、應用程式和 .NET Framework 之間的合約。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback3 介面](icordebugmanagedcallback3-interface.md)
- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
