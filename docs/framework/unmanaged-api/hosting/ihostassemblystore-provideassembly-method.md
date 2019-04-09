---
title: IHostAssemblyStore::ProvideAssembly 方法
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 62a8be1e330338043df50bd80576b5aa65447b9c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111900"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly 方法
取得未參考的組件的參考[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)傳回[ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)。 Common language runtime (CLR) 呼叫`ProvideAssembly`不會出現在清單中每個組件。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>參數  
 `pBindInfo`  
 [in]指標[AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)主機用來判斷特定繫結的特性，包括任何版本設定的原則，是否存在的執行個體和要繫結至哪個組件。  
  
 `pAssemblyId`  
 [out]此要求的組件的唯一識別碼的指標`IStream`。  
  
 `pHostContext`  
 [out]用來判斷要求的組件，而不需要的平台的辨識項的主應用程式專屬資料的指標叫用呼叫。 `pHostContext` 對應至<xref:System.Reflection.Assembly.HostContext%2A>的 managed 屬性<xref:System.Reflection.Assembly>類別。  
  
 `ppStmAssemblyImage`  
 [out]位址指標`IStream`，包含要載入，或如果找不到組件，則為 null 的可攜式執行檔 (PE) 映像。  
  
 `ppStmPDB`  
 [out]位址指標`IStream`如果找不到.pdb 檔案包含的程式偵錯 (PDB) 的資訊或 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL CLR 已不再可在此程序中使用。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND (0x80070002)|找不到要求的組件。|  
|E_NOT_SUFFICIENT_BUFFER|所指定的緩衝區大小`pAssemblyId`不夠大，無法存放主機想要傳回的識別項。|  
  
## <a name="remarks"></a>備註  
 針對傳回的識別值`pAssemblyId`由主應用程式。 在處理序的存留期內，識別碼必須是唯一的。 CLR 會使用此值的唯一識別碼做為資料流。 它會檢查每個值的值對`pAssemblyId`傳回的其他呼叫`ProvideAssembly`。 如果主應用程式會傳回相同`pAssemblyId`另一個值`IStream`，CLR 會檢查該資料流的內容是否已經對應。 如果是的話，則執行階段會載入而不是一個新的映像的現有副本。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
