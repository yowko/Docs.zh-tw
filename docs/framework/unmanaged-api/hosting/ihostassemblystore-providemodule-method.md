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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e07e2c3f2c6000f5a081b13316c269f322b1ef8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078334"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule 方法
解析組件或連結 （但非內嵌） 內的模組資源檔案。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>參數  
 `pBindInfo`  
 [in]指標[ModuleBindInfo](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)執行個體，描述要求的模組<xref:System.AppDomain>，組件，以及模組名稱。  
  
 `pdwModuleId`  
 [out]唯一識別碼的指標`IStream`包含載入的模組。  
  
 `ppStmModuleImage`  
 [out]位址指標`IStream`物件，其中包含要載入，可攜式執行檔 (PE) 映像，或如果找不到模組，則為 null。  
  
 `ppStmPDB`  
 [out]位址指標`IStream`物件，其中包含程式的偵錯 (PDB) 資訊要求的模組，或如果找不到.pdb 檔案，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ProvideModule` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND (0x80070002)|要求的組件或連結的資源找不到。|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` 不能夠容納主機想要傳回的識別項。|  
  
## <a name="remarks"></a>備註  
 針對傳回的識別值`pdwModuleId`由主應用程式。 在處理序的存留期內，識別碼必須是唯一的。 CLR 會使用此值的唯一識別碼做為相關聯的資料流。 它會檢查每個值的值對`pAssemblyId`呼叫所傳回[ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)而的值是針對`pdwModuleId`傳回的其他呼叫`ProvideModule`。 如果主應用程式會傳回相同的識別碼值的另一個`IStream`，CLR 會檢查該資料流的內容是否已經對應。 如果是的話，則 CLR 會載入而不是一個新的映像的現有副本。 因此，識別項也不能重疊與從傳回的組件識別碼`ProvideAssembly`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
