---
title: CorRuntimeHost Coclass
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 942c9544a6ce868c3b6296569d4a16a44281cdba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758328"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost Coclass
提供介面來管理由 common language runtime 所執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>介面  
  
|介面|描述|  
|---------------|-----------------|  
|[ICorConfiguration 介面](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|提供用於設定 common language runtime (CLR) 方法。|  
|[ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|提供方法，讓主應用程式啟動，並明確地停止通用語言執行平台，來建立及設定應用程式定義域，若要存取預設網域，並列舉處理序中執行的所有網域。|  
|[IDebuggerInfo 介面](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|提供方法來取得有關偵錯服務的狀態資訊。|  
|[IGCHost 介面](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。|  
|「 IValidator"|提供用於驗證的可攜式執行檔映像和詳細報告驗證錯誤的方法。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載 Coclass](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
