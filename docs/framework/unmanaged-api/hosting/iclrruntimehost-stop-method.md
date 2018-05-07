---
title: ICLRRuntimeHost::Stop 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d479e271c2cc4ebf9ea6ff349fd28bff37c3857
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimehoststop-method"></a>ICLRRuntimeHost::Stop 方法
停止執行的程式碼，common language runtime (CLR)。  
  
> [!IMPORTANT]
>  這個方法不釋放資源給主機、 卸載應用程式定義域或終結執行緒。 您必須終止處理序釋放這些資源。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Stop` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 若方法會傳回 E_FAIL，CLR 就不會再處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
