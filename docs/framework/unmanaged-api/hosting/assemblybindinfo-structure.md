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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce79987c7fcf45b8d10dcc4613e053ee735941de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112810"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo 結構
提供參考的組件的詳細的資訊。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`dwAppDomainId`|唯一識別碼`IStream`呼叫所傳回的[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)，從參考的組件即載入。|  
|`lpReferencedIdentity`|參考的組件的唯一識別碼。|  
|`lpPostPolicyIdentity`|參考的組件之後的任何繫結的原則值的應用程式識別碼。|  
|`ePolicyLevel`|其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指出哪一個版本控制，如果有的話，應該套用原則的參考組件。|  
  
## <a name="remarks"></a>備註  
 主應用程式提供的唯一識別碼`dwAppDomainId`common language runtime (CLR)。 在呼叫之後`IHostAssemblyStore::ProvideAssembly`傳回時，執行階段會使用識別碼來判斷是否內容`IStream`已經對應。 如果是的話，則執行階段會載入現有的複本，而不是重新對應之資料流。 執行階段也會使用此識別碼做為查閱索引鍵從傳回的資料流呼叫[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)。 因此，識別碼必須是唯一的模組要求，並針對組件要求。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [ICLRAssemblyIdentityManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [ModuleBindInfo 結構](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
