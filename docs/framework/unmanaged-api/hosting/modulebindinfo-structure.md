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
ms.openlocfilehash: ae40d8adaae70ccff6e8058858a506267d58873f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133753"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo 結構
提供參考模組和包含它之元件的詳細資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`dwAppDomainId`|呼叫[IHostAssemblyStore：:P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)方法時所傳回之 `IStream` 的唯一識別碼，所參考的模組會從中載入。|  
|`lpAssemblyIdentity`|包含參考模組之元件的唯一識別碼。|  
|`lpModuleName`|參考模組的名稱。|  
  
## <a name="remarks"></a>備註  
 `ModuleBindInfo` 會當做參數傳遞給 `IHostAssemblyStore::ProvideModule`。 主機會將唯一識別碼提供給 common language runtime （CLR） `dwAppDomainId`。 呼叫[IHostAssemblyStore：:P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)方法之後，執行時間會使用識別碼來判斷是否已對應 `IStream` 的內容。 若是如此，執行時間就會載入現有的複本，而不是重新對應資料流程。 執行時間也會使用這個識別碼做為從呼叫 `IHostAssemblyStore::ProvideAssembly` 方法所傳回之資料流程的查閱索引鍵。 因此，識別碼在模組要求和元件要求中都必須是唯一的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll .idl  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [AssemblyBindInfo 結構](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
