---
title: IHostAssemblyManager::GetNonHostStoreAssemblies 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccd73963302ae99c7d5d1a7201bc77c4544363f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937901"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies 方法
取得[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)的介面指標, 表示主機預期會載入 common language RUNTIME (CLR) 的元件清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppReferenceList`  
 脫銷位址的`ICLRAssemblyReferenceList`指標, 其中包含主機預期 CLR 載入之元件的參考清單。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來建立所要求`ICLRAssemblyReferenceList`的參考清單。|  
  
## <a name="remarks"></a>備註  
 CLR 會使用下列一組指導方針來解析參考:  
  
- 首先, 它會參考所傳回`GetNonHostStoreAssemblies`的元件參考清單。  
  
- 如果元件出現在清單中, 則 CLR 會正常地系結至它。  
  
- 如果元件未出現在清單中, 而且主機已提供[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)的執行, 則 CLR 會呼叫[IHostAssemblyStore::P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) , 讓主機能夠提供要系結的元件。  
  
- 否則, CLR 會無法系結至元件。  
  
 如果主機設定`ppReferenceList`為 null, CLR 會先探查全域組件快取、呼叫`ProvideAssembly`, 然後再探查應用程式基底, 以解析元件參考。  
  
> [!NOTE]
> 在初始化之後, CLR 只`GetNonHostStoreAssemblies`會呼叫一次。 不會再次呼叫方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
