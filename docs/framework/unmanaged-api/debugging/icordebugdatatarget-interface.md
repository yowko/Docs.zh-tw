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
ms.openlocfilehash: 14f0b247ded363dedce193886aab50538db3e6a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683676"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget 介面

提供回呼介面，該介面可供存取特定的目標處理序。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetPlatform 方法](icordebugdatatarget-getplatform-method.md)|提供目標進程執行所在平臺的相關資訊，包括處理器架構和作業系統。|  
|[ReadVirtual 方法](icordebugdatatarget-readvirtual-method.md)|從指定的位址開始，取得連續記憶體的區塊，並在提供的緩衝區中傳回。|  
|[GetThreadContext 方法](icordebugdatatarget-getthreadcontext-method.md)|要求指定執行緒目前的執行緒內容。|  
  
## <a name="remarks"></a>備註  

 `ICorDebugDataTarget` 而且其方法具有下列特性：  
  
- 偵錯工具服務會呼叫這個介面上的方法，以存取目標進程中的記憶體和其他資料。  
  
- 偵錯工具用戶端必須適當地執行此介面，以適用于特定目標 (例如，即時進程或記憶體傾印) 。  
  
- 您只能 `ICorDebugDataTarget` 從在其他介面中執行的方法內叫用方法 `ICorDebug*` 。 這可確保偵錯工具用戶端可以控制叫用的執行緒，以及時機。  
  
- `ICorDebugDataTarget`執行必須一律傳回最新的目標資訊。  
  
 在 `ICorDebug*` 介面 (以及呼叫) 的方法時，目標進程應以任何方式停止且不會變更 `ICorDebugDataTarget` 。 如果目標是即時進程且其狀態變更，則必須再次呼叫 [ICLRDebugging：： OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) 方法，以提供取代的 ICorDebugProcess 實例。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
- [偵錯](index.md)
