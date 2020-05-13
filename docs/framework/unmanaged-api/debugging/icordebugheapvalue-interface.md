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
ms.openlocfilehash: 36a485413490045ca49b99fca4fe5d43edc37114
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213006"
---
# <a name="icordebugheapvalue-interface"></a>ICorDebugHeapValue 介面

"ICorDebugValue" 的子類別，代表由 common language runtime （CLR）垃圾收集行程所收集的物件。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateRelocBreakpoint 方法](icordebugheapvalue-createrelocbreakpoint-method.md)|未實作。|  
|[IsValid 方法](icordebugheapvalue-isvalid-method.md)|取得值，指出這個所表示的物件是否 `ICorDebugHeapValue` 有效，或已由垃圾收集行程回收。 這個方法已在 .NET Framework 版本2.0 中被取代。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
