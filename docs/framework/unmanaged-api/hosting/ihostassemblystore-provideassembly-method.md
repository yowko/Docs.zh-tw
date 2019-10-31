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
ms.openlocfilehash: a93d700c9c398076d87156cd2eb9c6d0d08cccfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124480"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly 方法
取得從[IHostAssemblyManager：： GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)傳回之[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)未參考的元件參考。 Common language runtime （CLR）會針對每個未出現在清單中的元件呼叫 `ProvideAssembly`。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
 在[AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)實例的指標，可供主機用來判斷特定系結特性，包括是否有任何版本設定原則，以及要系結至哪個元件。  
  
 `pAssemblyId`  
 脫銷這個 `IStream`之要求元件的唯一識別碼指標。  
  
 `pHostContext`  
 脫銷主機特定資料的指標，用來判斷所要求元件的辨識項，而不需要平台叫用呼叫。 `pHostContext` 對應至 managed <xref:System.Reflection.Assembly> 類別的 <xref:System.Reflection.Assembly.HostContext%2A> 屬性。  
  
 `ppStmAssemblyImage`  
 脫銷`IStream` 的位址指標，其中包含要載入的可移植執行檔（PE）影像，如果找不到元件，則為 null。  
  
 `ppStmPDB`  
 脫銷包含程式 debug （PDB）資訊之 `IStream` 位址的指標，如果找不到 .pdb 檔，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `ProvideAssembly`。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND （0x80070002）|找不到要求的元件。|  
|E_NOT_SUFFICIENT_BUFFER|`pAssemblyId` 所指定的緩衝區大小不夠大，無法容納主機想要傳回的識別碼。|  
  
## <a name="remarks"></a>備註  
 針對 `pAssemblyId` 所傳回的識別值是由主機指定。 識別碼在進程的存留期間內必須是唯一的。 CLR 會使用此值做為資料流程的唯一識別碼。 它會根據 `ProvideAssembly`的其他呼叫所傳回的 `pAssemblyId` 值來檢查每個值。 如果主機針對另一個 `IStream`傳回相同的 `pAssemblyId` 值，則 CLR 會檢查該資料流程的內容是否已對應。 若是如此，執行時間就會載入影像的現有複本，而不是對應新的映射。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
