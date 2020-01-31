---
title: ICorDebugProcess6::ProcessStateChanged 方法
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792208"
---
# <a name="icordebugprocess6processstatechanged-method"></a>ICorDebugProcess6::ProcessStateChanged 方法
通知[ICorDebug](icordebug-interface.md)進程正在執行。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a>參數  
 `change`  
 在[ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)列舉的成員  
  
## <a name="remarks"></a>備註  
 偵錯工具會呼叫這個方法，以通知[ICorDebug](icordebug-interface.md)進程正在執行。  
  
> [!NOTE]
> 這個方法僅適用於 .NET Native。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugProcess6 介面](icordebugprocess6-interface.md)
- [偵錯介面](debugging-interfaces.md)
