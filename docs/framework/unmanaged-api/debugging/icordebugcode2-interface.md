---
title: ICorDebugCode2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dce3e3e4baeaa351c5ed1d9e5ca2c03631c3fce4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750107"
---
# <a name="icordebugcode2-interface"></a>ICorDebugCode2 介面

提供擴充功能的 「 ICorDebugCode"的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCodeChunks 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|取得這個程式碼物件組成的程式碼區塊。|  
|[GetCompilerFlags 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|取得指定所在這個程式碼物件是其中一個在 just-in-time (JIT) 編譯，或使用原生映像產生器 (Ngen.exe) 所產生之條件的旗標。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugCode3 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
