---
title: AssemblyBindInfo 結構
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 8764a3d665c997460419561eb168f92ca769c30c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192105"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo 結構
提供有關所參考元件的詳細資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`dwAppDomainId`|呼叫[IHostAssemblyStore：:P rovideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)所傳回之 `IStream` 的唯一識別碼，所參考的元件會從中載入。|  
|`lpReferencedIdentity`|參考元件的唯一識別碼。|  
|`lpPostPolicyIdentity`|應用程式的任何系結原則值之後，所參考元件的識別碼。|  
|`ePolicyLevel`|其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指出哪些版本設定原則（如果有的話）應套用至參考的元件。|  
  
## <a name="remarks"></a>備註  
 主機會將唯一識別碼提供給 common language runtime （CLR） `dwAppDomainId`。 呼叫 `IHostAssemblyStore::ProvideAssembly` 傳回之後，執行時間會使用識別碼來判斷是否已對應 `IStream` 的內容。 若是如此，執行時間就會載入現有的複本，而不是重新對應資料流程。 執行時間也會使用此識別碼作為從呼叫 IHostAssemblyStore 所傳回之資料流程的查閱索引鍵[：:P rovidemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)。 因此，對於模組要求和元件要求而言，識別碼必須是唯一的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll .idl  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [ModuleBindInfo 結構](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
