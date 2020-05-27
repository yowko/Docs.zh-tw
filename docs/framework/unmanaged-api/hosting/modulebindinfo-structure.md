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
ms.openlocfilehash: 31be0525c637e50c1161129277d651b56dadfaa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006749"
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
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`dwAppDomainId`|`IStream`呼叫[IHostAssemblyStore：:P rovidemodule](ihostassemblystore-providemodule-method.md)方法時所傳回的唯一識別碼，參考的模組會從中載入。|  
|`lpAssemblyIdentity`|包含參考模組之元件的唯一識別碼。|  
|`lpModuleName`|參考模組的名稱。|  
  
## <a name="remarks"></a>備註  
 `ModuleBindInfo`會當做參數傳遞至 `IHostAssemblyStore::ProvideModule` 。 主機會提供唯一識別碼 `dwAppDomainId` 給 common language runtime （CLR）。 呼叫[IHostAssemblyStore：:P rovideassembly](ihostassemblystore-provideassembly-method.md)方法之後，執行時間會使用識別碼來判斷的內容是否 `IStream` 已對應。 若是如此，執行時間就會載入現有的複本，而不是重新對應資料流程。 執行時間也會使用這個識別碼做為從呼叫方法所傳回之資料流程的查閱索引鍵 `IHostAssemblyStore::ProvideAssembly` 。 因此，識別碼在模組要求和元件要求中都必須是唯一的。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll .idl  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載結構](hosting-structures.md)
- [AssemblyBindInfo 結構](assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager 介面](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList 介面](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](ihostassemblymanager-interface.md)
