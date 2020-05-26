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
ms.openlocfilehash: 002f4177f19c2aae99e91e3fe1029b81e17481dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805004"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule 方法
解析元件中的模組或連結的（但不是內嵌的）資源檔。  
  
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
 在[ModuleBindInfo](modulebindinfo-structure.md)實例的指標，其描述所要求的模組 <xref:System.AppDomain> 、元件和模組名稱。  
  
 `pdwModuleId`  
 脫銷包含已載入模組之唯一識別碼的指標 `IStream` 。  
  
 `ppStmModuleImage`  
 脫銷物件位址的指標 `IStream` ，其中包含要載入的可移植執行檔（PE）影像，如果找不到模組，則為 null。  
  
 `ppStmPDB`  
 脫銷物件位址的指標 `IStream` ，其中包含所要求模組的程式 debug （PDB）資訊，如果找不到 .pdb 檔，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ProvideModule`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND （0x80070002）|找不到要求的元件或連結的資源。|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId`不夠大，無法包含主機想要傳回的識別碼。|  
  
## <a name="remarks"></a>備註  
 為傳回的識別值 `pdwModuleId` 由主機指定。 識別碼在進程的存留期間內必須是唯一的。 CLR 會使用此值做為相關聯資料流程的唯一識別碼。 它會根據 ProvideAssembly 的呼叫所傳回的值 `pAssemblyId` ，以及[ProvideAssembly](ihostassemblystore-provideassembly-method.md)針對其他呼叫所傳回的值，檢查每個值 `pdwModuleId` `ProvideModule` 。 如果主機針對另一個傳回相同的識別碼值 `IStream` ，CLR 會檢查該資料流程的內容是否已對應。 若是如此，CLR 會載入影像的現有複本，而不是對應新的映射。 因此，此識別碼也不能與從傳回的元件識別碼重迭 `ProvideAssembly` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
