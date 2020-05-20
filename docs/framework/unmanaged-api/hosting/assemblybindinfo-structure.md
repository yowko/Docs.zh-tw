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
ms.openlocfilehash: 615637813b08629aaea74b23fa2737f52d61bafb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616914"
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
  
## <a name="members"></a>成員  
  
|成員|說明|  
|------------|-----------------|  
|`dwAppDomainId`|`IStream`呼叫[IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md)所傳回的唯一識別碼，參考的元件會從此處載入。|  
|`lpReferencedIdentity`|參考元件的唯一識別碼。|  
|`lpPostPolicyIdentity`|應用程式的任何系結原則值之後，所參考元件的識別碼。|  
|`ePolicyLevel`|其中一個[EPolicyAction](epolicyaction-enumeration.md)值，指出哪些版本設定原則（如果有的話）應套用至參考的元件。|  
  
## <a name="remarks"></a>備註  
 主機會提供唯一識別碼 `dwAppDomainId` 給 common language runtime （CLR）。 呼叫傳回之後 `IHostAssemblyStore::ProvideAssembly` ，執行時間會使用識別碼來判斷的內容是否 `IStream` 已對應。 若是如此，執行時間就會載入現有的複本，而不是重新對應資料流程。 執行時間也會使用此識別碼作為從呼叫 IHostAssemblyStore 所傳回之資料流程的查閱索引鍵[：:P rovidemodule](ihostassemblystore-providemodule-method.md)。 因此，對於模組要求和元件要求而言，識別碼必須是唯一的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll .idl  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](hosting-structures.md)
- [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
- [IHostAssemblyStore 介面](ihostassemblystore-interface.md)
- [ModuleBindInfo 結構](modulebindinfo-structure.md)
