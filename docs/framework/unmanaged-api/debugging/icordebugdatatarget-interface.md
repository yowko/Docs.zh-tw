---
title: ICorDebugDataTarget 介面
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 480fc27bd41f7ca559ceee379b7f6f81c94da0ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59188704"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget 介面
提供回呼介面，該介面可供存取特定的目標處理序。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetPlatform 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|提供的平台，包括處理器架構與目標處理序執行所在的作業系統的相關資訊。|  
|[ReadVirtual 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|取得從指定的位址、 開始的連續記憶體區塊，並傳回它在提供的緩衝區。|  
|[GetThreadContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|要求目前的執行緒內容，針對指定的執行緒。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugDataTarget` 其方法具有下列特性：  
  
-   偵錯的服務會呼叫這個介面來存取記憶體和目標處理序中的其他資料上的方法。  
  
-   偵錯工具用戶端必須實作這個介面適用於特定的目標 （例如，即時處理序或傾印記憶體）。  
  
-   `ICorDebugDataTarget`可以叫用方法只會從內實作的其他方法`ICorDebug*`介面。 這可確保具有控制哪一個執行緒上叫用它，而當偵錯工具用戶端。  
  
-   `ICorDebugDataTarget`實作必須永遠會傳回目標的最新狀態資訊。  
  
 目標處理序應該停止，並不會變更以任何方式，同時`ICorDebug*`介面 (因此`ICorDebugDataTarget`方法) 呼叫。 如果目標是即時的處理序和其狀態變更， [iclrdebugging:: Openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)方法必須再次呼叫，以提供取代 ICorDebugProcess 執行個體。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
