---
title: IHostAssemblyManager 介面
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e300d4645939a131ceb8206999d95056b96a678
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118946"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager 介面
提供方法，可讓主應用程式指定的 common language runtime (CLR) 或由主機載入的組件集合。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAssemblyStore 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|取得的介面指標[IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)表示主應用程式所載入的組件清單。|  
|[GetNonHostStoreAssemblies 方法](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|取得的介面指標[ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)表示主機必須要有 CLR 載入的組件清單。|  
  
## <a name="remarks"></a>備註  
 主應用程式不需要實作`IHostAssemblyManager`或`IHostAssemblyStore`。 如果主應用程式會實作`IHostAssemblyManager`，它也必須實作`IHostAssemblyStore`。  
  
 執行階段查詢`IHostAssemblyManager`藉由呼叫[ihostcontrol:: Gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md)時使用的初始化`IID`IID_IHostAssemblyManager。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAssemblyReferenceList 介面](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore 介面](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
