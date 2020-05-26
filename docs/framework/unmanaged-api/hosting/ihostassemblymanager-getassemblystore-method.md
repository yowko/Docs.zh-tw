---
title: IHostAssemblyManager::GetAssemblyStore 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 587861529c340fad9fd817b904e4d3651b236e8d
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805077"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a>IHostAssemblyManager::GetAssemblyStore 方法
取得[IHostAssemblyStore](ihostassemblystore-interface.md)的介面指標，表示主機所載入的元件清單。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppAssemblyStore`  
 脫銷實例的函式指標 `IHostAssemblyStore` ，如果主機未執行，則為 null `IHostAssemblyStore` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetAssemblyStore`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOINTERFACE|主機未提供的執行 `IHostAssemblyStore` 。|  
  
## <a name="remarks"></a>備註  
 `IHostAssemblyStore`提供的方法可讓主機與 CLR 獨立系結至元件和模組。 主機通常會提供元件存放區，以允許從檔案系統以外的格式載入元件。  
  
> [!NOTE]
> 如果主機未執行 `IHostAssemblyStore` ， `GetAssemblyStore` 應該會傳回 E_NOINTERFACE 的 HRESULT 值，而且應該將設定 `ppAssemblyStore` 為 null。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
