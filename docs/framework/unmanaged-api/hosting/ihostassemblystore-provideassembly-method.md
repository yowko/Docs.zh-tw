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
ms.openlocfilehash: db65519579104dd01816bb6d7cacaec947f24f53
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680861"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly 方法

取得從[IHostAssemblyManager：： GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md)傳回的[ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md)未參考之元件的參考。 Common language runtime (CLR) 呼叫 `ProvideAssembly` 未出現在清單中的每個元件。  
  
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
 在 [AssemblyBindInfo](assemblybindinfo-structure.md) 實例的指標，主機會使用此實例來判斷特定系結特性，包括是否存在任何版本控制原則，以及要系結至哪個元件。  
  
 `pAssemblyId`  
 擴展所要求元件的唯一識別碼指標 `IStream` 。  
  
 `pHostContext`  
 擴展主機特定資料的指標，可用來判斷所要求元件的辨識項，而不需要平台叫用呼叫。 `pHostContext` 對應至 <xref:System.Reflection.Assembly.HostContext%2A> managed 類別的屬性 <xref:System.Reflection.Assembly> 。  
  
 `ppStmAssemblyImage`  
 擴展的位址指標， `IStream` 其中包含要載入的可攜式可執行檔 (PE) 映射，如果找不到元件，則為 null。  
  
 `ppStmPDB`  
 擴展的位址指標， `IStream` 其中包含程式 debug (PDB) 資訊; 如果找不到 .pdb 檔案，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND (0x80070002) |找不到要求的元件。|  
|E_NOT_SUFFICIENT_BUFFER|指定的緩衝區大小不夠 `pAssemblyId` 大，無法容納主機想要傳回的識別碼。|  
  
## <a name="remarks"></a>備註  

 傳回的識別值 `pAssemblyId` 是由主控制項所指定。 識別碼在進程的存留期內必須是唯一的。 CLR 會使用此值做為資料流程的唯一識別碼。 它會根據的其他呼叫所傳回的值來檢查每個值 `pAssemblyId` `ProvideAssembly` 。 如果主機 `pAssemblyId` 針對另一個傳回相同的值 `IStream` ，則 CLR 會檢查是否已對應該資料流程的內容。 如果是，執行時間會載入映射的現有複本，而不是對應新的映射。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
