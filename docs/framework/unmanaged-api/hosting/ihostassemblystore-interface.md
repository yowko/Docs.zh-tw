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
ms.openlocfilehash: f881440b2e93745723bd090cfbab0286dcd0a4e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937867"
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore 介面
提供的方法可讓主機獨立載入元件和模組, 而不受 common language runtime (CLR) 的影響。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ProvideAssembly 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|取得對[IHostAssemblyManager:: GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)的呼叫所傳回之[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)未參考的元件參考。|  
|[ProvideModule 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|解析元件或連結 (非內嵌) 資源檔內的模組。|  
  
## <a name="remarks"></a>備註  
 `IHostAssemblyStore`提供一種方式, 讓主機根據元件識別有效率地載入元件。 主機會藉由`IStream`傳回直接指向位元組的實例來載入元件。  
  
 CLR 會藉由在初始化時呼叫`IHostAssemblyStore` `IHostAssemblyManager::GetNonHostAssemblyStores`來判斷主機是否已執行。 例如, 這可讓主機控制使用者元件的系結, 但依賴執行時間來系結至 .NET Framework 元件。  
  
> [!NOTE]
> 在提供的`IHostAssemblyStore`執行時, 主機會指定其目的, 以解析傳回之`IHostAssemblyManager::GetNonHostStoreAssemblies`所參考的`ICLRAssemblyReferenceList`所有元件。  
  
> [!NOTE]
> .NET Framework 版本2.0 不會提供方法, 讓主機載入元件的原生映射, 如同[原生映射產生器 (ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)公用程式所提供。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
