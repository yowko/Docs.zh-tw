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
ms.openlocfilehash: 162def0d703ea81efc3df3ea5ee08b58e34822e6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501569"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly 方法
取得從[IHostAssemblyManager：： GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)傳回之[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)未參考的元件參考。 不 `ProvideAssembly` 會出現在清單中的每個元件的 common language runtime （CLR）呼叫。  
  
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
 在[AssemblyBindInfo](assemblybindinfo-structure.md)實例的指標，可供主機用來判斷特定系結特性，包括是否有任何版本設定原則，以及要系結至哪個元件。  
  
 `pAssemblyId`  
 脫銷這個之所要求元件的唯一識別碼指標 `IStream` 。  
  
 `pHostContext`  
 脫銷主機特定資料的指標，用來判斷所要求元件的辨識項，而不需要平台叫用呼叫。 `pHostContext`對應至 <xref:System.Reflection.Assembly.HostContext%2A> managed 類別的屬性 <xref:System.Reflection.Assembly> 。  
  
 `ppStmAssemblyImage`  
 脫銷位址的指標， `IStream` 其中包含要載入的可移植執行檔（PE）影像，如果找不到元件，則為 null。  
  
 `ppStmPDB`  
 脫銷`IStream`包含程式 debug （PDB）資訊之位址的指標，如果找不到 .pdb 檔，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND （0x80070002）|找不到要求的元件。|  
|E_NOT_SUFFICIENT_BUFFER|所指定的緩衝區大小不夠 `pAssemblyId` 大，無法容納主機想要傳回的識別碼。|  
  
## <a name="remarks"></a>備註  
 為傳回的識別值 `pAssemblyId` 由主機指定。 識別碼在進程的存留期間內必須是唯一的。 CLR 會使用此值做為資料流程的唯一識別碼。 它會針對其他呼叫所傳回的值，檢查每個值 `pAssemblyId` `ProvideAssembly` 。 如果主機 `pAssemblyId` 針對另一個傳回相同的值 `IStream` ，CLR 會檢查該資料流程的內容是否已對應。 若是如此，執行時間就會載入影像的現有複本，而不是對應新的映射。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
