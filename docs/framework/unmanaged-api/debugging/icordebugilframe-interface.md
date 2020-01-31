---
title: ICorDebugILFrame 介面
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
ms.openlocfilehash: 7a27b8ec512498c7bf817aca36267c37d8070a4c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788574"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame 介面

表示 Microsoft 中繼語言（MSIL）程式碼的堆疊框架。 這個介面是 ICorDebugFrame 介面的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanSetIP 方法](icordebugilframe-cansetip-method.md)|取得值，指出是否可以安全地將指令指標設定為指定的位移位置。|  
|[EnumerateArguments 方法](icordebugilframe-enumeratearguments-method.md)|取得此框架中引數的列舉值。|  
|[EnumerateLocalVariables 方法](icordebugilframe-enumeratelocalvariables-method.md)|取得此框架中區域變數的列舉值。|  
|[GetArgument 方法](icordebugilframe-getargument-method.md)|取得這個 MSIL 堆疊框架中指定之引數的值。|  
|[GetIP 方法](icordebugilframe-getip-method.md)|取得指令指標的值，以及描述如何取得指令指標值的位組合值。|  
|[GetLocalVariable 方法](icordebugilframe-getlocalvariable-method.md)|取得這個 MSIL 堆疊框架中指定之區域變數的值。|  
|[GetStackDepth 方法](icordebugilframe-getstackdepth-method.md)|未實作。|  
|[GetStackValue 方法](icordebugilframe-getstackvalue-method.md)|未實作。|  
|[SetIP 方法](icordebugilframe-setip-method.md)|將指令指標設定為 MSIL 程式碼中指定的位移位置。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugILFrame` 介面是特製化的 ICorDebugFrame 介面。 它可用於 MSIL 程式碼框架或即時（JIT）編譯的框架。 JIT 編譯的框架會同時執行 `ICorDebugILFrame` 介面和 ICorDebugNativeFrame 介面。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯介面](debugging-interfaces.md)
