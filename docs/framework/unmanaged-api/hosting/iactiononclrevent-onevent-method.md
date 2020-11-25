---
title: IActionOnCLREvent::OnEvent 方法
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
ms.openlocfilehash: 3bfcb01e30b4cb33ec9276f1d3c6ac2f3bde4b58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721760"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent 方法

針對已使用 [ICLROnEventManager：： RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) 方法呼叫註冊的事件，執行回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>參數  

 `event`  
 在其中一個 [EClrEvent](eclrevent-enumeration.md) 值，表示事件的類型。  
  
 `data`  
 在物件的指標，其中包含的詳細資料 `event` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`OnEvent` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。 對任何裝載方法的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 `data`參數是未指定類型之物件的指標。 如果 `event` 參數為 `Event_DomainUnload` ， `data` 則是已卸載之的數值識別碼 <xref:System.AppDomain> 。 主機可以使用此識別碼作為索引鍵，以採取適當的動作。  
  
 如果 `event` 為 `Event_MDAFired` ， `data` 則是 [MDAInfo](mdainfo-structure.md) 實例的指標，其中包含 Managed 偵錯工具 (MDA) 的訊息輸出。 Mda 是 CLR 的一項功能，可協助開發人員進行偵錯工具，方法是產生有關其他難以捕捉之事件的 XML 訊息。 這類訊息在 managed 和非受控碼之間的轉換進行調試時特別有用。 如需詳細資訊，請參閱 [診斷 Managed 偵錯工具的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [診斷 Managed 偵錯助理的錯誤](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent 列舉](eclrevent-enumeration.md)
- [IActionOnCLREvent 介面](iactiononclrevent-interface.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [ICLROnEventManager 介面](iclroneventmanager-interface.md)
- [MDAInfo 結構](mdainfo-structure.md)
