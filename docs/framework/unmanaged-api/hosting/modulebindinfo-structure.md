---
title: "ModuleBindInfo 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6488503e0300530b22c0c6f904e11db7f5d5b41c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo 結構
提供參考的模組和包含它的組件的詳細的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`dwAppDomainId`|唯一識別碼`IStream`呼叫所傳回[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)從中參照的模組已載入的方法。|  
|`lpAssemblyIdentity`|組件，其中包含參考之的模組的唯一識別碼。|  
|`lpModuleName`|參照的模組名稱。|  
  
## <a name="remarks"></a>備註  
 `ModuleBindInfo`會當做參數傳遞`IHostAssemblyStore::ProvideModule`。 主機提供的唯一識別碼`dwAppDomainId`common language runtime (CLR)。 若要在呼叫之後[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)方法傳回時，執行階段使用的識別項來決定是否的內容`IStream`已經對應。 如果是這樣，執行階段會載入現有的複本，而非重新對應資料流。 執行階段也使用此識別碼做為查閱索引鍵，會從呼叫傳回的資料流的`IHostAssemblyStore::ProvideAssembly`方法。 因此，識別碼必須是唯一的模組要求和與組件的要求。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [AssemblyBindInfo 結構](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
