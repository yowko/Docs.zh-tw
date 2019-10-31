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
ms.openlocfilehash: 98807717fc913052dae15f9f3cbd462d4f537ad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126923"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent 方法
在已使用[ICLROnEventManager：： RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法的呼叫註冊的事件上執行回呼。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>參數  
 `event`  
 在其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，表示事件的類型。  
  
 `data`  
 在物件的指標，其中包含 `event`的詳細資料。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `OnEvent`。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。 對任何裝載方法的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `data` 參數是未指定類型物件的指標。 如果 `event` 參數是 `Event_DomainUnload`，`data` 就是已卸載之 <xref:System.AppDomain> 的數值識別碼。 主機可以使用此識別碼做為金鑰來採取適當的動作。  
  
 如果 `Event_MDAFired``event`，`data` 是[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)實例的指標，其中包含來自 Managed 偵錯工具（MDA）的訊息輸出。 Mda 是 CLR 的一項功能，可協助開發人員進行偵錯工具，方法是產生關於事件的 XML 訊息，這是很棘手的陷阱。 這類訊息特別適用于在受控和非受控碼之間的轉換。 如需詳細資訊，請參閱[使用受控偵錯工具診斷錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent 介面](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLROnEventManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [MDAInfo 結構](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
