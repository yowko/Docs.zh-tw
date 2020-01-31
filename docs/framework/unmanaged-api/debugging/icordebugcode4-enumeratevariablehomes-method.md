---
title: ICorDebugCode4：： EnumerateVariableHomes 方法
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: ca452b230e2508f2d69c9aa38f274db506f3a906
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784094"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4：： EnumerateVariableHomes 方法
取得函數中區域變數和引數的列舉值。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppEnum`  
 [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)介面物件之位址的指標，這是函式中區域變數和引數的列舉值。  
  
## <a name="remarks"></a>備註  
 [ICorDebugVariableHomeEnum](icordebugvariablehomeenum-interface.md)介面物件是衍生自 "ICorDebugEnum" 介面的標準列舉值，可讓您列舉[ICorDebugVariableHome](icordebugvariablehome-interface.md)物件。 如果相同的位置或引數索引在函式的不同點有不同的主物件，則該集合可能包含多個[ICorDebugVariableHome](icordebugvariablehome-interface.md)物件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugCode4 介面](icordebugcode4-interface.md)
- [偵錯介面](debugging-interfaces.md)
