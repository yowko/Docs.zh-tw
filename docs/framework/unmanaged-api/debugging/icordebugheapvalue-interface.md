---
title: ICorDebugHeapValue 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: ee3ea319360bba1a113c15daf8cf143ea512e5cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733317"
---
# <a name="icordebugheapvalue-interface"></a>ICorDebugHeapValue 介面

"ICorDebugValue" 的子類別，代表 common language runtime (CLR) 垃圾收集行程所收集的物件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateRelocBreakpoint 方法](icordebugheapvalue-createrelocbreakpoint-method.md)|未實作。|  
|[IsValid 方法](icordebugheapvalue-isvalid-method.md)|取得值，這個值表示這個所表示的物件是否 `ICorDebugHeapValue` 有效，或是否已由垃圾收集行程回收。 在 .NET Framework 版本2.0 中，此方法已被取代。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
