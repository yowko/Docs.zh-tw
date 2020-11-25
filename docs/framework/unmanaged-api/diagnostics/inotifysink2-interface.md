---
title: INotifySink2 介面
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
ms.openlocfilehash: 255fe51f86157842a5807145bf7c58ae1ff5ba8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720018"
---
# <a name="inotifysink2-interface"></a>INotifySink2 介面

宣告接收通知的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[OnSyncCallEnter 方法](inotifysink2-onsynccallenter-method.md)|在輸入呼叫時叫用。|  
|[OnSyncCallExit 方法](inotifysink2-onsynccallexit-method.md)|在結束呼叫時叫用。|  
|[OnSyncCallOut 方法](inotifysink2-onsynccallout-method.md)|在呼叫超時時叫用。|  
|[OnSyncCallReturn 方法](inotifysink2-onsynccallreturn-method.md)|當呼叫傳回時，就會叫用。|  
  
## <a name="requirements"></a>需求  

 **標頭：** ProtocolNotify2 .idl  
  
## <a name="see-also"></a>另請參閱

- [INotifyConnection2 介面](inotifyconnection2-interface.md)
- [INotifySource2 介面](inotifysource2-interface.md)
- [診斷符號存放區介面](diagnostics-symbol-store-interfaces.md)
