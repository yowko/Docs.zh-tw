---
title: IHostAssemblyStore::ProvideModule 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
ms.openlocfilehash: 35805d277774e1de03bb7dee1740a2e1305a97c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732992"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule 方法

解析元件或連結 (內的模組，但不是內嵌) 資源檔。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>參數  

 `pBindInfo`  
 在 [ModuleBindInfo](modulebindinfo-structure.md) 實例的指標，可描述所要求模組的 <xref:System.AppDomain> 、元件和模組名稱。  
  
 `pdwModuleId`  
 擴展的唯一識別碼指標， `IStream` 包含載入的模組。  
  
 `ppStmModuleImage`  
 擴展物件位址的指標 `IStream` ，其中包含要載入的可攜式可執行檔 (PE) 映射，如果找不到模組，則為 null。  
  
 `ppStmPDB`  
 擴展物件位址的指標 `IStream` ，其中包含所要求模組的程式 debug (PDB) 資訊; 如果找不到 .pdb 檔案，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ProvideModule` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND (0x80070002) |找不到要求的元件或連結的資源。|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` 不夠大，無法包含主機想要傳回的識別碼。|  
  
## <a name="remarks"></a>備註  

 傳回的識別值 `pdwModuleId` 是由主控制項所指定。 識別碼在進程的存留期內必須是唯一的。 CLR 會使用此值做為相關資料流程的唯一識別碼。 它會針對 `pAssemblyId` [ProvideAssembly](ihostassemblystore-provideassembly-method.md) 的呼叫，以及對的其他呼叫所傳回的值，檢查每個值的值 `pdwModuleId` `ProvideModule` 。 如果主機為另一個傳回相同的識別碼值 `IStream` ，則 CLR 會檢查該資料流程的內容是否已對應。 若是如此，CLR 就會載入映射的現有複本，而不是對應新的映射。 因此，識別碼也必須與從傳回的元件識別碼重迭 `ProvideAssembly` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
