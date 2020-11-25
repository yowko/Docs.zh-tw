---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: df0b2d96963ad03e04bd8770d8a8078c6c20b8ff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728858"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain 方法

呼叫指定之 managed 元件中指定之類型的指定方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a>參數  

 `pwzAssemblyPath`  
 在的路徑 <xref:System.Reflection.Assembly> ，它會定義 <xref:System.Type> 要叫用其方法的。  
  
 `pwzTypeName`  
 在的名稱 <xref:System.Type> ，定義要叫用的方法。  
  
 `pwzMethodName`  
 在要叫用之方法的名稱。  
  
 `pwzArgument`  
 在要傳遞給方法的字串參數。  
  
 `pReturnValue`  
 擴展叫用方法所傳回的整數值。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則在進程內將無法再使用 CRL。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 叫用的方法必須具有下列簽章：  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 其中 `pwzMethodName` 代表已叫用之方法的名稱，並 `pwzArgument` 代表傳遞給該方法之參數的字串值。 如果 HRESULT 值設定為 S_OK， `pReturnValue` 會設定為叫用方法所傳回的整數值。 否則， `pReturnValue` 就不會設定。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)
