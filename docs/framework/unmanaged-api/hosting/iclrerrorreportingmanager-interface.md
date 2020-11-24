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
ms.openlocfilehash: d3816c8a3b6204b053505aa888eb28d696f8990b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677835"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager 介面

提供可讓主機針對錯誤報表設定自訂堆疊傾印的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginCustomDump 方法](iclrerrorreportingmanager-begincustomdump-method.md)|針對錯誤報表，指定自訂堆疊傾印的設定。|  
|[EndCustomDump 方法](iclrerrorreportingmanager-endcustomdump-method.md)|清除先前呼叫所設定的自訂堆疊傾印設定 `BeginCustomDump` 。|  
|[GetBucketParametersForCurrentException 方法](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|取得目前例外狀況在呼叫執行緒上的 Watson 值區。|  
  
## <a name="remarks"></a>備註  

 `BeginCustomDump`方法會設定自訂堆疊傾印設定。 `EndCustomDump`方法會清除自訂堆疊傾印設定，並釋出任何相關聯的狀態。 它應該在自訂傾印完成後呼叫。  
  
> [!IMPORTANT]
> 呼叫失敗 `EndCustomDump` 會導致記憶體流失。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ECustomDumpItemKind 列舉](ecustomdumpitemkind-enumeration.md)
- [裝載介面](hosting-interfaces.md)
