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
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616992"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager 介面
提供的方法可讓主機設定錯誤報表的自訂堆疊傾印。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginCustomDump 方法](iclrerrorreportingmanager-begincustomdump-method.md)|指定錯誤報表的自訂堆疊傾印設定。|  
|[EndCustomDump 方法](iclrerrorreportingmanager-endcustomdump-method.md)|清除先前呼叫所設定的自訂堆疊傾印設定 `BeginCustomDump` 。|  
|[GetBucketParametersForCurrentException 方法](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|取得呼叫執行緒上目前例外狀況的 Watson 值區。|  
  
## <a name="remarks"></a>備註  
 `BeginCustomDump`方法會設定自訂堆疊傾印設定。 `EndCustomDump`方法會清除自訂堆疊傾印設定，並釋放任何相關聯的狀態。 它應該在自訂傾印完成後呼叫。  
  
> [!IMPORTANT]
> 呼叫失敗 `EndCustomDump` 會造成記憶體流失。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ECustomDumpItemKind 列舉](ecustomdumpitemkind-enumeration.md)
- [裝載介面](hosting-interfaces.md)
