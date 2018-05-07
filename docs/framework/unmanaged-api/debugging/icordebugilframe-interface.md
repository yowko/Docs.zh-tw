---
title: ICorDebugILFrame Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a97704e00278e19181df569f108f428cb1ec90f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugilframe-interface1"></a>ICorDebugILFrame Interface1
表示 Microsoft intermediate language (MSIL) 程式碼的堆疊框架。 這個介面是 ICorDebugFrame 介面的子類別。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CanSetIP 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|取得值，指出是否能夠安全地將指令指標設定至指定的位移位置。|  
|[EnumerateArguments 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|在這個框架中取得的引數的列舉值。|  
|[EnumerateLocalVariables 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|取得在這個框架中區域變數的列舉值。|  
|[GetArgument 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|在這個 MSIL 堆疊框架中取得指定的引數的值。|  
|[GetIP 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|取得指令指標的值以及說明如何取得指令指標的值的位元組合值。|  
|[GetLocalVariable 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|從此 MSIL 堆疊框架中取得指定的本機變數的值。|  
|[GetStackDepth 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|未實作。|  
|[GetStackValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|未實作。|  
|[SetIP 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|將指令指標設定為 MSIL 程式碼中指定的位移位置。|  
  
## <a name="remarks"></a>備註  
 `ICorDebugILFrame`介面是特殊的 ICorDebugFrame 介面。 它用 MSIL 程式碼框架，或在 just-in-time (JIT) 編譯的框架。 JIT 編譯的框架會同時實作`ICorDebugILFrame`介面和 ICorDebugNativeFrame 介面。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
