---
title: ICLRIoCompletionManager 介面
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: e23675351e1fd0de510243c9ee8b3a6dd6f29cec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714116"
---
# <a name="iclriocompletionmanager-interface"></a>ICLRIoCompletionManager 介面

執行回呼方法，這個方法可讓主機通知 common language runtime (CLR) 指定的 i/o 要求的狀態。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OnComplete 方法](iclriocompletionmanager-oncomplete-method.md)|使用 [IHostIoCompletionManager：： Bind](ihostiocompletionmanager-bind-method.md) 方法的呼叫，將發出的 i/o 要求狀態通知 CLR。|  
  
## <a name="remarks"></a>備註  

 主機會使用 [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) 介面來執行 i/o 完成抽象概念。 CLR 會透過這個介面提出 i/o 要求，且主機會使用介面，通知執行時間結果這類要求的結果 `ICLRIoCompletionManager` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IHostIoCompletionManager 介面](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager 介面](ihostthreadpoolmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
