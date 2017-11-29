---
title: "IGCHost2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2
helpviewer_keywords: IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c6706696e3fd5158d2b49a4d114d978a26510b67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="igchost2-interface"></a>IGCHost2 介面
提供方法來取得記憶體回收系統的相關資訊，以及控制記憶體回收的某些層面。  
  
> [!NOTE]
>  進行新開發，我們建議您改用[ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)改為介面。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[SetGCStartupLimitsEx 方法](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|層代 0 設定區段的大小和大小上限。 可讓層代 0 和區段大小大於`DWORD`。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** GCHost.idl、 GCHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
