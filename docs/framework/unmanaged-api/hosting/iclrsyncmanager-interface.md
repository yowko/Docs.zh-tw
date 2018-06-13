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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b87ccc3d6c3e957d0384499048032e35247093a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436477"
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager 介面
定義方法，讓主應用程式取得要求的工作的相關資訊，並在同步處理實作偵測死結。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator 方法](iclrsyncmanager-createrwlockowneriterator-method.md)|Common language runtime (CLR) 建立的主機可用來判斷一組工作正在等候讀取器-寫入器鎖定之迭代器的要求。|  
|[DeleteRWLockOwnerIterator 方法](iclrsyncmanager-deleterwlockowneriterator-method.md)|要求 CLR 終結迭代器所建立的呼叫`CreateRWLockOwnerIterator`。|  
|[GetMonitorOwner 方法](iclrsyncmanager-getmonitorowner-method.md)|取得擁有指定的監視的工作。|  
|[GetRWLockOwnerNext 方法](iclrsyncmanager-getrwlockownernext-method.md)|取得正在等候目前的讀取器-寫入器鎖定下一個工作。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Thread>  
 [IHostSyncManager 介面](ihostsyncmanager-interface.md)  
 [Managed 和 Unmanaged 執行緒處理](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [裝載介面](hosting-interfaces.md)
