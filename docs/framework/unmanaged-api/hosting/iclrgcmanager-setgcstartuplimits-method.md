---
title: ICLRGCManager::SetGCStartupLimits 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
ms.openlocfilehash: 645b64c8b536029663c350bdcde9a716a715aab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178088"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a>ICLRGCManager::SetGCStartupLimits 方法
設置垃圾回收段的大小和垃圾回收系統第 0 代的最大大小。  
  
> [!IMPORTANT]
> 從 .NET 框架 4.5 開始，可以將段大小和最大生成 0 大小設置為`DWORD`大於使用[ICLRGCManager2：：setGC 啟動極限Ex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法的值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>參數  
 `SegmentSize`  
 [在]垃圾回收段的指定大小。  
  
 最小段大小為 4 MB。 段可以以 1 MB 或更大的增量增加。  
  
 `MaxGen0Size`  
 [在]第 0 代的指定最大大小。  
  
 最小生成 0 大小為 64 KB。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimits`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|調用方不擁有鎖。|  
|HOST_E_ABANDONED|當阻塞的執行緒或光纖等待事件時，事件已被取消。|  
|E_FAIL|發生了未知的災難性故障。 方法返回E_FAIL後，CLR 在進程中不再可用。 對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 只能指定一`SetGCStartupLimits`次設置的值。 稍後將忽略對`SetGCStartupLimits`的調用。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [自動記憶體管理](../../../standard/automatic-memory-management.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRGCManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
