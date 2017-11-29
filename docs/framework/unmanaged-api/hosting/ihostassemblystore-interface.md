---
title: "IHostAssemblyStore 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyStore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyStore
helpviewer_keywords: IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 284afbe73bea28a0aafe8d5e9e030c43be94aea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblystore-interface"></a>IHostAssemblyStore 介面
提供方法，讓主應用程式載入組件和模組與 common language runtime (CLR) 無關。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[ProvideAssembly 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)|取得未被參考的組件的參考[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)從呼叫傳回[ihostassemblymanager:: Getnonhoststoreassemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)。|  
|[ProvideModule 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)|解析組件或連結 （不使用內嵌） 的資源檔內的模組。|  
  
## <a name="remarks"></a>備註  
 `IHostAssemblyStore`提供方法，讓主應用程式能夠有效率地根據組件識別的組件載入。 主控件載入的組件藉由傳回`IStream`直接指向位元組的執行個體。  
  
 CLR 會判斷主機是否已實作`IHostAssemblyStore`藉由呼叫`IHostAssemblyManager::GetNonHostAssemblyStores`在初始化時。 這可讓主應用程式，例如，控制使用者組件，繫結，但依賴.NET Framework 組件繫結的執行階段。  
  
> [!NOTE]
>  在提供的實作`IHostAssemblyStore`，主機指定試圖解決所有未參考的組件`ICLRAssemblyReferenceList`從傳回`IHostAssemblyManager::GetNonHostStoreAssemblies`。  
  
> [!NOTE]
>  .NET Framework 2.0 版不提供方法，讓主應用程式載入組件的原生映像所提供[原生映像產生器 (Ngen.exe)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)公用程式。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
