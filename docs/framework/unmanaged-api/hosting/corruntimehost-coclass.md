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
ms.openlocfilehash: cd4e675b4ba50b47146428d204c28cc943c23c69
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687999"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost Coclass

提供介面來管理 common language runtime 所執行的應用程式。  
  
## <a name="syntax"></a>Syntax  
  
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
|[ICorConfiguration 介面](icorconfiguration-interface.md)|提供 (CLR) 設定 common language runtime 的方法。|  
|[ICorRuntimeHost 介面](icorruntimehost-interface.md)|提供的方法可讓主機明確地啟動及停止 common language runtime、建立和設定應用程式域、存取預設網域，以及列舉在進程中執行的所有網域。|  
|[IDebuggerInfo 介面](idebuggerinfo-interface.md)|提供方法，以取得有關偵錯工具狀態的資訊。|  
|[IGCHost 介面](igchost-interface.md)|提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。|  
|IValidator|提供驗證可攜式可執行檔映射和詳細報告驗證錯誤的方法。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載 Coclass](hosting-coclasses.md)
