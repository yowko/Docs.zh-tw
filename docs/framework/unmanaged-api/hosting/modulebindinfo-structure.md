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
ms.openlocfilehash: 505015877985492edab4b761b379f33f1e5c6660
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729976"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo 結構

提供參考的模組和包含它的元件的詳細資訊。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>成員  
  
|member|描述|  
|------------|-----------------|  
|`dwAppDomainId`|的唯一識別碼 `IStream` ，它是由呼叫 [IHostAssemblyStore：:P rovidemodule](ihostassemblystore-providemodule-method.md) 方法所傳回，該方法是要從中載入參考的模組。|  
|`lpAssemblyIdentity`|包含參考模組之元件的唯一識別碼。|  
|`lpModuleName`|參考模組的名稱。|  
  
## <a name="remarks"></a>備註  

 `ModuleBindInfo` 以參數形式傳遞至 `IHostAssemblyStore::ProvideModule` 。 主機會將唯一識別碼提供 `dwAppDomainId` 給 common language runtime (CLR) 。 在呼叫 [IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md) 方法之後，執行時間會使用此識別碼來判斷的內容是否已 `IStream` 對應。 如果是，執行時間會載入現有的複本，而不是重新對應資料流程。 執行時間也會使用這個識別碼做為呼叫方法所傳回之資料流程的查閱索引鍵 `IHostAssemblyStore::ProvideAssembly` 。 因此，識別碼對於模組要求以及元件要求都必須是唯一的。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](hosting-structures.md)
- [AssemblyBindInfo 結構](assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
