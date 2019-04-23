---
title: IHostAssemblyStore 介面
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4067c1fbcf99c903c892eaec58262d95569114b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173416"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore 介面
提供方法，可讓主應用程式載入組件和模組與 common language runtime (CLR) 無關。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ProvideAssembly 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|取得未參考的組件的參考[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)從呼叫傳回[ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)。|  
|[ProvideModule 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|解析組件或連結的 （未內嵌） 的資源檔內的模組。|  
  
## <a name="remarks"></a>備註  
 `IHostAssemblyStore` 可讓主應用程式載入有效的組件識別為基礎的組件。 主應用程式載入的組件，藉由傳回`IStream`直接指向位元組的執行個體。  
  
 CLR 可讓您判斷主機是否已實作`IHostAssemblyStore`藉由呼叫`IHostAssemblyManager::GetNonHostAssemblyStores`初始化時。 這可讓主應用程式，例如，控制繫結至使用者的組件，而是依賴執行階段繫結至.NET Framework 組件。  
  
> [!NOTE]
>  提供實作`IHostAssemblyStore`，主應用程式指定解析所有組件，不會參考其意圖`ICLRAssemblyReferenceList`傳回`IHostAssemblyManager::GetNonHostStoreAssemblies`。  
  
> [!NOTE]
>  .NET Framework 2.0 版不提供主應用程式載入的組件，原生映像的方式，提供[原生映像產生器 (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)公用程式。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
