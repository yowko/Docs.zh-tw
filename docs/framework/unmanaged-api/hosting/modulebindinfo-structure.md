---
title: ModuleBindInfo 結構
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e0e877402daf27c375aedddf8922e919a546ae5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781171"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo 結構
提供參考的模組和包含它的組件的詳細的資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`dwAppDomainId`|唯一識別碼`IStream`所傳回的呼叫所[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)從其中參考的模組是要載入的方法。|  
|`lpAssemblyIdentity`|包含參考的模組之組件的唯一識別碼。|  
|`lpModuleName`|參考的模組名稱。|  
  
## <a name="remarks"></a>備註  
 `ModuleBindInfo` 做為參數傳遞`IHostAssemblyStore::ProvideModule`。 主應用程式提供的唯一識別碼`dwAppDomainId`common language runtime (CLR)。 在呼叫之後[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)方法傳回時，執行階段會使用識別碼來判斷是否內容`IStream`已經對應。 如果是的話，則執行階段會載入現有的複本，而不是重新對應之資料流。 執行階段也會使用此識別碼做為查閱索引鍵，從呼叫傳回的資料流`IHostAssemblyStore::ProvideAssembly`方法。 因此，識別碼必須是唯一的模組要求也與組件要求。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [AssemblyBindInfo 結構](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
