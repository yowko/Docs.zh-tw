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
ms.openlocfilehash: a34b907514376927d8a1aa66b136916108b704d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681141"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a>IHostAssemblyManager::GetNonHostStoreAssemblies 方法

取得 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) 的介面指標，該指標表示主機預期 common language RUNTIME (CLR) 載入的元件清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppReferenceList`  
 擴展的位址指標 `ICLRAssemblyReferenceList` ，其中包含主機預期 CLR 載入的元件參考清單。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetNonHostStoreAssemblies` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_OUTOFMEMORY|沒有足夠的記憶體可用來建立所要求的參考清單 `ICLRAssemblyReferenceList` 。|  
  
## <a name="remarks"></a>備註  

 CLR 會使用下列一組指導方針來解析參考：  
  
- 首先，它會查閱所傳回的元件參考清單 `GetNonHostStoreAssemblies` 。  
  
- 如果元件出現在清單中，則 CLR 會正常地系結至該元件。  
  
- 如果元件未出現在清單中，且主機已提供 [IHostAssemblyStore](ihostassemblystore-interface.md)的執行，則 CLR 會呼叫 [IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md) ，以允許主機提供要系結的元件。  
  
- 否則，CLR 會無法系結至元件。  
  
 如果主機設 `ppReferenceList` 為 null，CLR 會先探查全域組件快取、呼叫 `ProvideAssembly` ，然後探查應用程式基底來解析元件參考。  
  
> [!NOTE]
> 初始化時，CLR 只會呼叫 `GetNonHostStoreAssemblies` 一次。 未再次呼叫方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
