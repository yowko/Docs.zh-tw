---
title: ICLRErrorReportingManager 介面
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a9d9cff0360e4eb27584fe0f22c1c20396ff8f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966250"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager 介面
提供的方法可讓主機設定錯誤報表的自訂堆疊傾印。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[BeginCustomDump 方法](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|指定錯誤報表的自訂堆疊傾印設定。|  
|[EndCustomDump 方法](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|清除先前呼叫`BeginCustomDump`所設定的自訂堆疊傾印設定。|  
|[GetBucketParametersForCurrentException 方法](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|取得呼叫執行緒上目前例外狀況的 Watson 值區。|  
  
## <a name="remarks"></a>備註  
 `BeginCustomDump`方法會設定自訂堆疊傾印設定。 `EndCustomDump`方法會清除自訂堆疊傾印設定, 並釋放任何相關聯的狀態。 它應該在自訂傾印完成後呼叫。  
  
> [!IMPORTANT]
> 呼叫`EndCustomDump`失敗會造成記憶體流失。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ECustomDumpItemKind 列舉](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
