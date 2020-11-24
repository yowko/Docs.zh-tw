---
title: ICLRSyncManager 介面
ms.date: 03/30/2017
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
ms.openlocfilehash: 5bfab21a36becf943b1813f266cf70c4b5e5b1d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690989"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager 介面

定義方法，可讓主機取得所要求之工作的相關資訊，並偵測其同步處理執行中的鎖死。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator 方法](iclrsyncmanager-createrwlockowneriterator-method.md)|要求 common language runtime (CLR) 為主機建立反覆運算器，以用來判斷等候讀取器寫入器鎖定的工作集。|  
|[DeleteRWLockOwnerIterator 方法](iclrsyncmanager-deleterwlockowneriterator-method.md)|要求 CLR 終結由的呼叫所建立的反覆運算器 `CreateRWLockOwnerIterator` 。|  
|[GetMonitorOwner 方法](iclrsyncmanager-getmonitorowner-method.md)|取得擁有指定之監視的工作。|  
|[GetRWLockOwnerNext 方法](iclrsyncmanager-getrwlockownernext-method.md)|取得正在等候目前讀取器寫入器鎖定的下一個工作。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Thread>
- [IHostSyncManager 介面](ihostsyncmanager-interface.md)
- [Managed 和 Unmanaged 執行緒](/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [裝載介面](hosting-interfaces.md)
