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
ms.openlocfilehash: 4e7045d3b095b6a35be8b55e1066b459e9583c93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147013"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent 方法
對事件所使用的呼叫已註冊的回呼[iclroneventmanager:: Registeractiononevent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>參數  
 `event`  
 [in]其中一個[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)值，指出事件的型別。  
  
 `data`  
 [in]包含有關的詳細資料物件的指標`event`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`OnEvent` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。 任何裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 `data`參數是未指定類型之物件的指標。 如果`event`參數是`Event_DomainUnload`，`data`的數值識別碼<xref:System.AppDomain>，已經卸載。 主機可以採取適當的動作，使用這個識別碼做為索引鍵。  
  
 如果`event`已`Event_MDAFired`，`data`是一個指向[MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)執行個體，包含的訊息輸出從 Managed 偵錯助理 (MDA)。 Mda 是協助開發人員偵錯，藉由產生 XML 訊息的相關事件，否則很難攔截的 clr 功能。 這類訊息可以是特別適用於偵錯 managed 和 unmanaged 程式碼之間的轉換。 如需詳細資訊，請參閱 < [Managed 偵錯助理診斷錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [診斷 Managed 偵錯助理的錯誤](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent 介面](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLROnEventManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [MDAInfo 結構](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
