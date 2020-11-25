---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
ms.openlocfilehash: 1088374c9df18ded38b44384be44de245f0bd403
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728949"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a>ICLRPolicyManager::SetUnhandledExceptionPolicy 方法

指定發生未處理的例外狀況時，common language runtime (CLR) 的行為。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a>參數  

 `policy`  
 在其中一個 [EClrUnhandledException](eclrunhandledexception-enumeration.md) 值，指出行為是由 CLR 或主控制項設定。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetUnhandledExceptionPolicy` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 根據預設，CLR 是所有未處理之例外狀況的最終處理常式，而其預設行為是卸載進程。 主機可以藉由將值設定為 eHostDeterminedPolicy 來變更此行為 `policy` 。 此值可讓主機執行它自己的預設行為，如同舊版的 CLR 一樣。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrUnhandledException 列舉](eclrunhandledexception-enumeration.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [ICLRPolicyManager 介面](iclrpolicymanager-interface.md)
- [IHostPolicyManager 介面](ihostpolicymanager-interface.md)
