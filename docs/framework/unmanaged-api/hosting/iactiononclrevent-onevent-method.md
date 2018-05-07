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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28178cca27c257e480a7c5ec87c1925af7de4f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent 方法
執行所使用的呼叫已註冊的事件回呼[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a>參數  
 `event`  
 [in]其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，指出事件類型。  
  
 `data`  
 [in]包含有關的詳細資料物件的指標`event`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`OnEvent` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 若方法會傳回 E_FAIL，CLR 就不會再處理序內。 任何裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `data`參數是未指定類型的物件的指標。 如果`event`參數是`Event_DomainUnload`，`data`的數值識別碼<xref:System.AppDomain>，已經卸載。 主機可以採取適當的動作，使用這個識別碼做為索引鍵。  
  
 如果`event`是`Event_MDAFired`，`data`是指向[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)包含的訊息輸出從 Managed 偵錯助理 (MDA) 的執行個體。 Mda 是協助開發人員偵錯，所產生 XML 訊息，否則很難設陷事件有關的 clr 功能。 此類訊息可以是特別適用於偵錯 managed 和 unmanaged 程式碼之間的轉換。 如需詳細資訊，請參閱[診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [EClrEvent 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [IActionOnCLREvent 介面](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLROnEventManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [MDAInfo 結構](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
