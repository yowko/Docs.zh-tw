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
ms.openlocfilehash: 1a1bc7609042422de876fe167a9e61655aaf62b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176405"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain 方法
調用指定託管程式集中指定類型的指定方法。  
  
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
 [在]定義要調用其<xref:System.Reflection.Assembly>方法的 的<xref:System.Type>的 路徑。  
  
 `pwzTypeName`  
 [在]定義要調用的方法<xref:System.Type>的名稱。  
  
 `pwzMethodName`  
 [在]要調用的方法的名稱。  
  
 `pwzArgument`  
 [在]要傳遞給方法的字串參數。  
  
 `pReturnValue`  
 [出]被呼叫者法返回的整數值。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|調用方不擁有鎖。|  
|HOST_E_ABANDONED|當阻塞的執行緒或光纖等待事件時，事件已被取消。|  
|E_FAIL|發生了未知的災難性故障。 如果方法返回E_FAIL，則 CRL 在進程中不再可用。 對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 調用的方法必須具有以下簽名：  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 表示`pwzMethodName`被呼叫者法的名稱，並`pwzArgument`表示作為該方法的參數傳遞的字串值。 如果 HRESULT 值設置為S_OK，`pReturnValue`則設置為被呼叫者法返回的整數值。 否則，`pReturnValue`未設置。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
