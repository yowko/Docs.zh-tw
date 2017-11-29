---
title: "IHostAssemblyStore::ProvideAssembly 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore.ProvideAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cda88c2e93b4f90844ad3dec2ed0fa4366dba6d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly 方法
取得未被參考的組件的參考[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)從傳回[ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)。 Common language runtime (CLR) 呼叫`ProvideAssembly`不會出現在清單中每一個組件。  
  
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
  
#### <a name="parameters"></a>參數  
 `pBindInfo`  
 [in]指標[AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)主機用來判斷特定繫結的特性，包括任何版本設定的原則，是否存在的執行個體和要繫結至哪個組件。  
  
 `pAssemblyId`  
 [out]這個要求的組件的唯一識別碼的指標`IStream`。  
  
 `pHostContext`  
 [out]用來判斷要求的組件，而不需要為平台的辨識項的主應用程式特定資料的指標叫用呼叫。 `pHostContext`對應至<xref:System.Reflection.Assembly.HostContext%2A>managed 屬性<xref:System.Reflection.Assembly>類別。  
  
 `ppStmAssemblyImage`  
 [out]位址指標`IStream`其中包含要載入，或者如果找不到組件，則為 null 的可攜式執行檔 (PE) 映像。  
  
 `ppStmPDB`  
 [out]位址指標`IStream`如果找不到.pdb 檔案包含的程式 (PDB) 偵錯資訊或為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 方法會傳回 E_FAIL CLR 已不再可用的處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|COR_E_FILENOTFOUND (0X80070002)|找不到要求的組件。|  
|E_NOT_SUFFICIENT_BUFFER|所指定的緩衝區大小`pAssemblyId`不夠大，無法保存主應用程式想要傳回的識別項。|  
  
## <a name="remarks"></a>備註  
 傳回識別值`pAssemblyId`由主應用程式所指定。 處理序的存留期內，識別項必須是唯一的。 資料流，CLR 會使用此值做為唯一的識別項。 它會檢查每個值的值對`pAssemblyId`其他呼叫所傳回`ProvideAssembly`。 如果主機傳回相同`pAssemblyId`另一個值`IStream`，CLR 會檢查是否已經對應資料流的內容。 如果是這樣，執行階段載入而不是一個新的映像的現有複本。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
