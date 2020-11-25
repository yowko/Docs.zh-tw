---
title: ICorDebugHeapValue2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2
helpviewer_keywords:
- ICorDebugHeapValue2 interface [.NET Framework debugging]
ms.assetid: 87360a52-90b1-4ada-80c0-589a556116d8
topic_type:
- apiref
ms.openlocfilehash: c959856e8c019f95d38cac9bc4d8d03bc31ef195
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726544"
---
# <a name="icordebugheapvalue2-interface"></a>ICorDebugHeapValue2 介面

ICorDebugHeapValue 的延伸模組，可提供 common language runtime (CLR) 控制碼的支援。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateHandle 方法](icordebugheapvalue2-createhandle-method.md)|為此物件建立指定之類型的控制碼 `ICorDebugHeapValue2` 。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯介面](debugging-interfaces.md)
