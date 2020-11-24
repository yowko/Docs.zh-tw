---
title: ICLRGCManager::Collect 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
ms.openlocfilehash: 90ce4e888ddb3a10dd0dfd7e68463311db86742f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677761"
---
# <a name="iclrgcmanagercollect-method"></a>ICLRGCManager::Collect 方法

針對指定的層級強制進行垃圾收集。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a>參數  

 `Generation`  
 在要收集的世代。 值-1 會強制所有層代的集合。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Collect` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 `Collect`無論目前的狀態為何，方法都會強制 CLR 的垃圾收集行程執行集合。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [自動記憶體管理](../../../standard/automatic-memory-management.md)
- [記憶體回收](../../../standard/garbage-collection/index.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [ICLRGCManager 介面](iclrgcmanager-interface.md)
- [CLR 裝載介面](clr-hosting-interfaces.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
