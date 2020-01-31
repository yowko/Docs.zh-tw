---
title: ICorDebugILFrame3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: 739c648173d45a9c147ea2a4e469a3a4b518e893
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794341"
---
# <a name="icordebugilframe3-interface"></a>ICorDebugILFrame3 介面
提供封裝函式傳回值的方法。 `ICorDebugILFrame3` 是 ICorDebugILFrame 和 ICorDebugILFrame2 介面的邏輯擴充。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReturnValueForILOffset 方法](icordebugilframe3-getreturnvalueforiloffset-method.md)|取得 ICorDebugValue 物件，它會封裝函式的傳回值。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugCode3 介面](icordebugcode3-interface.md)
- [偵錯介面](debugging-interfaces.md)
